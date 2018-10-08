---
title: "Pop-ups bonitos, responsivos e customizáveis em ASP.NET"
date: "2018-02-18"
description: "Neste post rápido irei dar uma dica para quem precisa mostrar mensagens estilo pop-up e precisa de algo mais personalizado e bonito."
---

Neste post rápido irei dar uma dica para quem precisa mostrar mensagens estilo pop-up e precisa de algo mais personalizado e bonito.

![enter image description here](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/SweetAlert/SWEETALERT.png)

## Sobre o SweetAlert

O SweetAlert é uma biblioteca javascript que deixa a criação de pop-ups muito mais fácil e rápida, não sendo necessário centralizar os pop-ups no centro da tela, pois o SweetAlert cuida disto tudo.

## Instalação

O nuget já tem o SweetAlert, bastando apenas ir no nuget e digitar SweetAlert, ou no console do Visual Studio, digitar:

    Install-Package SweetAlert

## Usando o SweetAlert

Primeiro você precisa adicionar o SweetAlert no seu `BundleConfig`para que seja importado ao seu projeto. Com isto feito podemos criar um exemplo bem simples usando apenas uma com uma linha que seria:

    swal("Here's a message!");

que terá o seguinte resultado:

![enter image description here](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/SweetAlert/PrtScr%20capture.jpg)

este exemplo mais simples se parece com um modal normal, só que com uma linha de código.

No site do [SweetAlert](https://lipis.github.io/bootstrap-sweetalert/) há outros exemplos de uso.
