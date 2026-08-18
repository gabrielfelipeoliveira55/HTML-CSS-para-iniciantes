# CSS Grid - Introdução ao Layout em Colunas

## O que é o CSS Grid?

O **CSS Grid Layout** é um modelo de layout bidimensional do CSS que permite organizar elementos em **linhas e colunas** de forma simples, organizada e responsiva.

Ao aplicar `display: grid` em um elemento, ele se torna um **container Grid**, e seus filhos diretos passam a ser **itens do Grid**, podendo ser posicionados através de propriedades específicas.

O Grid é muito utilizado para criar:

- Layouts de páginas
- Galerias
- Cards de produtos
- Dashboards
- Seções com múltiplas colunas

---

# Como funciona

O Grid sempre é aplicado ao **elemento pai**.

```css
.container{
    display: grid;
}
```

Todos os elementos filhos passam a ser organizados pelo Grid.

```html
<div class="container">
    <div>Item 1</div>
    <div>Item 2</div>
    <div>Item 3</div>
</div>
```

---

# Comportamento inicial

Adicionar apenas:

```css
display: grid;
```

não altera visualmente a página.

Isso acontece porque o Grid possui, por padrão, **uma única coluna**.

```
Item 1

Item 2

Item 3
```

Para criar colunas é necessário definir sua quantidade.

---

# Criando um exemplo prático

Antes de utilizar o Grid, foi criado um pequeno catálogo de produtos.

Cada produto possui:

- Nome
- Preço
- Descrição
- Botão de compra

Estrutura HTML:

```html
<h1>Comércio Eletrônico</h1>

<div class="grid">

    <div class="item">
        <h2>Camisa Polo</h2>

        <p class="preco">R$39</p>

        <p>Camisa polo feita de algodão com detalhes em azul claro.</p>

        <a class="comprar" href="/">Comprar</a>
    </div>

    <div class="item">
        <h2>Bermuda Preta</h2>

        <p class="preco">R$59</p>

        <p>Bermuda confortável.</p>

        <a class="comprar" href="/">Comprar</a>
    </div>

    <div class="item">
        <h2>Calça Jeans</h2>

        <p class="preco">R$99</p>

        <p>Calça jeans tradicional.</p>

        <a class="comprar" href="/">Comprar</a>
    </div>

    <div class="item">
        <h2>Casaco Azul</h2>

        <p class="preco">R$149</p>

        <p>Casaco de inverno.</p>

        <a class="comprar" href="/">Comprar</a>
    </div>

</div>
```

---

# Estilização inicial

Antes de utilizar o Grid, foi aplicada uma estilização básica.

```css
body{
    font-family: Arial;
}

h1{
    text-align:center;
}

.item{
    background:#f7f7f7;
    border:1px solid #e7e7e7;
    padding:20px;
    border-radius:4px;
    margin-bottom:20px;
}

h2{
    margin-top:0;
}

.comprar{
    background:#a8f;
    color:#103;
    padding:10px 20px;
    text-decoration:none;
    border-radius:4px;
}
```

Resultado inicial:

```
Produto

Produto

Produto

Produto
```

Todos os itens aparecem um abaixo do outro, pois `<div>` é um elemento de bloco.

---

# Criando o Grid

O Grid deve ser aplicado no elemento que envolve os itens.

```css
.grid{
    display:grid;
}
```

Visualmente nada muda.

Isso ocorre porque ainda existe apenas uma coluna.

---

# grid-template-columns

A propriedade responsável por criar colunas é:

```css
grid-template-columns;
```

Cada valor representa uma coluna.

---

## Colunas com tamanho fixo

```css
.grid{
    display:grid;
    grid-template-columns:200px 200px;
}
```

Resultado:

```
┌───────────┬───────────┐
│ Produto 1 │ Produto 2 │
├───────────┼───────────┤
│ Produto 3 │ Produto 4 │
└───────────┴───────────┘
```

---

## Três colunas

```css
grid-template-columns:
200px
200px
200px;
```

Resultado:

```
200px | 200px | 200px
```

---

# Utilizando porcentagens

Também é possível utilizar porcentagem.

```css
grid-template-columns:50% 50%;
```

Inicialmente funciona.

Porém, quando adicionamos um espaço entre as colunas (`gap`), ocorre um problema:

```
50%
+
50%
+
20px
```

Resultado:

```
100% + 20px
```

O layout ultrapassa o tamanho do container, gerando barra de rolagem horizontal.

Por esse motivo, normalmente não se utiliza porcentagem para dividir colunas em Grid.

---

# Unidade fr

A unidade **fr (fraction)** foi criada exatamente para resolver esse problema.

Ela distribui automaticamente o espaço restante entre as colunas.

```css
grid-template-columns:1fr 1fr;
```

Resultado:

```
┌──────────────┬──────────────┐
│              │              │
└──────────────┴──────────────┘
```

Cada coluna recebe metade do espaço disponível.

---

## Distribuição proporcional

Também é possível distribuir os espaços em proporções diferentes.

```css
grid-template-columns:1fr 2fr;
```

Resultado:

```
┌──────────┬────────────────────┐
│ 1 parte  │      2 partes      │
└──────────┴────────────────────┘
```

Mais exemplos:

```css
1fr 1fr
```

```
50% | 50%
```

```css
1fr 3fr
```

```
25% | 75%
```

```css
2fr 1fr
```

```
66% | 33%
```

---

# gap

O `gap` cria o espaçamento entre linhas e colunas.

```css
gap:20px;
```

Resultado:

```
┌─────────┐    ┌─────────┐
│ Produto │    │ Produto │
└─────────┘    └─────────┘
```

Sem necessidade de utilizar margens entre os elementos.

---

# Gap x Margin

Quando utilizamos Grid, normalmente substituímos:

```css
margin-bottom:20px;
```

por:

```css
gap:20px;
```

Vantagens:

- Espaçamento uniforme
- Funciona nas linhas e colunas
- Código mais limpo
- Não exige margens individuais

---

# Grid dentro de Grid

Um item do Grid também pode ser transformado em outro Grid.

```css
.item{
    display:grid;
}
```

Isso é muito comum em:

- Cards
- Dashboards
- Componentes
- Interfaces modernas

```
Grid Principal

┌─────────────────────┐
│                     │
│     Grid interno    │
│                     │
└─────────────────────┘
```

---

# Mudanças no comportamento dos filhos

Quando um elemento entra em um Grid, ele deixa de seguir completamente o comportamento tradicional de elementos **inline** e **block**.

Por exemplo, um link (`<a>`), que normalmente é um elemento inline, passa a ocupar automaticamente a célula do Grid.

Isso facilita o alinhamento dos elementos sem precisar alterar manualmente propriedades como:

```css
display:inline-block;
```

---

# Margens deixam de colidir

Fora do Grid, margens verticais podem sofrer o fenômeno chamado **Margin Collapse**, onde duas margens se unem e apenas a maior é considerada.

Dentro de um Grid isso não acontece.

Cada item possui seu próprio espaço interno, fazendo com que as margens sejam respeitadas individualmente.

Isso torna o comportamento muito mais previsível.

---

# Organização do HTML

Para aplicar Grid apenas aos produtos, foi criada uma `<div>` envolvendo todos eles.

```html
<div class="grid">

    <div class="item">...</div>

    <div class="item">...</div>

    <div class="item">...</div>

</div>
```

É comum encontrar estruturas como:

```html
<div>
    <div>
        <div>
            ...
        </div>
    </div>
</div>
```

Mais adiante, essas `<div>` podem ser substituídas por elementos semânticos, como:

- `<section>`
- `<article>`
- `<main>`
- `<aside>`

Eles possuem praticamente o mesmo comportamento visual da `<div>`, porém adicionam significado semântico ao documento.

---

# Inspecionando o Grid

As ferramentas de desenvolvedor do navegador permitem visualizar o Grid.

Ao inspecionar um elemento com `display:grid`, é possível ver:

- Linhas
- Colunas
- Gap
- Divisão das células

Esse recurso facilita muito a construção e depuração de layouts.

---

# Exemplo completo

### HTML

```html
<h1>Comércio Eletrônico</h1>

<div class="grid">

    <div class="item">
        <h2>Camisa Polo</h2>
        <p class="preco">R$39</p>
        <p>Camisa polo feita de algodão.</p>
        <a class="comprar" href="/">Comprar</a>
    </div>

    <div class="item">
        <h2>Bermuda Preta</h2>
        <p class="preco">R$59</p>
        <p>Bermuda confortável.</p>
        <a class="comprar" href="/">Comprar</a>
    </div>

    <div class="item">
        <h2>Calça Jeans</h2>
        <p class="preco">R$99</p>
        <p>Calça jeans tradicional.</p>
        <a class="comprar" href="/">Comprar</a>
    </div>

    <div class="item">
        <h2>Casaco Azul</h2>
        <p class="preco">R$149</p>
        <p>Casaco de inverno.</p>
        <a class="comprar" href="/">Comprar</a>
    </div>

</div>
```

### CSS

```css
body{
    font-family:Arial;
}

h1{
    text-align:center;
}

.grid{
    display:grid;
    grid-template-columns:1fr 1fr;
    gap:20px;
}

.item{
    display:grid;
    background:#f7f7f7;
    border:1px solid #e7e7e7;
    padding:20px;
    border-radius:4px;
}

h2{
    margin-top:0;
}

.comprar{
    background:#a8f;
    color:#103;
    padding:10px 20px;
    text-decoration:none;
    border-radius:4px;
}
```

---

# Boas práticas

- Sempre aplique `display:grid` ao elemento pai.
- Utilize `grid-template-columns` para definir as colunas.
- Prefira `fr` ao invés de porcentagens para dividir o espaço.
- Utilize `gap` para espaçamentos entre os itens.
- Evite usar margens para separar elementos quando o Grid puder fazer isso.
- É comum utilizar Grid dentro de Grid em componentes mais complexos.
- Organize corretamente as tags HTML para evitar layouts quebrados.

---

# Resumo

- `display: grid` transforma um elemento em um container Grid.
- Os filhos passam a ser organizados em linhas e colunas.
- `grid-template-columns` define a quantidade e o tamanho das colunas.
- A unidade `fr` distribui o espaço disponível proporcionalmente.
- `gap` cria espaçamentos uniformes entre linhas e colunas.
- Um Grid pode conter outros Grids.
- Elementos dentro do Grid possuem um comportamento diferente dos elementos inline e block tradicionais.
- O Grid é uma das principais ferramentas para construir layouts modernos e responsivos.