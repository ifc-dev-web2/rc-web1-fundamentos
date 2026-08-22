# Portal de Notícias

Projeto desenvolvido na disciplina **Desenvolvimento Web I**, do curso de
Redes de Computadores do **IFC — Campus Araquari**.

Na primeira aula, desenvolvemos uma página de perfil.
Na aula de 2 começamos a transformar essa página isolada em um pequeno portal com
conteúdos sobre: `programação, hobbies e informações pessoais`.

## Objetivos da aula

Nesta etapa do projeto, trabalhamos:

- Estrutura básica de um documento HTML;
- Organização semântica do conteúdo;
- Criação de um menu de navegação;
- Links entre páginas do mesmo projeto;
- Estrutura de uma matéria ou publicação;
- Imagens com descrição e legenda;
- Datas e horários no HTML;
- Separação dos arquivos CSS;
- Diferença entre estilos globais e específicos;
- Influência do CSS Reset sobre os elementos HTML.

## Tecnologias utilizadas

- HTML5;
- CSS3;
- Git;
- GitHub;
- GitHub Pages.

## Estrutura do projeto

```text
portal-noticias/
├── index.html
├── hobbies.html
├── perfil.html
├── README.md
├── css/
│   ├── reset.css
│   ├── global.css
│   └── styles.css
└── img/
    └── estrada.avif
```

> As páginas `hobbies.html` e `perfil.html` são acessadas pelo menu e podem ser
> desenvolvidas ou aprimoradas nas próximas etapas do projeto.

## Página principal

O arquivo `index.html` representa a área de **Programação** do portal. Ele
possui:

- Cabeçalho principal;
- Nome e descrição do portal;
- Menu de navegação;
- Conteúdo principal;
- Três matérias;
- Imagem com legenda;
- Data e horário das publicações;
- Rodapé institucional.

As matérias apresentadas abordam:

1. Desenvolvimento Web I;
2. Banco de Dados;
3. Segurança de Redes.

## Menu de navegação

O menu conecta as páginas do projeto por meio de links internos:

```html
<nav>
  <ul>
    <li><a href="index.html">Programação</a></li>
    <li><a href="hobbies.html">Hobbies</a></li>
    <li><a href="perfil.html">Sobre Mim</a></li>
  </ul>
</nav>
```

Esses links são internos porque apontam para arquivos do mesmo site.

## Estrutura semântica

O projeto utiliza elementos semânticos do HTML5 para indicar a função de cada
parte do documento.

| Elemento       | Função no projeto                                   |
| -------------- | --------------------------------------------------- |
| `<header>`     | Cabeçalho do portal ou de uma matéria.              |
| `<nav>`        | Área que reúne os links do menu.                    |
| `<main>`       | Conteúdo principal da página.                       |
| `<section>`    | Agrupamento de uma matéria do portal.               |
| `<article>`    | Conteúdo independente de uma notícia ou publicação. |
| `<figure>`     | Agrupamento da imagem relacionada à matéria.        |
| `<figcaption>` | Legenda visível da imagem.                          |
| `<time>`       | Data e horário da publicação.                       |
| `<footer>`     | Rodapé da matéria ou da página.                     |

## Estrutura de uma matéria

Cada matéria foi organizada como um conteúdo independente:

```html
<section>
  <article>
    <header>
      <p class="categoria">Desenvolvimento Web I</p>
      <h3>Título da matéria</h3>
      <p class="subtitulo">Subtítulo da matéria.</p>
    </header>

    <figure class="imagem-publicacao">
      <img src="./img/estrada.avif" alt="Estrada entre montanhas" />

      <figcaption>
        A aprendizagem em Desenvolvimento Web acontece por etapas!
      </figcaption>
    </figure>

    <p>Texto da publicação.</p>

    <footer>
      <time datetime="2026-08-21T21:06"> 21 de agosto de 2026, às 21h06 </time>
    </footer>
  </article>
</section>
```

O `<header>` aparece mais de uma vez porque ele também pode representar a
introdução de uma seção ou de um artigo, e não somente o topo da página.

Da mesma forma, cada matéria pode possuir seu próprio `<footer>`, contendo
informações como autoria, data e horário.

## Imagem, descrição e legenda

A primeira matéria utiliza os elementos `figure` e `figcaption`:

```html
<figure class="imagem-publicacao">
  <img src="./img/estrada.avif" alt="Estrada entre montanhas" />

  <figcaption>
    A aprendizagem em Desenvolvimento Web acontece por etapas!
  </figcaption>
</figure>
```

Cada parte possui uma finalidade:

- `figure` agrupa a imagem e sua legenda;
- `figcaption` apresenta uma legenda visível;
- `alt` descreve a imagem para acessibilidade e para situações em que ela não
  seja carregada.

O `figcaption` não substitui o atributo `alt`.

## Datas e horários

As datas foram marcadas com o elemento `time`:

```html
<time datetime="2026-08-21T21:06"> 21 de agosto de 2026, às 21h06 </time>
```

O atributo `datetime` fornece uma representação da data e do horário que pode
ser interpretada por navegadores, mecanismos de busca e outras ferramentas.

## Organização dos estilos

Os estilos são carregados nesta ordem:

```html
<link rel="stylesheet" href="./css/reset.css" />
<link rel="stylesheet" href="./css/global.css" />
<link rel="stylesheet" href="./css/styles.css" />
```

### `reset.css`

Utiliza o CSS Reset de Eric Meyer para reduzir diferenças entre os estilos
padrão dos navegadores.

### `global.css`

Armazena os estilos compartilhados pelo portal, como tipografia, cabeçalho,
menu, área principal e rodapé.

### `styles.css`

Armazena os estilos específicos da página de Programação, como categorias,
títulos, subtítulos, matérias, imagens, legendas e datas.

## CSS Reset e o elemento `strong`

O CSS Reset de Eric Meyer utiliza `font: inherit` em diversos elementos. Por
isso, o navegador pode deixar de apresentar o `<strong>` em negrito.

O comportamento pode ser restaurado no `global.css`:

```css
strong,
b {
  font-weight: 700;
}

em,
i {
  font-style: italic;
}
```

Quando nomes de elementos HTML forem apresentados no texto, também podemos
utilizar `<code>`:

```html
<code>&lt;header&gt;</code>
```

## Como executar

1. Faça o download ou clone o repositório;
2. Abra a pasta do projeto no Visual Studio Code;
3. Confirme se os arquivos estão organizados conforme a estrutura apresentada;
4. Abra o arquivo `index.html` no navegador;
5. Utilize o menu para navegar entre as páginas.

Também é possível utilizar a extensão **Live Server** no Visual Studio Code.

## Próximas etapas

- Finalizar a página de Hobbies;
- Reaproveitar a página de perfil criada na primeira aula;
- Manter o mesmo cabeçalho, menu e rodapé nas páginas;
- Adicionar imagens às demais matérias;
- Aprimorar a organização visual com CSS;
- Publicar a nova versão no GitHub Pages.

## Checklist

- [x] Cabeçalho principal;
- [x] Menu com links internos;
- [x] Conteúdo organizado com `main`;
- [x] Matérias estruturadas com `section` e `article`;
- [x] Cabeçalho dentro de cada matéria;
- [x] Imagem com `figure` e `figcaption`;
- [x] Datas utilizando `time`;
- [x] Rodapé em cada matéria;
- [x] Rodapé principal do portal;
- [x] Separação entre reset, estilos globais e específicos;
- [ ] Finalização da página de Hobbies;
- [ ] Revisão da página Sobre Mim;
- [ ] Publicação final no GitHub Pages.

---

**Disciplina:** Desenvolvimento Web I  
**Instituição:** IFC — Campus Araquari  
**Projeto:** Portal de Notícias  
**Aula:** Semântica, navegação e organização de conteúdo
