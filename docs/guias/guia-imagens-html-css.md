# Guia de imagens no HTML e CSS

Este guia apresenta formas de inserir, dimensionar, recortar e posicionar imagens em páginas web sem distorcê-las. Os exemplos contemplam imagens responsivas, cartões, avatares e imagens de capa.

## 1. Inserindo uma imagem no HTML

Uma imagem de conteúdo deve ser inserida com o elemento `img`:

```html
<img
  src="./img/hobbies/hockey.jpg"
  alt="Jogador praticando hóquei em linha"
>
```

Os atributos principais são:

| Atributo | Função |
| --- | --- |
| `src` | Informa o caminho do arquivo da imagem. |
| `alt` | Descreve o conteúdo ou a função da imagem. |
| `width` e `height` | Informam ao navegador as dimensões ou a proporção do arquivo. |

## 2. Texto alternativo com `alt`

O atributo `alt` é importante para acessibilidade e também é exibido quando a imagem não pode ser carregada.

```html
<img
  src="./img/perfil/cristofer.jpg"
  alt="Foto de perfil de Cristofer Sousa"
>
```

Evite descrições genéricas:

```html
<!-- Evite -->
<img src="./img/perfil/cristofer.jpg" alt="Imagem">
```

Quando a imagem é apenas decorativa e não transmite informação, utilize um texto alternativo vazio:

```html
<img src="./img/detalhe-decorativo.svg" alt="">
```

## 3. Por que usar `display: block`?

O elemento `img` é apresentado como `inline` por padrão. Elementos inline participam da linha de texto e reservam um pequeno espaço abaixo deles para caracteres que ultrapassam a linha de base, como `g`, `p` e `y`.

Esse comportamento pode produzir um espaço aparentemente inexplicável abaixo da imagem:

```css
img {
  display: block;
}
```

Ao utilizar `display: block`:

- a imagem deixa de se comportar como um caractere dentro de uma linha;
- o espaço associado à linha de base desaparece;
- largura, margem e alinhamento ficam mais previsíveis;
- a imagem passa a ocupar sua própria linha.

Essa configuração é especialmente útil em cartões, banners e galerias.

## 4. Imagens responsivas

Uma imagem não deve ultrapassar a largura de seu elemento pai. Uma configuração global comum é:

```css
img {
  display: block;
  max-width: 100%;
  height: auto;
}
```

### `max-width: 100%`

Limita a imagem à largura máxima do elemento pai, mas permite que imagens menores mantenham seu tamanho original.

### `height: auto`

Faz a altura ser calculada automaticamente, preservando a proporção original da imagem.

Também é possível obrigar uma imagem a acompanhar toda a largura disponível:

```css
.banner img {
  display: block;
  width: 100%;
  height: auto;
}
```

Existe uma diferença importante:

| Propriedade | Comportamento |
| --- | --- |
| `max-width: 100%` | A imagem diminui quando necessário, mas não é ampliada além do tamanho original. |
| `width: 100%` | A imagem sempre tenta ocupar toda a largura do elemento pai. |

## 5. Proporção de uma imagem

A proporção é a relação entre a largura e a altura. Alguns exemplos comuns são:

| Proporção | Uso comum |
| --- | --- |
| `1 / 1` | avatar ou miniatura quadrada |
| `4 / 3` | fotografia tradicional |
| `16 / 9` | vídeo, banner ou capa |
| `3 / 4` | retrato vertical |

A propriedade `aspect-ratio` permite reservar uma área com uma proporção determinada:

```css
.cartao-hobby img {
  width: 100%;
  aspect-ratio: 16 / 9;
  object-fit: cover;
}
```

Nesse exemplo, a largura pode variar, mas a relação `16 / 9` será mantida.

## 6. O problema da distorção

Uma imagem pode ficar deformada quando largura e altura são forçadas sem uma regra de ajuste:

```css
/* A imagem pode ficar achatada ou esticada. */
.cartao-hobby img {
  width: 100%;
  height: 220px;
}
```

Isso acontece porque o navegador precisa encaixar a imagem exatamente nas duas dimensões informadas, mesmo que a proporção da fotografia seja diferente.

Para evitar a distorção, utilize `object-fit`.

## 7. A propriedade `object-fit`

A propriedade `object-fit` determina como a imagem será ajustada dentro da área definida por `width`, `height` ou `aspect-ratio`.

Ela produz um efeito perceptível quando a imagem possui uma área delimitada:

```css
.exemplo img {
  width: 100%;
  height: 220px;
  object-fit: cover;
}
```

### `object-fit: cover`

```css
object-fit: cover;
```

- preenche toda a área disponível;
- mantém a proporção original;
- pode recortar partes da imagem;
- é indicado para cartões, capas, avatares e miniaturas.

### `object-fit: contain`

```css
object-fit: contain;
```

- mostra a imagem inteira;
- mantém a proporção original;
- pode deixar espaços vazios nas laterais ou acima e abaixo;
- é indicado para logotipos, produtos e imagens que não podem ser recortadas.

### Outros valores

| Valor | Comportamento |
| --- | --- |
| `fill` | Preenche toda a área e pode distorcer a imagem. É o valor inicial. |
| `cover` | Preenche a área, mantém a proporção e pode recortar. |
| `contain` | Exibe a imagem inteira e pode deixar espaço vazio. |
| `none` | Mantém o tamanho original da imagem. |
| `scale-down` | Escolhe entre `none` e `contain`, utilizando o menor resultado. |

## 8. A propriedade `object-position`

Quando `object-fit: cover` recorta a imagem, `object-position` determina qual região deve permanecer visível.

```css
.cartao-hobby img {
  object-fit: cover;
  object-position: center;
}
```

Valores úteis:

```css
object-position: center;
object-position: center top;
object-position: center bottom;
object-position: left center;
object-position: right center;
```

Também é possível utilizar porcentagens:

```css
object-position: 50% 25%;
```

O primeiro valor controla o eixo horizontal e o segundo controla o eixo vertical:

```text
object-position: posição-horizontal posição-vertical;
```

### Exemplo com uma fotografia vertical

Uma fotografia vertical inserida em um cartão horizontal terá partes recortadas com `cover`. Para preservar o rosto ou a parte superior da imagem, podemos mover o ponto de interesse:

```css
.cartao-hobby img {
  display: block;
  width: 100%;
  height: 220px;
  object-fit: cover;
  object-position: center top;
}
```

Nesse exemplo:

- `width: 100%` acompanha a largura do cartão;
- `height: 220px` estabelece uma altura igual para todos os cartões;
- `object-fit: cover` preenche a área sem distorcer a fotografia;
- `object-position: center top` prioriza a região central e superior;
- `display: block` remove o espaço de linha abaixo da imagem.

## 9. Exemplo completo de cartão

### HTML

```html
<article class="cartao-hobby">
  <img
    src="./img/hobbies/hockey.jpg"
    alt="Partida de hóquei em linha"
    width="1200"
    height="800"
  >

  <div class="cartao-hobby__conteudo">
    <h2>Hóquei em linha</h2>
    <p>Um dos meus esportes favoritos.</p>
  </div>
</article>
```

### CSS

```css
.cartao-hobby {
  overflow: hidden;
  background-color: #fff;
  border: 1px solid #dee2e6;
  border-radius: 1rem;
}

.cartao-hobby img {
  display: block;
  width: 100%;
  height: 220px;
  object-fit: cover;
  object-position: center top;
}

.cartao-hobby__conteudo {
  padding: 1rem;
}
```

O `overflow: hidden` aplicado ao cartão faz a imagem respeitar os cantos arredondados do elemento pai.

## 10. Avatar circular

Para criar uma imagem de perfil circular, a largura e a altura precisam formar uma área quadrada:

```css
.foto-perfil {
  display: block;
  width: 10rem;
  height: 10rem;
  object-fit: cover;
  object-position: center top;
  border: 0.375rem solid #fff;
  border-radius: 50%;
}
```

Uma alternativa é utilizar `aspect-ratio`:

```css
.foto-perfil {
  display: block;
  width: 10rem;
  aspect-ratio: 1 / 1;
  object-fit: cover;
  object-position: center top;
  border-radius: 50%;
}
```

O `border-radius: 50%` só produzirá um círculo perfeito quando a área da imagem for quadrada. Se largura e altura forem diferentes, o resultado será oval.

## 11. Imagem de capa com `background-image`

Imagens decorativas podem ser aplicadas como plano de fundo:

```css
.hero-cover {
  width: 100%;
  min-height: 12rem;
  background-image: url("../img/perfil/capa.jpg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}
```

As propriedades de fundo possuem funções semelhantes às propriedades usadas em `img`:

| Elemento `img` | Imagem de fundo |
| --- | --- |
| `object-fit: cover` | `background-size: cover` |
| `object-position: center top` | `background-position: center top` |

### Quando usar `img`?

Utilize `img` quando a imagem fizer parte do conteúdo e precisar de texto alternativo, por exemplo:

- foto de perfil;
- imagem de uma notícia;
- fotografia de um produto;
- ilustração necessária para compreender o texto.

### Quando usar `background-image`?

Utilize `background-image` quando a imagem for principalmente decorativa ou fizer parte da composição visual, por exemplo:

- textura;
- plano de fundo;
- imagem de capa que não acrescenta informação essencial;
- detalhe visual atrás de um conteúdo.

Uma imagem informativa não deve ser transformada em fundo apenas para facilitar seu posicionamento, pois imagens de fundo não possuem atributo `alt`.

## 12. `cover` ou `contain`?

Use `cover` quando preencher toda a área for mais importante do que mostrar a imagem inteira:

```css
.miniatura {
  object-fit: cover;
}
```

Use `contain` quando mostrar a imagem inteira for mais importante do que preencher toda a área:

```css
.logotipo {
  object-fit: contain;
}
```

| Situação | Valor sugerido |
| --- | --- |
| Foto de perfil | `cover` |
| Imagem de cartão | `cover` |
| Banner ou capa | `cover` |
| Logotipo | `contain` |
| Fotografia que não pode ser recortada | `contain` ou `height: auto` |
| Imagem de produto | depende da composição, normalmente `contain` |

## 13. Carregamento e estabilidade da página

Informar as dimensões originais no HTML ajuda o navegador a reservar o espaço antes de terminar o download:

```html
<img
  src="./img/hobbies/hockey.jpg"
  alt="Partida de hóquei em linha"
  width="1200"
  height="800"
  loading="lazy"
>
```

Mesmo que o CSS altere o tamanho visual, `width` e `height` ajudam o navegador a descobrir a proporção da imagem.

O atributo `loading="lazy"` adia o carregamento de imagens que estão fora da área visível. Ele é útil em galerias e listas extensas.

Não é recomendável utilizá-lo na principal imagem visível no início da página, pois essa imagem precisa carregar rapidamente.

## 14. Imagens com legenda

Quando uma imagem precisa de legenda, utilize `figure` e `figcaption`:

```html
<figure class="imagem-com-legenda">
  <img
    src="./img/hobbies/hockey.jpg"
    alt="Jogadores durante uma partida de hóquei em linha"
  >

  <figcaption>Treino de hóquei em linha.</figcaption>
</figure>
```

```css
.imagem-com-legenda {
  margin: 0;
}

.imagem-com-legenda img {
  display: block;
  max-width: 100%;
  height: auto;
}

.imagem-com-legenda figcaption {
  margin-top: 0.5rem;
  color: #6c757d;
  font-size: 0.875rem;
}
```

## 15. Erros comuns

### Alterar apenas a largura e a altura sem `object-fit`

```css
/* Pode distorcer a imagem. */
img {
  width: 300px;
  height: 100px;
}
```

### Usar `cover` esperando visualizar a imagem inteira

`cover` sempre prioriza o preenchimento da área. Se a proporção da área for diferente da fotografia, algum recorte será necessário.

### Usar `object-position` sem uma área de recorte

`object-position` só produz um resultado perceptível quando existe espaço disponível ou recorte, normalmente em conjunto com dimensões definidas e `object-fit`.

### Aplicar `border-radius` apenas no cartão

Se a imagem ultrapassar os cantos arredondados, aplique:

```css
.cartao {
  overflow: hidden;
  border-radius: 1rem;
}
```

### Utilizar `100vw` dentro de um container

`100vw` representa toda a largura da janela, não a largura do elemento pai. Dentro de um container, prefira:

```css
.imagem {
  width: 100%;
}
```

### Confundir `object-fit` com `background-size`

```css
/* Para elementos img */
img {
  object-fit: cover;
}

/* Para imagens de fundo */
.capa {
  background-size: cover;
}
```

## 16. Configuração-base sugerida

Uma regra global simples pode ser utilizada como ponto de partida:

```css
img {
  display: block;
  max-width: 100%;
  height: auto;
}
```

Depois, cada contexto recebe suas próprias regras:

```css
.cartao-hobby img {
  width: 100%;
  height: 220px;
  object-fit: cover;
  object-position: center top;
}

.foto-perfil {
  width: 10rem;
  height: 10rem;
  object-fit: cover;
  object-position: center top;
  border-radius: 50%;
}

.logotipo {
  width: 8rem;
  height: 4rem;
  object-fit: contain;
}
```

## Resumo

- `display: block` remove o comportamento de linha e o espaço inferior associado à linha de base.
- `max-width: 100%` evita que a imagem ultrapasse o elemento pai.
- `height: auto` preserva a proporção original.
- `aspect-ratio` estabelece uma proporção para a área da imagem.
- `object-fit: cover` preenche a área sem distorcer, mas pode recortar.
- `object-fit: contain` mostra a imagem inteira, mas pode deixar espaços vazios.
- `object-position` escolhe qual parte da imagem deve permanecer em destaque.
- `background-size` e `background-position` são utilizados em imagens de fundo.
- `alt` descreve imagens de conteúdo para tecnologias assistivas.
- `width` e `height` no HTML ajudam o navegador a reservar espaço durante o carregamento.

O ponto principal é decidir se a imagem deve ser completamente exibida ou se deve preencher uma área. Essa escolha determina se devemos preservar seu tamanho natural, utilizar `contain` ou aceitar um recorte com `cover`.
