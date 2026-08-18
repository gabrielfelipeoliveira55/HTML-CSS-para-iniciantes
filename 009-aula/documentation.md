# Shorthand de Margin, Padding e Border

## Introdução

As propriedades `margin`, `padding` e `border-width` permitem definir espaçamentos e tamanhos para diferentes lados de um elemento.

Em vez de declarar cada lado individualmente, o CSS fornece uma sintaxe abreviada (*shorthand*) que permite configurar vários lados em uma única linha.

---

# Ordem dos Valores

Quando múltiplos valores são informados, o CSS segue sempre a mesma ordem:

```text
top → right → bottom → left
```

Sentido horário:

```text
      top
       ↑
left ←   → right
       ↓
    bottom
```

---

# Padding

A propriedade `padding` define o espaço interno entre o conteúdo e a borda do elemento.

## Um valor

Aplica o mesmo valor para todos os lados.

```css
padding: 20px;
```

Equivale a:

```css
padding-top: 20px;
padding-right: 20px;
padding-bottom: 20px;
padding-left: 20px;
```

---

## Dois valores

```css
padding: 20px 40px;
```

Equivale a:

```css
padding-top: 20px;
padding-bottom: 20px;
padding-right: 40px;
padding-left: 40px;
```

Formato:

```text
padding: vertical horizontal;
```

---

## Quatro valores

```css
padding: 40px 100px 200px 10px;
```

Equivale a:

```css
padding-top: 40px;
padding-right: 100px;
padding-bottom: 200px;
padding-left: 10px;
```

---

# Margin

A propriedade `margin` funciona exatamente da mesma forma, porém controla o espaço externo do elemento.

## Um valor

```css
margin: 30px;
```

Todos os lados recebem o mesmo valor.

---

## Dois valores

```css
margin: 20px 40px;
```

```text
20px → topo e base
40px → direita e esquerda
```

---

## Quatro valores

```css
margin: 10px 20px 30px 40px;
```

```text
top    → 10px
right  → 20px
bottom → 30px
left   → 40px
```

---

# Definindo Lados Individualmente

Quando for necessário maior controle, cada lado pode ser configurado separadamente.

## Padding

```css
padding-top: 20px;
padding-right: 40px;
padding-bottom: 20px;
padding-left: 40px;
```

---

## Margin

```css
margin-top: 20px;
margin-right: 40px;
margin-bottom: 20px;
margin-left: 40px;
```

Essa abordagem é útil quando apenas um lado precisa ser alterado.

---

# Border e seus Lados

A propriedade abreviada `border` combina três valores:

```css
border: 2px solid black;
```

Onde:

```text
2px    → largura
solid  → estilo
black  → cor
```

Por receber múltiplos tipos de valor ao mesmo tempo, ela não aceita a sintaxe de quatro lados como `margin` e `padding`.

---

## Definindo uma borda específica

### Borda superior

```css
border-top: 4px solid blue;
```

### Borda direita

```css
border-right: 4px solid blue;
```

### Borda inferior

```css
border-bottom: 4px solid blue;
```

### Borda esquerda

```css
border-left: 4px solid blue;
```

---

# Border Width

Quando o objetivo é alterar apenas a espessura das bordas, pode-se utilizar `border-width`.

## Um valor

```css
border-width: 10px;
```

Aplica o mesmo valor em todos os lados.

---

## Dois valores

```css
border-width: 10px 20px;
```

```text
10px → topo e base
20px → direita e esquerda
```

---

## Quatro valores

```css
border-width: 10px 20px 30px 40px;
```

```text
top    → 10px
right  → 20px
bottom → 30px
left   → 40px
```

---

# Propriedades Lógicas (Logical Properties)

Além das propriedades tradicionais (`margin-top`, `padding-left`, etc.), o CSS moderno possui propriedades lógicas.

Essas propriedades se adaptam automaticamente ao modo de escrita do documento.

Exemplo:

```css
margin-block-start: 30px;
```

---

## O que significa?

A propriedade:

```css
margin-block-start
```

adiciona margem no início do eixo de bloco (*block axis*).

Em páginas escritas normalmente (português, inglês, espanhol etc.), isso equivale ao topo do elemento.

```text
↓ fluxo normal

margin-block-start
        ↓
      topo
```

---

## Vantagem

Se o modo de escrita mudar utilizando:

```css
writing-mode: vertical-rl;
```

o início do bloco deixa de ser o topo e passa a acompanhar o novo fluxo de leitura.

Assim, a margem continua sendo aplicada corretamente de acordo com a direção do texto.

---

# Propriedades Lógicas Mais Comuns

## Margens

```css
margin-block-start
margin-block-end
margin-inline-start
margin-inline-end
```

---

## Padding

```css
padding-block-start
padding-block-end
padding-inline-start
padding-inline-end
```

---

# Diferença Entre `margin-top` e `margin-block-start`

## Física

```css
margin-top: 30px;
```

Sempre será aplicada no topo físico da página.

---

## Lógica

```css
margin-block-start: 30px;
```

Será aplicada no início do fluxo de escrita atual.

---

# Quando Utilizar?

Na maioria dos projetos em português, inglês ou espanhol, é comum utilizar:

```css
margin-top
margin-right
margin-bottom
margin-left
```

As propriedades lógicas tornam-se especialmente úteis em aplicações multilíngues que precisam suportar diferentes direções de escrita.

---

# Resumo

## Ordem dos Shorthands

```text
top → right → bottom → left
```

---

## Dois Valores

```css
padding: 20px 40px;
```

```text
20px → vertical
40px → horizontal
```

---

## Border por Lado

```css
border-top
border-right
border-bottom
border-left
```

---

## Propriedades Lógicas

```css
margin-block-start
margin-block-end
padding-inline-start
padding-inline-end
```

Adaptam-se automaticamente ao modo de escrita definido pelo documento.

---

## Boas Práticas

- Utilize shorthand quando os valores forem simples.
- Utilize propriedades individuais quando precisar de controle específico.
- Prefira propriedades lógicas em projetos internacionais.
- Mantenha consistência na ordem dos valores (`top → right → bottom → left`).
- Utilize `border-width` quando apenas a espessura das bordas precisar variar.