## Tags HTML Mais Comuns

> O HTML possui diversas tags, cada uma com uma função específica. Nesta aula foram apresentadas algumas das tags mais utilizadas para estruturar o conteúdo de uma página web: `<p>`, `<h1>` até `<h6>` e `<a>`.

---

### Tag `<p>` (Parágrafo)

> A tag `<p>` é utilizada para representar um **parágrafo** de texto. Além de organizar o conteúdo visualmente, ela informa ao navegador e às tecnologias assistivas que aquele trecho representa um parágrafo.

**Sintaxe:**

```html
<p>Este é um parágrafo.</p>
```

---

### Tags `<h1>` até `<h6>` (Títulos)

> As tags `<h1>` até `<h6>` representam os **títulos e subtítulos** de uma página, organizando o conteúdo de forma hierárquica.

A hierarquia é definida da seguinte maneira:

- `<h1>` → Título principal da página.
- `<h2>` → Subtítulo do `<h1>`.
- `<h3>` → Subtítulo do `<h2>`.
- `<h4>` → Subtítulo do `<h3>`.
- `<h5>` → Subtítulo do `<h4>`.
- `<h6>` → Subtítulo do `<h5>`.

**Exemplo:**

```html
<h1>Cursos Online de HTML e CSS</h1>

<h2>HTML</h2>

<p>Curso de HTML, aprenda do zero.</p>

<h2>CSS</h2>

<p>Curso de CSS, aprenda do zero.</p>
```

> **Importante:** A hierarquia dos títulos **não define seu tamanho visual**. Ela define apenas a **semântica** do conteúdo. A aparência dos títulos será personalizada posteriormente com CSS.

#### Benefícios da hierarquia

Uma boa hierarquia de títulos oferece diversas vantagens:

- Organiza o conteúdo da página.
- Facilita a leitura por pessoas e leitores de tela.
- Auxilia mecanismos de busca (SEO) a compreenderem quais informações são mais importantes.
- Torna a estrutura da página mais clara e organizada.

---

### Tag `<a>` (Link)

> A tag `<a>` é utilizada para criar **hiperlinks**, permitindo navegar para outras páginas, arquivos ou recursos.

Para funcionar corretamente, normalmente ela precisa do atributo **`href`**, responsável por informar o destino do link.

**Sintaxe:**

```html
<a href="/html">Curso de HTML</a>
```

#### Partes da sintaxe

```html
<a href="/html">Curso de HTML</a>
│ │      │         │
│ │      │         └── Conteúdo do link
│ │      └──────────── Valor do atributo
│ └─────────────────── Atributo (href)
└───────────────────── Tag de abertura
```

> **Observação:** Se a tag `<a>` não possuir o atributo `href`, ela não terá um destino para navegar.

---

## Aninhamento de Tags

> No HTML, é possível colocar uma tag dentro de outra. Esse processo é chamado de **aninhamento de elementos** (*nesting*).

**Exemplo:**

```html
<p>
    Curso de HTML.
    <a href="/html">Saiba mais</a>
</p>
```

Nesse exemplo:

- A tag `<p>` representa um parágrafo.
- A tag `<a>` está dentro do parágrafo.
- O link passa a fazer parte do conteúdo desse parágrafo.

> O aninhamento é uma das bases da construção de documentos HTML e será utilizado constantemente durante o desenvolvimento de páginas web.

---

## Observações importantes

- Pressionar **Enter** no código HTML não faz o conteúdo aparecer em uma nova linha na página.
- O comportamento visual dos elementos depende do tipo de elemento e, posteriormente, dos estilos aplicados com CSS.
- As tags HTML podem conter outras tags, formando uma estrutura hierárquica que organiza o conteúdo da página.

# Estrutura Básica de um Documento HTML

> Todo documento HTML segue uma estrutura básica composta por elementos que identificam o tipo do documento, definem sua estrutura e organizam as informações visíveis e invisíveis da página.

---

## Estrutura Completa

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Título da Página</title>
        <meta charset="UTF-8">
    </head>

    <body>

    </body>
</html>
```

---

## `<!DOCTYPE html>`

> O `<!DOCTYPE html>` deve ser a primeira declaração do documento HTML. Ele informa ao navegador que o arquivo utiliza a especificação **HTML5**.

**Sintaxe:**

```html
<!DOCTYPE html>
```

### Função

- Identifica o documento como HTML5.
- Auxilia o navegador a interpretar corretamente a página.
- Faz parte da estrutura padrão de qualquer documento HTML.

> **Observação:** Atualmente utiliza-se apenas `<!DOCTYPE html>`, pois o HTML5 é o padrão adotado pelos navegadores modernos.

---

## Tag `<html>`

> A tag `<html>` representa o elemento raiz do documento. Todo o conteúdo da página deve estar contido dentro dela.

**Sintaxe:**

```html
<html>

</html>
```

### Estrutura

```html
<html>
    <!-- Todo o documento HTML -->
</html>
```

### Função

- Delimita o início e o fim do documento HTML.
- Contém todas as demais tags da página.

### Atributo `lang`

A tag `<html>` pode receber o atributo `lang`, responsável por informar o idioma principal da página.

**Exemplo:**

```html
<html lang="pt-BR">
```

> O atributo `lang` melhora a acessibilidade e auxilia mecanismos de busca a identificarem o idioma do conteúdo.

---

## Tag `<head>`

> A tag `<head>` armazena informações sobre o documento que não são exibidas diretamente na página, mas que são importantes para o navegador e outros serviços.

**Sintaxe:**

```html
<head>

</head>
```

### Alguns elementos que ficam dentro do `<head>`

- `<title>`
- `<meta>`
- Links para arquivos CSS
- Scripts JavaScript (dependendo da estratégia utilizada)

> Nesta aula foram apresentados apenas os elementos `<title>` e `<meta>`.

---

## Tag `<body>`

> A tag `<body>` contém todo o conteúdo visível da página.

É dentro dela que normalmente ficam:

- Títulos (`<h1>` até `<h6>`)
- Parágrafos (`<p>`)
- Links (`<a>`)
- Imagens
- Listas
- Tabelas
- Formulários
- Demais elementos visíveis ao usuário.

**Sintaxe:**

```html
<body>

</body>
```

---

## Tag `<title>`

> A tag `<title>` define o título da página exibido na aba do navegador.

Ela deve ser declarada dentro da tag `<head>`.

**Exemplo:**

```html
<head>
    <title>Cursos de HTML</title>
</head>
```

### Benefícios

- Identifica a página na aba do navegador.
- Facilita a navegação entre várias abas abertas.
- Auxilia mecanismos de busca (SEO) na identificação do conteúdo da página.

---

## Tag `<meta>`

> A tag `<meta>` fornece informações adicionais (**metadados**) sobre o documento HTML.

Diferentemente da maioria das tags HTML, ela **não possui tag de fechamento**.

### Sintaxe

```html
<meta atributo="valor">
```

---

### Meta Charset

Nesta aula foi apresentado o atributo **`charset`**, responsável por definir a codificação de caracteres utilizada pela página.

**Exemplo:**

```html
<meta charset="UTF-8">
```

### Função

- Permite que caracteres especiais sejam interpretados corretamente.
- Garante o funcionamento de acentos, cedilha (`ç`), símbolos e diversos caracteres especiais.

> Atualmente, a codificação **UTF-8** é o padrão utilizado na maioria dos documentos HTML.

---

# Hierarquia da Estrutura

```text
Documento HTML
│
├── <!DOCTYPE html>
│
└── <html>
    │
    ├── <head>
    │   ├── <title>
    │   └── <meta>
    │
    └── <body>
        ├── <h1>
        ├── <p>
        ├── <a>
        └── ...
```

---

## Resumo

A estrutura mínima de um documento HTML é composta por:

- `<!DOCTYPE html>` → identifica o documento como HTML5.
- `<html>` → elemento raiz da página.
- `<head>` → informações para o navegador.
- `<title>` → título exibido na aba do navegador.
- `<meta charset="UTF-8">` → define a codificação de caracteres.
- `<body>` → conteúdo visível da página.