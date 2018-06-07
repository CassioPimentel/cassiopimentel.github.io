---
title: "Ionic 3 - Mudar browser default"
date: "2018-06-07"
description: "Neste post irei mostrar como mudar o browser padrão ao executar um app ionic."

---

Neste post irei mostrar como mudar o browser padrão ao executar um app ionic.

![](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/pluginPreviewVSCodeIonic/ionic.jpeg)

# Uso

Bem simples, para escolher outro browser ao executar o app, adicione:

```ts 
--browser "chrome"
```

apos o ionic serve;

e para mudar de ver o browser padrão, vá ate o arquivo ionic.project, na raiz do seu projeto e adicione a linha (se não houver):

```ts 
"defaultBrowser": "chrome"
```


**Observação**: este nome do browser pode estar diferente, baseado na versão do seu navegador, para ter certeza, vá no ícone do browser desejado e em propriedades e em destino verifique o **nome.exe**, este é o nome que você deve usar.
