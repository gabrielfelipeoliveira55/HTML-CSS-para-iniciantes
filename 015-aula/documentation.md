# CSS Flexbox — `flex-grow`, `flex-basis`, `flex-shrink` e `flex`

## 1. Visão geral

A propriedade `flex` é uma propriedade aplicada aos **flex items**.

Um elemento se torna um `flex item` quando é filho direto de um elemento que possui:

```css
.container {
  display: flex;
}
```

Por exemplo:

```html
<div class="container">
  <h2>Senhor dos Anéis</h2>
  <h2>Interestelar</h2>
  <h2>O Hobbit</h2>
  <h2>Titanic</h2>
</div>
```

```css
.container {
  display: flex;
}
```

Nesse caso:

```text
.container
    │
    ├── h2  → flex item
    ├── h2  → flex item
    ├── h2  → flex item
    └── h2  → flex item
```

A propriedade `flex` reúne três propriedades:

```css
flex-grow
flex-shrink
flex-basis
```

Portanto:

```css
flex
```

é um **atalho (shorthand)** para essas três propriedades.

---

# 2. `flex-grow`

## Para que serve?

`flex-grow` determina quanto um flex item pode **crescer para ocupar o espaço livre** existente no container.

A pergunta que devemos fazer é:

> **"Quanto este item pode crescer quando sobra espaço?"**

O valor padrão é:

```css
flex-grow: 0;
```

Isso significa:

> O elemento não deve crescer para ocupar o espaço vazio.

---

## Exemplo

Imagine que temos:

```css
.container {
  display: flex;
}
```

e os itens:

```text
┌─────────────────────────────────────────────┐
│ [Senhor dos Anéis] [Interestelar] [Hobbit] │ 
└─────────────────────────────────────────────┘
```

Cada item possui inicialmente o tamanho necessário para seu conteúdo.

Podemos permitir que eles cresçam:

```css
h2 {
  flex-grow: 1;
}
```

Agora o espaço vazio disponível será distribuído entre os itens.

```text
┌─────────────────────────────────────────────┐
│ [      Senhor dos Anéis      ]              │
│ [       Interestelar         ]              │
│ [         O Hobbit           ]              │
└─────────────────────────────────────────────┘
```

A ideia principal é:

```text
ESPAÇO LIVRE
     ↓
flex-grow
     ↓
crescimento dos itens
```

---

# 3. `flex-grow: 1`

Quando utilizamos:

```css
.item {
  flex-grow: 1;
}
```

estamos dizendo:

> **"Este elemento pode crescer para utilizar o espaço disponível."**

Quando vários elementos possuem:

```css
flex-grow: 1;
```

eles participam da distribuição do espaço livre.

Por exemplo:

```css
.item1,
.item2,
.item3,
.item4 {
  flex-grow: 1;
}
```

A tendência será que o espaço disponível seja dividido igualmente entre eles.

---

# 4. `flex-basis`

## Para que serve?

`flex-basis` define o **tamanho base do flex item antes da distribuição do espaço**.

Seu valor padrão é:

```css
flex-basis: auto;
```

O `auto` faz com que a base considere o tamanho do conteúdo e as dimensões definidas para o elemento.

---

# 5. `flex-basis: auto`

Considere:

```css
h2 {
  flex-grow: 1;
  flex-basis: auto;
}
```

Primeiro, cada elemento terá sua base calculada considerando seu conteúdo.

Depois, o `flex-grow` distribui o espaço que **sobrou**.

Por exemplo:

```text
Senhor dos Anéis
```

possui mais caracteres do que:

```text
Titanic
```

Consequentemente, com:

```css
flex-basis: auto;
```

o primeiro item pode começar com uma base maior.

Podemos representar o processo assim:

```text
Tamanho do conteúdo
        ↓
   base inicial
        ↓
espaço restante
        ↓
   flex-grow
        ↓
   tamanho final
```

---

# 6. `flex-basis: 0`

Podemos alterar:

```css
flex-basis: auto;
```

para:

```css
flex-basis: 0;
```

Agora o conteúdo deixa de determinar a base inicial para a distribuição do espaço.

Exemplo:

```css
.item {
  flex-grow: 1;
  flex-basis: 0;
}
```

O Flexbox passa a distribuir o espaço entre os itens a partir de uma base igual.

Podemos imaginar:

```text
ANTES

[ conteúdo grande ] [ médio ] [ pequeno ]
      ↓                 ↓          ↓
   base maior        base média   base menor
```

Com `flex-basis: 0`:

```text
[      0      ] [      0      ] [      0      ]
        ↓              ↓              ↓
       espaço disponível distribuído
        ↓              ↓              ↓
[   tamanho   ] [   tamanho   ] [   tamanho   ]
```

Por isso, quando usamos:

```css
flex-grow: 1;
flex-basis: 0;
```

os itens tendem a ficar com **tamanhos iguais**, independentemente da quantidade de conteúdo.

---

# 7. `flex-basis` com uma medida

Também podemos definir uma medida:

```css
.item {
  flex-basis: 200px;
}
```

Isso estabelece uma base de `200px`.

Por exemplo:

```css
.item {
  flex-basis: 200px;
  padding: 20px;
}
```

Dependendo do `box-sizing`, o tamanho total da caixa poderá ser maior que `200px`.

Com o modelo de caixa padrão:

```text
200px de conteúdo
+
20px de padding esquerdo
+
20px de padding direito
=
240px
```

Por isso, no exemplo da aula, um item que possuía:

```css
flex-basis: 200px;
padding: 20px;
```

aparecia com aproximadamente:

```text
240px
```

---

# 8. Quando usar `flex-basis`?

É possível utilizar valores específicos:

```css
flex-basis: 200px;
flex-basis: 50%;
flex-basis: 10rem;
```

Porém, em muitos layouts comuns, encontramos principalmente:

```css
flex-basis: auto;
```

ou:

```css
flex-basis: 0;
```

O importante é entender a diferença:

```text
auto
 ↓
considera o tamanho inicial do conteúdo

0
 ↓
começa com base zero para distribuir o espaço
```

---

# 9. `flex-shrink`

## Para que serve?

`flex-shrink` controla a capacidade do flex item de **diminuir quando falta espaço**.

A pergunta que devemos fazer é:

> **"Se o container ficar pequeno demais, este item pode encolher?"**

O valor padrão é:

```css
flex-shrink: 1;
```

Ou seja:

> **Sim, o elemento pode diminuir.**

---

# 10. `flex-shrink: 1`

Imagine:

```css
.item {
  flex-shrink: 1;
}
```

Se o container ficar menor:

```text
┌───────────────────────────────┐
│ [Item] [Item] [Item] [Item]   │
└───────────────────────────────┘
```

o Flexbox pode reduzir os itens para tentar fazê-los caber.

Isso pode resultar em:

```text
┌─────────────────┐
│ [Item][Item]... │
└─────────────────┘
```

O conteúdo também pode quebrar de linha, dependendo das propriedades aplicadas.

---

# 11. `flex-shrink: 0`

Podemos impedir que o item seja reduzido:

```css
.item {
  flex-shrink: 0;
}
```

Agora estamos dizendo:

> **"Não permita que este item encolha."**

Isso significa que ele tentará preservar seu tamanho.

Se não houver espaço suficiente, pode ocorrer **overflow**, dependendo das demais regras do layout.

---

## Comparação

### `flex-shrink: 1`

```text
Falta espaço?
     ↓
SIM
     ↓
Pode diminuir
```

### `flex-shrink: 0`

```text
Falta espaço?
     ↓
SIM
     ↓
Não diminui
```

Na maioria dos casos, podemos manter:

```css
flex-shrink: 1;
```

porque esse já é o comportamento padrão.

---

# 12. A propriedade `flex`

Agora chegamos ao ponto principal.

Em vez de escrever:

```css
.item {
  flex-grow: 1;
  flex-shrink: 1;
  flex-basis: 0%;
}
```

podemos utilizar:

```css
.item {
  flex: 1;
}
```

A propriedade:

```css
flex
```

é o shorthand das três propriedades:

```text
flex-grow
flex-shrink
flex-basis
```

---

# 13. O que significa `flex: 1`?

Quando usamos:

```css
.item {
  flex: 1;
}
```

o navegador interpreta essa configuração de forma equivalente, para o uso comum do shorthand, como:

```css
.item {
  flex-grow: 1;
  flex-shrink: 1;
  flex-basis: 0%;
}
```

Podemos escrever explicitamente:

```css
.item {
  flex: 1 1 0%;
}
```

A ordem é:

```text
flex: grow shrink basis;
       ↓     ↓     ↓
       1     1    0%
```

Portanto:

```css
flex: 1;
```

pode ser memorizado como:

```text
crescer → 1
diminuir → 1
base → 0%
```

---

# 14. Por que `flex: 1` é tão utilizado?

Porque ele cria um comportamento muito útil:

```css
.item {
  flex: 1;
}
```

Cada item pode:

* crescer;
* diminuir;
* participar da distribuição do espaço de maneira uniforme.

Imagine quatro itens:

```text
┌──────────────────────────────────────────────┐
│    ITEM 1    │    ITEM 2    │    ITEM 3     │
└──────────────────────────────────────────────┘
```

Com:

```css
.item {
  flex: 1;
}
```

eles tendem a dividir igualmente o espaço disponível.

---

# 15. Exemplo completo

HTML:

```html
<div class="filmes">
  <h2>Senhor dos Anéis</h2>
  <h2>Interestelar</h2>
  <h2>O Hobbit</h2>
  <h2>Titanic</h2>
</div>
```

CSS:

```css
.filmes {
  display: flex;
}

h2 {
  flex: 1;
}
```

O resultado será semelhante a:

```text
┌───────────────────────────────────────────────────┐
│ Senhor dos │ Interestelar │ O Hobbit │  Titanic   │
│   Anéis    │              │          │            │
└───────────────────────────────────────────────────┘
```

Os itens participam da distribuição do espaço disponível.

---

# 16. `display: flex` + `flex-wrap` + `flex: 1`

Um padrão apresentado na aula é:

```css
.container {
  display: flex;
  flex-wrap: wrap;
}

.item {
  flex: 1;
}
```

Cada propriedade possui uma responsabilidade diferente.

### `display: flex`

Ativa o Flexbox:

```css
display: flex;
```

### `flex-wrap: wrap`

Permite que os itens quebrem para outra linha quando necessário:

```css
flex-wrap: wrap;
```

### `flex: 1`

Permite que os itens cresçam e diminuam de forma flexível:

```css
flex: 1;
```

Podemos memorizar:

```text
display: flex
    ↓
ativa o Flexbox

flex-wrap: wrap
    ↓
permite quebra de linha

flex: 1
    ↓
distribui o espaço entre os itens
```

---

# 17. `flex: 1` e `justify-content`

Este é um ponto importante.

Imagine:

```css
.container {
  display: flex;
  justify-content: center;
}

.item {
  flex: 1;
}
```

Pode parecer que:

```css
justify-content: center;
```

irá centralizar os itens.

Porém, o `flex: 1` faz os itens crescerem e ocuparem o espaço disponível.

Consequentemente, pode não existir **espaço livre no eixo principal** para o `justify-content` distribuir.

Podemos visualizar:

```text
┌──────────────────────────────────────────────┐
│ [       ITEM 1       ][       ITEM 2       ] │
└──────────────────────────────────────────────┘
```

O espaço já foi distribuído pelo Flexbox através do crescimento dos itens.

---

# 18. Quando usar `justify-content`

Se queremos que os itens mantenham seus tamanhos naturais e sejam posicionados no centro, podemos fazer:

```css
.container {
  display: flex;
  justify-content: center;
}
```

Sem:

```css
.item {
  flex: 1;
}
```

Agora o espaço livre permanece no container e pode ser utilizado pelo:

```css
justify-content: center;
```

Visualmente:

```text
┌──────────────────────────────────────────────┐
│            [A] [B] [C]                      │
└──────────────────────────────────────────────┘
                ↑
         itens centralizados
```

---

# 19. Diferença fundamental

## Com `flex: 1`

```css
.item {
  flex: 1;
}
```

O objetivo é:

```text
OCUPAR O ESPAÇO
       ↓
DISTRIBUIR O ESPAÇO
```

---

## Com `justify-content: center`

```css
.container {
  justify-content: center;
}
```

O objetivo é:

```text
MANTER OS TAMANHOS
       ↓
POSICIONAR NO CENTRO
```

Por isso, não devemos pensar em `flex: 1` como simplesmente "centralizar".

Ele está relacionado principalmente à **distribuição e expansão dos flex items**.

---

# 20. Tabela de revisão

| Propriedade   | Função                             | Valor padrão          |
| ------------- | ---------------------------------- | --------------------- |
| `flex-grow`   | Define quanto o item pode crescer  | `0`                   |
| `flex-shrink` | Define quanto o item pode diminuir | `1`                   |
| `flex-basis`  | Define o tamanho base inicial      | `auto`                |
| `flex`        | Atalho para as três propriedades   | depende da declaração |

---

# 21. Como memorizar

Uma maneira simples de lembrar:

```text
GROW
 ↓
CRESCER

SHRINK
 ↓
DIMINUIR

BASIS
 ↓
BASE / TAMANHO INICIAL
```

Então:

```text
flex-grow
→ crescer

flex-shrink
→ diminuir

flex-basis
→ tamanho inicial

flex
→ atalho dos três
```

---

# 22. Regra mental para `flex: 1`

Sempre que encontrar:

```css
.item {
  flex: 1;
}
```

pense:

```text
┌───────────────────────────────┐
│ flex-grow   → 1               │
│ flex-shrink  → 1              │
│ flex-basis   → 0%             │
└───────────────────────────────┘
```

Ou, de forma mais simples:

> **"Pode crescer, pode diminuir e divide o espaço de forma flexível."**

---

# 23. Fluxo completo do Flexbox

Podemos imaginar o processo assim:

```text
              FLEX CONTAINER
                    │
                    ↓
             display: flex
                    │
                    ↓
              FLEX ITEMS
                    │
        ┌───────────┼───────────┐
        ↓           ↓           ↓
  flex-basis   flex-grow   flex-shrink
        │           │           │
        ↓           ↓           ↓
   base inicial   crescer     diminuir
                    │
                    ↓
             tamanho final
```

---

# 24. Exemplo comparativo

## Apenas `display: flex`

```css
.container {
  display: flex;
}
```

Os itens mantêm seus tamanhos naturais:

```text
┌──────────────────────────────────────────────┐
│ [A] [B] [CONTEÚDO MAIOR]                    │
└──────────────────────────────────────────────┘
```

---

## `flex-grow: 1`

```css
.item {
  flex-grow: 1;
}
```

O espaço livre é distribuído:

```text
┌──────────────────────────────────────────────┐
│ [     A     ][     B     ][     C     ]      │
└──────────────────────────────────────────────┘
```

---

## `flex-basis: 0`

```css
.item {
  flex-grow: 1;
  flex-basis: 0;
}
```

A distribuição tende a ser igual:

```text
┌──────────────────────────────────────────────┐
│ [     A     ][     B     ][     C     ]      │
│      1/3          1/3          1/3           │
└──────────────────────────────────────────────┘
```

---

## `flex-shrink: 0`

```css
.item {
  flex-shrink: 0;
}
```

O item não participa do encolhimento:

```text
container pequeno
       ↓
item tenta preservar seu tamanho
       ↓
pode ocorrer overflow
```

---

## `flex: 1`

```css
.item {
  flex: 1;
}
```

É o shorthand mais comum para combinar:

```css
flex-grow: 1;
flex-shrink: 1;
flex-basis: 0%;
```

---

# 25. ⚠️ Correção importante sobre `flex-basis`

É importante separar duas ideias:

### O valor padrão da propriedade

```css
flex-basis: auto;
```

é o padrão de `flex-basis`.

### O valor utilizado por `flex: 1`

```css
flex: 1;
```

resulta em uma configuração com base:

```css
flex-basis: 0%;
```

Portanto:

```text
flex-basis padrão → auto
flex: 1            → base 0%
```

Não devemos confundir os dois.

---

# 26. Resumo final

```text
FLEXBOX
│
├── flex-grow
│   └── controla o crescimento
│
├── flex-shrink
│   └── controla a redução
│
├── flex-basis
│   └── define a base inicial
│
└── flex
    └── shorthand das três
```

A declaração mais importante desta aula é:

```css
.item {
  flex: 1;
}
```

Que podemos associar mentalmente a:

```css
.item {
  flex-grow: 1;
  flex-shrink: 1;
  flex-basis: 0%;
}
```

### 🧠 Regra para lembrar

> **`grow` cresce → `shrink` diminui → `basis` define a base → `flex` junta os três.**

E uma diferença importante para o posicionamento:

```text
flex: 1
→ distribui/ocupa espaço

justify-content: center
→ posiciona os itens dentro do espaço disponível
```
