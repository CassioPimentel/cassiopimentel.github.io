---
title: "Testando App ionic diretamento no VS Code"
date: "2018-02-25"
description: "Aprenda a testar um app feito em ionic diretamente no Visual studio Code."

---

Neste post irei mostrar como testar um app feito em ionic diretamente no Visual studio Code, não sendo necessário ficar utilizando ALT+TAB.

![](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/pluginPreviewVSCodeIonic/ionic.jpeg)

# O que será usado

 - Visual Studio Code
 - Plugin Ionic Preview for VS Code

## Instalando

*Obs:* Estou levando em consideração que você já tenha o Visual Studio Code instalado e configurado e que tenha um projeto ionic criado para teste.

Com o VS Code aberto você deve ir na barra lateral esquerda e ir em Extensions(Ctrl+Shift+X) e pesquisar por:

```cs
ionic preview
```

e instalar o primeiro pacote. Há outros plugins com o mesmo nome, caso tenha duvidas basta instalar o que tenha a maior quantidade de instalações.

![](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/pluginPreviewVSCodeIonic/install%20plugin.jpg)

## Configurando o Plugin

Este plugin no VS Code necessita de uma pequena configuração. basta ir em Settings e em USER SETTINGS, mudar o valor de ionic-preview.host para:

```cs
"0.0.0.0"
```
    
[Mais informações](https://github.com/jadsonbr/ionic-preview/issues/4)

![](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/pluginPreviewVSCodeIonic/config%20preview.jpg)

## Teste

Com o VS Code aberto com o seu projeto ionic, basta rodar a aplicação usando o comando abaixo:

```cs
ionic serve --adress 127.0.0.1
 ```      
    
E depois ir em View->Command Palette e digitar ionic preview, que ira mostrar as opções para você:

![](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/pluginPreviewVSCodeIonic/executa%20preview.jpg)

Bem simples, assim você não precisa ficar mudando de tela enquanto programa, pois o app será executado em uma aba do VS Code.

![](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/pluginPreviewVSCodeIonic/visualizar%20preview.jpg)


Espero que tenham gostado.
