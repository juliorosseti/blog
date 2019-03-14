---
title: 'Maneira correta/certa de instalar o Cygwin do Zero'
subtitle: 'Como fazer em poucos passos uma instalação rápida e fácil do Cygwin junto com os packages.'
cover: header.png
share_cover: header.png
published: true
date: '04-11-2017 00:46'
metadata:
    keywords: 'cygwin, terminal, windows'
taxonomy:
    category:
        - 'command line'
    tag:
        - cygwin
---

É de praxe pelo menos uma vêz no ano ter que refazer todo meu workspace para trabalhar com desenvolvimento. E um dos pontos que eu sempre acabava me batendo (e muito) era na instalação do CygWin, então resolvi criar esse artigo para as pessoas que possuem dificuldade ou sempre possuem problemas na instalação.

O que vamos aprender nesse tutorial:
* Instalação completa do Cygwin (easy).
* Instalação dos packages necessários de maneira produtiva.
* Solução de possíveis problemas com Authentication Agent.
* Links simbólicos.

## Instalação completa do Cygwin

Você não vai acreditar, _mãns_, a instalação do Cygwin que vou passar é basicamente baixar o instalador ([32bit](http://www.cygwin.com/setup-x86.exe)/[64bit](http://www.cygwin.com/setup-x86_64.exe)) e então _next,next,next,next,next,next,next,next_,**finish**. São 8 passos de "avançar" e é isso, vualá!
Mas vou explicar ponto por ponto, ok?
1. Introdução/Apresentação > Next;
2. **Install from internet** > Next;
3. Root Directory: ``c:/cygwin`` (ou) ``c:/cygwin64`` > **All users** > Next;
4. Local Package Directory: Você decide o local que ficará os packages que serão baixados, no meu caso ficou ``C:\Users\<USER>\Downloads`` > Next;
5. Select Internet Connection > **Direct Connection** > Next;
6. Avaible Download Sites (local para baixar os packages) > Escolha qualquer um, você é livre! Eu escolhi o primeiro "**http://cygwin.mirror.constant.com**" > Next;
7. Select Packages > Simplismente não mexa em nada > Next;
8. Resolving Dependencies > Lista das dependencias/Packages que vão ser baixados/instalados > Next;
9. Installation Complete > Finish.

## Instalação dos packages necessários de maneira produtiva.

Na minha visão o Cygwin possui uma aparencia confusa para instalação de packages, por esse motivo no início do tutorial de instalação solicitei que não fosse mexido em nada dessas telas pois vamos instalar os mesmos através da linha de comando (dentro do próprio cygwin). 
A instalação desses packages que vou mostrar, necessáriamente você precisa ter o instalador do Cygwin ainda no seu HD, pois será através dele que iremos realizar as instalações.

1. Abra o terminal do Cygwin e vá até a pasta onde o instalador está localizado, no meu caso ainda está em "Downloads", então irei até lá com o seguinte comando: ``cd /cygdrive/c/Users/<USER>/Downloads``;
2. Rode o seguinte comando: ``./INSTALADOR.exe -q -P package1,package2,package3,package4``. No meu caso, o instalador é 32bit eu instalei algumas dependencias que sempre utilizo, ficando dessa maneira: ``./setup-x86.exe -q -P curl,git,nano,unzip,util-linux,vim,wget``;
3. A interface de instalação do Cygwin vai abrir e basta aguardar o mesmo fazer o trabalho sozinho.
4. A partir daí você já consegue utilizar seus packages normalmente como git, nano ou wget! Fichinha né?

## Alguns possíveis problemas com Authentication Agent (ssh/git)

Caso você esteja tentando utilizar o git, vai perceber que ao tentar dar um push/pull ou até um git-add e o mesmo retornará um erro com a seguinte mensagem:
**Could not open a connection to your authentication agent**

Para resolver, vá até seu `~/.bash_profile` e adicione essa linha no final do mesmo:
<script src="https://gist.github.com/juliorosseti/322162629cd161ab9e13ad4a38094250.js"></script>
Após isso, reinicie seu cygwin OU dê um source no arquivo e estará funcionando normalmente.

## Links simbolicos

O Cygwin cria um link simbólico para acessar seus discos locais através do _/cygdrive/_, então para acessar qualquer local disco basta ir em _/cygdrive/c/_ OU _/cygdrive/d/_ OU _/cygdrive/e/_ e assim continua, vai que você tem umas 12 partições né, nunca se sabe.
Mas que tal ter uma produtividade ainda maior com seus próprios links simbólicos? Pensa ao invés de ir até sua pasta de downloads da forma natural, poder abreviar sua escrita, já pensou que louco? Ao invés de utilizar o caminho padrão `cd /cygdrive/c/Users/USER/Downloads` utilizar apenas `cd ~/Home/Downloads` ou `cd ~/Sites/` para sua pasta www|htdocs. É meu caro, você pode!
1. Vá até sua pasta home do Cygwin: `cd ~`;
2. E crie seu link simbólico: `ln -s /cygdrive/c/seu/destino/bacana ArquivoSimbolico`. 
3. No meu caso possuo dois, um para minha htdocs (do xampp) e outro para o home do meu usuário Windows.
3. * **htdocs**: `ln -s /cygdrive/c/xampp/htdocs Sites`
3. * **Desktop**: `ln -s /cygdrive/c/Users/<USER>/Desktop/ Desktop`
3. * **Downloads**: `ln -s /cygdrive/c/Users/<USER>/Downloads/ Downloads`
3. * **Documents**: `ln -s /cygdrive/c/Users/<USER>/Documents/ Documents`
4. Agora caso queira acessar seu desktop independente do lugar que esteja, é só escrever `cd ~/Desktop`.

## Finalização

Bom, se você chegou até aqui e ocorreu tudo certo, fico muito feliz por ter te ajudado! Fique a vontade para deixar suas possíveis dúvidas ou só comentar um simples "UHUUUUU ME AJUDOUUUUUUUU PACANÁRIO" :).

E vou ficando por aqui, cheers, câmbio desligo!