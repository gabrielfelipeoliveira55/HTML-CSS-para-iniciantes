# Tag `<img>` (Imagens)

> A tag `<img>` é utilizada para incorporar imagens em uma página HTML. Ela é um **elemento vazio (_void element_)**, ou seja, **não possui tag de fechamento**, pois não envolve conteúdo, apenas referencia um recurso externo.

---

## Principais atributos

### `src` (Source)

> O atributo `src` informa ao navegador onde a imagem está localizada. O valor pode ser um caminho **relativo**, **absoluto** ou uma URL.

**Exemplo:**

```html
<img src="./img/bicicleta.jpg">
```

---

### `alt` (Alternative Text)

> O atributo `alt` fornece um **texto alternativo** para a imagem.

Ele é utilizado quando:

- A imagem não pode ser carregada;
- Um leitor de tela interpreta o conteúdo para usuários com deficiência visual;
- Motores de busca (SEO) precisam compreender o conteúdo da imagem.

> **Boa prática:** descreva apenas o que é importante para o contexto da página.

**Exemplo:**

```html
<img
  src="./img/bicicleta.jpg"
  alt="Bicicleta preta esportiva"
>
```

---

## Sintaxe da tag

### Estrutura

```text
<img
 ├── src="caminho-da-imagem"
 └── alt="descrição-da-imagem">
```

### Exemplo completo

```html
<img
  src="./img/bicicleta.jpg"
  alt="Bicicleta preta esportiva"
>
```

---

# Trabalhando com várias imagens

Basta criar uma nova tag `<img>` para cada imagem.

```html
<img src="./img/bicicleta.jpg" alt="Bicicleta preta">

<img src="./img/floresta.jpg" alt="Floresta">

<img src="./img/lobo.jpg" alt="Lobo cinza">
```

---

# Extensões de imagens

As imagens podem possuir diferentes formatos, cada um indicado para determinadas situações.

| Extensão | Características | Uso recomendado |
|----------|-----------------|-----------------|
| `.jpg` / `.jpeg` | Alta compressão, arquivos menores | Fotografias |
| `.png` | Suporta transparência e maior qualidade | Logos e imagens com fundo transparente |
| `.svg` | Formato vetorial, não perde qualidade ao ampliar | Ícones, logotipos e ilustrações |

---

# Tornando imagens responsivas

Ao inserir uma imagem, ela será exibida em seu tamanho original.

Para evitar que ultrapasse os limites do elemento pai, normalmente utilizamos CSS.

```css
img {
  max-width: 100%;
}
```

## O que `max-width: 100%` faz?

> Limita a largura máxima da imagem ao tamanho do elemento pai (**container**), permitindo que ela diminua quando necessário, sem ultrapassar esse limite.

### Exemplo

```html
<div class="container">
  <img src="./img/bicicleta.jpg" alt="Bicicleta">
</div>
```

```css
.container {
  width: 200px;
}

img {
  max-width: 100%;
}
```

Nesse caso, a imagem ocupará no máximo **200px**, respeitando o tamanho da `<div>`.

---

# `max-width` × `width`

## `max-width: 100%` (Recomendado)

```css
img {
  max-width: 100%;
}
```

### Comportamento

- Nunca aumenta além do tamanho original da imagem;
- Diminui quando necessário;
- Mantém a proporção automaticamente;
- Evita perda de qualidade.

---

## `width: 100%`

```css
img {
  width: 100%;
}
```

### Comportamento

- Sempre tenta ocupar 100% da largura do container;
- Pode ampliar imagens pequenas;
- Ao ampliar além da resolução original, a imagem perde qualidade.

> Na maioria dos casos, **prefira utilizar `max-width: 100%`**.

---

# `display: block` em imagens

Por padrão, a tag `<img>` é um elemento **inline** (mais precisamente, um elemento *inline replaced*).

Isso faz com que exista um pequeno espaço abaixo da imagem devido ao alinhamento da linha de texto (*baseline*).

Uma prática muito comum é alterar seu comportamento para bloco.

```css
img {
  display: block;
}
```

## Vantagens

- Remove o pequeno espaço abaixo da imagem;
- Facilita o posicionamento;
- Evita problemas de alinhamento.

Na maioria dos projetos encontramos a seguinte configuração:

```css
img {
  display: block;
  max-width: 100%;
}
```

---

# Resolução da imagem

A resolução representa a quantidade de pixels existentes em uma imagem.

Exemplo:

```
1200 × 800 px
```

Significa:

- 1200 pixels de largura;
- 800 pixels de altura.

Quanto maior a resolução:

- maior tende a ser a qualidade;
- maior tende a ser o tamanho do arquivo.

---

# Resolução × Tamanho do arquivo

Duas imagens podem mostrar exatamente a mesma fotografia, porém possuir resoluções diferentes.

| Resolução | Qualidade | Arquivo |
|-----------|-----------|----------|
| 300 × 200 | Menor | Menor |
| 1200 × 800 | Média | Médio |
| 2718 × 1920 | Alta | Maior |

Arquivos menores carregam mais rapidamente, porém possuem menos detalhes.

---

# Escolhendo a resolução correta

Cada situação exige um tamanho diferente.

| Situação | Resolução recomendada |
|----------|-----------------------|
| Thumbnail | Pequena |
| Conteúdo da página | Média |
| Banner | Alta |

Usar imagens maiores do que o necessário aumenta o tempo de carregamento da página.

Usar imagens pequenas em espaços grandes resulta em imagens borradas.

---

# Alta densidade de pixels (HiDPI / Retina)

Alguns dispositivos possuem telas com alta densidade de pixels.

Nesses casos, uma imagem pode aparentar estar levemente borrada mesmo sendo exibida em seu tamanho original.

Uma prática bastante utilizada é fornecer imagens com aproximadamente **o dobro da resolução** do tamanho em que serão exibidas.

### Exemplo

A imagem possui:

```
600px de largura
```

Ela será exibida com:

```css
width: 300px;
```

Assim, ela continuará nítida mesmo em telas Retina e outros dispositivos HiDPI.

---

# Boas práticas

✔ Sempre utilize o atributo `alt`.

✔ Utilize imagens na resolução adequada ao espaço onde serão exibidas.

✔ Prefira:

```css
img {
  display: block;
  max-width: 100%;
}
```

✔ Evite ampliar imagens além da resolução original.

✔ Utilize SVG para ícones e logotipos sempre que possível.

✔ Prefira caminhos relativos em projetos locais.

---

# Exemplo completo

## HTML

```html
<div class="produto">
  <img
    src="./img/bicicleta.jpg"
    alt="Bicicleta preta esportiva"
  >
</div>
```

## CSS

```css
.produto {
  width: 350px;
}

img {
  display: block;
  max-width: 100%;
}
```

---

# Resumo

- `<img>` adiciona imagens ao documento HTML.
- `src` define o caminho da imagem.
- `alt` fornece um texto alternativo para acessibilidade e SEO.
- A tag `<img>` é um **void element** (não possui fechamento).
- `max-width: 100%` torna a imagem responsiva sem aumentar além da resolução original.
- `display: block` remove o espaço inferior causado pelo alinhamento da linha.
- Utilize imagens com resolução compatível com o espaço onde serão exibidas.
- Em telas HiDPI, imagens com aproximadamente o dobro da resolução oferecem melhor nitidez.

# SVG, PNG e Otimização de Imagens

## SVG e PNG

Além do formato **JPG/JPEG**, muito utilizado para fotografias, existem outros formatos importantes para desenvolvimento web: **SVG** e **PNG**.

Cada formato possui características específicas e deve ser utilizado conforme o tipo de imagem.

---

## SVG (Scalable Vector Graphics)

O **SVG** é um formato de imagem vetorial baseado em XML.

Diferente das imagens tradicionais compostas por pixels, um SVG é formado por instruções matemáticas (vetores) que desenham linhas, curvas e formas geométricas.

### Principais características

- Escalável infinitamente sem perder qualidade.
- Arquivo baseado em texto.
- Pode ser editado manualmente ou por softwares vetoriais.
- Permite alterar cores e outras propriedades facilmente.
- Geralmente possui tamanho reduzido para ícones e logotipos.

### Exemplo

```html
<img src="./img/logo.svg" alt="Logo da Bikcraft">
```

---

## Estrutura simplificada de um SVG

Um arquivo SVG é composto por código semelhante ao HTML.

```xml
<svg width="100" height="100">
  <circle cx="50" cy="50" r="40" fill="black" />
</svg>
```

O atributo `fill` define a cor do desenho.

Alterando:

```xml
fill="black"
```

para

```xml
fill="blue"
```

a imagem muda de cor sem necessidade de editar uma imagem em um programa gráfico.

Essa é uma das grandes vantagens do SVG.

---

## Vantagens do SVG

Segundo a documentação da Mozilla (MDN):

- Não perde qualidade ao aumentar ou diminuir.
- Ideal para logotipos.
- Ideal para ícones.
- Excelente para ilustrações simples.
- Pode ser estilizado com CSS.
- Pode ser manipulado via JavaScript.
- Mantém ótima nitidez em telas de alta resolução (Retina/HiDPI).

---

## Quando utilizar SVG

Utilize SVG para:

- Logos
- Ícones
- Ilustrações
- Botões gráficos
- Elementos da interface
- Diagramas

Exemplos:

- Logo da empresa
- Ícones de redes sociais
- Ícone de menu
- Ícone de pesquisa
- Setas
- Ilustrações simples

---

# PNG (Portable Network Graphics)

O PNG é um formato de imagem baseado em pixels (bitmap).

Ao contrário do SVG, sua resolução é fixa.

Exemplo:

Uma imagem PNG de:

```
144 × 144 pixels
```

Sempre terá exatamente essa quantidade de pixels.

Ao ampliá-la além desse tamanho, ocorrerá perda de qualidade.

---

## Principais características

- Suporta transparência.
- Excelente para imagens com poucas cores.
- Mantém alta qualidade.
- Não sofre compressão com perdas (lossless).

---

## Quando utilizar PNG

PNG é recomendado para:

- Logos (quando não existir SVG)
- Capturas de tela
- Ícones exportados
- Elementos gráficos pequenos

---

## Transparência

Uma das maiores vantagens do PNG é possuir canal alfa (transparência).

Isso significa que o fundo da imagem pode ser completamente transparente.

Exemplo:

```css
body{
    background: lightblue;
}
```

Se a imagem possuir transparência, o fundo azul aparecerá atrás dela normalmente.

---

## Comparação entre SVG e PNG

| SVG | PNG |
|------|------|
| Vetorial | Bitmap |
| Escala infinita | Resolução fixa |
| Não perde qualidade | Perde qualidade ao ampliar |
| Pode ser editado por código | Não pode ser editado por código |
| Arquivos geralmente menores para ícones | Arquivos maiores para gráficos simples |
| Ideal para logos | Ideal para imagens rasterizadas |

---

# Por que não usar JPG para logos?

O JPG foi criado para fotografias.

Ele:

- não possui transparência;
- utiliza compressão com perdas (lossy);
- perde qualidade ao ser salvo repetidamente.

Logo, não é indicado para:

- logos;
- ícones;
- gráficos simples.

---

# Fotografias utilizam JPG

Fotos possuem milhares de cores e gradientes.

Exemplos:

- paisagens;
- pessoas;
- animais;
- produtos.

Nesses casos o JPG produz arquivos muito menores do que um SVG ou PNG equivalente.

---

# Escolhendo o formato correto

| Tipo de imagem | Melhor formato |
|----------------|----------------|
| Fotografia | JPG/JPEG |
| Logo | SVG |
| Ícone | SVG |
| Ilustração simples | SVG |
| Captura de tela | PNG |
| Logo sem versão vetorial | PNG |

---

# Tamanho da imagem

Nem sempre a imagem com maior resolução é a melhor escolha.

Uma imagem muito grande:

- aumenta o tempo de carregamento;
- consome mais banda;
- prejudica a experiência do usuário.

Por isso, escolha uma resolução compatível com o espaço onde ela será exibida.

---

# Otimização de imagens

Antes de adicionar imagens ao site, é recomendável otimizá-las.

A otimização reduz o tamanho do arquivo sem perda perceptível de qualidade.

Benefícios:

- carregamento mais rápido;
- menor consumo de dados;
- melhor desempenho;
- melhor pontuação em métricas como Core Web Vitals.

---

## Redimensionamento

Também é importante reduzir a resolução da imagem quando ela for maior do que o necessário.

Exemplo:

Uma imagem de:

```
5184 × 3456 px
```

que será exibida com apenas:

```
1200 px
```

de largura pode ser redimensionada antes de ser utilizada.

Isso reduz significativamente o tamanho do arquivo.

---

# Ferramenta recomendada

Uma das ferramentas gratuitas mais utilizadas para otimização é:

**Squoosh**

https://squoosh.app

Ela permite:

- reduzir resolução;
- alterar formato;
- aplicar compressão;
- comparar antes e depois da otimização.

---

# Banco gratuito de imagens

Para obter fotografias gratuitas de alta qualidade, um dos serviços mais utilizados é:

**Unsplash**

https://unsplash.com

As imagens podem ser utilizadas em projetos pessoais e comerciais, conforme os termos da plataforma.

---

# Boas práticas

- Utilize **SVG** para logos e ícones.
- Utilize **PNG** quando precisar de transparência e não houver versão vetorial.
- Utilize **JPG** para fotografias.
- Sempre otimize as imagens antes de enviá-las para o site.
- Escolha uma resolução compatível com o tamanho em que a imagem será exibida.
- Evite arquivos muito grandes sem necessidade.
- Prefira arquivos leves para melhorar o desempenho da página.