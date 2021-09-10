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

### Section Navbar

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

​	Estilizando com CSS:

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

### Section Header

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

​	Aplicando CSS:

```css
/* home section */

.home {
    width: 100%;
    min-height: calc(100vh - 60px);
    height: auto;
    margin-top: auto;
    padding: 0 10vw;
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: relative;
    background-color: #1d1d1d;
}

.hero-content {
    width: 50%;
}

.hero-heading {
    font-size: 4rem;
    text-transform: capitalize;
    font-weight: 500;
}

.highlight {
    color: #ff3559;
}

.profession {
    width: fit-content;
    display: block;
    margin: 10px 0 20px;
    margin-left: auto;
    text-transform: capitalize;
    position: relative;
    padding: 10px 20px;
    color: #1d1d1d;
    z-index: 2;
}

.profession::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: #e3e3e3;
    z-index: -1;
    transform: skewX(10deg);
}

.profession::after {
    content: '';
    position: absolute;
    top: 0;
    left: -100px;
    width: 100px;
    height: 2px;
    background: #e3e3e3;
}

.info {
    line-height: 30px;
    margin-bottom: 50px;
}

.btn {
    padding: 10px 20px;
    text-decoration: none;
    border-radius: 50px;
    background: #ff3559;
    color: #fff;
    text-transform: capitalize;
    border: none;
}
```

---

### Section About

​	Nosso projeto já está bem avançado, mas agora vamos adicionar um campo Sobre, para isso devemos criar um section about.

​	Em HTML:

```html
<!-- about section -->
<section  class="about" id="about-section">
    <h2 class="heading">about <span class="highlight">me</span></h2>
    <p class="sub-heading">info. </p>
    <div class="separator"></div>

    <div class="about-me-container">
        <div class="left-col">
            <img src="img/" class="about-image" alt="" />
        </div>
        <div class="right-col">
            <p class="about-para">info. </p>
            <a href="#" class="btn">download cv</a>
        </div>
    </div>
</section>
```

​	Vamos ao CSS:

```css
/* about section */

.about {
    width: 100%;
    height: auto;
    padding: 50px 10vw;
}

.heading {
    text-align: center;
    font-weight: 500;
    font-size: 3.5rem;
    text-transform: capitalize;
}

.sub-heading {
    text-align: center;
    font-size: 1rem;
    margin: 10px;
    opacity: 0.7;
}

.seperator {
    width: 25%;
    margin: 20px auto;
    position: relative;
}

.about-me-container {
    margin: 150px 0 100px;
    width: 100%;
    display: grid;
    grid-template-columns: 40% 60%;
    grid-gap: 50px;
}

.left-col, .right-col {
    position: relative;
}

.left-col::before {
    content: 'yes, its me';
    text-transform: capitalize;
    position: absolute;
    right: 0;
    top: -20px;
}

.left-col::after {
    content: '';
    position: absolute;
    top: -10px;
    right: 80px;
    width: 50px;
    height: 2px;
    background: #fff;
    transform-origin: right;
    transform: rotate(-30deg);
}

.about-image {
    border-radius: 10px;
    box-shadow: 0 10px 10px rgba(0, 0, 0, 0.25);
}

.about-para {
    font-size: 1.2rem;
    font-weight: 300;
    line-height: 35px;
    margin-bottom: 40px;
}
```

---

### Section Skill

​	Vamos adicionar uma listagem visual das skill que temos conhecimento? Agora é a hora, com certeza o resultado será uma delicinha.

​	O código em HTML:

```html
<!-- about section -->
<section  class="about" id="about-section">
// elementos anteriores
	
   <!-- skills section -->
   <h2 class="heading">languages and frameworks i know</h2>
       <div class="seperator"></div>
       <div class="skill-container">
           <div class="skill-card large" style="--bg: #f06529">
               <p class="skill">HTML</p>
           </div>
           <div class="skill-card" style="--bg: #379ad6">
               <p class="skill">TypeScript</p>
           </div>
           <div class="skill-card" style="--bg: #cc6699">
               <p class="skill">JavaScript</p>
           </div>
           <div class="skill-card" style="--bg: #f7df1e">
               <p class="skill">NodeJS</p>
           </div>
           <div class="skill-card" style="--bg: #5ed9fb">
               <p class="skill">ReactJS</p>
           </div>
           <div class="skill-card large" style="--bg: #83cd29">
               <p class="skill">CSS</p>
           </div>
           <div class="skill-card" style="--bg: #326690">
               <p class="skill">Styled Components</p>
           </div>
           <div class="skill-card" style="--bg: #ffa000">
               <p class="skill">Git</p>
           </div>
           <div class="skill-card large" style="--bg: #5ed9fb">
               <p class="skill">Much More</p>
           </div>
       </div>
</section>
```

​	Aparência a seção de skill, abaixo o código CSS:

```css
/* about section skills */

.skill-container {
    position: relative;
    margin-top: 100px;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-gap: 20px;
}

.skill-card {
    height: 200px;
    border-radius: 10px;
    border: 1px solid #464646;
    text-align: center;
    position: relative;
    cursor: pointer;
    transition: .5s;
}

.skill {
    font-size: 2rem;
    color: #464646;
    line-height: 200px;
}

.skill-card:hover{
    background: var(--bg);
}

.skill-card:hover .skill {
    color: #fff;
}

.skill-card.large {
    grid-column: 2 span;
}
```

---

### Section Projects

​	Na section projects, o objetivo é ser vitrine para os projetos já desenvolvidos e aqueles que ainda sergirão.

​	Vamos adicionar primeiro os botões de busca:

```html
<!-- project section -->
<section class="project" id="project-section">
    <h2 class="heading">Project<span class="highlight">s</span></h2>
    <p class="sub-heading">info. </p>
    <div class="seperator"></div>

    <div class="filters">
        <button class="filter-btn active" if="all">all</button>
        <button class="filter-btn" id="javascript">javascript</button>
        <button class="filter-btn" id="frontend">frontend</button>
        <button class="filter-btn" id="backend">backend</button>
        <button class="filter-btn" id="fullstack">fullstack</button>
    </div>
</section>
```

​	CSS mantendo padrão de construção do projeto:

```css
/* project section */

.project, .contact {
    position: relative;
    padding: 50px 10vw;
}

.filters {
    width: fit-content;
    display: block;
    margin: 100px auto;
}

.filter-btn {
    padding: 10px 20px;
    border-radius: 5px;
    border: none;
    text-transform: capitalize;
    margin: 0 5px 10px;
    cursor: pointer;
}

.filter-btn.active {
    background: #ff3559;
    color: #fff;
}
```

​	Agora é hora de criar os cards, com finalidade de estiliza-los posteriormente:

```html
// elementos anteriores
	<div class="project-container">
        <div class="project-card">
            <img src="img/" alt="">
            <div class="content">
                <h1 class="project-name">project #one</h1>
                <span class="tags">#javascript</span>
            </div>
        </div>
    </div>
</section>
```

​	Estilzar o card de projeto:

```css
/* project card */

.project-container {
    width: 100%;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
}

.project-card {
    position: relative;
    cursor: pointer;
    display: block;
}

.project-card img {
    width: 100%;
    height: 100%;
    object-fit: cover;
}

.project-card .content{
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.7);
    display: flex;
    justify-content: center;
    align-items: center;
    transition: .5s;
    text-transform: capitalize;
    opacity: 0;
}

.project-name {
    font-weight: 300;
    font-size: 2.5rem;
    text-align: center;
}

.tags {
    position: absolute;
    bottom: 20px;
    opacity: 0.6;
    width: 90%;
}

.project-card:hover .content {
    opacity: 1;
}

.project-card.hide {
    display: none;
}
```

---

### Dinamismo

​	Agora é hora de tornar a section project dinâmica, vamos iniciar importando dois arquivos, primeiro o arquivo que será nosso data e segundo os scripts utilizados na aplicação:

```html
<script src="project.js"></script>
<script src="app.js"></script>
```

​	Criando as alternâncias dos links entre classes ativas:

```java
// Links

const links = document.querySelectorAll('.link');

links.forEach(link => {
    link.addEventListener('click', () => {
        links.forEach(ele => ele.classList.remove('active'))/
        link.classList.add('active');
    })
})
```

​	Hora de criar o dinamismo no project cards. Para isso vamos adicionar ao app.js o código abaixo:

```javascript
// creating dynamic project card

const projectContainer = document.querySelector('.project-container');

projects.forEach(project => {
    projectContainer.innerHTML += `
    <div class="project-card" data-tags="#all, ${project.tags}">
        <img src="img/${project.image}" alt="">
        <div class="content">
            <h1 class="project-name">${project.name}</h1>
            <span class="tags">${project.tags}</span>
        </div>
    </div>
    `;
})
```

*Obs: Este método de construção que utiliza `` se chama template strings, onde podemos usar atributos de um objeto, neste caso o objeto está contido em project.js*

​	Vamos tornar os botões de filtro funcionais:

```javascript
// filters

const filters = document.querySelectorAll('.filter-btn');

filters.forEach(filterBtn => {
    filterBtn.addEventListener('click', () => {
        let id = filterBtn.getAttribute('id');
        let projectCards = document.querySelectorAll('.project-card');
        projectCards.forEach(card => {
            if(card.getAttribute('data-tags').includes(id)){
                card.classList.remove('hide');
            } else {
                card.classList.add('hide');
            }
        })

        filters.forEach(btn => btn.classList.remove('active'));
        filterBtn.classList.add('active');
    })
})
```

---

### Section Contact

​	Dev, agora é a hora de dar destaque ao que mais importa... Voce! Aqui será a section que os recrutadores e colegas dev entrarão em contato com você.

​	Section contact em HTML:

```html
<!--  contact form -->
<section class="contact" id="contact-section">
    <h2 class="heading">Contact<span class="highlight"> me</span></h2>
    <p class="sub-heading">Info</p>
    <div class="seperator"></div>

    <div class="contact-form">
        <div class="name">
            <input type="text" class="fist-name" required placeholder="first name" />
            <input type="text" class="last-name" required placeholder="last name" />
        </div>
        <input type="email" required class="email" placeholder="email" />
        <textarea class="message" placeholder="message" required></textarea>
        <button class="btn contact-btn">contact</button>
    </div>
</section>
    
<footer class="footer">made with love by Wilian S. | LazOliver</footer>
```

