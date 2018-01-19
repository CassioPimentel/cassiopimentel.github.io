---
title: "WebApi com ASP.NET CORE 2.0 com MySQL no AppHarbor"
date: "2018-01-18"
description: "Web Api usando ASP.NET CORE com MySQL e coloca-la em produção no AppHarbor, que é uma boa alternativa para testar projetos em .NET"

---

Neste post irei mostrar como criar uma Web Api usando ASP.NET CORE e coloca-la em produção no AppHarbor, que é uma boa alternativa para testar projetos em .NET, e numa segunda etapa irei implementar o swagger.


![enter image description here](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/PostWebApiAppHarbor/2318.WithAPIArchitecture.PNG)

**O que será usado:**

 - Visual Studio 2017 ou 2015(com o ASP.NET CORE instalado)
 - EntityFrameworkCore
 - MySql.Data.EntityFrameworkCore
 
Instale estes dois últimos via nuget.

**Criando o projeto**

Então com o Visual Studio aberto, basta ir em:

Arquivo->Novo->Novo Projeto, dê um nome a sua escolha.
Após isto escolha Web Api na próxima janela:


![enter image description here](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/PostWebApiAppHarbor/criarprojeto.jpg)


**Classes e Contexto do banco de dados**

Com o projeto criado, crie uma pasta chamada Models, lembrando que esta pasta pode ser chamada por outro nome, isto é apenas uma convenção do ASP.NET.

Este projeto será simples, terá apenas dois models, Modelo e Marca, basta clicar com o botão direito em:

Models->Adicionar->Classe

Os Modelos tem apenas uma marca, e uma marca tem vários Modelos. E para exemplificar as classes terão apenas duas propriedades, código e nome:

**As classes ficaram assim:**

    public class Modelo
    {
	    [Key]
        public int Codigo { get; set; }
        public string Nome { get; set; }
        public virtual Marca Marca { get; set; }
    }

    public class Marca
    {
        public Marca()
        {
            Modelo = new List<Modelo>();
        }
		[Key]
        public int Codigo { get; set; }
        public string Nome { get; set; }

        public virtual ICollection<Modelo> Modelo { get; set; }
    }

*Obs: para criar propriedades de classe de forma mais rapida, digite prop na sua classe aperte Tab, que o Visual Studio ira preencher o get e set.*

onde [Key] é onde dizemos ao EntyFramework que aquele atributo é uma chave primeira do banco de dados.

E deve-se usar os using abaixo nestas classes:
	
    using System.Collections.Generic;
    using System.ComponentModel.DataAnnotations;

Agora crie uma nova classe chamada Context, que herda de `DbContext`, que sera nosso contexto de dados:

    public class Context : DbContext
    {
	    public Context(DbContextOptions<Context> options)
                : base(options)
        {
        }
        public DbSet<Marca> Marca { get; set; }
        public DbSet<Modelo> Modelo { get; set; }
    }

Bem simples, nada novo ate aqui.

**Criando o Site no AppHarbor**

O [AppHarbor](https://appharbor.com/) é uma plataforma alternativa para publicar sites em ASP.NET do qual gosto muito, e uso em alguns projetos, inclusive em WebApi.

Primeiramente você deve fazer o cadastro no site acessando o link acima, e depois ir em Your Aplications e criar uma nova aplicação:

![enter image description here](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/PostWebApiAppHarbor/criarProjetoAppHarbor.jpg)


O AppHarbor traz vários banco de dados que são criados e adicionados ao projeto de forma muito rápida, iremos adicionar um novo add-on do MySql, basta adicionar a versão gratuita que te da 20M de espaço para testes, clicando em **Add-on Catalog** e depois escolher MySql e em **Install**:

![enter image description here](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/PostWebApiAppHarbor/AdicionarAddon2.jpg)

Após instalar o banco, clique em **MySql->Go to MySql** e copie a Connection string no rodapé da pagina, você usara na próxima etapa no arquivo `Startup.cs`:


![enter image description here](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/PostWebApiAppHarbor/connectionstring.jpg)


**Configuração do Startup.cs e Criação do banco de dados**

Neste ponto devemos registrar nosso Context de bando de dados, isto é feito ConfigureServices do arquivo Startup.cs (**Nesta etapa você cola sua connection string**):

    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();

        services.AddDbContext<Context>(options =>
                 options.UseMySQL("STRING DE CONEXAO"));

    }

Após isto vamos criar o banco de dados, mas antes disso, devemos criar uma tabela de migrations history manualmente, já que o conector do MySql ainda não prove suporte total com o EntityFramework Core, então devemos fazer isto manualmente. Basta copiar e colar o sql abaixo e gerar a tabela no MySql(Eu utilizo o MySql workbench para isto):


    CREATE TABLE `NOME DO SEU DATABASE`.`__EFMigrationsHistory` 
    ( 
	    `MigrationId` nvarchar(150) NOT NULL, 
	    `ProductVersion` nvarchar(32) NOT NULL, 
	     PRIMARY KEY (`MigrationId`) 
	);

Para saber mais sobre este [problema](https://stackoverflow.com/questions/46089982/ef-core-update-database-on-mysql-fails-with-efmigrationshistory-doesnt-ex).

Depois de criar a tabela manualmente, basta adicionar a Migration e fazer o Update no banco de dados:

   

 - Add-Migration FirstMigration 	
 - Update-Database

**Criação dos Controllers**

Parte bem simples, iremos utilizar o scaffolding do ASP.NET CORE, para isto clique com o botão direito em Controllers vá em adicionar->Controller, e escolha a opção Controlador API com ações, usando Entity Framework:


![enter image description here](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/PostWebApiAppHarbor/criarController1.jpg)


E mudar o nome padrão do controller, exemplo da classe Modelo:

![Modelo](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/PostWebApiAppHarbor/modelo.jpg)

Depois faça o mesmo para Marca.

**Testando a API localmente**

A api já esta funcionando, mesmo com o banco de dados estando na nuvem(já vou mostrar como colocar o código também), irei testar usando o [Postman](https://www.getpostman.com/), primeiro irei gravar uma marca, e depois buscar todas as marcas:

**POST Marca:**

![enter image description here](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/PostWebApiAppHarbor/PostMarca.jpg)

**GET Marca:**

![enter image description here](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/PostWebApiAppHarbor/GetMarca.jpg)

Perceba que ao buscar todas as Marcas o atributo modelo esta vazio pois esta Marca não tem nenhum modelo de carro cadastrado. Perceba também que utilizo a rota api/Marca, o scaffolding gera esta nomenclatura automaticamente: **api/Nome do Controller**, mas nada impede de você muda-la.

**Deploy**

Com o projeto funcionando localmente, nos falta apenas fazer o deploy para o AppHarbor, esta etapa é bem facial, primeiramente você deve acessar [esta ](https://blog.appharbor.com/2012/4/25/introducing-the-appharbor-command-line-utility) pagina do AppHarbor e clicar em **Download AppHarbor CLI**, que é um programa do AppHarbor para fazermos o deploy via linha de comando no cmd. A instalação é bem simples, e apos conclui-la basta abrir o cmd, navegar até a pagina do projeto e digitar os comandos abaixo:

 - **dotnet publish**
 - Após isso vá ate Debug\netcoreapp2.0\publish
 - digite o comando **appharbor user login**, irá pedir o seu login e senha
 - **appharbor deploy -a NomeDoProjetoCriadoNoAppHarbor**

Agora volte ao AppHarbor, na pagina do seu projeto, e se der tudo certo, basta clicar no link  **Go to your application** que vai ta logo a frente do nome do seu projeto.

Obs: o deploy pode demorar um pouco, no meu caso foi 30 segundos ate funcionar normalmente, caso demore muito é porque houve algum erro no deploy, basta clicar no status, e terá o ocorreu:

![enter image description here](https://raw.githubusercontent.com/CassioPimentel/cassiopimentel.github.io/master/images/PostWebApiAppHarbor/status.jpg)

A url da sua WebApi sera: **NomeProjeto.apphb.com/SuaRota**.


No próximo post irei implementar neste projeto, ate mais.

**Link da WebAPI:** 
http://aspnetcorewebapiappharbor.apphb.com/api/marca
http://aspnetcorewebapiappharbor.apphb.com/api/modelo

**Link Github:** https://github.com/CassioPimentel/ASPNETCOREWebAPIAppHarbor

