# Documentação da página de Hobbies

Esta documentação apresenta a estrutura da página `hobbies.html` e explica as
principais regras presentes em `css/hobbies.css`.

O objetivo da página é aplicar os conteúdos da Aula 3 de Desenvolvimento Web I:

- HTML semântico;
- organização de conteúdo com `section` e `article`;
- Flexbox;
- medidas absolutas e relativas;
- containers fluidos;
- imagens adaptáveis;
- separação entre CSS global e CSS específico da página.

## Organização dos arquivos

```text
meu-portal/
├── index.html
├── hobbies.html
├── perfil.html
├── css/
│   ├── reset.css
│   ├── global.css
│   └── hobbies.css
├── docs/
│   └── hobbies.md
└── img/
    └── hobbies/
        ├── musica.jpg
        ├── cinema.jpg
        └── hockey.jpg
```

## Responsabilidade de cada arquivo CSS

| Arquivo | Responsabilidade |
|---|---|
| `reset.css` | Remove ou normaliza estilos que o navegador aplica automaticamente. |
| `global.css` | Armazena regras compartilhadas entre todas as páginas, como cabeçalho, menu, tipografia e rodapé. |
| `hobbies.css` | Armazena regras exclusivas da página de Hobbies, como container, galeria, cartões e imagens. |

A ordem de importação é importante:

```html
<link rel="stylesheet" href="./css/reset.css">
<link rel="stylesheet" href="./css/global.css">
<link rel="stylesheet" href="./css/hobbies.css">
```

O navegador lê o CSS de cima para baixo. Por isso, as regras específicas da
página são carregadas depois das regras globais.

## Estrutura semântica da página

```text
body
├── header
│   ├── h1 - título do portal
│   ├── p - descrição do portal
│   └── nav - navegação principal
│       └── ul
│           ├── li + a - Programação
│           ├── li + a - Hobbies
│           └── li + a - Sobre Mim
├── main.container
│   ├── section.introducao-hobbies
│   │   ├── h2 - título da página
│   │   └── p - apresentação do conteúdo
│   └── section.galeria-hobbies
│       ├── h2.titulo-galeria
│       ├── article.cartao-hobby - Música
│       ├── article.cartao-hobby - Cinema
│       └── article.cartao-hobby - Hóquei
└── footer.footer
    ├── p - identificação do projeto
    └── p - identificação da instituição
```

### Por que utilizar essas tags?

| Elemento | Função na página |
|---|---|
| `<header>` | Apresenta o portal e contém sua navegação principal. |
| `<nav>` | Identifica o conjunto de links utilizado para navegar entre as páginas. |
| `<main>` | Representa o conteúdo principal e exclusivo da página. |
| `<section>` | Agrupa conteúdos relacionados por um mesmo assunto. |
| `<article>` | Representa um conteúdo independente, neste caso, cada hobby. |
| `<figure>` | Agrupa uma imagem e sua legenda. |
| `<figcaption>` | Apresenta a legenda associada à imagem. |
| `<time>` | Representa uma data em formato compreensível pelo navegador. |
| `<footer>` | Apresenta informações finais sobre o projeto e a instituição. |

## Sketch de um cartão de hobby

Cada hobby é representado por um elemento `<article>` independente.

```text
article.cartao-hobby
┌──────────────────────────────────┐
│ figure                           │
│ ┌──────────────────────────────┐ │
│ │ img                          │ │
│ │ fotografia do hobby          │ │
│ └──────────────────────────────┘ │
│ figcaption: legenda da imagem    │
├──────────────────────────────────┤
│ div.conteudo-cartao              │
│                                  │
│ h3: nome do hobby                │
│                                  │
│ p: descrição do hobby            │
│                                  │
│ p.data-publicacao                │
│ └── time: data da publicação     │
└──────────────────────────────────┘
```

O HTML correspondente segue este padrão:

```html
<article class="cartao-hobby">
    <figure>
        <img
            src="./img/hobbies/musica.jpg"
            alt="Pessoa utilizando fones de ouvido"
        >
        <figcaption>
            Música para relaxar e buscar inspiração
        </figcaption>
    </figure>

    <div class="conteudo-cartao">
        <h3>Música</h3>

        <p>
            Gosto de escutar música durante os momentos de descanso.
        </p>

        <p class="data-publicacao">
            Publicado em
            <time datetime="2026-08-28">28 de agosto de 2026</time>
        </p>
    </div>
</article>
```

## Representação da galeria com Flexbox

```text
section.galeria-hobbies - container Flexbox
┌─────────────────────────────────────────────────────────────────┐
│ Título da galeria                                               │
├───────────────────┬───────────────────┬─────────────────────────┤
│ article           │ article           │ article                 │
│ Música            │ Cinema            │ Hóquei                  │
│ item flexível     │ item flexível     │ item flexível           │
└───────────────────┴───────────────────┴─────────────────────────┘

Quando não existir espaço horizontal suficiente:

┌──────────────────────────┬──────────────────────────┐
│ article - Música         │ article - Cinema         │
├──────────────────────────┴──────────────────────────┤
│ article - Hóquei                                    │
└─────────────────────────────────────────────────────┘
```

Essa mudança de linha acontece por causa de:

```css
.galeria-hobbies {
    display: flex;
    flex-wrap: wrap;
    gap: 1.5rem;
}
```

## Referência das propriedades CSS

### Configuração geral

| Propriedade | Valor utilizado | Função |
|---|---:|---|
| `box-sizing` | `border-box` | Faz com que padding e borda sejam considerados dentro da largura e da altura declaradas. |
| `width` | `90%` | Faz o container ocupar 90% do espaço disponível no elemento pai. |
| `max-width` | `1200px` | Impede que o conteúdo cresça excessivamente em telas grandes. |
| `margin` | `0 auto` | Remove a margem vertical e centraliza o container horizontalmente. |
| `padding` | `2rem 0` | Cria espaçamento interno vertical no conteúdo principal. |
| `line-height` | `1.6` | Aumenta o espaço entre as linhas e melhora a leitura dos textos. |
| `text-align` | `center` | Centraliza o conteúdo textual da introdução. |

### Flexbox e galeria

| Propriedade | Valor utilizado | Função |
|---|---:|---|
| `display` | `flex` | Transforma a galeria em um container Flexbox. |
| `flex-wrap` | `wrap` | Permite que os cartões mudem de linha quando não houver espaço. |
| `gap` | `1.5rem` | Define o espaço entre os itens da galeria. |
| `align-items` | `stretch` | Faz os itens ocuparem a altura disponível na linha. |
| `flex-basis` | `100%` | Faz o título da galeria ocupar uma linha completa. |
| `flex` | `1 1 280px` | Permite que o cartão cresça, diminua e utilize `280px` como tamanho inicial. |

O atalho abaixo:

```css
flex: 1 1 280px;
```

representa:

| Parte | Propriedade | Significado |
|---:|---|---|
| `1` | `flex-grow` | O cartão pode crescer para aproveitar o espaço disponível. |
| `1` | `flex-shrink` | O cartão pode diminuir quando o espaço ficar reduzido. |
| `280px` | `flex-basis` | O tamanho inicial de referência do cartão é `280px`. |

### Aparência dos cartões

| Propriedade | Valor utilizado | Função |
|---|---:|---|
| `overflow` | `hidden` | Esconde conteúdos que ultrapassem os limites arredondados do cartão. |
| `border` | `1px solid #d8d8d8` | Desenha uma borda fina ao redor do cartão. |
| `border-radius` | `0.75rem` | Arredonda os cantos do cartão. |
| `background-color` | `#ffffff` | Define o fundo branco do cartão. |
| `box-shadow` | `0 4px 12px rgba(...)` | Cria uma sombra leve e produz sensação de profundidade. |

### Imagens

| Propriedade | Valor utilizado | Função |
|---|---:|---|
| `display` | `block` | Remove o pequeno espaço inferior normalmente existente em imagens inline. |
| `width` | `100%` | Faz a imagem acompanhar toda a largura do cartão. |
| `height` | `220px` | Padroniza a altura visual das imagens. |
| `object-fit` | `cover` | Preenche toda a área da imagem, mantendo a proporção e realizando recortes quando necessário. |
| `object-fit` | `contain` | Exibe a imagem inteira, mantendo sua proporção, mas pode criar espaços livres. |
| `object-position` | `center top` | Define qual região deverá ser priorizada quando ocorrer um recorte. |

## Imagens horizontais e verticais

Com uma altura fixa, imagens horizontais e verticais precisam adotar uma regra
de encaixe. Não é possível manter simultaneamente a imagem inteira, preencher
todo o espaço, preservar a proporção e evitar diferenças de tamanho.

### `cover`: preenche e pode recortar

```css
.cartao-hobby img {
    display: block;
    width: 100%;
    height: 220px;
    object-fit: cover;
}
```

É indicado para imagens horizontais ou fotografias em que o recorte não elimina
uma informação importante.

### `contain`: preserva a imagem inteira

Para imagens verticais, pode-se adicionar uma classe específica:

```html
<img
    class="imagem-vertical"
    src="./img/hobbies/musica.jpg"
    alt="Pessoa utilizando fones de ouvido"
>
```

```css
.cartao-hobby img.imagem-vertical {
    object-fit: contain;
    background-color: #e9ecef;
}
```

Nesse caso, a imagem inteira será apresentada e os cartões continuarão com a
mesma altura. Entretanto, podem surgir espaços laterais ao redor da fotografia.

### `object-position`: escolhe a região do recorte

Quando o preenchimento completo for mais importante, o recorte pode ser
reposicionado:

```css
.cartao-hobby img {
    object-fit: cover;
    object-position: center top;
}
```

Essa regra prioriza a parte superior central, algo útil em fotografias de
pessoas. Ela não elimina o recorte, apenas determina onde ele acontecerá.

## `gap` e `margin` não são a mesma coisa

```css
.galeria-hobbies {
    gap: 1.5rem;
}
```

O `gap` pertence ao container e controla o espaço entre seus itens. A propriedade
`margin` pertence ao próprio elemento e controla sua distância em relação aos
elementos ao redor.

| Propriedade | Aplicada em | Uso principal |
|---|---|---|
| `gap` | Container Flexbox | Criar espaçamento uniforme entre os cartões. |
| `margin` | Elemento individual | Criar distância externa específica para um elemento. |
| `padding` | Elemento individual | Criar espaço entre o conteúdo e as bordas do elemento. |

## Medidas utilizadas

| Unidade | Referência | Exemplo na página |
|---|---|---|
| `px` | Valor fixo em pixels | `height: 220px` e `max-width: 1200px`. |
| `rem` | Tamanho da fonte do elemento raiz | `padding: 2rem` e `gap: 1.5rem`. |
| `%` | Espaço disponível no elemento pai | `width: 90%` e `width: 100%`. |

Por padrão, os navegadores normalmente utilizam `16px` como tamanho da fonte
raiz. Nesse cenário, `1rem` corresponde a `16px`. Essa relação pode mudar se o
tamanho da fonte do elemento `<html>` for alterado.

## Checklist da página

- [ ] A página importa `reset.css`, `global.css` e `hobbies.css` nessa ordem.
- [ ] O menu conecta as páginas Programação, Hobbies e Sobre Mim.
- [ ] A página possui somente um conteúdo principal representado por `<main>`.
- [ ] Cada hobby está dentro de um `<article>` independente.
- [ ] As imagens possuem textos alternativos por meio do atributo `alt`.
- [ ] As imagens e legendas estão agrupadas com `<figure>` e `<figcaption>`.
- [ ] As datas estão representadas pela tag `<time>`.
- [ ] A galeria utiliza `display: flex`, `flex-wrap` e `gap`.
- [ ] O container utiliza largura fluida, largura máxima e centralização.
- [ ] As imagens horizontais e verticais foram testadas.
- [ ] O projeto foi testado em diferentes larguras de navegador.
- [ ] As alterações foram registradas com commit e enviadas ao GitHub.

## Próxima evolução

Na Aula 4, a página poderá receber regras específicas para diferentes larguras
de tela utilizando media queries. Até este momento, a adaptação ocorre
principalmente por meio do Flexbox, do `flex-wrap`, das medidas relativas e dos
containers fluidos.
