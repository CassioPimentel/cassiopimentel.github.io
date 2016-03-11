
#Web service RESTful com NodeJS e MongoDB - Parte 1

Bem vindo ao meu primeiro post onde irei mostrar como implementar um web service RESTful com nodejs e mondodb. Este projeto será dividido em duas partes e na parte 1 irei mostrar os conceitos básicos e a instalação de componentes, e na parte 2 o desenvolvimento em si do web service.

##Conceitos básicos
[Web Service](https://pt.wikipedia.org/wiki/Web_service): É uma fonte de dados acessada por um aplicativo local ou através da internet, e é um método mais inteligente de prover dados para aplicações, sem que seja necessário expor o banco de dados.

[REST](https://pt.wikipedia.org/wiki/REST): É a metodologia usada para implementar um web service, e esta metodologia usa o protocolo HTTP e seus verbos GET, POST, UPDATE, DELETE entre outros, que são usados para dizer ao web service o que será feito.

[RESTful](http://www.infoq.com/br/articles/rest-introduction):  é a implementação do conceito REST.

##Tecnologias usadas
- *MongoDB*: banco de dados [NoSQL](https://pt.wikipedia.org/wiki/NoSQL) baseado em documentos.
- *NodeJS*: é uma plataforma para desenvolvimento de aplicações server-side baseadas em rede utilizando JavaScript e o V8 JavaScript Engine.
- *ExpressJS*: modulo para NodeJS, que permite implementar rotas.
- *Body-Parse*: plugin para ExpressJS, que vai nos permitir usar JSON.
- *Mongoose*: modulo para NodeJS, para fazer operações no Mongodb.

##Instalação dos Módulos

*As instalações foram feitas em uma maquina com ubuntu 14.01.*
Primeiro será necessario instalar o Gerenciador de pacotes do NodeJS [npm](https://www.npmjs.com/).
execulte na linha de comando:
	
		curl http://npmjs.org/install.sh | sudo sh
e para testar:

		npm -v

Agora será gerado um arquivo chamado Package.json que entre outras coisas vai servir como uma lista de dependencias ou modulos a serem instalados. o comando usado para gerar este arquivo é o:

		npm init
este comando ira te fazer varias perguntas como o nome do projeto, a versão etc. E o resultado será parecido com isso:

![enter image description here](https://lh3.googleusercontent.com/-yk8BZSWob4c/VuMRL-1AiEI/AAAAAAAAAcA/edbDXESbfBYuA79c-GibBwBIrxST6eJZw/s0/Screenshot+from+2016-03-11+15%253A25%253A34.png "Screenshot from 2016-03-11 15:25:34.png")

Depois de criado o Package.json vamos as instalações dos pacotes para NodeJS (se você não tiver o NodeJS instalado, siga [este](https://www.digitalocean.com/community/tutorials/como-instalar-o-node-js-em-um-servidor-ubuntu-14-04-pt) tutorial). primeiro será o express.js:

	sudo npm install express --save
se atente a flag *save*, esta flag é importante pois com ela o arquivo Package.json será complementado com as dependencias que serão instaladas. Agora vem o body-parser:

	sudo npm install body-parser --save
	
e por ultimo o mongoose:

	sudo npm install mongoose --save
Agora o arquivo Package.json ficou parecido com isso:

![enter image description here](https://lh3.googleusercontent.com/ZXrHtkYA_4HlwmH5smBtmXegoVzpF9tKZSDhBaZ7xiHq6bFBeiGYqdxKvwqnlwwnlLMf=s0 "Screenshot from 2016-03-11 15:37:20.png")
	
E com isso chegamos ao final desta primeira parte, ate a próxima.
