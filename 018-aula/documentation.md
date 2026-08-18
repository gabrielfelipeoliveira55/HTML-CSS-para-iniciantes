# CSS `z-index` — Controle de Profundidade dos Elementos

## 1. O que é `z-index`?

A propriedade:

```css id="a8h3f1"
z-index
```

controla a **ordem de sobreposição dos elementos**.

Enquanto propriedades como:

```css id="k8x1v3"
top
right
bottom
left
```

influenciam principalmente a posição do elemento no espaço, o:

```css id="u9q5r2"
z-index
```

atua no **eixo de profundidade**.

Podemos imaginar três eixos:

```text id="p6m2s8"
           Y
           ↑
           │
           │
           │
           └────────→ X
          /
         /
        ↓
        Z
```

O eixo `Z` representa a ideia de:

```text id="w4d7k1"
frente
  ↑
  │
  │
trás
```

### Regra mental

> **`z-index` controla quem fica por cima e quem fica por baixo.**

---

# 2. O comportamento normal

Imagine:

```html id="n3k8p0"
<h1>Elemento 1</h1>
<h1>Elemento 2</h1>
<h1>Elemento 3</h1>
<h1>Elemento 4</h1>
<h1>Elemento 5</h1>
```

Normalmente:

```text id="r7c5m2"
Elemento 1
Elemento 2
Elemento 3
Elemento 4
Elemento 5
```

Os elementos seguem o fluxo normal.

Quando algum elemento é reposicionado e passa a se sobrepor a outro, surge a necessidade de controlar **qual deles ficará na frente**.

É aí que entra o `z-index`.

---

# 3. `position` e `z-index`

Uma situação comum é:

```css id="c2p7v4"
.elemento {
  position: relative;
}
```

Depois podemos deslocá-lo:

```css id="j5q0s1"
.elemento {
  position: relative;
  top: 20px;
}
```

Agora ele pode acabar sobrepondo outro elemento:

```text id="w9k3d6"
┌───────────────┐
│ Elemento 2    │
└───────────────┘
       ↓
┌───────────────┐
│ Elemento 3    │
└───────────────┘
```

Se o elemento reposicionado passar para cima de outro, precisamos entender a ordem de profundidade.

---

# 4. O eixo `Z`

Imagine vários elementos empilhados:

```text id="s4w8y2"
Frente
  ↑
  │
[Elemento A]
[Elemento B]
[Elemento C]
  │
  ↓
Trás
```

O `z-index` altera essa ordem.

Exemplo:

```css id="m7q2v5"
.elemento {
  z-index: 2;
}
```

significa:

> Este elemento terá uma prioridade de profundidade maior que elementos com valores menores, dentro do mesmo contexto de empilhamento.

---

# 5. Valores positivos

Podemos utilizar:

```css id="f8c3n1"
z-index: 1;
```

ou:

```css id="d5m9k2"
z-index: 2;
```

ou:

```css id="r6v1x8"
z-index: 10;
```

A ideia é:

```text id="a2s7q4"
z-index: 10
     ↑
     │
z-index: 2
     ↑
     │
z-index: 1
```

Quanto maior o valor, maior a prioridade de sobreposição dentro do contexto aplicável.

---

# 6. Comparando dois elementos

Imagine:

```css id="q4m8s1"
.index-1 {
  position: relative;
  z-index: 1;
}

.index-2 {
  position: absolute;
  z-index: 2;
}
```

Temos:

```text id="cz7n4v"
.index-1 → z-index: 1
.index-2 → z-index: 2
```

Então:

```text id="h6p2j9"
        [ index-2 ]
             ↑
             │
        [ index-1 ]
```

O `index-2` fica acima.

### Regra mental

```text id="b8y3k5"
maior z-index
     ↓
mais à frente
```

---

# 7. `z-index: 0`

Podemos utilizar:

```css id="v5q1j8"
z-index: 0;
```

Dentro do contexto de empilhamento aplicável, ele fica entre valores negativos e positivos.

Uma forma mental simples:

```text id="x3n6s0"
z-index: 2
      ↑
z-index: 1
      ↑
z-index: 0
      ↑
z-index: -1
```

---

# 8. `z-index` negativo

Também podemos utilizar valores negativos:

```css id="k9d2p6"
z-index: -1;
```

Isso pode colocar o elemento atrás de elementos com valores maiores.

Exemplo:

```text id="m5x7v3"
Elemento com z-index: 1
        ↑
Elemento com z-index: 0
        ↑
Elemento com z-index: -1
```

Portanto:

```css id="g2w8q1"
z-index: -1;
```

pode ser utilizado quando queremos enviar o elemento para trás.

---

# 9. Regra básica de comparação

Podemos guardar:

```text id="u4c8m2"
z-index: 3
→ frente

z-index: 2
→ meio

z-index: 1
→ atrás

z-index: 0
→ mais atrás

z-index: -1
→ ainda mais atrás
```

### Fórmula mental

```text id="n7p3f5"
maior valor
     ↓
mais à frente
```

---

# 10. A posição de origem também influencia

Existe uma situação importante quando dois elementos estão posicionados e possuem o mesmo `z-index` ou não possuem um valor explícito.

Nesse caso, a ordem de pintura também pode fazer diferença.

Imagine:

```text id="y5k8c2"
Elemento 2
Elemento 4
```

Se ambos estiverem posicionados e houver sobreposição, um elemento que aparece posteriormente na ordem de pintura pode acabar ficando à frente.

Por isso, não é somente:

```text id="2d6x9n"
"qual foi criado primeiro?"
```

Também devemos considerar:

```text id="g1v4m7"
posição
+
ordem de pintura
+
z-index
```

---

# 11. Por que um elemento pode ficar na frente mesmo sem `z-index`?

Suponha:

```css id="a5r2z7"
.index-1 {
  position: relative;
  top: 20px;
}

.index-2 {
  position: absolute;
}
```

Mesmo sem definir:

```css id="z3h8v1"
z-index
```

podemos ter sobreposição.

A ordem de empilhamento pode fazer com que um elemento apareça acima do outro.

Por isso, o `z-index` é utilizado quando queremos **controlar explicitamente essa profundidade**.

---

# 12. O `z-index` precisa de um contexto adequado

Um ponto fundamental para esta propriedade é que ela não funciona simplesmente em qualquer situação como um número mágico.

No contexto estudado aqui, ela é aplicada em elementos que possuem posicionamento, por exemplo:

```css id="f7m4q1"
position: relative;
```

```css id="p8x2v6"
position: absolute;
```

```css id="w3n9k5"
position: fixed;
```

Assim podemos utilizar:

```css id="c6j1s4"
z-index: 10;
```

---

# 13. Exemplo

```css id="d4m7p2"
.index-1 {
  position: relative;
  top: 20px;
  z-index: 1;
}

.index-2 {
  position: absolute;
  z-index: 2;
}
```

Temos:

```text id="x8q4n7"
index-2 → 2
   ↑
index-1 → 1
```

Resultado:

```text id="s3k9v5"
┌──────────────────┐
│     index-2       │
├──────────────────┤
│     index-1       │
└──────────────────┘
```

---

# 14. O valor `9999999`

É muito comum encontrar código como:

```css id="m2v7q4"
z-index: 9999999;
```

A intenção geralmente é:

> "Quero garantir que esse elemento fique muito acima dos outros."

Um exemplo comum seria um modal:

```css id="j8w5s2"
.modal {
  position: fixed;
  z-index: 9999999;
}
```

Porém, valores enormes não são obrigatórios.

---

# 15. Não existe necessidade de usar números gigantes

Em vez de:

```css id="k4p9x1"
z-index: 9999999;
```

podemos organizar:

```text id="g3n8m5"
conteúdo normal → 1
elementos acima  → 2
modal            → 3
```

Por exemplo:

```css id="u6c2r7"
.content {
  position: relative;
  z-index: 1;
}

.menu {
  position: fixed;
  z-index: 2;
}

.modal {
  position: fixed;
  z-index: 3;
}
```

Isso é muito mais organizado.

### Regra mental

> **O importante é a relação entre os valores, não usar números gigantes.**

---

# 16. Exemplo de organização

Podemos criar uma pequena hierarquia:

```text id="p4s7d1"
z-index: 1
→ conteúdo

z-index: 2
→ navegação

z-index: 3
→ elementos flutuantes

z-index: 4
→ modal
```

Visualmente:

```text id="v8k3m6"
z-index: 4
      ↑
    MODAL

z-index: 3
      ↑
  FLUTUANTE

z-index: 2
      ↑
    MENU

z-index: 1
      ↑
   CONTEÚDO
```

---

# 17. `z-index` não significa "posição"

É importante não confundir:

```text id="x5n7p2"
position
```

com:

```text id="c9m4v8"
z-index
```

`position` determina **como e em relação a quê o elemento será posicionado**.

`z-index` controla a **profundidade/ordem de sobreposição**.

```text id="f2q8s6"
position
→ posicionamento

z-index
→ profundidade
```

---

# 18. Exemplo comparativo

```css id="e7m1k4"
.elemento {
  position: relative;
  top: 20px;
  z-index: 2;
}
```

Temos duas coisas diferentes:

```text id="s8x3n9"
top: 20px
   ↓
move o elemento

z-index: 2
   ↓
controla sua profundidade
```

---

# 19. Alterar `top` pode mudar a percepção de sobreposição

Imagine:

```css id="q7d2m5"
.elemento {
  position: relative;
  top: 20px;
}
```

O elemento se desloca fisicamente para uma região onde outro elemento está.

Agora temos uma sobreposição:

```text id="h4v8c2"
      [Elemento 2]
┌────────────────────┐
│    Elemento 3      │
└────────────────────┘
```

O `z-index` entra justamente para decidir:

> **Qual deles deve ser pintado por cima?**

---

# 20. Exemplo com `z-index: -1`

```css id="a8p3m6"
.elemento {
  position: relative;
  top: 20px;
  z-index: -1;
}
```

Agora o elemento pode ficar atrás de outros elementos:

```text id="n5v7k2"
[Elemento da frente]
─────────────────────
   [Elemento -1]
─────────────────────
```

Isso pode ser útil para determinados efeitos visuais, mas deve ser utilizado com cuidado porque a interação com o contexto de empilhamento pode produzir resultados diferentes do que simplesmente "mandar para trás".

---

# 21. `z-index` e elementos `relative`, `absolute` e `fixed`

No contexto desta abordagem:

```text id="f1k7s3"
relative
   +
z-index
   ↓
controla profundidade
```

```text id="v4q9m8"
absolute
   +
z-index
   ↓
controla profundidade
```

```text id="c6w2n5"
fixed
   +
z-index
   ↓
controla profundidade
```

Essa combinação aparece com frequência em interfaces.

---

# 22. Exemplo clássico: modal

Um modal geralmente precisa ficar sobre o restante da página.

Podemos ter:

```css id="d7m3q8"
.modal {
  position: fixed;
  z-index: 3;
}
```

Enquanto o conteúdo permanece:

```css id="r9x4k2"
.content {
  position: relative;
  z-index: 1;
}
```

Então:

```text id="j8p6v4"
┌───────────────────────────────────┐
│                                   │
│           CONTEÚDO                │
│                                   │
│      ┌─────────────────┐          │
│      │      MODAL      │          │
│      │     z: 3        │          │
│      └─────────────────┘          │
│                                   │
└───────────────────────────────────┘
```

O modal fica acima.

---

# 23. O que acontece se outro elemento tiver um valor maior?

Imagine:

```css id="v6n2k8"
.modal {
  position: fixed;
  z-index: 3;
}

.menu {
  position: fixed;
  z-index: 4;
}
```

Agora:

```text id="0r5p7s"
MENU
z-index: 4
     ↑
MODAL
z-index: 3
```

O menu terá prioridade de empilhamento dentro do contexto aplicável.

Por isso, a regra é:

> **Maior `z-index` vence quando os elementos estão no mesmo contexto de empilhamento.**

---

# 24. Contexto de empilhamento

Este é um conceito importante para entender `z-index`.

Não devemos pensar que:

```css id="e8v5j2"
z-index: 9999999;
```

sempre significa:

> "Esse elemento estará acima de absolutamente tudo na página."

O `z-index` atua dentro de um **stacking context**.

Podemos imaginar:

```text id="q2m7d5"
Página
│
├── Contexto A
│   ├── elemento z-index: 1
│   └── elemento z-index: 2
│
└── Contexto B
    ├── elemento z-index: 1
    └── elemento z-index: 9999999
```

O número `9999999` não significa automaticamente que esse elemento atravessará qualquer contexto superior.

### Regra mental

> **`z-index` compara prioridades dentro do contexto de empilhamento aplicável.**

---

# 25. Por que o `z-index: 9999999` pode não funcionar?

Imagine:

```css id="elemento" 
.elemento {
  z-index: 9999999;
}
```

mas o elemento não possui um posicionamento ou outra condição que permita que o `z-index` seja aplicado da maneira esperada no cenário.

Podemos alterar:

```css id="e1m7k3"
.elemento {
  position: relative;
  z-index: 9999999;
}
```

Agora ele passa a participar do posicionamento que permite controlar sua profundidade nesse contexto.

---

# 26. Exemplo prático

Temos:

```html id="j9k3p2"
<h1 class="elemento-1">Elemento 1</h1>
<h1 class="elemento-2">Elemento 2</h1>
<h1 class="elemento-3">Elemento 3</h1>
```

Podemos escrever:

```css id="r8m5v1"
.elemento-2 {
  position: relative;
  top: 20px;
  z-index: 1;
}
```

Agora o elemento 2 pode ficar sobre o elemento 3.

Se quisermos que outro elemento fique acima:

```css id="d3q7s8"
.elemento-3 {
  position: relative;
  z-index: 2;
}
```

Então:

```text id="e4v9k2"
z-index: 2
   ↑
Elemento 3

z-index: 1
   ↑
Elemento 2
```

---

# 27. `z-index` negativo

Também podemos fazer:

```css id="a7s2m4"
.elemento-2 {
  position: relative;
  z-index: -1;
}
```

Agora ele pode ficar atrás dos elementos que possuem valores maiores.

```text id="p6k8q3"
Elemento 3
Elemento 1
Elemento 2
   ↑
 z-index -1
```

---

# 28. Mapa mental — `z-index`

```text id="k1m7x5"
                         z-index
                            │
                            ↓
                   EIXO DE PROFUNDIDADE
                            │
              ┌─────────────┴─────────────┐
              ↓                           ↓
           maior                         menor
              │                           │
              ↓                           ↓
           frente                        trás
```

### Corte mental ①

```text id="w4n8s2"
X → horizontal
Y → vertical
Z → profundidade
```

---

# 29. Mapa mental — valores

```text id="y2p7m8"
                   z-index
                      │
        ┌─────────────┼─────────────┐
        ↓             ↓             ↓
      positivo        0          negativo
        │             │             │
        ↓             ↓             ↓
      frente       referência      trás
        │
        ↓
quanto maior
maior prioridade
```

---

# 30. Mapa mental — comparação

```text id="f7q3k9"
ELEMENTO A
z-index: 1
     │
     │
     ▼
ELEMENTO B
z-index: 2
```

Resultado:

```text id="x5m8p2"
B
↑
A
```

Porque:

```text id="m3k7s1"
2 > 1
```

---

# 31. Mapa mental — `position` + `z-index`

```text id="q8v4m6"
                      POSITION
                         │
          ┌──────────────┼──────────────┐
          ↓              ↓              ↓
       relative       absolute         fixed
          │              │              │
          └──────────────┼──────────────┘
                         ↓
                    z-index
                         ↓
                  profundidade
                         ↓
             quem fica por cima?
```

### Corte mental ②

```text id="r5n9x3"
position
→ "onde está?"

z-index
→ "quem está na frente?"
```

---

# 32. Mapa mental — organização de valores

Em vez de:

```css id="d6q2m7"
z-index: 9999999;
```

podemos criar uma hierarquia simples:

```text id="w8s4k1"
1 → conteúdo
2 → navegação
3 → elementos flutuantes
4 → modal
```

Visualmente:

```text id="q3m7v9"
        MODAL
       z-index 4
           ↑
      FLUTUANTE
       z-index 3
           ↑
        MENU
       z-index 2
           ↑
       CONTEÚDO
       z-index 1
```

Isso torna o projeto mais previsível.

---

# 33. Mapa mental — quando pensar em `z-index`

```text id="p9v3k6"
ELEMENTOS SE SOBREPOEM?
          │
      ┌───┴───┐
      ↓       ↓
     NÃO     SIM
      │       │
      ↓       ↓
   ignore    pense em
   z-index   profundidade
              │
              ↓
           z-index
```

---

# 34. `z-index` não organiza layout

Não use:

```css id="j5m8r2"
z-index
```

para construir:

```text id="v4q9x1"
menus
colunas
cards
estrutura de página
```

O `z-index` não é uma ferramenta para organizar o layout.

Ele serve para controlar a **sobreposição**.

Para estruturar páginas:

```text id="s7p2m4"
CSS Grid
Flexbox
```

Para controlar profundidade:

```text id="b3x8k6"
z-index
```

---

# 35. ⚠️ Regra importante sobre contexto

Ao estudar `z-index`, memorize:

```text id="n2q7v5"
z-index não significa
"número mágico universal"
```

Ele funciona dentro de um contexto de empilhamento.

Por isso:

```css id="c8m4x2"
z-index: 9999999;
```

não deve ser utilizado simplesmente para "forçar tudo para cima".

Uma estrutura organizada como:

```css id="a6v1p9"
z-index: 1;
z-index: 2;
z-index: 3;
```

costuma ser muito mais fácil de manter.

---

# 36. Exemplo final

HTML:

```html id="x5q8r3"
<div class="container">
  <div class="item item-1">1</div>
  <div class="item item-2">2</div>
  <div class="item item-3">3</div>
</div>
```

CSS:

```css id="m8k2v4"
.item {
  padding: 20px;
}

.item-1 {
  position: relative;
  top: 20px;
  z-index: 1;
}

.item-2 {
  position: absolute;
  z-index: 2;
}

.item-3 {
  position: relative;
  z-index: 0;
}
```

Podemos interpretar:

```text id="q6n3s8"
ITEM 2
z-index: 2
      ↑
ITEM 1
z-index: 1
      ↑
ITEM 3
z-index: 0
```

Portanto:

```text id="w9m4k2"
frente
  ↑
ITEM 2
ITEM 1
ITEM 3
  ↓
trás
```

---

# 37. 📌 Resumo final

```text id="j7q2m5"
                    z-index
                       │
                       ↓
             controla profundidade
                       │
           ┌───────────┴───────────┐
           ↓                       ↓
        maior                   menor
           ↓                       ↓
        frente                    trás
```

Exemplo:

```css id="c9v3n7"
.elemento {
  position: relative;
  z-index: 10;
}
```

O:

```css id="x2m8q5"
position
```

define a forma de posicionamento.

O:

```css id="h4k7s1"
z-index
```

define a prioridade de sobreposição.

---

# 38. 🧠 Três frases para guardar

> **`position` controla o posicionamento.**

> **`z-index` controla a profundidade.**

> **Quanto maior o `z-index`, maior a prioridade de sobreposição dentro do mesmo contexto de empilhamento.**

### Regra mental definitiva

```text id="p8m3v6"
POSIÇÃO
   ↓
position

PROFUNDIDADE
   ↓
z-index

ESTRUTURA DO LAYOUT
   ↓
Grid / Flexbox
```

Essa separação evita uma das confusões mais comuns:

```text id="r7k2s5"
Grid/Flexbox
→ organizam

position
→ posiciona

z-index
→ controla sobreposição
```
