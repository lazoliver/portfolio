# Criando portfólio com puro HTML, CSS e Javascript

### Finalidade do projeto

​	Este projeto tem como finalidade criar um portfólio moderno, treinando conceitos de responsividade, sem uso de bibliotecas, desenvolvido apenas com HTML, CSS e JAVASCRIPT. *Bônus*: Aprender e treinar conceitos de Nodemailer ao desenvolver um formulário de contato.

Link original: <https://dev.to/kunaal438/how-to-make-fully-responsive-modern-portfolio-using-pure-html-css-and-js-1p65>

---

### Criando diretórios necessários

​	Nesta parte vamos organizar corretamente os diretórios e arquivos necessários para a nossa aplicação, abaixo uma imagem para ilustrar corretamente a estrutura:

<img src=".\public\img\folders.PNG?raw=true" />

 * IMG = Esta pasta é destinada a armazenar as imagens utilizadas no projeto;
 * APP.js = Arquivo que conterá os scripts utilizados na aplicação;
 * INDEX.html = Esté será o resposável por armazerar todo o código HTML utilizado;
 * PROJECT.js = Este arquivo irá conter os dados referentes aos projetos a serem apresentados;
 * STYLE.css = Por fim, aqui ficará todas as configurações CSS de estilização.

----

### Project.js

​	Este arquivo servirá de base para os dados usados no projeto, ele será construído da seguinte forma:

```javascript
let projects = [
    {
        name: "project one",
        tags: "#javascript",
        image: "project_1.png"
    },
    {
        name: "project two",
        tags: "#javascript",
        image: "project_2.png"
    },
]
```

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

```json
"scripts": {
	"start": "nodemon server.js"
}
```

----

### Server.js

​	Aqui começa jornada para criar nosso servidor, utilizaremos Express como visto a seguir. Devemos criar um arquivo com o nome server.js no diretório raiz.

​	Vamos começar importando as bibliotecas:

```javascript
const express = require('express');
const path = require('path');
const nodemailer = require('nodemailer');
const dotenv = require('dotenv');
```

​	Adicionando dotenv para acessar variável de ambiente:

```javascript
dotenv.config();
```

​	Armazenando o endereço da pasta public em uma variável e criando o servidor:

```javascript
let initialPath = path.join(__dirname, "public");
let app = express();
```

​	Configurando os midelewares com app.use:

```javascript
app.use(express.static(initialPath));
app.use(express.json());
```

​	*Obs: express.json permitirá o compartilhamento de dados do formulário, quanto o express.static irá definir a pasta public caminho estático*

​	Configurando a rota home:

```javascript
app.get('/', (req, res) => {
    res.sendFile(path.join(initialPath, "index.html"));
})
```

​	Listening para a porta 3000, como forma de verificar se o servidor está rodando:

```javascript
app.listen(3000, () => {
    console.log('Server listening on port 3000');
})
```

​	Agora que nosso servidor já está pronto, podemos rodar o comando `npm start` no terminal e Voilà!

---

### Navbar

​	Enfim chegou, a fatidica hora em que veremos o front-end do portfólio (aplicação), devemos criar dentro de index.html uma estrutura básica e fazer os devidos imports de Css e Javascript.

​	Criando a navbar em HTML: 

```javascript
<!-- navbar -->
<nav class="navbar">
    <h1 class="brand">logo</h1>
    <div class="toggle-btn">
        <span></span>
        <span></span>
    </div>
    <ul class="links-container">
        <li class="links-item"><a href="#" class="link active">home</a></li>
        <li class="links-item"><a href="#project-section" class="link">project</a></li>
        <li class="links-item"><a href="#about-section" class="link">about</a></li>
        <li class="links-item"><a href="#contact-section" class="link">contact</a></li>
    </ul>
</nav>
```

​	Estilizando com um toque de CSS:

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html {
    scroll-behavior: smooth;
}

body {
    width: 100%;
    position: relative;
    background: relative;
    color: #fff;
    font-family: 'roboto', sans-serif;
}

/* navbar */

.navbar {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 60px;
    background: #1d1d1d;
    padding: 0 10vw;
    display: flex;
    justify-content: space-between;
    align-items: center;
    z-index: 9;
}

.brand {
    text-transform: capitalize;
    font-weight: 500;
}

.links-container {
    display: flex;
    list-style: none;
}

.link {
    text-transform: capitalize;
    color: #fff;
    text-decoration: none;
    margin: 0 10px;
    padding: 10px;
    position: relative;
}

.link:hover:not(.active) {
    opacity: 0.7;
}

.link.active::before,
.separetor::before {
    content: '';
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    width: 5px;
    height: 5px;
    border-radius: 50%;
    background: #fff;
}

.link.active::after,
.separetor::after {
    content: '';
    position: absolute;
    bottom: 2px;
    left: 0;
    width: 100%;
    height: 1px;
    background: #fff;
}
```

​	*Obs: O scroll-behavior permite uma rolagem de página mais suave*

----

### Header

​	Para o nosso header partiremos do index.html novamente, abaixo como foi criado a section:

```html
<!-- home section -->
<section class="home">
    <div class="hero-content">
        <h1 class="hero-heading"><span class="highlight">Olá, </span>eu sou o Wilian</h1>
        <p class="profession">web developer</p>
        <p class="info">info</p>
        <a href="#contact-section" class="btn">contact</a>
    </div>
    <img src="img/" class="image" alt="" />
</section>
```

