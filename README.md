# Criando portfólio com puro HTML, CSS e Javascript

### Finalidade do projeto

​	Este projeto tem como finalidade criar um portfólio moderno, treinando conceitos de responsividade, sem uso de bibliotecas, desenvolvido apenas com HTML, CSS e JAVASCRIPT. *Bônus*: Aprender e treinar conceitos de Nodemailer ao desenvolver um formulário de contato.

Link original: <https://dev.to/kunaal438/how-to-make-fully-responsive-modern-portfolio-using-pure-html-css-and-js-1p65>

---

### Criando diretórios necessários

​	Nesta parte vamos organizar corretamente os diretórios e arquivos necessários para a nossa aplicação, abaixo uma imagem para ilustrar corretamente a estrutura:
<img src=".\public\img\readme\folders.PNG?raw=true" />

 * IMG = ;
 * APP.js = ;
 * INDEX.html = ;
 * PROJECT.js = Este arquivo irá conter os dados referentes aos projetos a serem apresentados;
 * STYLE.css = ;

---

### NPM

​	Dentro do diretório principal, vamos executar um `npm i express.js nodemon nodemailer dotenv` para iniciar o NPM no nosso projeto. Utilizaremos os seguintes itens:

* Express para criar o servidor;
* Nodemon para rodar o servidor continuadamente;
* Nodemailer como formar de enviar os emails formulário;
* Dotenv como forma de tornar o ambiente variável.

---

### Package.json

​	Nosso arquivo `package.json` precisa de algumas adições a esta altura e aqui começaremos:

​	Começamos adicionando o "scripts":
<img src=".\public\img\readme\scripts.PNG?raw=true" />

----

### Server.js

​	Aqui começa jornada para criar nosso servidor, utilizaremos Express como visto a seguir.

​	Vamos começar importando as bibliotecas:
<img src=".\public\img\readme\import.PNG?raw=true" />

​	Adicionando dotenv para acessar variável de ambiente:
<img src=".\public\img\readme\dotenv.PNG?raw=true" />

​	Armazenando o endereço da pasta public em uma variável e criando o servidor:<img src=".\public\img\readme\server.PNG?raw=true" />

