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

​	Aqui começa jornada para criar nosso servidor, utilizaremos Express como visto a seguir. Devemos criar um arquivo com o nome server.js no diretório raiz.

​	Vamos começar importando as bibliotecas:
<img src=".\public\img\readme\import.PNG?raw=true" />

​	Adicionando dotenv para acessar variável de ambiente:
<img src=".\public\img\readme\dotenv.PNG?raw=true" />

​	Armazenando o endereço da pasta public em uma variável e criando o servidor:<img src=".\public\img\readme\server.PNG?raw=true" />

​	Configurando os midelewares com app.use:
<img src=".\public\img\readme\app.use.PNG?raw=true" />

​	*Obs: express.json permitirá o compartilhamento de dados do formulário, quanto o express.static irá definir a pasta public caminho estático*

​	Configurando a rota home:
<img src=".\public\img\readme\rotaHome.PNG?raw=true" />

​	Listening para a porta 3000, como forma de verificar se o servidor está rodando:
<img src=".\public\img\readme\listening.PNG?raw=true" />

​	Agora que nosso servidor já está pronto, podemos rodar o comando `npm start` no terminal e Voilà!

---

### Nav-bar

​	Enfim chegou, a fatidica hora em que veremos o front-end do portfólio (aplicação), devemos criar dentro de index.html uma estrutura básica.

​	Criando a nav-bar em HTML: <img src=".\public\img\readme\nav.PNG?raw=true" />

​	Estilizando com um toque de CSS: