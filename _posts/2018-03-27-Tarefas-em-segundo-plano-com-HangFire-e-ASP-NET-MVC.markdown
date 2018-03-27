---
title: "Tarefas em segundo plano com HangFire e ASP.NET MVC"
date: "2018-03-27"
description: "O hangfire foi construído para facilitar o agendamentos de Jobs e tarefas recorrentes de forma muito fácil. O que o diferencia de outros, por exemplo o Quartz.Net, que é bastante conhecido, é que não precisa de serviços do windows para o seu funcionamento."

---

No nosso exemplo iremos simular uma tarefa recorrente de envio de e-mail em um aplicativo web ASP.NET MVC, este exemplo é baseado em algo real que usei no trabalho.

![enter image description here](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/hangfire-aspnet/hangfire.jpg)

## Requisitos

 - .NET Framework >= 4.5
 - Biblioteca de [Newtonsoft.Json](https://www.nuget.org/packages/Newtonsoft.Json/) ≥ 5.0.1
 - Banco de dados: -   [SQL Azure, SQL Server 2008 R2](http://docs.hangfire.io/en/latest/configuration/using-sql-server.html) (incluindo Express) ou [Redis](http://docs.hangfire.io/en/latest/configuration/using-redis.html). 

 No nosso exemplo iremos utilizar o SQLServer Express.

## Demo

Lembrando que o HangFire pode ser utilizado em sistemas web, sistemas desktop e windows serviçes,

Iremos fazer a demo usando um aplicativo web em ASP.NET MVC simples e criaremos um Job recorrente simulando o envio e emails de 2 em 2 minutos.

Primeiramente crie um aplicativo web ASP.NET MVC e apos isto instale o HangFire usando o Nuget ou via Package Manager Console:

    Install-Package HangFire -Version 1.6.17

Com o projeto criado, no Visual Studio, vá até: View->SQL Server Object Explorer:

![enter image description here](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/hangfire-aspnet/SQL%20SERVER%20LOCAL.jpg)

Clique com o botão direito no segundo DB do SQL Server e vá até as propriedades e copie a connection string:

![enter image description here](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/hangfire-aspnet/CONECTION%20STRING.jpg)

E neste DB que as tabelas do HangFire serão criadas. A próxima etapa será colocar algumas linhas de código no arquivo `startup.cs` para que o HangFire funcione corretamente:

    public void Configuration(IAppBuilder app)
    {
			GlobalConfiguration.Configuration
	            .UseSqlServerStorage("Data Source=(localdb)\v11.0;Initial Catalog=master;Integrated Security=True;Connect Timeout=30;Encrypt=False;TrustServerCertificate=True;ApplicationIntent=ReadWrite;MultiSubnetFailover=False");
    
            app.UseHangfireDashboard();
            app.UseHangfireServer();
    }

Em UseSqlServerStorage eu coloquei a string de conexão copiada acima, mas em um projeto "real" você colocar o nome da string de conexão que estará no arquivo Web.config.

O próximo passo é criar o Job Recorrente, no exemplo criei um controller chamado Home e numa action Index adicionei o seguinte codigo:

    public ActionResult Index()
    {
			RecurringJob.AddOrUpdate(
	            () => EnviarEmails(),
                Cron.MinuteInterval(2));
                
            return View();
    }
Não irei implementar o envio do e-mail em si, caso tenha interrese, [este](https://stackoverflow.com/questions/9201239/send-e-mail-via-smtp-using-c-sharp) link tem as informações necessárias para implementar a função

O código acima cria o job, que ira executar  a função `EnviarEmails()`, por dois minutos. No lugar de minutos poderia usar segundos, horas, dias e assim por diante.

Quando você executar o site pela primeira vez, algumas tabelas serão criadas pelo HangFire e o Job de envio de emails será criado. Eu deixei o site rodando por um tempo e acessei o DashBoard, adicionando "/ hangfire" ao final da URL e ir em Recurring Jobs, que é onde os jobs recorrentes estão.
	
![enter image description here](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/hangfire-aspnet/dasboard.jpg)

O painel do Hangfire mostra informações detalhadas sobre tarefas, filas, status de tarefas e assim por diante.
