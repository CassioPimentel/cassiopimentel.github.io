---
title: "Ionic 3 - Como passar valores entre pages"
date: "2018-07-26"
description: "Neste post irei mostrar como passar valores entre pages, algo muito usado, e que vejo algumas pessoas com duvidas sobre isto.."

---

Neste post irei mostrar como passar valores entre pages, algo muito usado, e que vejo muitas pessoas com duvidas sobre isto.

![](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/pluginPreviewVSCodeIonic/ionic.jpeg)


# Inicio

Já tenho um projeto criado e irei gerar duas pages, chamado page1 e page2 para ficar mais fácil o entendimento.

# Passando os valores

Irei simular o envio de dados para outra page depois de um click em uma lista de times. No page1 eu criei uma lista com nomes de times e quando clicado o nome do time será enviado para a page2:

```ts 
   items  = [
   	'Flamengo',
   	'São Paulo',
   	'Gremio',
   ];
```

Este items ficará acima do construtor e será lido no **ngFor** no nosso frontend, abaixo

Nosso page1.html ficará assim:

```ts 
   <ion-content>
     <ion-list  inset>
     <button  ion-item *ngFor="let item of items" (click)="SelecionarItem(item)">
       {{ item }}
     </button>
   </ion-list>
   </ion-content>
```

E o SelecionarItem ficara assim:

```ts 
   SelecionarItem(item:  string) {
     this.navCtrl.push(Page2Page, {time:  item});
   }
```

Aqui passamos o time clicado para a page2.

# Pegando os valores

No page2 temos que criar uma variavel que ira receber o nome do time:

```ts
   time:  any;
```

E no construtor pegar o valor:

```ts
   this.time  =  navParams.get('time');
```

E mostrar o time:

```ts
   <ion-content  padding>
     <h2> **{{time}}** </h2>
   </ion-content>
```

# Demo

![](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/PassandoDadosEntrePages/girapp.gif)
