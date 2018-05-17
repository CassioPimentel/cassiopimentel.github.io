---
title: "Ionic 3 - Notificações com Toast"
date: "2018-05-15"
description: "Neste post rápido, iremos implementar o Toast, que é uma pequena notificação usada em aplicações modernas, seja mobile ou web."

---

Neste post rápido, iremos implementar o Toast, que é uma pequena notificação usada em aplicações modernas, seja mobile ou web.

![](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/NotificacaoToast/Toast.jpg)

**Uso**

Primeiro devemos importar o ToastController:

```javascript
    import { ToastController } from 'ionic-angular';
```

Apos isto crie uma variavel no Construtor da sua page:

```javascript
    constructor(private toast: ToastController){ }
```

Agora para usar, basta adicionar a linha abaixo para que a mensagem seja apresentada:

```javascript
this.toast.create({ message: 'Teste', duration: 3000, position: 'botton' }).present();
```

**message**: mensagem a ser exibida.&nbsp;
**duration**: duração em milissegundos que a mensagem fica na tela.&nbsp;
**position**: posição na tela. Valores aceitos: "top", "middle", "bottom".&nbsp;

Documentação: https://ionicframework.com/docs/api/components/toast/ToastController/

Caso queira testar seu app dentro do proprio Visual Studio Code por exemplo, [aqui](http://cassiopimentel.github.io/2018/Testando-app-ionic-diretamente-no-VSCode/) eu mostro como.
