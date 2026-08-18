# Seletores CSS
> Os seletores css são usados para selecinar elementos e estilizalos. Exstem vários tipos de seletores no entanto os mais comuns vamos ver aqui.
---

## Seletor tag
> Usando a tag como seletor para aplicar estilo no elemento, ao usar uma tag como seletor todos os elementos que possuem a mesma tag será estilizada como o mesmo estilo. Se usarmos virgula é possível estlizar mais de um elemento com o mesmo estilo, mas se separarmos um elemento do outro com espaço iremos estlizar o **< a >** que é flho de **< p >**.
- Exemplo:

```css

h1, a {

  color: red;

} 

p a {

  color: black;

}

```

## Seletor id
> Este seletor ele é usado como marca/propredade na tag do HTML para adicionar um identficar único nesse elemento, possibilitando a estilização desse elemento usando #nomeID para isso, por questão de boas práticas é necessário usarmos esse ID em apenas um elemento em todo o documento.

- Exemplo:

```html

  <h1 id="logo">Bicicletas e Carros</h1>

```

```css

  #logo {

    color: gold; 

  }

```

---

## Seletor Class
> O seletor class é usado para identifcar um elemento para ser possível estiliza-lo no css, a diferênça é que diferente do ID que podemos usar apenas um, a classa podemos reutiliza-la em outros elementos que queremos estilzar com o mesmo estilo. É possível usar múltiplas classe em um ou mais elementos. 
- Exemplo:

```html

  <h2 class="design">Curso de UX Design</h2>
  <h2 class="codigo">Curso de CSS</h2>

  <h2 class="codigo grande underline">Curso de CSS</h2>

```

```css

  .codigo {

    color: blue;

  }

  .design {

    color: blueviolet;

  }

  .grande {

    font-size: 32px;

  }

  .underline {

    text-decoration: underline;

  }

```