---
layout: post
title: "Como se prepara a chegada de novos desenvolvedores"
categories: [team]
tags: [docker, vagrant, career]
date: 2016-12-27 18:11:36 -0200
author: Celso Crivelaro
---

Sempre é uma novidade a troca de um emprego para o desenvolvedor de software: aprender sobre o negócio da empresa, sobre as linguagens/frameworks/tecnologias da empresa e finalmente sobre o processo.

Infelizmente há um paradoxo com o tratamento do novo funcionário: o querem o mais rápido possível na equipe e quando este chega, nada está preparado. E no primeiro momento surgem dores no novo funcionário e na sua equipe:

* Desconhecimento da tecnologia (linguagem, frameworks);
* Desconhecimento da instalação dos projetos (passar dias instalando tudo);
* Desconhecimento dos processos; 
* Ainda não tem máquina disponível;
* Não consegue ter acesso a nenhum sistema interno;
* A quem se deve perguntar sobre o projeto?
* A equipe sofre paradas para ajudar no novo dev;

Outro ponto que quero sensibilizar é a primeira impressão de quem chega: Como vai exigir qualidade, empenho e motivação de um funcionário, se no seu primeiro dia a empresa não estava preparada a sua vinda?

> "Você nunca tem uma segunda chance de causar uma primeira impressão" (Aaron Burns)

Se um dev escolheu sair da sua zona de conforto para ir para a sua empresa, é porque ele está interessado em aprender coisas novas, estar em um projeto novo e **quer produzir rapidamente**. Ninguém muda de emprego para ficar lendo documentação, ficar instalando o ambiente ou ficar vendo código sem saber o que faz.

O ideal é reduzir este tempo que pode demorar até 3 meses para o mínimo possível. Como podemos fazer? 

## Para quem não é este post e o que não é este post

Este é um post para devs e seus coordenadores e não para gerentões ou profissionais de RH. Minha intenção aqui é dar dicas de preparação aos devs e ao time para a chegada de um novo par. Este post não é sobre como empresas devem contratar ou selecionar o seu desenvolvedor.

No lado pessoal, este post não é um dedo na cara dos lugares onde passei, apesar de ter visto esta situação por onde passei. O que quero dividir as experiências que deram certo e as experiências ruins que passei e vi com pares.

## Antes da chegada do novo funcionário

### Dê um computador deste o primeiro dia

Acho que quase em todas as empresas que passei o primeiro dia não tive um computador. Isso porque:

* O gestor esqueceu completamente o dia de entrada;
* O processo da empresa é burocrático para nova máquina para novo funcionário.

> Não existe coisa mais desmotivante do que não ter o que fazer, ainda mais em um lugar novo.

Poxa, se você contratou um dev, dê um computador (e bom) deste o primeiro momento da empresa. Daí ele pode preparar o ambiente conforme as necessidades.

### Ter acessos e senhas  

Também não adianta dar um computador se o funcionário não tem acesso a nenhum sistema interno e a base de código. Isso acontece também pelos mesmos motivos do computador no primeiro dia.

Monte uma lista de quais acessos os seu dev precisar para executar as principais funções desde o primeiro dia e garanta que os principais acessos estão garantidos.

Outro ponto importante: se sua empresa precisa de crachá para entrar, forneça o mais rápido possível. É péssimo sempre ter que pedir para alguém para abrir a porta e desconcentra quem está trabalhando.

## Primeira semana 

### Explique o que a empresa faz e a importância do projeto

Esta é uma atividade mais interessante para os coordenadores que têm visão macro. Já vi muito dev entrando em projeto que nem sabe para que serve dentro do propósito da empresa ou mesmo sabe pouco das regras de negócio.

Uma visão geral do projeto e da empresa ajuda a quem estar de fora a saber os pontos chaves que não foram explicados no processo seletivo. 

Números de negócio, pontos fortes e pontos a melhorar dão uma visão dos desafios pela frente.

### Coach com o novo dev

Um fato que vi que gera uma certa angústia aos novatos, é para quem perguntar e se está atrapalhando o time. Já vi situações em que as pessoas evitam de ajudar o novato pois estão empenhadas nas entregas. Isso gera um desconforto e falta de confiança para quem está chegando e ao mesmo tempo atrasa o seu desenvolvimento dentro da equipe.

Uma experiência muito legal que participei é ter um dev mais experiente alocado exclusivamente para os primeiros dias desta pessoa. Esta pessoa era responsável por explicar o projeto, ajudar na instalação do ambiente de desenvolvimento, explicar uma base da linguagem/frameworks usados, enfim, irá ambientar o dev novo ao time.

Esse dev experiente não deve estar comprometido com as entregas naquele momento para que não fique preocupado com outros fatores além de ambientar o novo dev. 

### Fazer deploy de aplicação NO PRIMEIRO DIA

Ao contratar um dev, o seu objetivo é entregar mais software, não apenas fazer. Ou seja, software vale mesmo quando está em produção.

Então, faça o seu novo dev por software em produção deste o primeiro dia! Mesmo que seja uma alteração no Readme do projeto.

Ao fazer isso, ele conhecerá o processo de ponta-a-ponto e perderá o medo de fazer o deploy da aplicação. Quanto mais cedo este dev entregar, mais produtivo ele é.

### Kit boas-vindas

Se sua empresa dispõe de souvenirs como camisetas, caneca, canetas ou cadernos, já deixei tudo na mesma no primeiro dia. Faça-o vestir a camisa literalmente desde o primeiro dia. 

![Kit boas vindas da 360i](/images/360i_welcome_kit.jpg)

Kit boas vindas da i360. Fonte: [Digiday](http://digiday.com/agencies/best-agency-employee-welcome-kits-2/)

Pode parece bobagem, mas kit boas-vindas tem sex appeal, o novo empregado vai compartilhar nas redes sociais e a sua empresa se torna atrativa.

## Processos e Documentação

Aqui também entra em atividades antes da contração, mas que ajuda o time todo em geral na troca de informações sobre o projeto.

* **Start Guide**: O que é e como funciona o projeto;
* **Como instalar o projeto**: Aqui é a pior parte. Ao tentar instalar o projeto de forma normal, o dev irá falhar miseravelmente, pois sempre tem um macetinho que não estava documentado. Logo documente:
  * Versão das dependências: Ruby 2.1.0
  * Configurações: O que mudar nos arquivos de configuração
  * Dependências: Ruby, Python, Banco de Dados, Servidor de File
  * Decisões arquiteturais: Porque usamos microserviços neste caso...

### Automatização de ambiente de dev

Outra decisão muito interessante é automatizar a instalação do ambiente de desenvolvimento. Assim, todos os devs mantém um mesmo ambiente padronizado e é só rodar um script para se ter tudo funcionando.

Algumas opções para Linux / Mac:

* Docker
* Vagrant 
* Shell Scripts

Afinal, ser dev é automatizar as coisas, então por que não automatizar o próprio ambiente?

Mesmo eu já sendo um veterano na empresa, esta automatização já me salvou a vida vários vezes depois de updates desastrados e trocas de máquinas. Só destruir e construir tudo de novo!

