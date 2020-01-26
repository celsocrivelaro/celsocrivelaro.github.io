---
layout: post
title: Se é possível fazer, é possível testar 
categories: [testing]
tags: [testing]
date: 2017-11-28 09:00:36 -0200
author: Celso Crivelaro
description: Principais pontos para desenvolver uma mentalidade do uso testes e como eles podem melhorar a qualidade do software e do processo de engenharia do seu time.
---

É um mantra que sempre aplico aos meus projetos e passo às pessoas com quem eu trabalho. 

Já fui contra testes no início da carreira, já resisti muito ao TDD e depois de muito código problemático, aprendi o valor dos testes. Mas mais importante do que simplesmente testar, é como fazer os testes terem valor no projeto.

Aqui neste post quero por alguns pontos que considero importante para a mentalidade de testes e como elas afetam o projeto e o time.

## Planejamento do teste

Não só só usar os testes para o TDD como metodologia de desenvolvimento, mas também usa-los para o levantamento de requisitos. Assim, sempre que uma funcionalidade é especificada, os testes ajudam a levantar detalhes funcionais:

* Que tipo de usuário pode executar esta ação?
* Qual a entrada e resultado esperado em um caso comum?
* Quais entradas fazem fluxos diferentes?
* Quais são os casos de falha?
* Quais são os pré-requisitos do sistema para fazer o teste?
* Preciso de alguma ferramenta ou adaptação para o teste?

Para o desenvolvedor, o teste automatizado é o artefato mais interessante e para o dono do produto, o plano de testes e aceitação em um planilha de Excel pode ser um guia de testes e os critérios de aceitação.

Então o objetivo é mais profundo: Só no ato de planejar o teste, já ocorre a especificação funcional e detalhes de implementação. Se os testes funcionais estão planejados, o desenvolvedor terá um critério de parada, sabendo o limite de desenvolvimento da tarefa e o cliente já terá um plano para verificar o software.

Nos passos seguintes do processo de Engenharia de Software que é a Especificação Técnica e o Desenvolvimento, um problema comum enfrentado em um software complexo é como testar condições difíceis. Exemplos:

* Dependência de integrações, integração que pode ter estado
* Simular condições que não é possível em um ambiente de testes como condições de rede
* Simular ataques ou mesmo carga de usuários

Ao planejar o teste, podemos ter que ser criativos em como testar uma condição que não é trivial e demonstrável com apenas o código de produção. Assim, se torna necessário o desenvolvimento de scripts e simuladores que auxiliem os testes.

***Resumo:***

* Planejar o teste
* Tirar artefatos como Plano de Testes, Especificação Funcional
* Ter um critério de parada de desenvolvimento com as condições de aceite
* Criar métodos e ferramentas que auxiliem o teste

## Estimar o tempo gasto nos testes junto com as tarefas

Assim como não existe almoço grátis, também não existe teste grátis. Sim, se no seu processo de engenharia os testes e a qualidade são valores fortes, precisam entrar na conta do projeto. Um erro clássico de desenvolvedores é não incluir os tempo que gasta nos testes em suas estimativas.

Por exemplo: uma mudança de regra de negócio pontual que demore tudo 2 horas mas o teste precise ser feito em 6 horas pelas pré-condições e casos de uso. Logo, o tempo total para fazer a mudança é de 8 horas e não 2 horas como é comum de ser estimado.

Quando isso acontece demostra que a funcionalidade é crítica, a montagem da situação do teste é complexa ou mesmo construção a infraestrutura prévia de testes é pequena. Neste momento, vale a pena por na conta da tarefa o planejamento de todo o teste e tê-lo para sempre, podendo ser replicado por outras pessoas conforme a necessidade.

**Resumo:**

* Considerar o tempo de testar a funcionalidade manualmente;
* Considerar o tempo de fazer teste automatizado.

## Tarefa é só considerada pronta se o teste foi feito

Já ouvi muitas vezes: "Está pronto, só falta testar”. Ou seja, não se tem ideia nenhuma se o código funciona, quase um problema de “Gato de Schrödinger”. Na minha opinião o trabalho ainda está na metade.

Em Pull Requests, só de baixar o código e rodar na minha máquina, já vi a funcionalidade desenvolvida não funcionando em nenhum caso. Ou seja, faltou o simples teste manual da funcionalidade e se fosse entregue ao cliente, obviamente não ia funcionar.

Se o time já tem o hábito de fazer testes e TDD ótimo. Outro mal hábito que surge frequentemente, é o desenvolvedor fazer mudanças rápidas e confiar apenas na suíte de testes automatizados (já fiz este erro várias vezes). Quando vai para o teste manual, quebra.

Não deixe este problema ser descoberto depois do ciclo de desenvolvimento, isso geralmente gera estresse na equipe e um mal estar com o cliente.

**Resumo:**

* Testes automatizados feitos;
* Testes manuais executados pelo desenvolvedor.

## Teste também é código e precisa de uma boa arquitetura

Já vi em muitos casos o código principal ter uma preocupação grande com arquitetura, estilo e boas práticas e por outro lado, o código do teste ser mal feito, difícil de entender e difícil de modificar.

O código dos testes automatizados deve-se ter o mesmo carinho do código de produção, especialmente porque o código de teste é um código não-testável (afinal, queremos evitar o loops infinitos).

Boas práticas como AAA (http://wiki.c2.com/?ArrangeActAssert) e padrões de projeto como Page Objects (https://martinfowler.com/bliki/PageObject.html), ajudam o código de teste ser compreensível, ser extensíveis e terem responsabilidades bem definidas.

**Resumo:**

* Código do teste bem feito reflete em um código de produção bem feito;
* Código de teste tem bons padrões do framework e estruturais.

## E quando assumir o risco de não testar?

O custo de fazer teste ser muito caro é um fator importante a se considerar. Se a ordem de grandeza de um teste é 10 vezes a da funcionalidade, é de se questionar se a automatização vale pena. Isso é bem comum para testes complexos como Teste de Carga que precisa de uma grande infraestrutura e planejamento. Alternativas é sempre o teste manual ou verificação de comportamento em produção mesmo.

Outro caso comum são correções de falhas emergenciais. Neste caso, deve-se sim testar manualmente a funcionalidade problemática e subir a correção o mais rápido possível. Geralmente uso a automatização e corrijo se o teste quebra, mas evito fazer alguma modificação substancial que pode ser feita após a situação se normalizar.

Prazo de projeto em que vc não participou já passou. Este caso deve ser evitado ao máximo, mas infelizmente pegamos projetos com prazos que não foram estimados por nós. Neste caso, o ideal é tentar negociar o prazo para incluir os testes ou diminuir o escopo da funcionalidade. Sempre é melhor entregar menos com mais qualidade. Porém, quando não é possível, deve-se focar nos testes automatizados mais simples e nos testes manuais.

**Resumo:**

* Não testar quando o custo do teste é proibitivo;
* Reduzir a quantidade para testes em correções emergenciais;
* Focar nos testes simples e manuais quando  prazo do projeto não permite testes com qualidade.
