---
title: "Ionic 3 - Abrir pagina web em aplicativo ionic"
date: "2018-05-17"
description: "Neste post ire mostrar como abrir paginas web dentro do seu aplicativo Ionic."

---

Neste post ire mostrar como abrir paginas web dentro do seu aplicativo Ionic.

## instalação

Irei levar em consideração que você já tenha criado um projeto ionic, se nunca fez isto, [este](https://ionicframework.com/docs/intro/installation/) tutorial oficial do Ionic irá te ajudar.
Com o projeto criado, basta instalar o plugin nativo inappbrowser:

 - ionic cordova plugin add cordova-plugin-inappbrowser 
 - npm install  --save @ionic-native/in-app-browser

## Teste

O uso do plugin é bem simples, primeiramente, no page que você quer abrir o site, basta adicionar o import do plugin:

```ts
import { InAppBrowser } from '@ionic-native/in-app-browser';
```

Depois adicione o InAppBrowser nos providers do page:

```ts
@Component({
	selector:  'your-page',
	templateUrl:  'your-page.html',
	providers: [ InAppBrowse ]
})
```

e após isto, crie uma variavel no construtor do page:

```ts
constructor(private iab: InAppBrowser) { }
```

e para abrir o site, basta adicionar a linha abaixo, por exemplo, após o clique de um botão:

```ts
const browser = this.iab.create('https://ionicframework.com/');
```

Clique [aqui](https://ionicframework.com/docs/native/in-app-browser/) para acessar a documentação do plugin.
