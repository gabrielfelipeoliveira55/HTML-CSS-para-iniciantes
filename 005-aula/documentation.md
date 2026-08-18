# Box Model (Modelo de Caixa)

> No CSS, todos os elementos HTML são renderizados como uma **caixa retangular** (*box*). Esse conceito é conhecido como **Box Model** (Modelo de Caixa) e define como o navegador calcula o espaço ocupado por cada elemento na página.

Mesmo elementos que possuem formatos diferentes, como imagens circulares ou botões arredondados, continuam sendo tratados internamente como caixas retangulares.

---

# Estrutura do Box Model

O Box Model é composto por quatro áreas principais:

```text
┌─────────────────────────────────────────────┐
│                  Margin                     │
│  ┌───────────────────────────────────────┐  │
│  │                Border                 │  │
│  │  ┌─────────────────────────────────┐  │  │
│  │  │            Padding              │  │  │
│  │  │  ┌───────────────────────────┐  │  │  │
│  │  │  │         Content           │  │  │  │
│  │  │  └───────────────────────────┘  │  │  │
│  │  └─────────────────────────────────┘  │  │
│  └───────────────────────────────────────┘  │
└─────────────────────────────────────────────┘
```

A ordem das áreas é sempre:

1. **Content** (Conteúdo)
2. **Padding** (Espaçamento interno)
3. **Border** (Borda)
4. **Margin** (Espaçamento externo)

---

# Content (Conteúdo)

> O **Content** representa a área onde o conteúdo do elemento é exibido.

Esse conteúdo pode ser:

- Texto;
- Imagens;
- Vídeos;
- Outros elementos HTML.

É a partir dessa área que o navegador começa a calcular o tamanho da caixa.

---

# Padding

> O **Padding** é o espaço interno existente entre o conteúdo e a borda do elemento.

```text
┌──────── Border ────────┐
│      Padding           │
│   ┌───────────────┐    │
│   │   Content     │    │
│   └───────────────┘    │
└────────────────────────┘
```

Quanto maior o `padding`, maior será a distância entre o conteúdo e a borda.

**Exemplo:**

```css
div {
    padding: 20px;
}
```

---

# Border

> A **Border** representa a borda do elemento.

Ela pode possuir:

- Espessura;
- Estilo;
- Cor.

**Exemplo:**

```css
div {
    border: 2px solid black;
}
```

A borda envolve completamente o conteúdo e o padding.

---

# Margin

> A **Margin** é o espaço externo da caixa.

Sua função é criar distância entre um elemento e os demais elementos da página.

```text
Elemento A

↓↓ Margin ↓↓

Elemento B
```

**Exemplo:**

```css
div {
    margin: 20px;
}
```

---

# Width (Largura)

> A propriedade **`width`** define a largura da área de conteúdo (*Content*) do elemento.

```css
div {
    width: 300px;
}
```

> Por padrão (`box-sizing: content-box`), o valor de `width` **não inclui** o `padding` nem a `border`. Esses valores são adicionados ao tamanho final da caixa.

---

# Height (Altura)

> A propriedade **`height`** define a altura da área de conteúdo (*Content*).

```css
div {
    height: 150px;
}
```

Assim como ocorre com `width`, o valor definido representa apenas a área de conteúdo.

---

# Como o navegador calcula o tamanho da caixa

Por padrão (`box-sizing: content-box`), o tamanho total ocupado pelo elemento é calculado da seguinte forma:

## Largura Total

```text
Width
+ Padding Esquerdo
+ Padding Direito
+ Border Esquerda
+ Border Direita
```

## Altura Total

```text
Height
+ Padding Superior
+ Padding Inferior
+ Border Superior
+ Border Inferior
```

A **Margin** não faz parte da caixa propriamente dita, mas aumenta o espaço ocupado pelo elemento em relação aos elementos vizinhos.

---

# Unidade `px`

> Nesta aula utilizamos a unidade **`px`** (*pixel*), uma das unidades de medida mais utilizadas no CSS.

Exemplo:

```css
h1 {
    font-size: 32px;
}

div {
    width: 300px;
}
```

---

## O que é um Pixel no CSS?

Embora a unidade seja chamada de **pixel**, um **pixel CSS** não representa necessariamente um único pixel físico da tela.

Dispositivos diferentes possuem diferentes densidades de pixels (*Pixel Density*). Por isso, os navegadores utilizam um **pixel de referência (CSS Pixel)** para manter tamanhos visualmente consistentes entre diferentes telas.

Isso significa que:

- Um elemento com `100px` tende a apresentar aproximadamente o mesmo tamanho visual em diferentes dispositivos.
- O navegador realiza automaticamente os ajustes necessários de acordo com a densidade de pixels da tela.

---

# Resumo

O Box Model é composto por quatro áreas:

- **Content** → conteúdo do elemento.
- **Padding** → espaço interno entre o conteúdo e a borda.
- **Border** → borda do elemento.
- **Margin** → espaço externo entre os elementos.

Além disso:

- `width` define a largura da área de conteúdo.
- `height` define a altura da área de conteúdo.
- O tamanho final da caixa depende da combinação entre conteúdo, padding e borda.
- A unidade `px` representa um **pixel CSS**, adaptado para manter uma aparência consistente em diferentes dispositivos.

# Comportamento de Elementos de Bloco

> Elementos de bloco (*Block-level Elements*) ocupam, por padrão, toda a largura disponível do elemento pai e iniciam em uma nova linha.

Nesta aula utilizamos a tag `<div>` para compreender melhor esse comportamento.

---

## A Tag `<div>`

> A tag `<div>` é um elemento genérico utilizado para agrupar outros elementos HTML. Ela **não possui significado semântico**, sendo utilizada principalmente para organização, estruturação e estilização da página.

**Exemplo:**

```html
<div>
    Conteúdo da página
</div>
```

> A `<div>` é amplamente utilizada em conjunto com o CSS para criar seções, agrupar componentes e organizar o layout da página.

---

# Comportamento Padrão de uma `<div>`

Quando uma `<div>` não possui um valor definido para `width`, seu valor padrão é:

```css
width: auto;
```

Isso faz com que ela ocupe toda a largura disponível do elemento pai.

**Exemplo:**

```css
div {
    background: #aaa;
}
```

Mesmo que o conteúdo seja pequeno:

```html
<div>a</div>
```

A largura continuará ocupando toda a área disponível.

---

# Valor `auto`

O valor `auto` permite que o navegador calcule automaticamente determinadas propriedades.

Nesta aula vimos dois exemplos importantes:

## Width

```css
width: auto;
```

O navegador calcula automaticamente a largura disponível dentro do elemento pai.

---

## Height

```css
height: auto;
```

A altura é calculada automaticamente de acordo com a quantidade de conteúdo existente no elemento.

Quanto mais conteúdo existir, maior será a altura.

**Exemplo:**

```html
<h1>
    Front End
    Teste
    Teste
</h1>
```

Se o conteúdo ocupar mais linhas, a altura aumentará automaticamente.

---

# Definindo Dimensões Fixas

É possível substituir o valor automático por valores específicos.

**Exemplo:**

```css
div {
    width: 140px;
    height: 80px;
}
```

Nesse caso:

- A largura permanecerá em **140px**.
- A altura permanecerá em **80px**.

Independentemente da quantidade de conteúdo, essas dimensões serão respeitadas. Caso o conteúdo ultrapasse o espaço disponível, o navegador aplicará seu comportamento padrão de renderização (assunto que será aprofundado posteriormente).

---

# Margens Colapsadas (Margin Collapsing)

> Quando dois elementos de bloco estão empilhados verticalmente, suas margens superior e inferior podem **colapsar** (*Margin Collapsing*).

Nesse caso, as margens **não são somadas**.

O navegador utiliza apenas o maior valor entre elas.

**Exemplo:**

```css
div {
    margin-bottom: 30px;
}

h1 {
    margin-top: 40px;
}
```

A distância final entre os elementos será:

```text
40px
```

E não:

```text
70px
```

Da mesma forma:

```css
div {
    margin-bottom: 30px;
}

h1 {
    margin-top: 20px;
}
```

A distância continuará sendo:

```text
30px
```

> Esse comportamento é chamado de **Margin Collapsing** e ocorre apenas em situações específicas envolvendo margens verticais de elementos de bloco.

---

# Margem Padrão do Navegador

> Os navegadores aplicam uma folha de estilos padrão (*User Agent Stylesheet*), adicionando estilos iniciais a diversos elementos HTML.

Um exemplo é a margem aplicada ao elemento `<body>`.

Por isso, é comum remover essa margem no início do desenvolvimento.

```css
body {
    margin: 0;
}
```

Essa prática elimina o espaçamento padrão aplicado pelo navegador e permite maior controle sobre o layout da página.

---

# Conteúdo e Quebra de Linha

Quando a largura de um elemento é insuficiente para acomodar todo o conteúdo, o navegador realiza automaticamente a quebra de linha.

**Exemplo:**

```css
h1 {
    width: 100px;
}
```

Caso o texto seja maior que a largura disponível, ele será distribuído em novas linhas, aumentando automaticamente a altura do elemento quando `height` estiver com o valor padrão (`auto`).

---

# Overflow Horizontal

> Se um elemento possuir uma largura maior do que a área disponível da janela do navegador, poderá surgir uma barra de rolagem horizontal.

**Exemplo:**

```css
div {
    width: 2000px;
}
```

Na maioria dos projetos, procura-se evitar esse comportamento, desenvolvendo interfaces adaptáveis (*responsivas*) que se ajustem ao tamanho da tela do usuário.

---

# Resumo

Nesta aula aprendemos que:

- A `<div>` é um elemento genérico utilizado para agrupar conteúdo.
- Elementos de bloco possuem `width: auto` por padrão.
- `height: auto` cresce conforme o conteúdo.
- É possível definir larguras e alturas fixas.
- Margens verticais podem colapsar (*Margin Collapsing*).
- O `<body>` recebe uma margem padrão do navegador.
- Conteúdos maiores que a largura disponível quebram automaticamente em novas linhas.
- Larguras excessivas podem gerar rolagem horizontal, algo normalmente evitado em layouts responsivos.