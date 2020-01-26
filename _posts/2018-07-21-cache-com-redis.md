---
layout: post
title: Cache com Redis 
categories: [redis]
tags: [redis, cache]
date: 2018-07-21 09:00:36 -0200
author: Celso Crivelaro
description: O que considerar e técnica para cache usando Redis 
---

Sendo um banco de dados especializado em memória, o Redis fornece um conjunto de comandos que suportam caching de dados. Neste post mostro a importância de ser ter um cache e alguns pontos a se considerar para montar o cache de dados e como podemos fazer isso usando Redis.

A vantagme de se usar banco em memória está em ser agnóstico à aplicação, ou seja, posso usar uma app em Python, Ruby, C, Elixir, ou mesmo um conjunto de aplicações e não precisar reinventar a roda.

## Para que se usar cache?

- **Dados caros de se produzir**: Dados complexos oriundos processamento intenso, cálculos ou modelos de inteligência artificial;
- **Dados caros para se buscar**: Dados buscados de APIs externas, cruzamentos de dados de fontes distintas ou fontes de dados lentas.
- **Quando uma memória é mais veloz do que a outra**: No caso como o Redis fornece estrutura de dados em memória, tende a ser mais veloz salva e buscar do que na rede ou de diversos JOINs do banco de dados;
- **Aliviar a carga sobre um recurso**: Quando uma API ou mesmo o banco de dados é bombardeado de buscas repetidas, uma boa prática é usar um cache para evitar sobrecarga nos sistemas principais, o que aumenta a disponibilidade da plataforma. 

## Casos de uso para cache

- Dados de Sessão
- Últimas páginas visitadas
- Dados de uma busca de APIs
- Assets como JS e CSS
- Imagens e Vídeos

## O que precisamos considerar para um cache?

- Dado precisa ser buscável
  - Graceful degradation: Não pode explodir erros se a chave estiver indisponível
  - ID único

- Cache precisa morrer
  - A administração do cache precisa ser feita por fora da app
  - O cache precisa ser invalidado quando houver dados novos
  - Necessário determinar um tempo de vida

- Tolerância de consistência
  - Deve ser aceito um dado inválido por alguns instantes

## Criando um par cacheável usando Redis

Qualquer estrutura de dados criada do Redis serve como cache, já que será armazenada na memória. Assim, um simples comando SET armazena e um GET irá retorná-lo:

{% highlight bash %}
192.168.99.101:32768> SET cached_data 123
OK
192.168.99.101:32768> GET cached_data
"123"
{% endhighlight%}

Como fazer o dado ser expirável? Usando um SETEX

{% highlight bash %}
192.168.99.101:32768> SETEX cached_data 10 123
OK
192.168.99.101:32768> TTL cached_data
(integer) 9
{% endhighlight%}

Neste comando o valor '10' é o tempo em segundos em que este dado estará disponível, logo depois de 10s o GET retorna nulo:

{% highlight bash %}
192.168.99.101:32768> SETEX cached_data 10 123
OK
192.168.99.101:32768> GET cached_data
"123"
192.168.99.101:32768> GET cached_data
(nil)
{% endhighlight%}

Porém, se queremos usar outras estruturas de dados do Redis, o comando que deixa os dados invalidados será o EXPIRE. No exemplo abaixo, crio uma lista com 4 elementos e depois de expirada em 5s, a lista retorna tamanho vazio:

{% highlight bash %}
192.168.99.101:32768> LPUSH cached_list 1 2 3 4
(integer) 4
192.168.99.101:32768> LLEN cached_list
(integer) 4
192.168.99.101:32768> EXPIRE cached_list 5
(integer) 1
192.168.99.101:32768> LLEN cached_list
(integer) 0
{% endhighlight%}

Recomenda-se o uso do MULTI para inserir os dados e setar o cache de forma atômica.

O ponto fraco de usar outras estruturas de dados está em que o cache é cancelado quando a estrutura é alterada. Podemos checar quanto tempo de vida a estrutura de dados tem com o comando TTL que retorna os segundos restantes:

{% highlight bash %}
192.168.99.101:32768> LPUSH cached_list 1 2 3 4
(integer) 4
192.168.99.101:32768> EXPIRE cached_list 10
(integer) 1
192.168.99.101:32768> LPUSH cached_list 5
(integer) 5
192.168.99.101:32768> TTL cached_list
(integer) 0
{% endhighlight%}

## Expirando chaves de forma manual

Outra propriedade importante é invalidar o cache de forma manual. A sua aplicação pode necessitar fazer isso se a fonte original foi modificada ou se o cache pode conter uma inconsistência importante. Para isso podemos usar o comando UNLINK:

{% highlight bash %}
192.168.99.101:32768> SETEX cached_data 10 123
OK
192.168.99.101:32768> UNLINK cached_data
(integer) 1
192.168.99.101:32768> TTL cached_data
(integer) -2
192.168.99.101:32768> GET cached_data
(nil)
{% endhighlight%}

Este comando é similar ao DEL, porém, o UNLINK é feito em outra thread, ou seja, não fica bloqueado esperando a execução do comando.

## Referências
- [SETEX](https://redis.io/commands/setex)
- [EXPIRE](https://redis.io/commands/expire)
- [UNLINK](https://redis.io/commands/unlink)
- [TTL](https://redis.io/commands/ttl)
