# Start Code (Início de Código)

> Nesta aula, introduzimos o conceito da Web Moderna, conhecemos as principais linguagens utilizadas em seu desenvolvimento, entendemos suas possibilidades e adquirimos uma noção básica de seu potencial.

## Principais Tecnologias da Web Moderna

> As linguagens mais utilizadas são popularmente conhecidas como a tríade da Web: HTML, CSS e JavaScript. Juntas, elas são responsáveis pela construção da maior parte das páginas web existentes na Internet. Cada uma desempenha um papel específico no desenvolvimento de um site, e veremos com mais detalhes a função de cada uma logo abaixo.

---

## HTML - HyperText Markup Language
### (Base: Estrutura da Página)

> O HTML (HyperText Markup Language) é uma linguagem de marcação responsável por definir a estrutura e o significado do conteúdo de uma página web. Para isso, utiliza **tags**, que envolvem os elementos da página e atribuem um contexto ao seu conteúdo.

### O papel das tags

As tags têm como principal função dar **semântica** ao conteúdo da página, permitindo identificar o papel de cada elemento, como títulos, parágrafos, listas, imagens, tabelas, formulários, vídeos, ícones, entre outros.

### Benefícios da semântica

Uma estrutura semântica bem definida oferece diversas vantagens:

- Facilita a navegação para leitores de tela, tornando a página mais acessível.
- Auxilia mecanismos de busca (SEO) a compreenderem melhor o conteúdo da página.
- Organiza o conteúdo de forma hierárquica, tornando sua leitura e manutenção mais simples.
- Permite que o CSS aplique estilos de maneira mais consistente, sem depender apenas da aparência visual para identificar cada elemento.

> Em resumo, o HTML é responsável por estruturar e organizar o conteúdo da página, servindo como a base sobre a qual o CSS e o JavaScript irão atuar.

**A seguir, veremos sua estrutura e sua sintaxe.**

### Sintaxe das Tags HTML

> As tags HTML possuem uma sintaxe específica para funcionarem corretamente. Em sua forma mais comum, elas são constituídas por uma **tag de abertura** `<a>`, o **conteúdo** e uma **tag de fechamento** `</a>`.

**Partes da sintaxe:**

- **Nome da tag:** identifica o tipo de elemento HTML.
- **Tag de abertura:** marca o início do elemento.
- **Conteúdo:** informação exibida ou marcada pela tag.
- **Tag de fechamento:** marca o fim do elemento.

**Representação da sintaxe:**

```html
<tag>Conteúdo</tag>
│ │     │        │
│ │     │        └── Tag de fechamento
│ │     └────────── Conteúdo
│ └──────────────── Tag de abertura
└────────────────── Nome da tag
```

**Exemplo:**

```html
<p>Olá Mundo!</p>
│ │    │         │
│ │    │         └── Tag de fechamento
│ │    └──────────── Conteúdo
│ └───────────────── Tag de abertura
└─────────────────── Nome da tag (p = paragraph)
```

> **Observação:** Nem todas as tags possuem fechamento. Alguns elementos HTML são chamados de **elementos vazios (void elements)** e são compostos apenas pela tag de abertura, como `<img>`, `<br>` e `<input>`. Além disso, existem outros aspectos relacionados à sintaxe das tags, como atributos e diferentes tipos de elementos, que serão abordados mais adiante. Por enquanto, esta é a estrutura básica das tags HTML.

### Criando um Arquivo HTML

> Para criar um **arquivo HTML**, basta nomeá-lo seguindo o padrão **NomeDoArquivo.html**. A extensão **`.html`** é responsável por informar ao navegador que aquele arquivo deve ser interpretado como um documento HTML. Sem essa extensão, o arquivo será tratado como um arquivo de texto comum.

### Regras para nomear um arquivo HTML

Ao nomear um arquivo HTML, siga estas boas práticas:

- Não inicie o nome do arquivo com números.
- Não utilize espaços; prefira substituí-los por **`-`** (hífen) ou **`_`** (underscore).
- Evite caracteres especiais, como `@`, `#`, `%`, `&`, `ç` e acentos.
- Sempre que possível, utilize apenas letras minúsculas.
- Escolha nomes curtos, claros e descritivos.

**Exemplos:**

✅ Correto

```text
index.html
sobre.html
minha-pagina.html
contato_cliente.html
```

❌ Evite

```text
1pagina.html
Minha Página.html
Página@Inicial.html
Arquivo.HTML
```

---

## CSS - Cascading Style Sheets
#### (Estilo e Organização: Definindo Aparência, Posicionamento e Responsividade)

> O CSS (**Cascading Style Sheets**) é uma linguagem de estilos responsável por definir a aparência dos elementos HTML. Com ele, é possível alterar cores, fontes, espaçamentos, tamanhos, bordas, sombras, posicionamentos, animações e criar layouts responsivos para diferentes tamanhos de tela.

> O CSS atua selecionando elementos do HTML (como tags e, futuramente, classes, IDs e outros seletores) e aplicando regras de estilo por meio de um **seletor** `p`, seguido de um **bloco de declarações** `{Propriedades: Valor;}`, onde são definidas as **propriedades** e seus respectivos **valores**.

> Nesta introdução, veremos apenas a sintaxe básica do CSS. Ao longo das próximas aulas, aprofundaremos cada um desses conceitos.

#### Sintaxe Básica do CSS

> Uma regra CSS é composta por um **seletor** e um **bloco de declarações**. Dentro desse bloco são definidas uma ou mais **propriedades** e seus respectivos **valores**, que determinam como os elementos HTML serão exibidos.

**Estrutura da sintaxe:**

```css
seletor {
    propriedade: valor;
}
```

**Partes da sintaxe:**

- **Seletor:** identifica qual elemento HTML receberá o estilo.
- **Bloco de declarações:** conjunto de estilos delimitado pelas chaves `{}`.
- **Propriedade:** característica visual que será modificada.
- **Valor:** define como a propriedade será aplicada.

**Exemplo:**

```css
p {
    color: blue;
}
```

**Representação da sintaxe:**

```css
p {
│
├── Seletor (p)
│
├── color: blue;
│   │      │
│   │      └── Valor
│   └───────── Propriedade
│
└── Bloco de declarações ({ })
```

> Neste exemplo, o seletor **`p`** seleciona todas as tags `<p>` do documento HTML. Em seguida, a propriedade **`color`** recebe o valor **`blue`**, fazendo com que o texto desses parágrafos seja exibido na cor azul.

---

#### Criando um Arquivo CSS

> Para criar um **arquivo CSS**, basta nomeá-lo seguindo o padrão **NomeDoArquivo.css**. A extensão **`.css`** informa ao navegador que aquele arquivo contém regras de estilo que poderão ser aplicadas aos documentos HTML.

##### Regras para nomear um arquivo CSS

Ao nomear um arquivo CSS, siga as mesmas boas práticas utilizadas para arquivos HTML:

- Utilize nomes claros e descritivos.
- Evite espaços; prefira **`-`** (hífen) ou **`_`** (underscore).
- Evite caracteres especiais e acentos.
- Sempre que possível, utilize apenas letras minúsculas.

**Exemplos:**

✅ Correto

```text
style.css
main.css
home.css
responsivo.css
```

❌ Evite

```text
Meu Estilo.css
Style Principal.css
arquivo@css.css
```

---

### JavaScript
#### (Comportamento e Interatividade: Adicionando Lógica e Dinamismo às Páginas)

> O **JavaScript (JS)** é uma linguagem de programação responsável por adicionar comportamento e interatividade às páginas web. Com ela, é possível responder às ações do usuário, manipular elementos HTML, alterar estilos CSS, realizar cálculos, validar formulários, consumir APIs, criar animações, controlar dados e desenvolver aplicações completas.

> O JavaScript atua sobre os elementos da página por meio de seu código, podendo acessar e modificar o HTML e o CSS em tempo real. Dessa forma, uma página deixa de ser apenas estática e passa a responder dinamicamente às interações do usuário.

> Nesta introdução, veremos apenas a sintaxe básica da linguagem. Ao longo das próximas aulas, aprofundaremos seus conceitos e funcionalidades.

---

#### Sintaxe Básica do JavaScript

> Um código JavaScript é composto por **instruções** (*statements*), que são executadas na ordem em que são escritas. Essas instruções podem declarar variáveis, chamar funções, realizar cálculos, modificar elementos da página, entre diversas outras operações.

**Estrutura da sintaxe:**

```javascript
comando();
```

ou

```javascript
const nome = valor;
```

**Partes da sintaxe:**

- **Instrução (Statement):** comando que será executado.
- **Identificador:** nome dado a uma variável, função ou outro elemento da linguagem.
- **Operador:** símbolo utilizado para realizar operações ou atribuições.
- **Valor:** informação armazenada ou utilizada pelo código.
- **Ponto e vírgula (`;`):** utilizado para finalizar uma instrução (opcional em muitos casos, mas recomendado para manter a consistência do código).

**Exemplo:**

```javascript
const mensagem = "Olá Mundo!";

console.log(mensagem);
```

**Representação da sintaxe:**

```javascript
const mensagem = "Olá Mundo!";
│     │         │
│     │         └── Valor
│     └──────────── Identificador (variável)
└────────────────── Palavra-chave (const)

console.log(mensagem);
│      │   │
│      │   └── Argumento
│      └────── Método
└───────────── Objeto
```

> Neste exemplo, **`const`** declara uma variável chamada **`mensagem`**, que armazena o texto `"Olá Mundo!"`. Em seguida, **`console.log()`** exibe o conteúdo dessa variável no console do navegador.

---

#### Criando um Arquivo JavaScript

> Para criar um **arquivo JavaScript**, basta nomeá-lo seguindo o padrão **NomeDoArquivo.js**. A extensão **`.js`** informa ao navegador que aquele arquivo contém código JavaScript que poderá ser executado pela página web.

##### Regras para nomear um arquivo

Ao nomear um arquivo JavaScript, siga as mesmas boas práticas utilizadas para arquivos HTML e CSS:

- Utilize nomes claros e descritivos.
- Evite espaços; prefira **`-`** (hífen) ou **`_`** (underscore).
- Evite caracteres especiais e acentos.
- Sempre que possível, utilize apenas letras minúsculas.
- Se o projeto possuir vários arquivos JavaScript, utilize nomes que representem sua responsabilidade.

**Exemplos:**

✅ Correto

```text
script.js
main.js
app.js
menu.js
validacao.js
```

❌ Evite

```text
Meu Script.js
Arquivo@JS.js
JavaScript Principal.js
```

> **Observação:** Para utilizar arquivos **CSS** e **JavaScript** externos, eles devem ser vinculados corretamente ao documento HTML por meio de seus respectivos elementos de ligação.

> As diferentes formas de integrar e manipular o HTML utilizando **CSS** e **JavaScript** serão estudadas nas próximas aulas.

## Formas de Adicionar CSS

O CSS pode ser aplicado a uma página HTML de **três maneiras diferentes**. Todas funcionam, porém cada uma possui um propósito específico.

### 1. CSS Inline

O CSS é escrito diretamente no atributo `style` da própria tag HTML.

**Exemplo:**

```html
<p style="color: blue;">Olá Mundo!</p>
```

**Vantagens:**

- Rápido para testes.
- Útil para pequenos ajustes pontuais.

**Desvantagens:**

- Mistura estrutura (HTML) com apresentação (CSS).
- Dificulta a manutenção do código.
- Não permite reutilizar estilos.

> **Quando utilizar?**
>
> Apenas em situações muito específicas ou para testes rápidos.

---

### 2. CSS Interno (Internal CSS)

O CSS é escrito dentro da própria página HTML utilizando a tag `<style>`, geralmente dentro da seção `<head>`.

**Exemplo:**

```html
<head>
    <style>
        p {
            color: blue;
        }
    </style>
</head>
```

**Vantagens:**

- Mantém os estilos organizados em um único lugar da página.
- Indicado para páginas simples ou pequenos projetos.

**Desvantagens:**

- Os estilos ficam presos àquela página.
- Não podem ser reutilizados em outros arquivos HTML.

> **Quando utilizar?**
>
> Em pequenos projetos, exemplos de estudo ou páginas únicas.

---

### 3. CSS Externo (Recomendado ✅)

O CSS é escrito em um arquivo separado com extensão **`.css`** e vinculado ao documento HTML.

**Arquivo HTML**

```html
<head>
    <link rel="stylesheet" href="style.css">
</head>
```

**Arquivo `style.css`**

```css
p {
    color: blue;
}
```

**Vantagens:**

- Separa o HTML do CSS.
- Código mais organizado.
- Fácil manutenção.
- Reutilização do mesmo arquivo em várias páginas.
- Melhor escalabilidade para projetos grandes.

> **Esta é a forma mais utilizada no desenvolvimento profissional.**

---

## Qual é a melhor forma?

A melhor prática é utilizar **CSS Externo**.

Isso porque cada tecnologia fica responsável pela sua própria função:

- **HTML:** estrutura.
- **CSS:** aparência.
- **JavaScript:** comportamento.

Essa separação torna o projeto mais organizado, facilita a manutenção e permite reutilizar os mesmos estilos em diversas páginas.

---

## Vinculando um arquivo CSS

Para utilizar um arquivo CSS externo, utilize a tag `<link>` dentro do `<head>` do documento HTML.

```html
<link rel="stylesheet" href="style.css">
```

### Entendendo a sintaxe

- **`link`** → cria uma ligação com um recurso externo.
- **`rel="stylesheet"`** → informa que o recurso é uma folha de estilos.
- **`href`** → indica onde o arquivo CSS está localizado.

---

## Caminhos dos arquivos

No curso, utilizaremos principalmente **caminhos relativos**, pois eles funcionam dentro da estrutura do projeto.

```html
<link rel="stylesheet" href="style.css">
```

Mais adiante estudaremos também os **caminhos absolutos**, utilizados para acessar arquivos hospedados em outros locais, como servidores ou sites.

**Exemplo (caminho absoluto):**

```html
<link rel="stylesheet" href="https://site.com/style.css">
```

> **Por enquanto, utilize sempre caminhos relativos**, pois são os mais comuns durante o desenvolvimento de projetos.

## Formas de Adicionar JavaScript

Assim como o CSS, o JavaScript também pode ser utilizado de **três maneiras diferentes**.

---

### 1. JavaScript Inline

O código JavaScript é escrito diretamente em um atributo HTML, como `onclick`, `oninput`, entre outros.

**Exemplo:**

```html
<button onclick="alert('Olá Mundo!')">
    Clique aqui
</button>
```

**Vantagens:**

- Muito simples para testes rápidos.

**Desvantagens:**

- Mistura HTML com JavaScript.
- Dificulta a organização do projeto.
- Não é recomendado em aplicações reais.

> **Quando utilizar?**
>
> Apenas para testes ou exemplos simples.

---

### 2. JavaScript Interno

O código JavaScript é escrito dentro da própria página utilizando a tag `<script>`.

Geralmente essa tag é posicionada antes do fechamento do `<body>`.

```html
<body>

    <script>
        console.log("Olá Mundo!");
    </script>

</body>
```

**Vantagens:**

- Fácil para pequenos projetos.
- Todo o código permanece na mesma página.

**Desvantagens:**

- Não permite reutilizar o código em outras páginas.
- O arquivo HTML pode crescer rapidamente.

---

### 3. JavaScript Externo (Recomendado ✅)

O código JavaScript fica em um arquivo separado com extensão **`.js`**.

**Arquivo HTML**

```html
<body>

    <script src="script.js"></script>

</body>
```

**Arquivo `script.js`**

```javascript
console.log("Olá Mundo!");
```

**Vantagens:**

- Código organizado.
- Fácil manutenção.
- Reutilização em diversas páginas.
- Melhor separação das responsabilidades.

> **Esta é a forma utilizada na maioria dos projetos profissionais.**

---

## Qual é a melhor forma?

A melhor prática é utilizar **JavaScript Externo**.

Dessa forma:

- O HTML fica responsável pela estrutura.
- O CSS pela aparência.
- O JavaScript pela lógica e interatividade.

Essa organização facilita o desenvolvimento e a manutenção do projeto.

---

## Vinculando um arquivo JavaScript

Para conectar um arquivo JavaScript externo, utilize a tag `<script>` com o atributo `src`.

```html
<script src="script.js"></script>
```

### Entendendo a sintaxe

- **`script`** → informa ao navegador que será executado um código JavaScript.
- **`src`** → indica onde o arquivo JavaScript está localizado.

---

## Caminhos dos arquivos

Durante o curso utilizaremos principalmente **caminhos relativos**.

```html
<script src="script.js"></script>
```

Mais adiante veremos também os **caminhos absolutos**, utilizados para carregar arquivos hospedados em servidores externos.

**Exemplo (caminho absoluto):**

```html
<script src="https://site.com/script.js"></script>
```

> **Por enquanto, utilize sempre caminhos relativos**, pois eles fazem referência aos arquivos dentro do próprio projeto e são a forma mais utilizada durante o desenvolvimento.