---
title: "Ionic 3 - Suporte a vibração"
date: "2018-05-25"
description: "Neste post irei mostrar como adicionar vibração ao seu App."

---

Neste post irei mostrar como adicionar vibração ao seu App, algo não muito usual nós aplicavos de hoje, mas que talvez possa ser usado
em algum caso específico.

![](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/pluginPreviewVSCodeIonic/ionic.jpeg)

# Instalação

Com o projeto criado, basta instalar o plugin Vibration:

 - ionic cordova plugin add cordova-plugin-vibration
 - npm install --save @ionic-native/vibration


## Preparação do projeto

Primeiro adicione o plugin ao **app.module.ts**:

```ts
...
import { Vibration } from  '@ionic-native/vibration';
    
@NgModule({
...
providers: [
    ...
    Vibration
]
})
    
export  class  AppModule {}
```

Depois e só começar a usar. Para efeito de exemplo, irei colocar o celular para vibrar quando um botão for clicado. Usarei um Page chamado home.

**home.html**

```html
<ion-header>
    <ion-navbar>
        <ion-title>
    	    Ionic Vibração
    	 </ion-title>
    </ion-navbar>
</ion-header>
    
<ion-content  padding>
    <button  ion-button (click)="Vibre()">Vibre</button>
</ion-content>
```

**home.ts**

```ts
import { Component } from  '@angular/core';
import { NavController } from  'ionic-angular';
import { Vibration } from  '@ionic-native/vibration';
    
@Component({
    selector:  'page-home',
    templateUrl:  'home.html'
})
    
export  class  HomePage {
    
    constructor(public  navCtrl:  NavController, private  vibracao:  Vibration) {}
    
    Vibre(){
       this.vibracao.vibrate(1000);
     }
}
```

O código é bem simples, no click do botão, o celular ira vibrar por 1 segundo.

**vibrate**: a função vibrate recebe como parâmetro um valor *number ou Array.<number*> em milissegundos.

**Documentação**: https://ionicframework.com/docs/native/vibration/ e
https://github.com/apache/cordova-plugin-vibration

**Código**:  https://github.com/CassioPimentel/IonicVibration
