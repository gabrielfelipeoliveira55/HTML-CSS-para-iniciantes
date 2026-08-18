# CSS — Diferença entre Flexbox e Grid

## 1. Flexbox ou Grid?

Quando começamos a estudar:

```css
display: flex;
```

e:

```css
display: grid;
```

é comum surgir a dúvida:

> **"Qual é melhor: Flexbox ou Grid?"**

A resposta é:

> **Nenhum dos dois é "melhor". Eles resolvem problemas diferentes.**

A principal ideia desta aula é aprender a identificar **qual ferramenta se encaixa melhor no problema que queremos resolver**.

---

# 2. A diferença mais importante

A diferença pode ser resumida inicialmente assim:

```text
FLEXBOX
→ organiza elementos de forma flexível
→ trabalha principalmente em uma dimensão
→ os itens vão se encaixando conforme o espaço disponível

GRID
→ organiza elementos utilizando linhas e colunas
→ trabalha com duas dimensões
→ mantém uma estrutura de linhas e colunas
```

Uma forma simples de visualizar:

```text
FLEXBOX

[A] [B] [C] [D] [E]
       ↓ falta espaço
[A] [B] [C]
[D] [E]

Os itens simplesmente continuam sendo encaixados.
```

Enquanto no Grid:

```text
GRID

┌─────┬─────┬─────┐
│  A  │  B  │  C  │
├─────┼─────┼─────┤
│  D  │  E  │  F  │
└─────┴─────┴─────┘

A ideia de linhas e colunas é preservada.
```

---

# 3. Flexbox não trabalha com uma estrutura fixa de colunas

Imagine vários elementos dentro de um container:

```css
.container {
  display: flex;
  flex-wrap: wrap;
}
```

Quando a largura diminui, o Flexbox tenta encaixar os itens disponíveis.

Por exemplo:

```text
LARGURA GRANDE

[A] [B] [C] [D]
```

Ao diminuir:

```text
LARGURA MENOR

[A] [B] [C]
[D]
```

O Flexbox não precisa manter uma estrutura rígida de colunas.

Ele simplesmente vai colocando os itens conforme o espaço disponível.

---

# 4. O comportamento do Flexbox ao quebrar

Imagine:

```text
[A] [B] [C] [D]
```

Quando o espaço diminui, o Flexbox pode chegar a algo como:

```text
[A] [B] [C]
[D]
```

Ou:

```text
[A] [B]
[C] [D]
```

Dependendo do tamanho dos elementos e das regras utilizadas.

A ideia importante é:

> **O Flexbox não está tentando preservar uma grade específica de colunas.**

Ele está tentando organizar os elementos ao longo do eixo principal e quebrá-los quando necessário.

---

# 5. Grid trabalha com linhas e colunas

No Grid, podemos definir explicitamente uma estrutura:

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr;
}
```

Isso cria:

```text
┌──────────────┬──────────────┐
│   COLUNA 1   │   COLUNA 2   │
├──────────────┼──────────────┤
│   COLUNA 1   │   COLUNA 2   │
└──────────────┴──────────────┘
```

Aqui existem **duas colunas definidas**.

Se adicionarmos mais elementos, o Grid continua respeitando essa estrutura.

Por exemplo:

```text
[A] [B]
[C] [D]
[E] [F]
```

Mesmo que exista espaço visual para outro item ao lado, se a configuração continua sendo:

```css
grid-template-columns: 1fr 1fr;
```

o Grid continuará trabalhando com duas colunas explícitas.

---

# 6. `grid-template-columns`

A propriedade:

```css
grid-template-columns
```

define a estrutura das colunas do Grid.

Exemplo:

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr;
}
```

Temos:

```text
1fr    1fr
 ↓      ↓
Coluna Coluna
```

Ou seja:

```text
┌──────────┬──────────┐
│    1fr   │   1fr    │
└──────────┴──────────┘
```

As duas colunas dividem o espaço disponível.

---

# 7. O problema de definir um número fixo de colunas

Imagine:

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr;
}
```

Temos duas colunas.

Se adicionarmos mais itens:

```text
[A] [B]
[C] [D]
[E] [F]
```

o Grid continuará criando linhas com essas duas colunas.

Ou seja:

> **Definimos explicitamente a quantidade de colunas.**

Isso é diferente do comportamento mais flexível que podemos obter com `flex-wrap` no Flexbox.

---

# 8. Flexbox x Grid

Podemos comparar:

| Característica                  | Flexbox                      | Grid                   |
| ------------------------------- | ---------------------------- | ---------------------- |
| Organização principal           | Uma dimensão                 | Duas dimensões         |
| Trabalha com colunas explícitas | Não necessariamente          | Sim                    |
| Trabalha com linhas explícitas  | Não necessariamente          | Sim                    |
| Distribuição flexível           | Muito forte                  | Também possível        |
| Controle de linhas e colunas    | Mais limitado                | Muito forte            |
| Estrutura de grade              | Não é seu objetivo principal | É o objetivo principal |

A diferença fundamental é:

```text
FLEXBOX
→ "Como distribuo estes elementos?"

GRID
→ "Como distribuo estes elementos dentro de linhas e colunas?"
```

---

# 9. `repeat()`

O Grid possui uma função muito útil chamada:

```css
repeat()
```

Ela permite repetir uma definição de coluna ou linha.

Por exemplo:

```css
grid-template-columns: repeat(4, 1fr);
```

Significa:

```text
repita 4 vezes
        ↓
       1fr
```

Resultado:

```text
┌──────┬──────┬──────┬──────┐
│ 1fr  │ 1fr  │ 1fr  │ 1fr  │
└──────┴──────┴──────┴──────┘
```

É equivalente a:

```css
grid-template-columns: 1fr 1fr 1fr 1fr;
```

---

# 10. `auto-fit`

O Grid também possui valores especiais para criar uma quantidade dinâmica de colunas.

Um deles é:

```css
auto-fit
```

Por exemplo:

```css
grid-template-columns: repeat(auto-fit, 1fr);
```

A ideia é:

> **Tente encaixar a maior quantidade possível de colunas dentro do espaço disponível.**

Isso permite que a estrutura se adapte ao tamanho do container.

---

# 11. `auto-fit` com `1fr`

Considere:

```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, 1fr);
}
```

O `1fr` indica que o espaço disponível deve ser distribuído.

O `auto-fit` tenta encaixar as colunas possíveis.

Visualmente, à medida que o container muda:

```text
Espaço grande:

[A] [B] [C] [D]
```

Diminuindo:

```text
[A] [B] [C]
[D]
```

Diminuindo ainda mais:

```text
[A] [B]
[C] [D]
```

O Grid pode reorganizar a estrutura de acordo com o espaço disponível.

---

# 12. `auto-fit` precisa de uma largura mínima útil

Um ponto importante é que:

```css
repeat(auto-fit, 1fr)
```

sozinho pode não produzir o comportamento responsivo que desejamos em alguns casos.

Uma abordagem muito comum é determinar um tamanho mínimo para cada coluna.

Por exemplo:

```css
grid-template-columns: repeat(
  auto-fit,
  minmax(200px, 1fr)
);
```

Agora estamos dizendo:

> **Crie quantas colunas couberem, mas cada uma deve ter pelo menos `200px`.**

---

# 13. `minmax()`

A função:

```css
minmax()
```

recebe dois valores:

```css
minmax(mínimo, máximo)
```

Por exemplo:

```css
minmax(150px, 1fr)
```

significa:

```text
mínimo → 150px
máximo → 1fr
```

Ou seja:

> A coluna não deve ficar menor que `150px`, mas pode crescer para ocupar o espaço disponível.

---

# 14. `auto-fit` + `minmax()`

Agora podemos juntar:

```css
grid-template-columns:
  repeat(auto-fit, minmax(150px, 1fr));
```

Temos:

```text
repeat()
→ repete a configuração

auto-fit
→ tenta criar quantas colunas couberem

minmax()
→ define o tamanho mínimo e máximo

150px
→ tamanho mínimo

1fr
→ pode crescer e dividir o espaço
```

Essa combinação é muito utilizada para criar grids responsivos.

---

# 15. Exemplo visual

Considere:

```css
.container {
  display: grid;
  grid-template-columns:
    repeat(auto-fit, minmax(150px, 1fr));
  gap: 20px;
}
```

Em uma largura grande:

```text
┌─────────┬─────────┬─────────┬─────────┐
│    A    │    B    │    C    │    D    │
└─────────┴─────────┴─────────┴─────────┘
```

Quando o container diminui:

```text
┌─────────┬─────────┬─────────┐
│    A    │    B    │    C    │
├─────────┼─────────┼─────────┤
│    D    │    E    │    F    │
└─────────┴─────────┴─────────┘
```

Diminuindo ainda mais:

```text
┌─────────┬─────────┐
│    A    │    B    │
├─────────┼─────────┤
│    C    │    D    │
├─────────┼─────────┤
│    E    │    F    │
└─────────┴─────────┘
```

O número de colunas muda conforme o espaço disponível.

---

# 16. Por que `minmax()` é importante?

Imagine que usamos:

```css
grid-template-columns:
  repeat(auto-fit, 200px);
```

Nesse caso, cada coluna terá uma largura fixa de `200px`.

Se houver espaço para:

```text
200px + 200px + 200px
```

teremos três colunas.

Ao diminuir:

```text
200px + 200px
```

ficaremos com duas.

O problema é que os itens não podem crescer livremente além desse tamanho.

---

Com:

```css
grid-template-columns:
  repeat(auto-fit, minmax(200px, 1fr));
```

temos:

```text
mínimo → 200px
máximo → 1fr
```

Isso permite que as colunas:

1. tenham pelo menos `200px`;
2. cresçam quando houver espaço;
3. criem novas colunas quando houver espaço suficiente.

---

# 17. `gap`

Assim como no Flexbox, podemos utilizar:

```css
gap
```

no Grid.

Exemplo:

```css
.container {
  display: grid;
  gap: 20px;
}
```

Isso cria espaçamento entre os itens.

Visualmente:

```text
[A]    [B]    [C]
 ↑       ↑      ↑
     espaço
```

Podemos combinar:

```css
.container {
  display: grid;
  gap: 20px;
  grid-template-columns:
    repeat(auto-fit, minmax(150px, 1fr));
}
```

---

# 18. A principal diferença visual

Essa é provavelmente a parte mais importante para memorizar.

## Flexbox

O Flexbox pensa principalmente em uma sequência de itens:

```text
[A] [B] [C] [D]
```

Se faltar espaço:

```text
[A] [B] [C]
[D]
```

Ele vai reorganizando os itens de acordo com o espaço.

Não existe necessariamente uma grade rígida de colunas.

---

## Grid

O Grid pensa em uma estrutura:

```text
┌─────┬─────┬─────┐
│  A  │  B  │  C  │
├─────┼─────┼─────┤
│  D  │  E  │  F  │
└─────┴─────┴─────┘
```

Existe uma ideia explícita de:

```text
linha
+
coluna
```

A estrutura da grade faz parte do modelo.

---

# 19. Uma forma simples de pensar

Quando estiver escolhendo entre os dois, pense:

```text
Tenho uma sequência de elementos
e quero organizá-los de forma flexível?

→ FLEXBOX
```

Ou:

```text
Preciso estruturar elementos
em linhas e colunas?

→ GRID
```

Não significa que essas sejam regras absolutas, mas é uma excelente referência inicial.

---

# 20. Flexbox trabalha principalmente em uma dimensão

Podemos pensar no Flexbox como trabalhando em uma direção principal:

```text
→ → → → →
```

Por exemplo:

```text
[A] [B] [C] [D]
```

Com `flex-direction: column`, a direção muda:

```text
[A]
 ↓
[B]
 ↓
[C]
 ↓
[D]
```

Ainda estamos trabalhando principalmente com **uma dimensão por vez**.

---

# 21. Grid trabalha em duas dimensões

O Grid permite trabalhar simultaneamente com:

```text
linha
  ↕
  +
coluna
  ↔
```

Visualmente:

```text
        COLUNAS
       →  →  →
      ┌───┬───┬───┐
LINHAS│ A │ B │ C │
  ↓   ├───┼───┼───┤
  ↓   │ D │ E │ F │
      ├───┼───┼───┤
      │ G │ H │ I │
      └───┴───┴───┘
```

Por isso o Grid é muito forte quando a organização espacial em **linhas e colunas** é importante.

---

# 22. Não pense em "Grid é melhor"

Evite pensar:

```text
Grid > Flexbox
```

ou:

```text
Flexbox > Grid
```

O pensamento correto é:

```text
Problema
   ↓
Qual ferramenta resolve melhor?
   ↓
Flexbox ou Grid
```

Cada um possui características próprias.

---

# 23. Exemplo comparativo

## Flexbox

```css
.container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}
```

A ideia é:

```text
"Organize esses itens de forma flexível
e coloque-os onde houver espaço."
```

---

## Grid fixo

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 20px;
}
```

A ideia é:

```text
"Quero duas colunas."
```

---

## Grid responsivo

```css
.container {
  display: grid;
  grid-template-columns:
    repeat(auto-fit, minmax(150px, 1fr));
  gap: 20px;
}
```

A ideia é:

```text
"Quero que o Grid crie quantas colunas
forem possíveis, respeitando um tamanho mínimo."
```

---

# 24. Comparação mental

Podemos guardar esta imagem mental:

```text
FLEXBOX

"Tenho vários itens.
Como distribuo eles?"

        ↓

[A] [B] [C] [D]
        ↓
[A] [B] [C]
[D]
```

Já no Grid:

```text
GRID

"Como estruturo esses itens
em linhas e colunas?"

        ↓

┌─────┬─────┬─────┐
│  A  │  B  │  C  │
├─────┼─────┼─────┤
│  D  │  E  │  F  │
└─────┴─────┴─────┘
```

---

# 25. Resumo dos principais conceitos

| Conceito                | Significado                                       |
| ----------------------- | ------------------------------------------------- |
| `display: flex`         | Ativa o Flexbox                                   |
| `flex-wrap: wrap`       | Permite quebra dos itens                          |
| `display: grid`         | Ativa o Grid                                      |
| `grid-template-columns` | Define as colunas                                 |
| `repeat()`              | Repete uma estrutura                              |
| `auto-fit`              | Tenta encaixar o maior número possível de colunas |
| `minmax()`              | Define tamanho mínimo e máximo                    |
| `1fr`                   | Distribui uma fração do espaço disponível         |
| `gap`                   | Define espaçamento entre os itens                 |

---

# 26. A combinação mais importante da aula

Para um Grid responsivo:

```css
.container {
  display: grid;
  grid-template-columns:
    repeat(auto-fit, minmax(150px, 1fr));
  gap: 20px;
}
```

Podemos interpretar cada parte:

```text
display: grid
      ↓
usa Grid

repeat()
      ↓
repete a definição

auto-fit
      ↓
tenta encaixar mais colunas

minmax(150px, 1fr)
      ↓
mínimo de 150px
máximo flexível

gap: 20px
      ↓
espaçamento entre os itens
```

---

# 27. Regra mental para revisar

```text
┌─────────────────────────────────────────┐
│                FLEXBOX                  │
├─────────────────────────────────────────┤
│ Flexível                                │
│ Uma dimensão                            │
│ Itens se encaixam                       │
│ Ótimo para distribuir elementos         │
└─────────────────────────────────────────┘
```

```text
┌─────────────────────────────────────────┐
│                  GRID                   │
├─────────────────────────────────────────┤
│ Linhas + colunas                        │
│ Duas dimensões                          │
│ Estrutura de grade                      │
│ Ótimo para layouts em grade             │
└─────────────────────────────────────────┘
```

### 🧠 Para memorizar

> **Flexbox pensa mais em "itens e espaço".**

> **Grid pensa mais em "linhas e colunas".**

E o mais importante:

> **Não existe "Flexbox é melhor que Grid" ou "Grid é melhor que Flexbox". A escolha depende do problema que você precisa resolver.**
