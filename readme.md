# Portal de Notícias

Projeto didático desenvolvido na disciplina de **Desenvolvimento Web I**, do curso de Redes de Computadores do **IFC — Campus Araquari**.

O projeto começou com uma página de perfil pessoal e está evoluindo, aula após aula, para um portal com conteúdos sobre **programação**, **hobbies** e **informações pessoais**. Cada etapa permite aplicar novos conceitos de HTML, CSS, Git e publicação na Web.

## Acesso ao projeto

- Repositório: [github.com/cristofersousa/portal-noticias](https://github.com/cristofersousa/portal-noticias)
- Página publicada: após ativar o GitHub Pages, o endereço será disponibilizado nesta seção.

## Evolução do projeto

| Aula | Conteúdos trabalhados | Resultado no projeto |
| --- | --- | --- |
| Aula 1 | Estrutura básica do HTML, introdução ao CSS, Git e GitHub Pages | Criação da página inicial de perfil pessoal |
| Aula 2 | HTML semântico, navegação, links internos, imagens, legendas, datas e organização do CSS | Transformação da página isolada em um Portal de Notícias |
| Aula 3 | Flexbox, elementos em bloco e inline, `div`, `span`, semântica, medidas e imagens adaptáveis | Construção da página de Hobbies com cartões flexíveis |
| Próxima etapa | Reutilização do Flexbox, organização de layout e responsividade | Reformulação da página Sobre Mim inspirada em um perfil profissional |

## Objetivos de aprendizagem

Até esta etapa, o projeto permite praticar:

- Estrutura básica de um documento HTML;
- Organização semântica do conteúdo;
- Diferença entre elementos em bloco e elementos inline;
- Uso de `div` e `span` quando não existe um elemento semântico mais adequado;
- Criação de um menu de navegação;
- Links entre páginas do mesmo projeto;
- Estrutura de notícias e publicações;
- Uso de imagens com descrição e legenda;
- Representação de datas e horários com o elemento `time`;
- Separação entre estilos globais e estilos específicos;
- Influência do CSS Reset sobre os elementos HTML;
- Criação de layouts com Flexbox;
- Uso de medidas absolutas e relativas;
- Construção de containers centralizados e adaptáveis;
- Tratamento de imagens com diferentes proporções;
- Versionamento e publicação com Git, GitHub e GitHub Pages.

## Tecnologias utilizadas

- HTML5;
- CSS3;
- Git;
- GitHub;
- GitHub Pages;
- Visual Studio Code.

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
│   ├── styles.css
│   ├── hobbies.css
│   └── perfil.css
├── docs/
│   ├── index.md
│   └── hobbies.md
└── img/
    ├── estrada.avif
    ├── banco-de-dados.avif
    ├── seguranca-de-redes.jpeg
    └── hobbies/
        ├── musica.jpg
        ├── cinema.jpg
        └── hoquei.jpg
```

> A estrutura representa a organização proposta para o projeto. Os nomes das imagens podem variar conforme os arquivos escolhidos pela turma.

## Páginas do portal

### Programação — `index.html`

A página principal representa a área de **Programação** e apresenta:

- Cabeçalho e descrição do portal;
- Menu de navegação;
- Três matérias organizadas semanticamente;
- Categorias apresentadas como badges;
- Imagens com legenda;
- Datas e horários das publicações;
- Rodapé institucional.

As matérias utilizadas como exemplo abordam:

1. Desenvolvimento Web I;
2. Banco de Dados;
3. Segurança de Redes.

### Hobbies — `hobbies.html`

A página de Hobbies apresenta interesses pessoais por meio de cartões. Cada cartão contém:

- Imagem relacionada ao hobby;
- Legenda da imagem;
- Título;
- Descrição;
- Data da publicação.

Os cartões são organizados com Flexbox e podem mudar de linha de acordo com o espaço disponível.

### Sobre Mim — `perfil.html`

A página Sobre Mim reaproveita o perfil criado na primeira aula. Na próxima etapa, ela será reorganizada com Flexbox e passará a apresentar uma estrutura inspirada em perfis profissionais, com capa, fotografia, apresentação, informações pessoais, competências e projetos.

## Menu de navegação

O menu conecta as três páginas por meio de links internos:

```html
<nav aria-label="Navegação principal">
  <ul>
    <li><a href="index.html">Programação</a></li>
    <li><a href="hobbies.html">Hobbies</a></li>
    <li><a href="perfil.html">Sobre Mim</a></li>
  </ul>
</nav>
```

Os links são internos porque apontam para arquivos do mesmo site.

## Estrutura semântica

O projeto utiliza elementos semânticos do HTML5 para indicar a função de cada parte do documento.

| Elemento | Função no projeto |
| --- | --- |
| `<header>` | Representa o cabeçalho da página ou a introdução de uma publicação |
| `<nav>` | Reúne os links principais de navegação |
| `<main>` | Identifica o conteúdo principal da página |
| `<section>` | Agrupa conteúdos relacionados por tema |
| `<article>` | Representa um conteúdo independente, como notícia ou cartão de hobby |
| `<figure>` | Agrupa uma imagem ao seu conteúdo relacionado |
| `<figcaption>` | Apresenta a legenda visível de uma imagem |
| `<time>` | Representa uma data ou um horário |
| `<footer>` | Contém informações finais de uma publicação ou da página |
| `<div>` | Cria um agrupamento genérico para organização ou layout |
| `<span>` | Marca um pequeno trecho inline para estilo ou identificação |

O elemento `header` pode aparecer mais de uma vez na mesma página, pois também pode representar a introdução de um `article`. Da mesma forma, uma publicação pode possuir seu próprio `footer`.

## Estrutura de uma matéria

Cada matéria da página principal é organizada como um conteúdo independente:

```html
<section>
  <article>
    <header>
      <p class="categoria">Desenvolvimento Web I</p>
      <h3>Título da matéria</h3>
      <p class="subtitulo">Subtítulo da matéria.</p>
    </header>

    <figure class="imagem-publicacao">
      <img src="./img/estrada.avif" alt="Estrada entre montanhas">
      <figcaption>
        A aprendizagem em Desenvolvimento Web acontece por etapas!
      </figcaption>
    </figure>

    <p>Texto da publicação.</p>

    <footer>
      <p>
        Publicado em
        <time datetime="2026-08-21T21:06">
          21 de agosto de 2026, às 21h06
        </time>
      </p>
    </footer>
  </article>
</section>
```

## Estrutura de um cartão de hobby

Cada hobby também é um conteúdo independente e, por isso, utiliza `article`:

```html
<article class="cartao-hobby">
  <figure>
    <div class="area-imagem">
      <img src="./img/hobbies/musica.jpg" alt="Pessoa ouvindo música">
    </div>
    <figcaption>Música para relaxar e buscar inspiração</figcaption>
  </figure>

  <div class="conteudo-cartao">
    <h3>Música</h3>
    <p>Gosto de escutar música durante os momentos de descanso.</p>
    <footer>
      <time datetime="2026-08-28">28 de agosto de 2026</time>
    </footer>
  </div>
</article>
```

## Elementos em bloco e inline

Os elementos em bloco normalmente começam em uma nova linha e ocupam a largura disponível. Exemplos utilizados no projeto:

```text
header, nav, main, section, article, figure, div, p e footer
```

Os elementos inline permanecem no fluxo do texto. Exemplos:

```text
a, span, strong, em e time
```

O comportamento visual pode ser alterado pelo CSS com a propriedade `display`.

## Flexbox na página de Hobbies

O Flexbox organiza os cartões dentro de um container:

```css
.lista-hobbies {
  display: flex;
  flex-wrap: wrap;
  gap: 1.5rem;
}

.cartao-hobby {
  flex: 1 1 280px;
}
```

| Propriedade | Efeito no layout |
| --- | --- |
| `display: flex` | Transforma o elemento em um container flexível |
| `flex-wrap: wrap` | Permite que os cartões mudem de linha |
| `gap` | Define o espaço entre os cartões |
| `flex: 1 1 280px` | Permite que o cartão cresça, diminua e use `280px` como base |
| `justify-content` | Distribui os itens no eixo principal |
| `align-items` | Alinha os itens no eixo transversal |

## Medidas e adaptação do layout

O projeto combina medidas fixas e relativas:

| Unidade | Referência | Uso comum no projeto |
| --- | --- | --- |
| `px` | Unidade fixa em pixels CSS | Bordas e limites pontuais |
| `rem` | Tamanho da fonte do elemento raiz | Espaçamentos e tamanhos de texto |
| `em` | Tamanho da fonte do contexto atual | Legendas e ajustes locais |
| `%` | Dimensão do elemento pai | Larguras adaptáveis |
| `vw` | Largura da janela | Elementos relacionados ao viewport |
| `vh` | Altura da janela | Seções relacionadas à altura da tela |

Um container fluido, limitado e centralizado pode ser criado assim:

```css
.container {
  width: 90%;
  max-width: 1200px;
  margin: 0 auto;
}
```

- `width: 90%` permite que o conteúdo acompanhe o espaço disponível;
- `max-width` evita que o conteúdo cresça excessivamente;
- `margin: 0 auto` centraliza horizontalmente um elemento com largura definida.

## Imagens com diferentes proporções

Para exibir a imagem inteira e preservar sua proporção:

```css
img {
  display: block;
  width: 100%;
  height: auto;
}
```

Para manter todos os cartões com a mesma altura visual, uma área de imagem pode ser delimitada:

```css
.area-imagem {
  height: 220px;
  background-color: #e9edf3;
}

.area-imagem img {
  width: 100%;
  height: 100%;
  object-fit: contain;
}
```

- `object-fit: cover` preenche toda a área, mas pode recortar a imagem;
- `object-fit: contain` mostra a imagem inteira, mas pode deixar espaços livres;
- `height: auto` preserva a proporção natural, porém gera cartões com alturas diferentes.

A escolha depende do objetivo visual da página.

## Imagem, descrição e legenda

Os elementos `figure` e `figcaption` são usados quando a imagem faz parte do conteúdo:

```html
<figure class="imagem-publicacao">
  <img src="./img/estrada.avif" alt="Estrada entre montanhas">
  <figcaption>
    A aprendizagem em Desenvolvimento Web acontece por etapas!
  </figcaption>
</figure>
```

- `figure` agrupa a imagem e sua legenda;
- `figcaption` apresenta uma legenda visível;
- `alt` descreve a imagem para acessibilidade e também aparece quando o arquivo não é carregado.

O `figcaption` não substitui o atributo `alt`.

## Datas e horários

As datas das publicações são marcadas com o elemento `time`:

```html
<time datetime="2026-08-21T21:06">
  21 de agosto de 2026, às 21h06
</time>
```

O atributo `datetime` fornece uma representação que pode ser interpretada por navegadores, mecanismos de busca e outras ferramentas.

## Organização dos estilos

As folhas de estilo devem ser carregadas do arquivo mais geral para o mais específico:

```html
<link rel="stylesheet" href="./css/reset.css">
<link rel="stylesheet" href="./css/global.css">
<link rel="stylesheet" href="./css/hobbies.css">
```

| Arquivo | Responsabilidade |
| --- | --- |
| `reset.css` | Reduz diferenças entre os estilos padrão dos navegadores |
| `global.css` | Define tipografia, cabeçalho, menu, elementos compartilhados e rodapé principal |
| `styles.css` | Contém os estilos específicos da página de Programação |
| `hobbies.css` | Contém a galeria, os cartões e as imagens da página de Hobbies |
| `perfil.css` | Conterá os estilos específicos da página Sobre Mim |

## CSS Reset e formatação de texto

O CSS Reset de Eric Meyer aplica `font: inherit` em diversos elementos. Por isso, elementos como `strong` e `em` podem perder a formatação visual padrão.

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

Quando o texto mencionar um elemento HTML, também pode ser utilizado o elemento `code`:

```html
<code>&lt;header&gt;</code>
```

## Documentação complementar

A pasta `docs` apresenta explicações mais detalhadas sobre a estrutura e o CSS de cada página:

- [`docs/index.md`](./docs/index.md) — documentação da página de Programação;
- [`docs/hobbies.md`](./docs/hobbies.md) — documentação da página de Hobbies.

## Como executar

1. Faça o download ou clone o repositório:

   ```bash
   git clone https://github.com/cristofersousa/portal-noticias.git
   ```

2. Abra a pasta do projeto no Visual Studio Code;
3. Confirme se os arquivos estão organizados conforme a estrutura apresentada;
4. Abra o arquivo `index.html` no navegador;
5. Utilize o menu para navegar entre as páginas.

Também é possível utilizar a extensão **Live Server** no Visual Studio Code.

## Checklist atual

- [x] Cabeçalho principal;
- [x] Menu com links internos;
- [x] Conteúdo organizado com `main`;
- [x] Matérias estruturadas com `section` e `article`;
- [x] Cabeçalho e rodapé em cada matéria;
- [x] Imagens com `figure`, `figcaption` e `alt`;
- [x] Datas utilizando `time`;
- [x] Separação entre reset, estilos globais e estilos específicos;
- [x] Categorias apresentadas como badges;
- [x] Página de Hobbies com cartões;
- [x] Galeria de Hobbies organizada com Flexbox;
- [x] Tratamento de imagens horizontais e verticais;
- [x] Documentação das páginas Programação e Hobbies;
- [ ] Reformulação da página Sobre Mim com Flexbox;
- [ ] Revisão da adaptação para telas menores;
- [ ] Verificação final dos textos alternativos das imagens;
- [ ] Atualização da publicação no GitHub Pages.

## Próximas etapas

- Reorganizar a página Sobre Mim com Flexbox;
- Criar uma apresentação inspirada em perfis profissionais;
- Adaptar menu, perfil e cartões para telas menores;
- Introduzir media queries;
- Testar o portal pelo DevTools;
- Revisar acessibilidade, ortografia e caminhos dos arquivos;
- Publicar a nova versão no GitHub Pages.

---

**Disciplina:** Desenvolvimento Web I  
**Curso:** Redes de Computadores  
**Instituição:** IFC — Campus Araquari  
**Projeto:** Portal de Notícias
