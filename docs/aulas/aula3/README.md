## Aula 3 — Página de Hobbies e introdução ao Flexbox

Nesta aula, avançamos no desenvolvimento do nosso **Portal de Notícias** por meio da construção e da estilização da seção de **Hobbies**.

O objetivo foi compreender como os elementos HTML são organizados visualmente e como o CSS pode ser utilizado para criar uma galeria de conteúdos mais limpa, flexível e adaptável.

### 1. Elementos em bloco e elementos inline

Inicialmente, diferenciamos os dois principais comportamentos de exibição dos elementos HTML.

Os **elementos em bloco** normalmente ocupam toda a largura disponível e iniciam uma nova linha.

Exemplos:

```html
<div></div>
<section></section>
<article></article>
<p></p>
<h2></h2>
```

Os **elementos inline** ocupam apenas o espaço necessário para apresentar seu conteúdo e permanecem na mesma linha.

Exemplos:

```html
<span></span>
<a></a>
<strong></strong>
<em></em>
```

Também observamos que esses comportamentos podem ser alterados pelo CSS por meio da propriedade `display`.

### 2. Diferença entre `div` e `span`

Estudamos que a tag `<div>` é um elemento genérico em bloco. Ela pode ser utilizada para agrupar e organizar partes da página quando não existe uma tag semântica mais adequada.

```html
<div class="conteudo-cartao">
  <h3>Música</h3>
  <p>Descrição do hobby.</p>
</div>
```

A tag `<span>` é um elemento genérico inline, normalmente utilizada para selecionar ou estilizar uma pequena parte de um conteúdo.

```html
<p>
  Meu hobby favorito é
  <span class="destaque">ouvir música</span>.
</p>
```

Antes de utilizar uma `<div>` ou um `<span>`, devemos verificar se existe uma tag semântica que represente melhor a função daquele conteúdo.

### 3. Semântica HTML

Retomamos a importância de utilizar elementos HTML que descrevam adequadamente a função do conteúdo apresentado.

Na página de Hobbies, utilizamos:

* `<main>` para representar o conteúdo principal da página;
* `<section>` para agrupar conteúdos relacionados;
* `<article>` para representar cada hobby de maneira independente;
* `<figure>` para agrupar uma imagem;
* `<figcaption>` para apresentar a legenda da imagem;
* `<time>` para representar a data da publicação;
* `<header>`, `<nav>` e `<footer>` para organizar as principais áreas do portal.

Cada hobby foi estruturado como um artigo independente:

```html
<article class="cartao-hobby">
  <figure>
    <img
      src="./img/hobbies/musica.jpg"
      alt="Pessoa utilizando fones de ouvido"
    />

    <figcaption>
      Música para relaxar e buscar inspiração
    </figcaption>
  </figure>

  <div class="conteudo-cartao">
    <h3>Música</h3>
    <p>Descrição do hobby.</p>
  </div>
</article>
```

### 4. Introdução ao Flexbox

Utilizamos o Flexbox para transformar a lista vertical de hobbies em uma galeria de cartões.

```css
.galeria-hobbies {
  display: flex;
  flex-wrap: wrap;
  gap: 1.5rem;
}
```

Nessa estrutura:

* `display: flex` transforma a galeria em um contêiner Flexbox;
* `flex-wrap: wrap` permite que os cartões sejam distribuídos em novas linhas quando não houver espaço disponível;
* `gap` cria um espaçamento uniforme entre os cartões.

Cada elemento `<article>` tornou-se um item flexível:

```css
.cartao-hobby {
  flex: 1 1 280px;
}
```

Essa declaração indica que o cartão:

* pode crescer para aproveitar o espaço disponível;
* pode diminuir quando o espaço estiver reduzido;
* utiliza `280px` como tamanho inicial de referência.

### 5. Organização das imagens

Também trabalhamos com imagens de diferentes dimensões e proporções.

```css
.cartao-hobby img {
  display: block;
  width: 100%;
  height: 220px;
  object-fit: cover;
}
```

A propriedade `object-fit: cover` faz com que a imagem preencha toda a área disponível. Entretanto, ela poderá recortar partes da fotografia, especialmente quando a imagem estiver na orientação vertical.

Quando for necessário preservar a imagem inteira, podemos utilizar:

```css
.imagem-vertical {
  object-fit: contain;
  background-color: #e9ecef;
}
```

Dessa forma, as imagens horizontais podem utilizar `cover`, enquanto as imagens verticais podem utilizar `contain`.

## Resultado esperado

Ao final da atividade, a página de Hobbies deveria apresentar:

* cabeçalho e menu de navegação compartilhados com as demais páginas;
* introdução da seção de Hobbies;
* pelo menos três hobbies;
* um elemento `<article>` para cada hobby;
* imagem, legenda, título, descrição e data;
* galeria organizada com Flexbox;
* cartões capazes de crescer, diminuir e mudar de linha;
* imagens ajustadas ao espaço disponível;
* estilos específicos organizados no arquivo `hobbies.css`;
* alterações registradas e enviadas ao GitHub.

O conteúdo desenvolvido nesta aula servirá como base para os próximos estudos sobre **responsividade**, **media queries** e adaptação do portal para diferentes tamanhos de tela.
