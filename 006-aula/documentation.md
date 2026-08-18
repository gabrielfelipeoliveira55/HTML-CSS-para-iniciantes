# Estilos Padrão do Navegador (User Agent Stylesheet)

> Todo navegador possui uma folha de estilos padrão (*User Agent Stylesheet*), responsável por aplicar estilos iniciais aos elementos HTML.

Esses estilos fazem com que elementos como `<h1>`, `<p>`, `<a>` e `<button>` possuam uma aparência inicial, mesmo que nenhum CSS tenha sido escrito pelo desenvolvedor.

Por exemplo:

- `<h1>` normalmente possui uma fonte maior e em negrito;
- `<p>` possui margens padrão;
- `<a>` geralmente é exibido na cor azul e sublinhado;
- `<button>` recebe estilos próprios do navegador.

> Esses estilos existem para melhorar a experiência inicial do usuário e garantir uma apresentação mínima dos elementos.

---

# Inspecionando os Estilos

As ferramentas de desenvolvimento dos navegadores permitem visualizar:

- Os estilos definidos pelo desenvolvedor;
- Os estilos aplicados pelo navegador;
- A origem de cada propriedade CSS.

Isso facilita compreender quais estilos já existem antes mesmo da criação do CSS da aplicação.

---

# Consistência entre Navegadores

Os navegadores modernos procuram manter estilos padrão semelhantes para os principais elementos HTML.

Entretanto, pequenas diferenças ainda podem existir entre navegadores e sistemas operacionais.

Por esse motivo, durante muitos anos surgiram técnicas para padronizar esses estilos.

---

# CSS Reset

> O **CSS Reset** remove ou redefine grande parte dos estilos padrão aplicados pelo navegador.

Seu objetivo é fazer com que o desenvolvedor comece praticamente do zero, definindo manualmente todos os estilos da página.

**Exemplo simplificado:**

```css
* {
    margin: 0;
    padding: 0;
}
```

Essa abordagem reduz diferenças entre navegadores, mas exige que todos os estilos sejam definidos posteriormente.

---

# Normalize.css

> O **Normalize.css** busca manter os estilos úteis do navegador enquanto corrige inconsistências entre diferentes navegadores.

Ao contrário do Reset, ele **não remove todos os estilos**, apenas procura torná-los mais consistentes.

Essa abordagem preserva diversos comportamentos considerados desejáveis.

---

# Reboot

> O **Reboot** é uma folha de estilos utilizada pelo framework **Bootstrap**.

Sua proposta combina características do Reset e do Normalize:

- Remove alguns estilos padrão;
- Mantém outros considerados úteis;
- Aplica uma base consistente para projetos desenvolvidos com Bootstrap.

---

# Personalizando os Estilos Manualmente

Em vez de utilizar um Reset completo, é possível sobrescrever apenas os estilos necessários.

**Exemplo:**

```css
body {
    margin: 0;
}

h1,
h2,
p {
    margin: 0;
    font-size: 16px;
    font-weight: normal;
}
```

Essa abordagem oferece maior controle sobre quais estilos serão alterados.

---

# Herança (Inheritance)

> Algumas propriedades CSS são automaticamente herdadas pelos elementos filhos.

Isso significa que, ao definir determinada propriedade em um elemento pai, seus descendentes poderão utilizar esse mesmo valor.

**Exemplo:**

```css
body {
    color: seagreen;
}
```

```html
<body>

    <h1>Título</h1>

    <p>Parágrafo</p>

</body>
```

Nesse caso, tanto o `<h1>` quanto o `<p>` herdarão a propriedade `color`.

---

# Propriedades Herdáveis

Diversas propriedades relacionadas à tipografia são herdadas automaticamente.

Alguns exemplos:

- `color`
- `font-family`
- `font-size`
- `font-style`
- `font-weight`
- `line-height`

Isso reduz a necessidade de repetir as mesmas regras em vários elementos.

---

# Quando a Herança Não Acontece

Nem todas as propriedades são herdadas automaticamente.

Além disso, alguns elementos possuem valores definidos pelo próprio navegador.

É o caso, por exemplo, dos links (`<a>`) e dos botões (`<button>`), que normalmente recebem estilos padrão próprios.

Por isso, mesmo definindo:

```css
body {
    color: seagreen;
}
```

um link poderá continuar azul caso o navegador já tenha definido outra cor para esse elemento.

---

# Valor `inherit`

> O valor **`inherit`** força uma propriedade a utilizar exatamente o mesmo valor do elemento pai.

**Exemplo:**

```css
a {
    color: inherit;
}
```

Agora o link utilizará a mesma cor definida em seu elemento pai.

Se posteriormente o valor da propriedade mudar no pai, o link será atualizado automaticamente.

---

# Resumo

Nesta aula aprendemos que:

- Os navegadores aplicam uma folha de estilos padrão chamada **User Agent Stylesheet**.
- Esses estilos podem variar levemente entre navegadores.
- O **CSS Reset** remove praticamente todos os estilos padrão.
- O **Normalize.css** mantém os estilos úteis e corrige inconsistências.
- O **Reboot** combina características do Reset e do Normalize.
- Algumas propriedades CSS são herdadas automaticamente pelos elementos filhos.
- O valor `inherit` força uma propriedade a utilizar o mesmo valor definido no elemento pai.