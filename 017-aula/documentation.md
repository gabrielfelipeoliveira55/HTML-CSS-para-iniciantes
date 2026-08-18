# CSS `position` — `static`, `relative`, `absolute` e `fixed`

## 1. O que é `position`?

A propriedade:

```css id="h9d0bh"
position
```

controla como um elemento participa do **fluxo e do posicionamento do documento**.

Por padrão, os elementos seguem o fluxo normal da página.

Por exemplo:

```html id="9h0s9q"
<h1>Primeiro</h1>
<h1>Segundo</h1>
<h1>Terceiro</h1>
```

Em um fluxo normal:

```text id="vhbs6h"
[ Primeiro ]

[ Segundo ]

[ Terceiro ]
```

Cada elemento ocupa seu espaço e os próximos elementos são posicionados de acordo com ele.

A propriedade `position` permite alterar esse comportamento.

---

# 2. Os principais valores

Nesta etapa, os principais valores estudados são:

```css id="dxnqwl"
position: static;
position: relative;
position: absolute;
position: fixed;
```

Podemos pensar assim:

```text id="0xj95f"
position
   │
   ├── static
   │    └── fluxo normal
   │
   ├── relative
   │    └── posiciona em relação ao próprio local
   │
   ├── absolute
   │    └── sai do fluxo e usa um elemento de referência
   │
   └── fixed
        └── sai do fluxo e fica fixo em relação à janela
```

---

# 3. `position: static`

O valor padrão é:

```css id="z6qj3d"
position: static;
```

Nesse comportamento, o elemento permanece no fluxo normal do documento.

```text id="4s5g89"
Elemento 1
    ↓
Elemento 2
    ↓
Elemento 3
```

É como o navegador normalmente posiciona os elementos.

---

# 4. `top`, `right`, `bottom` e `left`

Existem quatro propriedades muito utilizadas com posicionamento:

```css id="lax0mo"
top
right
bottom
left
```

Elas indicam deslocamentos do elemento.

Exemplo:

```css id="8m0l26"
.elemento {
  top: 20px;
}
```

Porém, existe uma regra fundamental:

> **`top`, `right`, `bottom` e `left` não alteram o posicionamento de um elemento `static` da mesma forma que alteram um elemento posicionado.**

Para utilizá-las de forma efetiva, precisamos alterar o `position`.

Por exemplo:

```css id="pj4f9p"
.elemento {
  position: relative;
  top: 20px;
}
```

---

# 5. `position: relative`

O:

```css id="y4v7p8"
position: relative;
```

mantém o elemento **no fluxo normal**.

Essa é a característica mais importante para memorizar.

Considere:

```text id="s3bq3f"
[A]
[B]
[C]
```

Se `B` receber:

```css id="6xldnp"
position: relative;
top: -20px;
```

ele será deslocado visualmente para cima:

```text id="g6bqsh"
[A]
[B] ← deslocado visualmente
[C]
```

Mas o espaço original de `B` continua reservado.

---

# 6. `relative` não remove o espaço do elemento

Considere:

```css id="w90f84"
.item {
  position: relative;
  top: -40px;
}
```

O item sobe:

```text id="p6s0t6"
      [ ITEM ]
         ↑
      -40px
```

Porém, o espaço onde ele estaria originalmente continua existindo.

Podemos imaginar:

```text id="1b7m8m"
┌───────────────┐
│ espaço original│
│                │
└───────────────┘
       ↑
       │
   elemento
   deslocado
```

### Regra mental

> **`relative` move visualmente, mas continua ocupando seu espaço original.**

---

# 7. `relative` é relativo ao próprio local

Quando temos:

```css id="09cm9w"
.elemento {
  position: relative;
}
```

e não definimos:

```css id="m7n0cs"
top
left
right
bottom
```

nada muda visualmente.

```css id="a1vr2l"
.elemento {
  position: relative;
}
```

O elemento continua exatamente no local onde estava.

Só depois podemos deslocá-lo:

```css id="alry5h"
.elemento {
  position: relative;
  top: -20px;
}
```

Agora ele é deslocado em relação à sua posição original.

---

# 8. Exemplo com `top`

```css id="3t2wnm"
.elemento {
  position: relative;
  top: -20px;
}
```

Resultado:

```text id="f8u1a0"
posição original
      ↓
[ elemento ]

      ↑
   20px

posição visual
[ elemento ]
```

O espaço original continua reservado.

---

# 9. `relative` também pode usar `bottom`

Podemos utilizar:

```css id="j8y1uv"
.elemento {
  position: relative;
  bottom: 20px;
}
```

Também podemos utilizar:

```css id="d0w21l"
left
```

e:

```css id="td7lr6"
right
```

A ideia geral:

```text id="r9qgl1"
position: relative
        │
   ┌────┼────┐
   ↓    ↓    ↓
 top   left  right
   │
 bottom
```

---

# 10. `position: fixed`

Agora temos:

```css id="arxyxw"
position: fixed;
```

Essa é a opção adequada quando queremos que um elemento fique **fixo em relação à janela de visualização**.

Exemplos comuns:

* modal;
* aviso fixo;
* barra fixa;
* mensagem de cookies;
* botão flutuante.

---

# 11. `fixed` remove o elemento do fluxo

Quando usamos:

```css id="kccjwa"
.elemento {
  position: fixed;
}
```

o elemento deixa de ocupar o espaço original no fluxo normal.

Antes:

```text id="2mmg1p"
[A]
[B]
[C]
```

Depois que `B` recebe `fixed`:

```text id="zjdwvj"
[A]
[C]
```

Enquanto `B` é posicionado separadamente:

```text id="56x7ti"
[B]
```

Ele não reserva mais o espaço onde estaria originalmente.

### Regra mental

```text id="ao7ve7"
relative
→ mantém o espaço

fixed
→ remove do fluxo
```

---

# 12. `fixed` precisa de uma referência de posicionamento

Quando usamos:

```css id="x9n7l5"
position: fixed;
```

o elemento pode não aparecer onde esperamos imediatamente.

Precisamos informar sua posição usando:

```css id="bq6qwd"
top
right
bottom
left
```

Por exemplo:

```css id="q0ep5r"
.fixo {
  position: fixed;
  top: 0;
  left: 0;
}
```

Agora o elemento ficará no canto superior esquerdo da janela.

---

# 13. `top: 0`

```css id="t3m4hz"
.fixo {
  position: fixed;
  top: 0;
}
```

significa:

```text id="97y5h8"
distância do topo
      ↓
     0px
```

O elemento será posicionado no topo da área de visualização.

---

# 14. `left: 0`

Podemos adicionar:

```css id="3dksq0"
left: 0;
```

Agora:

```css id="qfmf8v"
.fixo {
  position: fixed;
  top: 0;
  left: 0;
}
```

O elemento ficará no canto superior esquerdo:

```text id="q0wxqp"
┌─────────────────────────────────┐
│ [ ELEMENTO ]                    │
│                                 │
│                                 │
└─────────────────────────────────┘
```

---

# 15. `right: 0`

Podemos trocar:

```css id="5g8i5s"
left: 0;
```

por:

```css id="2f09dv"
right: 0;
```

Agora:

```text id="lxl7xi"
┌─────────────────────────────────┐
│                     [ ELEMENTO ]│
│                                 │
│                                 │
└─────────────────────────────────┘
```

---

# 16. Distâncias diferentes de zero

Não precisamos utilizar somente `0`.

Podemos utilizar:

```css id="pp0wyv"
top: 20px;
left: 20px;
```

Isso significa:

```text id="o6nnmx"
20px do topo
20px da esquerda
```

Visualmente:

```text id="al4lve"
┌─────────────────────────────────┐
│      20px                        │
│      ┌────────────┐              │
│ 20px │  elemento  │              │
│      └────────────┘              │
└─────────────────────────────────┘
```

---

# 17. `top` + `left`

Com:

```css id="1pv604"
position: fixed;
top: 20px;
left: 20px;
```

o elemento fica:

```text id="1n4no9"
20px abaixo do topo
+
20px afastado da esquerda
```

---

# 18. `top` + `right`

Podemos fazer:

```css id="bi3nnp"
position: fixed;
top: 20px;
right: 20px;
```

Resultado:

```text id="kjj92i"
┌─────────────────────────────────┐
│                  ┌───────────┐  │
│                  │ elemento  │  │
│                  └───────────┘  │
└─────────────────────────────────┘
```

---

# 19. `bottom`

Para colocar um elemento próximo da parte inferior:

```css id="zngc3t"
position: fixed;
bottom: 20px;
left: 20px;
```

Resultado:

```text id="x3ddjj"
┌─────────────────────────────────┐
│                                 │
│                                 │
│ ┌──────────────┐                │
│ │   elemento   │                │
│ └──────────────┘                │
└─────────────────────────────────┘
```

Isso é útil para elementos como:

```text id="8yw5fz"
"Utilizamos cookies neste site."
```

---

# 20. `left` + `right`

Também podemos utilizar:

```css id="qnxl5q"
position: fixed;
left: 20px;
right: 20px;
```

Nesse caso, o navegador tenta ajustar a largura do elemento para que ele mantenha:

```text id="n1l8vz"
20px da esquerda
+
largura flexível
+
20px da direita
```

Visualmente:

```text id="3wqsf2"
┌──────────────────────────────────────┐
│ 20px ┌──────────────────────────┐ 20px│
│      │         elemento         │     │
│      └──────────────────────────┘     │
└──────────────────────────────────────┘
```

---

# 21. Não é necessário usar todas as direções

Não precisamos definir:

```css id="q4cd77"
top
right
bottom
left
```

ao mesmo tempo.

Normalmente escolhemos as propriedades necessárias para determinar a posição.

Exemplo:

```css id="o4xuyu"
position: fixed;
bottom: 20px;
right: 20px;
```

É suficiente para posicionar um elemento no canto inferior direito.

---

# 22. Exemplo clássico: aviso de cookies

```css id="u4de7k"
.cookie {
  position: fixed;
  bottom: 20px;
  left: 20px;
  right: 20px;
}
```

Resultado:

```text id="m78y5x"
┌──────────────────────────────────────────┐
│                                          │
│              conteúdo                    │
│                                          │
│                                          │
├──────────────────────────────────────────┤
│  "Neste site usamos cookies"             │
└──────────────────────────────────────────┘
```

Ao rolar a página:

```text id="hj6ty8"
scroll ↓

┌──────────────────────────────────────────┐
│     conteúdo diferente                   │
│                                          │
│                                          │
│                                          │
├──────────────────────────────────────────┤
│  aviso de cookies                        │
└──────────────────────────────────────────┘
```

O elemento continua fixo na janela.

---

# 23. `position: absolute`

Agora temos:

```css id="p4k73x"
position: absolute;
```

Esse posicionamento também remove o elemento do fluxo normal.

Portanto:

```text id="xhqj2n"
relative
→ continua no fluxo

absolute
→ sai do fluxo
```

---

# 24. `absolute` não ocupa mais o espaço original

Considere:

```text id="9t6qkg"
[A]
[B]
[C]
```

Se `B` receber:

```css id="df7cgg"
position: absolute;
```

o espaço de `B` deixa de ser reservado no fluxo:

```text id="z3e4yk"
[A]
[C]
```

Enquanto `B` pode ficar sobre outros elementos:

```text id="2jx8r4"
    [ B ]
      ↓
[A] [ B ] [ C ]
```

---

# 25. `absolute` e `fixed` retiram o elemento do fluxo

Essa é uma boa comparação:

```text id="5bl9xg"
relative
→ NÃO sai do fluxo

absolute
→ SAI do fluxo

fixed
→ SAI do fluxo
```

Mapa:

```text id="7otwy6"
position
  │
  ├── relative
  │    ↓
  │  mantém espaço
  │
  ├── absolute
  │    ↓
  │  remove do fluxo
  │
  └── fixed
       ↓
     remove do fluxo
```

---

# 26. A referência do `absolute`

Essa é uma das partes mais importantes.

Imagine:

```html id="6q97f5"
<div class="card">
  <span class="badge">Novo</span>
</div>
```

Queremos posicionar o `badge` dentro da `.card`.

Podemos fazer:

```css id="oslnvo"
.badge {
  position: absolute;
  top: 0;
  left: 0;
}
```

Mas precisamos definir uma referência para o posicionamento.

Colocamos no pai:

```css id="94m9v5"
.card {
  position: relative;
}
```

Agora:

```text id="6k8m5k"
.card
  │
  └── badge
       ↓
   position: absolute
```

O `badge` será posicionado em relação à `.card`.

---

# 27. Por que `position: relative` no elemento pai?

Considere:

```css id="zz1s8t"
.card {
  position: relative;
}
```

e:

```css id="y3n5mo"
.badge {
  position: absolute;
  top: 0;
  left: 0;
}
```

Podemos pensar:

```text id="ygnwr9"
PAI
.card
  │
  └── FILHO
      .badge
          │
          ↓
      absolute
          │
          ↓
    usa o pai posicionado
    como referência
```

Essa combinação é extremamente comum:

```css id="i68uq7"
.parent {
  position: relative;
}

.child {
  position: absolute;
}
```

---

# 28. Exemplo: badge sobre uma imagem

HTML:

```html id="q9g8p5"
<div class="card">
  <img src="produto.jpg" alt="Produto">

  <span class="badge">
    Novo
  </span>
</div>
```

CSS:

```css id="o3s9nn"
.card {
  position: relative;
}

.badge {
  position: absolute;
  top: -20px;
  right: 0;
}
```

Visualmente:

```text id="n8c5a1"
        ┌─────────┐
        │  Novo   │
        └─────────┘
       ┌─────────────────┐
       │                 │
       │     IMAGEM      │
       │                 │
       └─────────────────┘
```

Esse é um caso clássico para `absolute`.

---

# 29. `absolute` + `relative`

Essa combinação pode ser memorizada como:

```text id="t5r4r4"
PAI
relative
   │
   ↓
FILHO
absolute
```

Ou:

```text id="s3c5pj"
position: relative;
        +
position: absolute;
        ↓
posicionamento do filho
em relação ao pai
```

### Corte mental

> **O `relative` cria uma referência. O `absolute` usa essa referência para se posicionar.**

---

# 30. `top: 0` com `absolute`

Considere:

```css id="fxa7ax"
.card {
  position: relative;
}

.badge {
  position: absolute;
  top: 0;
  left: 0;
}
```

O `badge` ficará no canto superior esquerdo da `.card`.

```text id="bd2kpf"
┌─────────────────────────┐
│ [badge]                 │
│                         │
│       conteúdo          │
│                         │
└─────────────────────────┘
```

---

# 31. Valores negativos

Podemos utilizar:

```css id="4jk5zu"
top: -20px;
```

Isso move o elemento para cima da referência.

Por exemplo:

```css id="pygx9n"
.parent {
  position: relative;
}

.child {
  position: absolute;
  top: -20px;
}
```

Resultado:

```text id="8c6yyx"
      ┌──────────────┐
      │    child     │
      └──────────────┘
             ↑
          -20px
┌──────────────────────────┐
│          parent          │
│                          │
└──────────────────────────┘
```

Isso é útil para:

* badges;
* etiquetas;
* pequenos elementos sobrepostos;
* indicadores;
* botões sobre imagens.

---

# 32. `absolute` não é para montar o layout inteiro

É importante não utilizar:

```css id="vksh10"
position: absolute;
```

para começar a colocar cada elemento manualmente:

```text id="zpshpl"
Elemento A → 320px
Elemento B → 400px
Elemento C → 520px
Elemento D → 700px
```

Isso tende a produzir layouts difíceis de manter e pouco adaptáveis.

Para estruturar páginas, prefira:

```text id="xqg5y8"
Flexbox
ou
CSS Grid
```

O `position` deve ser utilizado para situações específicas de posicionamento.

---

# 33. Casos apropriados

`position: absolute` é muito útil para:

```text id="4b9l6e"
badge
↓
"Novo"

ícone
↓
canto de um card

botão
↓
sobre uma imagem

indicador
↓
canto de um elemento
```

---

# 34. Casos apropriados para `fixed`

`position: fixed` é adequado para:

```text id="sm4o0x"
Modal
↓
fica preso à janela

Aviso de cookies
↓
fica no rodapé

Botão flutuante
↓
fica fixo na tela

Barra fixa
↓
permanece visível durante o scroll
```

---

# 35. Comparação fundamental

| `position` | Sai do fluxo? | Referência principal   |
| ---------- | ------------: | ---------------------- |
| `static`   |           Não | fluxo normal           |
| `relative` |           Não | sua posição original   |
| `absolute` |           Sim | ancestral posicionado  |
| `fixed`    |           Sim | janela de visualização |

---

# 36. Mapa mental — `position`

```text id="cgtrbq"
                         position
                            │
           ┌────────────────┼────────────────┐
           ↓                ↓                ↓
        relative         absolute          fixed
           │                │                │
           ↓                ↓                ↓
       mantém o         sai do fluxo     sai do fluxo
        espaço             │                │
           │                ↓                ↓
           ↓          usa uma referência   viewport
    move visualmente       posicionada
```

### Corte mental ①

```text id="soj2a0"
relative
→ move
→ NÃO remove espaço
```

```text id="h0w4y4"
absolute
→ move
→ remove espaço
→ usa ancestral posicionado
```

```text id="lfh67k"
fixed
→ move
→ remove espaço
→ fica preso à viewport
```

---

# 37. Mapa mental — fluxo do documento

```text id="rhg6b6"
                 FLUXO NORMAL
                      │
              ┌───────┴───────┐
              ↓               ↓
         relative          static
              │               │
              ↓               ↓
        continua no      fluxo normal
           fluxo
```

Fora do fluxo:

```text id="5z6s8h"
              FORA DO FLUXO
                    │
             ┌──────┴──────┐
             ↓             ↓
          absolute       fixed
             │             │
             ↓             ↓
        não reserva    não reserva
        espaço         espaço
```

---

# 38. Mapa mental — `top`, `right`, `bottom`, `left`

```text id="2q0p1h"
                     ELEMENTO
                        │
          ┌─────────────┼─────────────┐
          ↓             ↓             ↓
         top          left          right
          │             │             │
          ↓             ↓             ↓
       distância      distância     distância
       do topo       da esquerda   da direita
                        │
                        ↓
                      bottom
                        │
                        ↓
                  distância de baixo
```

### Regra importante

```text id="qjmr1m"
top/right/bottom/left
          ↓
precisam de um
posicionamento adequado
```

---

# 39. Mapa mental — `absolute` + `relative`

```text id="hbj9i2"
                     PAI
                      │
              position: relative
                      │
                      ↓
                    FILHO
                      │
              position: absolute
                      │
                      ↓
          top / right / bottom / left
                      │
                      ↓
           posicionamento relativo
                 ao pai
```

### Corte mental ②

> **Quando precisar colocar um pequeno elemento sobre outro elemento, pense primeiro em: `pai { position: relative; }` + `filho { position: absolute; }`.**

---

# 40. Mapa mental — escolha do posicionamento

```text id="n2w2ba"
                         QUERO POSICIONAR
                               │
              ┌────────────────┼────────────────┐
              ↓                ↓                ↓
        manter espaço      remover fluxo     fixar na tela
              │                │                │
              ↓                ↓                ↓
          relative         absolute           fixed
              │                │                │
              ↓                ↓                ↓
      mover o próprio     elemento sobre      elemento preso
      elemento no fluxo   outro elemento      à viewport
```

---

# 41. Exemplos rápidos

## Mover sem retirar do fluxo

```css id="7o5dzp"
.elemento {
  position: relative;
  top: -20px;
}
```

```text id="t9t5iv"
→ sobe 20px
→ espaço original continua
```

---

## Colocar um elemento sobre outro

```css id="2ifddq"
.parent {
  position: relative;
}

.child {
  position: absolute;
  top: 0;
  right: 0;
}
```

```text id="pqq7ej"
→ child no canto do parent
```

---

## Fixar na tela

```css id="b0y7uq"
.cookie {
  position: fixed;
  bottom: 20px;
  left: 20px;
}
```

```text id="47ce1h"
→ continua no mesmo lugar da tela durante o scroll
```

---

# 42. `relative` não significa "em relação ao pai"

Um erro comum é pensar:

```text id="s6t46q"
position: relative
→ relativo ao pai
```

Não é essa a ideia principal.

O `relative` faz o elemento ser deslocado **em relação à sua própria posição original**.

Já o `absolute` pode usar um ancestral posicionado como referência.

```text id="u0hl7k"
relative
→ própria posição

absolute
→ ancestral posicionado
```

---

# 43. `fixed` não depende do fluxo normal

Quando usamos:

```css id="j1o6q9"
position: fixed;
```

o elemento é retirado do fluxo normal e fica posicionado em relação à área de visualização.

Por isso ele permanece no mesmo lugar da tela enquanto a página é rolada.

```text id="kqxuwp"
ANTES DO SCROLL

┌─────────────────────┐
│                     │
│                     │
│              [FIXO] │
└─────────────────────┘


DEPOIS DO SCROLL

┌─────────────────────┐
│                     │
│ conteúdo diferente  │
│              [FIXO] │
└─────────────────────┘
```

---

# 44. ⚠️ Cuidado com `absolute`

Não utilize `absolute` como substituto para:

```text id="3fkh3s"
Grid
Flexbox
```

Se o objetivo é:

```text id="tvfyi8"
organizar cards
criar colunas
estruturar menu
montar layout responsivo
```

normalmente devemos pensar primeiro em:

```text id="0m5ifh"
CSS Grid
ou
Flexbox
```

O `position` serve para situações de posicionamento mais específicas.

---

# 45. 📌 Resumo final

```text id="pz4j6b"
POSITION
   │
   ├── static
   │    ↓
   │  comportamento normal
   │
   ├── relative
   │    ↓
   │  mantém espaço
   │  move visualmente
   │
   ├── absolute
   │    ↓
   │  sai do fluxo
   │  usa ancestral posicionado
   │
   └── fixed
        ↓
      sai do fluxo
      fica preso à viewport
```

As quatro direções:

```text id="0d0e6x"
top
right
bottom
left
```

permitem controlar o deslocamento do elemento.

---

# 46. 🧠 Três frases para memorizar

### `relative`

> **"Mova-me, mas preserve meu espaço."**

```css id="jwhf2t"
position: relative;
```

### `absolute`

> **"Tire-me do fluxo e posicione-me em relação ao meu ancestral posicionado."**

```css id="4t5qhk"
position: absolute;
```

### `fixed`

> **"Tire-me do fluxo e mantenha-me fixo na tela."**

```css id="wk91qj"
position: fixed;
```

---

# 47. Regra prática final

```text id="jz5tdx"
QUERO MOVER UM ELEMENTO
SEM QUE ELE PERCA O ESPAÇO?
        ↓
    relative
```

```text id="zq9q4s"
QUERO COLOCAR UM ELEMENTO
SOBRE OUTRO?
        ↓
parent → relative
child  → absolute
```

```text id="7ad7bp"
QUERO QUE O ELEMENTO
FIQUE FIXO NA TELA?
        ↓
      fixed
```

```text id="e9hlx0"
QUERO ORGANIZAR O LAYOUT
INTEIRO?
        ↓
   Grid / Flexbox
```

### Regra mental definitiva

> **`position` serve para posicionamento específico; `Grid` e `Flexbox` servem para estruturar o layout.**
