---
layout: post
title: Importando Discos Virtuais no VirtualBox 
categories: [programming]
tags: [vm]
date: 2016-09-07 10:10:36 -0300
author: Celso Crivelaro
---

Recentemente precisei exportar uma VM do Virtualbox para o Hyper-V da Microsoft para ambientes Windows. Infelizmente a única forma encontrada foi de exportar do disco da VM para o formato .vhd que era lido pelo Hyper-V.

Agora preciso fazer o caminho inverso: usar este disco virtual para uma nova VM no Virtualbox. Seguem os passos de como foi feita esta tarefa:

# Passo 1: Criar uma nova VM

Como vamos importar apenas o disco, precisamos criar uma nova virtual machine. Para isso, basta clicar em Novo.

![Criando uma máquina virtual](/images/virtualbox1.png)

# Passo 2: Selecionar o disco

Neste segundo passo, deve-se nomear a máquina virtual, escolher o tipo e o tamanho da memória.

Na seção de "Disco Rígido" o padrão é "Criar um novo disco rígido virtual agora". Como vamos importar este disco rígido, selecione a opção "Utilizar um disco rígido existente" e selecione o arquivo do disco na pasta lateral.

![Selecionando o disco](/images/virtualbox2.png)

Clique em "Criar".

# Passo 3: Inicie a máquina Virtual

A máquina irá ser criada. Para inicializá-la, selecione a VM clique em "Iniciar"

![Inicializando a VM](/images/virtualbox3.png)

Virtualbox pode ser baixado em [VirtualBox][virtualbox]

[virtualbox]: https://www.virtualbox.org/ 
