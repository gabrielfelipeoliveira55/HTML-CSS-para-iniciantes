# CSS Grid — Preparando o Layout para Posicionamento (`grid-column`)

## Objetivo

Antes de aprender a posicionar elementos utilizando **`grid-column`**, é necessário montar uma estrutura organizada que servirá como base para os próximos exemplos.

Nesta etapa, o foco é preparar o HTML e aplicar uma estilização inicial, deixando todos os elementos prontos para serem posicionados dentro do Grid.

---

# Estrutura HTML

O exemplo será composto por um único produto, contendo:

- título;
- preço;
- descrição;
- botão de compra;
- imagem do produto.

Estrutura:

```html
<h1 class="titulo">Nimbus Stark</h1>

<span class="preco">R$ 39</span>

<p class="descricao">
  A Nimbus Stark é a melhor Bikecraft já criada pela nossa equipe.
  Ela vem equipada com os melhores acessórios,
  garantindo maior velocidade.
</p>

<a class="comprar" href="/">Comprar</a>

<img src="./img/bicicleta.jpg" alt="Bicicleta Preta">
```

---

# Alteração do elemento de preço

O preço deixa de utilizar um `<p>` e passa a utilizar um:

```html
<span>
```

O objetivo é mostrar que, dentro do Grid, a diferença entre elementos **inline** e **block** praticamente desaparece, pois o Grid controla o posicionamento dos itens.

---

# Organização do HTML

Alguns elementos recebem classes específicas para facilitar a estilização.

Exemplo:

```html
<h1 class="titulo">
```

```html
<span class="preco">
```

```html
<p class="descricao">
```

Essas classes permitem aplicar estilos diretamente aos elementos desejados.

---

# Inserindo uma imagem

A imagem é adicionada utilizando a tag `<img>`.

```html
<img
    src="./img/bicicleta.jpg"
    alt="Bicicleta Preta">
```

É necessário que o arquivo esteja dentro da pasta:

```text
img/
```

Exemplo da estrutura:

```text
projeto/
│
├── index.html
├── style.css
└── img/
    └── bicicleta.jpg
```

---

# Estilos gerais

Antes de utilizar o Grid, alguns estilos básicos são aplicados ao documento.

## Fonte padrão

```css
body{
    font-family: Arial;
}
```

Define a tipografia utilizada em toda a página.

---

## Margem da página

```css
body{
    margin: 40px;
}
```

Cria um espaçamento entre o conteúdo e as bordas da janela.

---

# Removendo margens padrão

Os títulos e parágrafos possuem margens aplicadas automaticamente pelo navegador.

Para ter maior controle sobre o layout, essas margens são removidas.

```css
h1,
p{
    margin: 0;
}
```

---

# Estilizando o título

```css
h1{
    font-size:48px;
    line-height:1;
}
```

### `font-size`

Define um tamanho maior para destacar o título.

### `line-height`

Controla a altura entre linhas.

Um valor de:

```css
line-height:1;
```

reduz o espaçamento entre linhas caso o título seja quebrado.

---

# Ajustando os textos

Parágrafo:

```css
p{
    font-size:20px;
}
```

Preço:

```css
span{
    font-size:20px;
}
```

Botão:

```css
.comprar{
    font-size:20px;
}
```

Assim todos os textos ficam visualmente equilibrados.

---

# Estilizando o preço

O preço recebe aparência semelhante a uma etiqueta.

```css
.preco{
    background:#ddd;
    padding:5px 10px;
    border-radius:4px;
}
```

### Resultado

- fundo cinza;
- espaçamento interno;
- cantos arredondados.

---

# Ajustando a imagem

Para impedir que a imagem ultrapasse o tamanho disponível:

```css
img{
    max-width:100%;
}
```

## Por que utilizar `max-width:100%`?

A imagem nunca ficará maior que o elemento que a contém.

Isso torna o layout mais responsivo e evita que a imagem ultrapasse os limites da página.

---

## Bordas arredondadas

Também é possível arredondar os cantos da imagem.

```css
img{
    border-radius:4px;
}
```

---

# Organização do CSS

Uma boa prática é separar os estilos em seções.

Exemplo:

```css
/* Estilos Gerais */

body{
    ...
}

h1{
    ...
}

p{
    ...
}
```

Essa organização facilita a leitura e manutenção do código conforme o projeto cresce.

---

# Código CSS produzido nesta etapa

```css
/* Estilos Gerais */

body{
    margin:40px;
    font-family:Arial;
}

h1,
p{
    margin:0;
}

h1{
    font-size:48px;
    line-height:1;
}

p{
    font-size:20px;
}

span{
    font-size:20px;
}

.preco{
    background:#ddd;
    padding:5px 10px;
    border-radius:4px;
}

img{
    max-width:100%;
    border-radius:4px;
}

.comprar{
    font-size:20px;
}
```

---

# Resumo

Nesta etapa foi preparada toda a estrutura necessária para os próximos exemplos de **CSS Grid**.

Foram abordados:

- criação da estrutura HTML do produto;
- utilização de classes para facilitar a estilização;
- inserção da imagem;
- organização dos estilos gerais;
- remoção das margens padrão do navegador;
- ajuste da tipografia;
- criação de uma etiqueta para o preço;
- limitação do tamanho da imagem utilizando `max-width: 100%`;
- organização do CSS em blocos para facilitar a manutenção.

> Com essa base pronta, o próximo passo será utilizar o **`display: grid`** juntamente com **`grid-column`** para controlar exatamente a posição que cada elemento ocupará dentro do layout.


# CSS Grid: Posicionando Itens com `grid-column`

## O que é `grid-column`?

A propriedade `grid-column` é utilizada para **definir a posição e a largura de um item dentro do Grid**. Diferente do `grid-template-columns`, que cria as colunas do layout, o `grid-column` controla apenas um elemento específico.

---

## Preparando o Grid

Primeiro, o elemento pai deve ser transformado em um Grid.

```css
.grid{
    display: grid;
    gap: 20px;
    grid-template-columns: 1fr 1fr;
}
```

Após isso, todos os elementos internos passam a ser **Grid Items**.

---

## O que acontece com os Grid Items?

Quando um elemento se torna um Grid Item:

- ocupa toda a largura da sua célula;
- elementos inline (`span`, `a`, etc.) passam a se comportar como itens de Grid;
- `padding` funciona normalmente;
- o posicionamento dos elementos fica muito mais flexível.

---

## Posicionando um item

Para mover um elemento para uma coluna específica:

```css
.foto{
    grid-column: 2;
}
```

O elemento será colocado na segunda coluna do Grid.

---

## Linhas do Grid

O posicionamento utiliza as **linhas do Grid**, e não o número das colunas.

Exemplo com duas colunas:

```
Linha 1 | Coluna 1 | Linha 2 | Coluna 2 | Linha 3
```

---

## Ocupando várias colunas

Para fazer um elemento ocupar duas colunas:

```css
.foto{
    grid-column: 1 / 3;
}
```

Leitura:

> Comece na linha **1** e termine na linha **3**.

---

## Utilizando `-1`

Em vez de informar a última linha manualmente, pode-se utilizar:

```css
.foto{
    grid-column: 1 / -1;
}
```

O valor `-1` representa **a última linha do Grid**, fazendo com que o elemento ocupe toda a largura disponível, independentemente da quantidade de colunas.

---

## Expandindo com `span`

Outra forma de ocupar várias colunas é utilizando `span`.

```css
.foto{
    grid-column: span 2;
}
```

Leitura:

> Expanda duas colunas a partir da posição atual.

Também é possível combinar posição inicial com expansão:

```css
.foto{
    grid-column: 2 / span 3;
}
```

Leitura:

> Comece na linha **2** e ocupe **3 colunas**.

---

## Inspecionando o Grid

O DevTools permite visualizar:

- linhas numeradas;
- colunas;
- áreas ocupadas pelos elementos.

Essa visualização facilita entender exatamente onde cada item está sendo posicionado.

---

# Resumo Final

- `display: grid` transforma o elemento pai em um Grid.
- Todos os filhos tornam-se **Grid Items**.
- `grid-column` posiciona um item dentro das colunas.
- O posicionamento utiliza as **linhas** do Grid.
- `grid-column: 2` posiciona o item na segunda coluna.
- `grid-column: 1 / 3` faz o item ocupar duas colunas.
- `grid-column: 1 / -1` ocupa toda a largura do Grid.
- `span` expande um item por um número específico de colunas.
- O DevTools ajuda a visualizar linhas, colunas e o posicionamento dos itens.