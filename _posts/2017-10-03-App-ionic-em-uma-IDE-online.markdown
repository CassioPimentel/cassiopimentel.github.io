---
title: "App ionic em uma IDE online"
date: "2017-10-03"
description: "Como execultar um App com ionic em uma IDE totalmente online"

---

Neste post irei mostrar como executar um App em ionic usando uma IDE totalmente online.

####  **IDE usada**


A IDE usada neste post será o  [Cloud 9](https://c9.io/) , que é uma ide totalmente online, onde se pode criar "Workspaces" gratuitos, que são maquinas virtuais que já vem com 512 de memoria ram e 2G de HD.

A cloud 9 ja tem alguns templates prontos, que ajuda muita na configuração dos projetos:

![](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/PrtScr%20capture.jpg)


Há também a possibilidade de se criar um workspace a partir de um repositório seu do github, o que é otimo para projetos onde outras pessoas estão trabalhando.

[Aqui](https://docs.c9.io/docs/) tem mais informações sobre o cloud 9.

####  **Criando o Workspace e Instalando o Ionic**

A criação do projeto no cloud 9 é bem simples, após logar, basta criar uma nova workspace, dar um titulo para o mesmo e escolher o templete, que no nosso caso será um templete Node JS, que é um pre requisito do ionic. O cloud 9 cria toda a estrutura Node Js para você, inclusive com alguns módulos já instalados.

Após o workspace ser criado, basta ir no console e instalar o ionic:

```sh
npm install -g cordova ionic
```


####  **Criando o projeto Ionic**

Após a instalação ser concluida iremos criar um projeto ionic de exemplo:

```sh
ionic start myApp sidemenu
```

Com o projeto criado podemos testa-lo. Para usar o ionic no cloud 9 iremos usar alguns parâmetros ao executar o app: 

```sh
ionic serve -p $PORT --nolivereload
```   

 - **$PORT:**  esta é uma variavel de ambiente do cloud 9, esta porta
   atualmente é a 8080.
 - **nolivereload:** este é um parâmetro do ionic que diz que o app não será
   automaticamente recarregado quando algo for alterado no código (isto é uma limitação do cloud9). 

####  **Testando o app**

Quando o comando terminar de ser execultado, você deve ir na barra superior da ide, em Preview->Preview Running Application, ira abrir uma aba, que é um navegador embutido dentro do cloud 9.

![](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/PrtScr%20capture_2.jpg)

Por ser uma ide online, a execução do projeto é um pouco mais demorada, mas nada que atrapalhe. Se quiser, você pode pegar o endereço do projeto e abri-lo em uma nova aba do seu navegador normalmente.
