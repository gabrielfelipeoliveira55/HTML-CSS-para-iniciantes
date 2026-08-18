# Seletores CSS

> Os **seletores CSS** são utilizados para identificar quais elementos HTML receberão uma ou mais regras de estilo. Existem diversos tipos de seletores, desde os mais simples até os mais avançados. Nesta aula, veremos os seletores mais utilizados no dia a dia.

---

# Seletores por Tipo (Tag)

> O **seletor por tipo** (Type Selector) seleciona todos os elementos de uma determinada tag HTML.

**Sintaxe:**

```css
h1 {
    color: blue;
}
```

### Como funciona

Nesse exemplo, o CSS seleciona **todos os elementos `<h1>`** da página e aplica a cor azul ao seu texto.

**Exemplo HTML:**

```html
<h1>Título Principal</h1>

<h1>Outro Título</h1>
```

**Resultado:**

Todos os elementos `<h1>` serão exibidos na cor azul.

---

# Selecionando Múltiplos Elementos

> É possível aplicar a mesma regra de estilo a diferentes elementos utilizando uma **lista de seletores**, separando-os por vírgulas.

**Sintaxe:**

```css
h1,
p,
a {
    color: red;
}
```

### Como funciona

A vírgula indica que a regra será aplicada individualmente a cada seletor listado.

Nesse exemplo serão selecionados:

- Todos os `<h1>`;
- Todos os `<p>`;
- Todos os `<a>`.

---

# Seletor Descendente

> O **seletor descendente** seleciona elementos que estejam dentro de outro elemento, independentemente do nível de profundidade na árvore do documento.

A sintaxe é formada por um **espaço** entre os seletores.

**Sintaxe:**

```css
p a {
    color: black;
}
```

### Como funciona

Esse seletor significa:

> Selecione todo elemento `<a>` que esteja dentro de um elemento `<p>`.

**Exemplo HTML:**

```html
<p>
    Conheça nosso
    <a href="/">curso</a>.
</p>

<a href="/">Contato</a>
```

Nesse caso, apenas o link que está dentro do `<p>` será estilizado.

---

## Descendentes em vários níveis

Também é possível criar seletores mais específicos.

```css
html body a {
    color: blue;
}
```

Nesse exemplo, será selecionado qualquer elemento `<a>` que esteja dentro do `<body>`, que por sua vez esteja dentro do `<html>`.

> Como todo documento HTML possui essa estrutura, esse seletor acaba selecionando praticamente todos os links da página.

---

# Atributo `id`

> O atributo **`id`** fornece um identificador **único** para um elemento HTML.

Cada documento HTML deve possuir apenas um elemento com determinado valor de `id`.

**Exemplo HTML:**

```html
<h1 id="logo">Minha Empresa</h1>
```

Para selecionar esse elemento no CSS utiliza-se o símbolo **`#`**.

```css
#logo {
    color: gold;
}
```

### Características do `id`

- Deve ser único na página.
- Identifica um único elemento.
- É selecionado utilizando `#`.

---

# Atributo `class`

> O atributo **`class`** identifica um ou mais elementos que compartilham as mesmas características.

Diferentemente do `id`, uma classe pode ser reutilizada em diversos elementos.

**Exemplo HTML:**

```html
<h2 class="codigo">Curso de HTML</h2>

<h2 class="codigo">Curso de CSS</h2>
```

**CSS**

```css
.codigo {
    color: blue;
}
```

Todos os elementos com a classe `codigo` receberão esse estilo.

---

## Diferença entre `id` e `class`

| `id` | `class` |
|------|---------|
| Deve ser único. | Pode ser reutilizada. |
| Identifica um único elemento. | Identifica um grupo de elementos. |
| Utiliza `#`. | Utiliza `.`. |

> Em projetos reais, é muito mais comum utilizar **classes** do que **ids**, pois elas oferecem maior reutilização e flexibilidade.

---

# Combinando Seletores

Assim como ocorre com as tags, também é possível combinar classes utilizando vírgulas.

```css
.codigo,
.design {
    color: blue;
}
```

Nesse exemplo, todos os elementos que possuírem as classes `codigo` **ou** `design` receberão a mesma regra.

---

# Seletores Descendentes com Classes

Também é possível combinar classes utilizando o seletor descendente.

```css
.codigo .design {
    color: red;
}
```

### Como funciona

Esse seletor significa:

> Selecione todo elemento que possua a classe `.design` e que esteja dentro de outro elemento com a classe `.codigo`.

**Exemplo HTML:**

```html
<div class="codigo">
    <h2 class="design">
        Curso
    </h2>
</div>
```

A regra será aplicada apenas porque `.design` está dentro de `.codigo`.

---

# Múltiplas Classes

Um elemento pode possuir mais de uma classe ao mesmo tempo.

As classes devem ser separadas por espaços.

**Exemplo HTML:**

```html
<h2 class="azul grande underline">
    Curso de HTML
</h2>
```

Cada classe adiciona uma responsabilidade diferente.

```css
.azul {
    color: blue;
}

.grande {
    font-size: 32px;
}

.underline {
    text-decoration: underline;
}
```

Nesse exemplo, o elemento receberá todos os estilos das três classes simultaneamente.

---

# Boas Práticas

- Utilize **classes** sempre que o estilo puder ser reutilizado.
- Utilize **ids** apenas quando o elemento for realmente único.
- Evite estilizar diretamente pelas tags em projetos grandes.
- Escolha nomes claros e descritivos para classes e ids.
- Certifique-se de que os nomes utilizados no HTML sejam exatamente iguais aos definidos no CSS, pois qualquer diferença impedirá a aplicação dos estilos.

---

# Resumo

Os seletores apresentados nesta aula foram:

- **Seletor por tipo (Tag)** → `h1`
- **Lista de seletores** → `h1, p, a`
- **Seletor descendente** → `p a`
- **Seletor por ID** → `#logo`
- **Seletor por Classe** → `.codigo`
- **Descendente com Classe** → `.codigo .design`
- **Múltiplas Classes** → `class="azul grande underline"`

