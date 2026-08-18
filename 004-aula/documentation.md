# Cores e Plano de Fundo no CSS

> O CSS oferece diversas formas de definir cores para textos, planos de fundo e outros elementos. Nesta aula, conheceremos a propriedade `background`, a propriedade `color` e os principais formatos de representação de cores.

---

# Propriedade `background`

> A propriedade **`background`** é uma **propriedade abreviada (shorthand)** utilizada para definir características do plano de fundo de um elemento.

Nesta aula utilizaremos apenas a cor de fundo, embora essa propriedade também possa definir imagem, posição, repetição, tamanho e outras configurações que serão estudadas futuramente.

Também é possível utilizar a propriedade específica:

```css
background-color: blue;
```

ou sua forma abreviada:

```css
background: blue;
```

Neste caso, ambas produzem o mesmo resultado.

**Exemplo:**

```css
h1 {
    background: red;
}
```

> O plano de fundo será aplicado apenas ao elemento selecionado.

---

# Propriedade `color`

> A propriedade **`color`** define a cor do texto (conteúdo) de um elemento.

**Exemplo:**

```css
h1 {
    color: white;
}
```

---

# Formas de Representar Cores

O CSS aceita diversos formatos para representar uma cor.

Nesta aula foram apresentados os principais.

---

## 1. Nome da Cor (Color Keywords)

Consiste em utilizar o nome da cor em inglês.

**Exemplo:**

```css
h1 {
    background: red;
    color: white;
}
```

Algumas cores disponíveis:

- `red`
- `blue`
- `green`
- `white`
- `black`
- `yellow`
- `gray`
- `purple`
- `seagreen`

> O CSS possui uma lista padronizada de nomes de cores reconhecidos pelos navegadores.

---

## 2. Hexadecimal

> O formato hexadecimal representa uma cor utilizando números e letras precedidos pelo símbolo `#`.

A forma mais comum utiliza **seis caracteres**.

```css
#8844ee
```

Cada par de caracteres representa uma intensidade das cores:

- Vermelho (Red)
- Verde (Green)
- Azul (Blue)

### Exemplos

Preto:

```css
#000000
```

Branco:

```css
#ffffff
```

Roxo:

```css
#8844ee
```

---

### Forma abreviada

Quando cada par possui caracteres iguais, é possível utilizar apenas três caracteres.

```css
#fff
```

equivale a

```css
#ffffff
```

Outro exemplo:

```css
#84e
```

equivale a

```css
#8844ee
```

---

## 3. RGB

> A função **`rgb()`** representa uma cor informando a intensidade das cores Vermelho (Red), Verde (Green) e Azul (Blue).

Cada valor varia entre **0** e **255**.

**Sintaxe:**

```css
rgb(red, green, blue)
```

**Exemplos:**

Preto:

```css
rgb(0, 0, 0)
```

Branco:

```css
rgb(255, 255, 255)
```

Vermelho:

```css
rgb(255, 0, 0)
```

Amarelo:

```css
rgb(255, 255, 0)
```

---

## 4. RGBA

> A função **`rgba()`** funciona da mesma forma que o `rgb()`, porém adiciona um quarto parâmetro chamado **canal alfa (Alpha)**.

Esse valor controla a opacidade da cor.

**Sintaxe:**

```css
rgba(red, green, blue, alpha)
```

O valor **alpha** varia entre:

- `0` → totalmente transparente.
- `1` → totalmente opaco.

Também é possível utilizar valores intermediários.

**Exemplos:**

```css
rgba(0, 0, 0, 1)
```

Preto totalmente opaco.

```css
rgba(0, 0, 0, 0.5)
```

Preto com 50% de transparência.

```css
rgba(0, 0, 0, 0)
```

Totalmente transparente.

---

# Exemplo Completo

```css
h1 {
    background: #8844ee;
    color: #ffffff;
}

a {
    background: seagreen;
    color: white;
}
```

---

# Resumo

Nesta aula conhecemos:

- `background` → define o plano de fundo do elemento.
- `background-color` → define especificamente a cor do plano de fundo.
- `color` → define a cor do texto.
- **Color Keywords** → nomes de cores.
- **Hexadecimal (`#RRGGBB`)** → formato mais utilizado para representar cores.
- **RGB (`rgb()`)** → define uma cor pela intensidade de vermelho, verde e azul.
- **RGBA (`rgba()`)** → adiciona transparência (canal alfa) ao RGB.