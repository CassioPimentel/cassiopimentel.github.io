---
title: "Ionic 3 - Verificar conexão a internet"
date: "2018-05-22"
description: "Neste post irei mostrar como detectar se o Aparelho está conectado a Internet."

---

Neste post irei mostrar como detectar se o Aparelho está conectado a Internet, seja 3G, 4G ou Wifi.

![enter image description here](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/networking/wifi1.png)

# Instalação do plugin

Com o projeto criado, execute os comandos abaixo:

 - ionic cordova plugin add cordova-plugin-network-information
 - npm install --save @ionic-native/network

## Adicionar o plugin como provider

Após instalado, devemos adicionar o plugin Network como provider no AppModule:

  ```ts
  import { Network } from  '@ionic-native/network';
    
  @NgModule({
    
  providers: [ Network ]
  })
   
  export class AppModule {}
```

## Teste

Irei utilizar um exemplo simples de um App com uma page chamada Home. Primeiro devemos importar o plugin na nossa page:

```ts
 import { Component } from  '@angular/core';
 import { NavController } from  'ionic-angular';
 import { Network } from  '@ionic-native/network';
    
 @Component({
   selector:  'page-home',
   templateUrl:  'home.html'
 })
 export  class  HomePage {

 constructor(public  navCtrl:  NavController,
             public  network:  Network) {
 }
```

Com isto, podemos usar o plugin Network. A conexão será verificada no evento de pagina *ionViewDidEnter()* evento que é disparado depois que a Page está ativa, veja mais sobre eventos de pagina [aqui](https://ionicframework.com/docs/api/navigation/NavController/#lifecycle-events).  Neste exemplo iremos verificar apenas se o aparelho está desconectado. Para isto basta adicionar o codigo abaixo no evento ionViewDidEnter():

```ts
 ionViewDidEnter(){
  this.network.onDisconnect().subscribe(data  => {
   console.log(data);
  }, error  =>  console.log(error));
 }
```

onDisconnect() retorna um Observable (emite notificações sempre que ocorre uma mudança em um de seus itens e a partir disso podemos executar uma ação, mais informações [aqui](https://tableless.com.br/entendendo-rxjs-observable-com-angular/)). Aqui você pode melhorar seu app usando notificações Toast do Ionic, eu mostrei como fazer isto [neste](http://cassiopimentel.github.io/2018/Ionic3-Notifica%C3%A7%C3%B5es-com-Toast/) post.

## Demo

Abaixo você pode ver o app em funcionamento:

![enter image description here](https://github.com/CassioPimentel/cassiopimentel.github.io/blob/master/images/networking/testeNetworkIonic.gif?raw=true)

Para fazer o teste como eu fiz, basta executar o app com:
 - ionic serve 
 - e no google chrome apertar  Ctrl+shift+J.
 - e depois em toggle device toolbar(simbolo de um celular) ou   
   Ctrl+shift+J, e escolher o device que quiser.
 - E depois na barra acima do device virtual ir em offline, para simular a desconexão da internet do aparelho.

**Código fonte**: https://github.com/CassioPimentel/NetworkPluginIonic3
