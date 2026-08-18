# CSS Grid - Linhas (Rows), Posicionamento Vertical e Organização do Layout

## Controlando o tamanho das linhas

Até esse momento, apenas as colunas estavam sendo configuradas (`grid-template-columns`). As linhas eram criadas automaticamente conforme surgiam novos elementos.

Agora é possível:

- Definir o tamanho das linhas.
- Controlar o tamanho das linhas criadas automaticamente.
- Posicionar elementos em linhas específicas.
- Melhorar a estrutura do layout utilizando Grid.

---

# grid-template-rows

Define o tamanho das linhas existentes do Grid.

```css
.grid {
    display: grid;
    grid-template-columns: 1fr 2fr;
    grid-template-rows: auto auto auto;
}
```

Também pode receber valores fixos.

```css
.grid {
    grid-template-rows: 300px 200px;
}
```

Nesse exemplo:

- Primeira linha → 300px
- Segunda linha → 200px
- As próximas linhas continuam sendo criadas automaticamente (`auto`).

---

## Importante

Se uma linha possuir um tamanho menor que o conteúdo necessário, o conteúdo irá ultrapassar ("estourar") seus limites.

Exemplo:

```css
grid-template-rows: 200px;
```

Se a imagem ou texto precisar de mais espaço que 200px, ele não será reduzido automaticamente.

Resultado:

- imagens estouram;
- textos ultrapassam a área;
- layout quebra.

Por isso, normalmente utiliza-se:

```css
auto
```

---

# grid-auto-rows

Define o tamanho das linhas criadas automaticamente.

Exemplo:

```css
.grid{
    grid-auto-rows:200px;
}
```

Toda nova linha criada automaticamente terá:

```text
200px
```

Pode ser combinado com `grid-template-rows`.

```css
.grid{
    grid-template-rows:300px auto;
    grid-auto-rows:200px;
}
```

Resultado:

Linha 1

```text
300px
```

Linha 2

```text
auto
```

Todas as próximas

```text
200px
```

---

# repeat()

Evita repetir vários valores iguais.

Em vez de escrever:

```css
grid-template-columns:1fr 1fr;
```

Pode escrever:

```css
grid-template-columns:repeat(2,1fr);
```

Outro exemplo:

```css
grid-template-columns:repeat(4,1fr);
```

Equivale a:

```css
1fr 1fr 1fr 1fr
```

Também funciona nas linhas.

```css
grid-template-rows:repeat(3,200px);
```

Equivale a:

```css
200px 200px 200px
```

---

# grid-row

Posiciona um item em uma linha específica.

Exemplo:

```css
.preco{
    grid-row:3;
}
```

O elemento será colocado na terceira linha do Grid.

Também pode ser combinado com coluna.

```css
.preco{
    grid-column:2;
    grid-row:2;
}
```

---

# grid-area

Atalho para definir posição do elemento.

Exemplo:

```css
grid-area:2 / 2;
```

Equivale a:

```css
grid-row:2;
grid-column:2;
```

---

# Expandindo um elemento em várias linhas

Assim como existe:

```css
grid-column
```

Também existe:

```css
grid-row
```

É possível fazer uma imagem ocupar diversas linhas.

```css
.foto{
    grid-row:2 / 4;
}
```

Ela começa na linha 2 e termina na linha 4.

Visualmente:

```text
Linha 1

Título

---------------------

Linha 2

Imagem | Preço

---------------------

Linha 3

Imagem | Descrição

---------------------
```

---

# Misturando linhas automáticas e fr

É possível controlar exatamente quais linhas serão automáticas e quais ocuparão o espaço restante.

```css
grid-template-rows:
repeat(3,auto)
1fr;
```

Resultado:

Linha 1

```text
auto
```

Linha 2

```text
auto
```

Linha 3

```text
auto
```

Linha 4

```text
1fr
```

Assim:

- conteúdo define a altura das três primeiras linhas;
- o restante da altura disponível fica para a última linha.

---

# Problema de layouts muito complexos

É possível construir layouts inteiros apenas posicionando elementos com:

- grid-column
- grid-row

Porém isso rapidamente gera código difícil de manter.

Exemplo:

```css
.foto{
    grid-row:2/5;
}

.comprar{
    grid-column:2;
}

.descricao{
    grid-column:2;
}

.preco{
    grid-column:2;
}
```

Apesar de funcionar, o código fica complexo.

---

# Melhor solução: melhorar o HTML

Em vez de posicionar vários elementos individualmente, agrupe-os.

Exemplo:

```html
<div class="grid">

    <h1>Nimbus Stark</h1>

    <img class="foto">

    <div class="info">

        <span class="preco"></span>

        <p class="descricao"></p>

        <a class="comprar"></a>

    </div>

</div>
```

Agora o Grid possui apenas:

- título;
- imagem;
- bloco de informações.

Isso reduz bastante a quantidade de posicionamentos.

---

# Transformando a div interna em Grid

Depois basta transformar apenas a área das informações em outro Grid.

```css
.info{
    display:grid;
}
```

Assim é possível controlar somente os elementos internos.

Exemplo:

```css
.info{
    display:grid;
    gap:20px;
    place-items:start;
}
```

---

# place-self

Alinha apenas um item específico dentro do Grid.

```css
.info{
    place-self:start;
}
```

Isso impede que a `<div>` ocupe toda a altura disponível e mantém o conteúdo alinhado ao topo.

---

# gap

Depois de organizar a estrutura basta adicionar o espaçamento.

```css
.info{
    gap:20px;
}
```

---

# Organização do código

Uma boa estrutura HTML reduz drasticamente a complexidade do CSS.

Em vez de criar diversos posicionamentos com `grid-row` e `grid-column`, normalmente é melhor:

1. Organizar melhor o HTML.
2. Criar grupos (`div`, `section`, etc.).
3. Aplicar `display: grid` apenas onde realmente for necessário.

Isso resulta em:

- menos código;
- código mais legível;
- manutenção mais simples;
- layouts mais fáceis de modificar futuramente.

---

# Resumo

## grid-template-rows

Define o tamanho das linhas existentes.

```css
grid-template-rows:auto auto 1fr;
```

---

## grid-auto-rows

Define o tamanho das novas linhas criadas automaticamente.

```css
grid-auto-rows:200px;
```

---

## repeat()

Evita repetir valores.

```css
repeat(4,1fr)
```

---

## grid-row

Posiciona um elemento em uma linha.

```css
grid-row:3;
```

ou

```css
grid-row:2/5;
```

---

## grid-area

Atalho para definir linha e coluna.

```css
grid-area:2/2;
```

---

## place-self

Alinha apenas um item.

```css
place-self:start;
```

---

## Boa prática

Antes de criar um Grid muito complexo:

- reorganize o HTML;
- agrupe elementos relacionados;
- utilize um Grid interno (`display:grid`) quando necessário.

Na maioria dos casos, uma boa estrutura HTML produz um CSS muito mais simples e fácil de manter.