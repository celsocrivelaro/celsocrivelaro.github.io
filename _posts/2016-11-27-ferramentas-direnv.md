---
layout: post
title: "Direnv para Variáveis de Ambiente e PATH"
categories: [tools]
tags: [tools]
date: 2016-11-27 21:11:36 -0300
author: Celso Crivelaro
---

Direnv é uma ferramenta tão útil que fiquei impressionado em ter descoberto agora. O seu objetivo é a gestão de variáveis de ambiente por diretório e a gestão da variável de ambiente PATH.

De acordo com o [The Twelve-Factor App](https://12factor.net/pt_br/config), é uma  boa prática que as configurações estejam como  variáveis de ambiente. Alguns frameworks permitem que suas configurações sejam divididas por ambiente como o Rails e Phoenix, mas isso não é geral, especialmente para frameworks simples como PyBottle ou se usa bash scripts.

Como prefiro ferramentas agnósticas (que não seja ligado apenas à uma linguagem ou framework), o Direnv entra como uma ótima opção da configuração de ambiente de desenvolvimento.

No Mac, a sua instalação é simples:

{% highlight bash %}
$ brew install direnv 
{% endhighlight %}

O mesmo no Ubuntu/Debian:

{% highlight bash %}
$ sudo apt-get install direnv 
{% endhighlight %}

Depois disto, precisa adicionar a inicialização na configuração do Bash. Se usa Bash tradicional, só adicionar no ~/.bashrc

{% highlight bash %}
$ eval "$(direnv hook bash)"
{% endhighlight %}

Para outros bashes como Zsh, Fish, veja a documentação: [http://direnv.net/](http://direnv.net/)

## Variáveis de Ambiente

Basta criar um arquivo .envrc no diretório em que está o projeto com o conteúdo:

{% highlight bash %}
  FOO=value
{% endhighlight %}

Ao entrar e sair do diretório:

{% highlight bash %}
╭─crivelaro@me:~/
╰─λ cd project/
direnv: loading .envrc
direnv: export +FOO
╭─crivelaro@me:~/me
╰─λ cd ..
direnv: unloading
{% endhighlight %}

Assim, a variável de ambiente só fica disponível quando entro no diretório e dessa maneira posso usar a mesma variável para cada tipo de projeto o que é uma prática comum quando se usa projetos parecidos.

## Adicionando diretórios ao PATH

Essa é a funcionalidade que mais gosto do Direnv. Quando monto alguns projetos com um diretório **bin** com alguns shell scripts, acho terrível ter que digitar algo como:

{% highlight bash %}
$ ./meu_script
$ bin/meu_script
{% endhighlight %}

No Linux ou Mac, um binário é chamado de acordo com os diretórios mapeados na variável de ambiente $PATH. O direnv pode configurar o PATH para que se tenha a configuração apenas para aquele projeto.

Para isso, mapeio o PATH para incluir a pasta de binários do projeto dentro do arquivo .envrc:

{% highlight bash %}
PATH_add ./bin
{% endhighlight %}

Pronto! Agora qualquer script executável pode ser chamado diretamente como qualquer software no Linux/Mac. 

Quando saio do diretório, os binários não estão mais disponíveis pois o PATH voltou ao original.

