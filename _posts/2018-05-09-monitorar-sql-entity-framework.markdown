---
title: "Monitorar SQL gerados pelo Entity Framework"
date: "2018-05-09"
description: "Neste post irei mostrar como monitorar todos os SQL gerados pelo entity framework, no output do visual studio."

---

Neste post irei mostrar como monitorar todos os SQL gerados pelo entity framework, no output do visual studio.

![enter image description here](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/monitorar-sql/orm.jpg)

Isto é algo importante, principalmente onde há consultas mais complexas que podem afetar o desempenho da aplicação.

O processo para visualizar os SQLs gerados no output do Visual Studio é bem simples, é apenas uma linha de codigo, no construtor da(s) classe(s) que herdem de DBContext:

```cs
Database.Log = s => System.Diagnostics.Debug.WriteLine(s);
```

A propriedade `Log`é um delegate do tipo `Action<string>` (**Delegate**: elemento que permite que você faça referencia a um método, parecido com ponteiros de funções) este delegate não retorna nada e espera um argumento **s** do tipo string.

**Obs**: Caso queira, você pode gravar estes comandos em arquivos para logs futuros.

Algo que uso também é colocar um if antes da instrução, para que o comando seja executado apenas em modo Debug:

```

    #if DEBUG
        Database.Log = s => System.Diagnostics.Debug.WriteLine(s);
    #endif

```


**Delegates**:  [C# - Delegates e Eventos : Conceitos básicos](http://www.macoratti.net/11/05/c_dlg1.htm)

**Delegate Action**: [C# - O Delegate Action](http://www.macoratti.net/14/11/c_deleg1.htm)
