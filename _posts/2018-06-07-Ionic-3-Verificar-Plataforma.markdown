---
title: "Ionic 3 - Verificar Plataforma"
date: "2018-06-07"
description: "Neste post iremos mostrar como verificar a plataforma que o usuário esta usando, seja IOS, Android ou o próprio navegador, 
se esta utilizando um tablet e a orientação do dispositivo."

---

Neste post iremos mostrar como verificar a plataforma que o usuário esta usando, seja IOS, Android ou o próprio navegador, 
se esta utilizando um tablet e a orientação do dispositivo.

![](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/pluginPreviewVSCodeIonic/ionic.jpeg)

# Utilização

Para utilizar o serviço, basta incluir a referencia do mesmo na page ou service onde deseja utiliza-lo:

```ts
    ...
import { Platform } from  'ionic-angular';

@Component({
    selector:  'page-home',
    templateUrl:  'home.html'
})
export  class  HomePage {

constructor(public  navCtrl:  NavController,
public  plt:  Platform) {

    if (this.plt.is('android')) {
    }
}

}
```

Onde ```ts this.plt.is``` é onde verifico a plataforma. Abaixo há a lista de plataformas aceitas:

 - android
 - cordova 
 - core: desktop device
 - ios
 - ipad 
 - iphone 
 - mobile 
 - mobileweb 
 - phablet 
 - tablet 
 - windows

Com o plugin platform você também pode verificar se o aparelho esta em modo paisagem ou não:

```ts
this.pltis.isLandscape();
```

ou se esta em modo retrato:

```ts
this.pltis.isPortrait();
```

Estes são os usos mais frequentes do plugin, caso queira saber mais basta acessar este [link](https://ionicframework.com/docs/api/platform/Platform/).
