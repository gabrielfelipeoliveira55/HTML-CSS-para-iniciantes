# A Propriedade `display`

> A propriedade **`display`** define como um elemento será exibido na página e como ele participará do fluxo de layout.

Cada elemento HTML possui um valor de `display` padrão, definido pela folha de estilos do navegador (*User Agent Stylesheet*). No entanto, esse comportamento pode ser alterado através do CSS.

**Sintaxe:**

```css
display: valor;
```

---

# Fluxo do Documento (Normal Flow)

> Por padrão, os elementos são posicionados seguindo o **fluxo normal do documento** (*Normal Flow*).

Na maioria dos idiomas, como português e inglês, o conteúdo é organizado:

- De cima para baixo;
- Da esquerda para a direita.

Cada elemento é inserido na página seguindo esse fluxo, respeitando seu tipo de exibição (`display`).

---

# `display: inline`

> Elementos com `display: inline` são exibidos na mesma linha, acompanhando o fluxo natural do texto.

Eles ocupam apenas o espaço necessário para seu conteúdo.

**Exemplo:**

```css
span {
    display: inline;
}
```

Características:

- Não iniciam uma nova linha.
- Ocupam apenas o espaço do conteúdo.
- Permitem que outros elementos `inline` fiquem ao seu lado.

---

## Limitações do `inline`

Elementos `inline` não aceitam algumas propriedades de dimensionamento da mesma forma que elementos de bloco.

Por exemplo:

```css
span {
    width: 200px;
    height: 100px;
}
```

Esses valores não produzem o efeito esperado.

Além disso:

- `margin-top`
- `margin-bottom`

não alteram o posicionamento vertical do elemento como ocorre em elementos de bloco.

> As propriedades horizontais, como `padding-left`, `padding-right`, `margin-left` e `margin-right`, continuam funcionando normalmente.

---

# `display: block`

> Elementos com `display: block` iniciam uma nova linha e, por padrão, ocupam toda a largura disponível do elemento pai.

Além disso, aceitam normalmente propriedades como:

- `width`
- `height`
- `margin`
- `padding`

Esse comportamento torna os elementos de bloco ideais para estruturar seções e componentes da página.

---

# `display: inline-block`

> O valor **`inline-block`** combina características dos elementos `inline` e `block`.

O elemento:

- permanece na mesma linha que outros elementos (`inline`);
- aceita propriedades de dimensionamento e espaçamento (`block`).

**Exemplo:**

```css
a {
    display: inline-block;
    padding: 20px;
}
```

Esse comportamento é bastante utilizado quando um elemento precisa permanecer na mesma linha, mas também necessita de largura, altura ou espaçamentos personalizados.

---

# `display: none`

> O valor **`none`** remove completamente o elemento da renderização da página.

```css
display: none;
```

Quando aplicado:

- o elemento deixa de ser exibido;
- deixa de ocupar espaço no layout.

Esse recurso é muito utilizado em interfaces dinâmicas, como menus, modais e componentes controlados por JavaScript.

---

# Alterando o Tipo de Exibição

O valor de `display` pode ser alterado independentemente da tag utilizada.

Por exemplo, um link pode passar a se comportar como um elemento de bloco:

```css
a {
    display: block;
}
```

Da mesma forma, uma `<div>` pode ser exibida como um elemento inline:

```css
div {
    display: inline;
}
```

Isso demonstra que o comportamento visual de um elemento não depende apenas da sua tag HTML, mas também do valor definido para a propriedade `display`.

---

# Introdução ao `flex` e `grid`

Além dos valores estudados nesta aula, o CSS oferece modos de layout mais avançados.

Os principais são:

```css
display: flex;
```

e

```css
display: grid;
```

Esses modos fornecem ferramentas específicas para organizar e posicionar elementos de maneira mais eficiente, sendo amplamente utilizados no desenvolvimento de layouts modernos.

> Esses conceitos serão estudados em detalhes nas próximas aulas.

---

# Resumo

Nesta aula aprendemos que:

- `display` define como um elemento será exibido.
- `inline` mantém os elementos na mesma linha, mas possui limitações de dimensionamento.
- `block` inicia uma nova linha e aceita normalmente propriedades do Box Model.
- `inline-block` combina características dos modos `inline` e `block`.
- `none` remove completamente o elemento do layout.
- `flex` e `grid` são modos de layout mais avançados, próprios para organizar interfaces complexas.