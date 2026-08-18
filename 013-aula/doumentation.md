# Resumo — Alinhamento dos Itens no CSS Grid

## Alinhamento do conteúdo × Alinhamento dos itens

No CSS Grid existem dois tipos principais de alinhamento:

- **Alinhar o conteúdo do Grid** → `justify-content` e `align-content` (visto anteriormente).
- **Alinhar os itens do Grid** → `justify-items`, `align-items`, `place-items`, `justify-self`, `align-self` e `place-self`.

Nesta aula o foco é o alinhamento dos **Grid Items**.

---

## Por que alinhar os itens?

Por padrão, um Grid Item ocupa **100% da largura e da altura disponíveis dentro da sua célula** (`stretch`).

Isso significa que elementos como:

- `h1`
- `span`
- `a`

expandem para preencher toda a área da célula.

Exemplo:

```css
.grid{
    display: grid;
}
```

Mesmo um `<span>`, que normalmente é um elemento inline, passa a ocupar toda a célula do Grid.

---

# align-items

Alinha todos os itens **na vertical** (eixo Y).

Aplicado no **container Grid**.

```css
.grid{
    align-items: center;
}
```

Valores comuns:

- `start`
- `center`
- `end`
- `stretch` (padrão)

---

# justify-items

Alinha todos os itens **na horizontal** (eixo X).

```css
.grid{
    justify-items: center;
}
```

Valores:

- `start`
- `center`
- `end`
- `stretch`

---

# place-items

É um atalho para:

```css
align-items + justify-items
```

Sintaxe:

```css
.grid{
    place-items: center;
}
```

Equivale a:

```css
.grid{
    align-items: center;
    justify-items: center;
}
```

Também aceita dois valores:

```css
.grid{
    place-items: start end;
}
```

Leitura:

- `start` → alinhamento vertical.
- `end` → alinhamento horizontal.

---

# align-self

Permite alinhar **apenas um Grid Item** na vertical.

Aplicado diretamente no elemento.

```css
.preco{
    align-self: start;
}
```

---

# justify-self

Permite alinhar **apenas um Grid Item** na horizontal.

```css
.preco{
    justify-self: end;
}
```

---

# place-self

Atalho para:

```css
align-self + justify-self
```

Exemplo:

```css
.preco{
    place-self: start end;
}
```

Leitura:

- `start` → topo da célula.
- `end` → lado direito da célula.

---

# text-align × justify-self

É importante entender que existe diferença entre:

## Alinhar a caixa do elemento

```css
justify-self: end;
```

Move **o elemento inteiro** dentro da célula do Grid.

---

## Alinhar apenas o texto

```css
text-align: right;
```

Move somente o conteúdo de texto, mantendo a caixa do elemento na mesma posição.

---

## Exemplo

```css
h1{
    text-align: right;
}
```

O texto será alinhado à direita, mas o elemento continuará ocupando toda a largura da célula.

---

# Resumo Final

- `align-items` → alinha todos os itens na vertical.
- `justify-items` → alinha todos os itens na horizontal.
- `place-items` → atalho para `align-items` + `justify-items`.
- `align-self` → alinha apenas um item na vertical.
- `justify-self` → alinha apenas um item na horizontal.
- `place-self` → atalho para `align-self` + `justify-self`.
- `text-align` alinha apenas o conteúdo do elemento, enquanto `justify-self` e `align-self` movimentam a caixa inteira do Grid Item.
- Por padrão, os Grid Items utilizam `stretch`, ocupando toda a área disponível dentro da célula.