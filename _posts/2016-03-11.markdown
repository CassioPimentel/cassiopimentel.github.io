<h1 id="web-service-restful-com-nodejs-e-mongodb-parte-1">Web service RESTful com NodeJS e MongoDB - Parte 1</h1>

<p>Bem vindo ao meu primeiro post onde irei mostrar como implementar um web service RESTful com nodejs e mondodb. Este projeto será dividido em duas partes e na parte 1 irei mostrar os conceitos básicos e a instalação de componentes, e na parte 2 o desenvolvimento em si do web service.</p>



<h2 id="conceitos-básicos">Conceitos básicos</h2>

<p><a href="https://pt.wikipedia.org/wiki/Web_service">Web Service</a>: É uma fonte de dados acessada por um aplicativo local ou através da internet, e é um método mais inteligente de prover dados para aplicações, sem que seja necessário expor o banco de dados.</p>

<p><a href="https://pt.wikipedia.org/wiki/REST">REST</a>: É a metodologia usada para implementar um web service, e esta metodologia usa o protocolo HTTP e seus verbos GET, POST, UPDATE, DELETE entre outros, que são usados para dizer ao web service o que será feito.</p>

<p><a href="http://www.infoq.com/br/articles/rest-introduction">RESTful</a>:  é a implementação do conceito REST.</p>



<h2 id="tecnologias-usadas">Tecnologias usadas</h2>

<ul>
<li><em>MongoDB</em>: banco de dados <a href="https://pt.wikipedia.org/wiki/NoSQL">NoSQL</a> baseado em documentos.</li>
<li><em>NodeJS</em>: é uma plataforma para desenvolvimento de aplicações server-side baseadas em rede utilizando JavaScript e o V8 JavaScript Engine.</li>
<li><em>ExpressJS</em>: modulo para NodeJS, que permite implementar rotas.</li>
<li><em>Body-Parse</em>: plugin para ExpressJS, que vai nos permitir usar JSON.</li>
<li><em>Mongoose</em>: modulo para NodeJS, para fazer operações no Mongodb.</li>
</ul>



<h2 id="instalação-dos-módulos">Instalação dos Módulos</h2>

<p><em>As instalações foram feitas em uma maquina com ubuntu 14.01.</em> <br>
Primeiro será necessario instalar o Gerenciador de pacotes do NodeJS <a href="https://www.npmjs.com/">npm</a>. <br>
execulte na linha de comando:</p>

<pre><code>    curl http://npmjs.org/install.sh | sudo sh
</code></pre>

<p>e para testar:</p>

<pre><code>    npm -v
</code></pre>

<p>Agora será gerado um arquivo chamado Package.json que entre outras coisas vai servir como uma lista de dependencias ou modulos a serem instalados. o comando usado para gerar este arquivo é o:</p>

<pre><code>    npm init
</code></pre>

<p>este comando ira te fazer varias perguntas como o nome do projeto, a versão etc. E o resultado será parecido com isso:</p>

<p><img src="https://lh3.googleusercontent.com/-yk8BZSWob4c/VuMRL-1AiEI/AAAAAAAAAcA/edbDXESbfBYuA79c-GibBwBIrxST6eJZw/s0/Screenshot+from+2016-03-11+15%253A25%253A34.png" alt="enter image description here" title="Screenshot from 2016-03-11 15:25:34.png"></p>

<p>Depois de criado o Package.json vamos as instalações dos pacotes para NodeJS (se você não tiver o NodeJS instalado, siga <a href="https://www.digitalocean.com/community/tutorials/como-instalar-o-node-js-em-um-servidor-ubuntu-14-04-pt">este</a> tutorial). primeiro será o express.js:</p>

<pre><code>sudo npm install express --save
</code></pre>

<p>se atente a flag <em>save</em>, esta flag é importante pois com ela o arquivo Package.json será complementado com as dependencias que serão instaladas. Agora vem o body-parser:</p>

<pre><code>sudo npm install body-parser --save
</code></pre>

<p>e por ultimo o mongoose:</p>

<pre><code>sudo npm install mongoose --save
</code></pre>

<p>Agora o arquivo Package.json ficou parecido com isso:</p>

<p><img src="https://lh3.googleusercontent.com/ZXrHtkYA_4HlwmH5smBtmXegoVzpF9tKZSDhBaZ7xiHq6bFBeiGYqdxKvwqnlwwnlLMf=s0" alt="enter image description here" title="Screenshot from 2016-03-11 15:37:20.png"></p>

<p>E com isso chegamos ao final desta primeira parte, ate a próxima.</p>
