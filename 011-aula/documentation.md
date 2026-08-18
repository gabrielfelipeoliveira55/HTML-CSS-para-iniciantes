# CSS Grid — Alinhamento de Conteúdo (`justify-content`, `align-content` e `place-content`)

## O que é o alinhamento no Grid?

Após criar as colunas e linhas com **CSS Grid**, é possível controlar **onde todo o conjunto de colunas será posicionado dentro do container** quando existir espaço livre.

As propriedades responsáveis por isso são:

- `justify-content` → alinha o grid no eixo horizontal.
- `align-content` → alinha o grid no eixo vertical.
- `place-content` → atalho para definir `align-content` e `justify-content` ao mesmo tempo.

> **Importante:** Essas propriedades alinham **o conjunto das colunas e linhas**, e **não** os elementos individualmente.

---

# Quando o alinhamento funciona?

Essas propriedades **só produzem efeito quando existe espaço sobrando dentro do container**.

Se o Grid já ocupa toda a largura ou altura disponível, não existe espaço para redistribuir, portanto o alinhamento não terá efeito.

Exemplo onde **não existe espaço sobrando**:

```css
.grid{
    display: grid;
    grid-template-columns: 1fr 1fr;
}
```

As unidades `fr` ocupam automaticamente todo o espaço disponível.

Nesse caso:

```css
justify-content: center;
```

não produzirá nenhuma mudança.

---

# Criando espaço para o alinhamento

Para que o alinhamento funcione é necessário utilizar colunas de tamanho fixo (ou qualquer configuração que deixe espaço livre).

Exemplo:

```css
.grid{
    display: grid;
    grid-template-columns: 300px 300px;
}
```

Agora, caso o container seja maior que **600px**, sobrará espaço ao redor das colunas, permitindo que elas sejam alinhadas.

---

# justify-content

Controla o alinhamento do Grid no **eixo horizontal (X)**.

```css
justify-content: valor;
```

## Valores principais

### `start`

Posiciona o Grid no início do container.

```css
.grid{
    justify-content: start;
}
```

Resultado:

```
|███ ███             |
```

---

### `center`

Centraliza o Grid.

```css
.grid{
    justify-content: center;
}
```

Resultado:

```
|      ███ ███       |
```

---

### `end`

Posiciona o Grid no final do container.

```css
.grid{
    justify-content: end;
}
```

Resultado:

```
|             ███ ███|
```

---

### `space-between`

Distribui todo o espaço **entre** as colunas.

```css
.grid{
    justify-content: space-between;
}
```

Resultado:

```
|███          ███|
```

Os itens ficam encostados nas extremidades.

---

### `space-around`

Distribui espaço ao redor das colunas.

```css
.grid{
    justify-content: space-around;
}
```

Resultado:

```
|  ███      ███  |
```

Existe espaço nas laterais e entre as colunas.

---

### `space-evenly`

Distribui espaços iguais em todas as direções.

```css
.grid{
    justify-content: space-evenly;
}
```

Resultado:

```
|   ███   ███   |
```

O espaço entre as bordas e entre as colunas permanece uniforme.

---

### `stretch`

É o comportamento padrão.

O Grid tenta expandir as colunas para ocupar o espaço disponível.

Quando utilizamos:

```css
1fr
```

ou

```css
auto
```

esse comportamento normalmente já acontece automaticamente.

---

# Utilizando `auto`

Outra forma de definir as colunas é utilizando:

```css
grid-template-columns: auto auto;
```

Nesse caso, cada coluna terá largura baseada no **maior conteúdo existente dentro dela**.

Exemplo:

```css
grid-template-columns: auto auto;
justify-content: center;
```

As colunas passam a ocupar apenas o espaço necessário para acomodar seu conteúdo e, como sobra espaço no container, o alinhamento funciona normalmente.

---

## Como o `auto` calcula a largura?

O Grid observa todos os elementos da coluna e utiliza o maior conteúdo como referência.

Se um texto for maior que os demais:

```html
<p>Descrição muito maior que as outras...</p>
```

a coluna inteira aumentará de largura para acomodá-lo.

---

## Diferença entre `auto` e `1fr`

### `auto`

- largura baseada no conteúdo;
- pode deixar espaço livre;
- permite o funcionamento do `justify-content`.

```css
grid-template-columns: auto auto;
```

---

### `1fr`

- divide todo o espaço disponível;
- normalmente não sobra espaço;
- o alinhamento horizontal praticamente não possui efeito.

```css
grid-template-columns: 1fr 1fr;
```

---

# align-content

Alinha o Grid no **eixo vertical (Y)**.

```css
align-content: valor;
```

Os valores disponíveis são praticamente os mesmos:

- `start`
- `center`
- `end`
- `space-between`
- `space-around`
- `space-evenly`
- `stretch`

---

## Por que normalmente não acontece nada?

Por padrão, a altura do Grid é exatamente a altura do conteúdo.

Exemplo:

```css
.grid{
    display:grid;
}
```

Como não existe espaço vertical sobrando, o alinhamento não tem efeito.

---

## Criando espaço vertical

Basta aumentar a altura do container.

```css
.grid{
    height: 800px;
}
```

Agora é possível utilizar:

```css
align-content: center;
```

Resultado:

Todo o Grid ficará centralizado verticalmente.

Também é possível utilizar:

```css
align-content: end;
```

ou

```css
align-content: space-evenly;
```

que distribuirão o espaço vertical conforme o valor escolhido.

---

# place-content

É um atalho para definir simultaneamente:

- `align-content`
- `justify-content`

Sintaxe:

```css
place-content: align justify;
```

Exemplo:

```css
place-content: center space-evenly;
```

Equivale a:

```css
align-content: center;
justify-content: space-evenly;
```

---

## Utilizando apenas um valor

Quando apenas um valor é informado:

```css
place-content: center;
```

O mesmo valor será aplicado aos dois eixos.

Equivale a:

```css
align-content: center;
justify-content: center;
```

Outro exemplo:

```css
place-content: start;
```

Equivale a:

```css
align-content: start;
justify-content: start;
```

---

# Resumo

## `justify-content`

Alinha todo o Grid na horizontal.

```css
justify-content: center;
```

---

## `align-content`

Alinha todo o Grid na vertical.

```css
align-content: center;
```

---

## `place-content`

Atalho para definir ambos.

```css
place-content: center space-evenly;
```

---

## O alinhamento só funciona quando houver espaço livre

✔ Funciona:

```css
grid-template-columns: 300px 300px;
```

✘ Não produz efeito:

```css
grid-template-columns: 1fr 1fr;
```

porque as colunas já ocupam toda a largura disponível.

---

# Boas práticas

- Utilize `1fr` quando desejar que as colunas ocupem todo o espaço disponível.
- Utilize tamanhos fixos ou `auto` quando precisar alinhar o Grid dentro do container.
- Prefira `gap` para controlar o espaçamento entre linhas e colunas.
- Utilize `place-content` quando quiser configurar alinhamento horizontal e vertical de forma mais concisa.
```