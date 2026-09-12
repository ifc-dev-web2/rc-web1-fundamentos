## Aula 1 — Introdução ao Desenvolvimento Web

Nesta primeira aula, realizamos a apresentação do professor, da disciplina e da turma.

Também conversamos sobre a carga horária, o cronograma das aulas, as atividades, os critérios de avaliação, a composição das notas e os principais combinados para o semestre.

### 1. Introdução ao Desenvolvimento Web

Inicialmente, estudamos como uma requisição percorre a rede até que o navegador receba os arquivos necessários e apresente uma página ao usuário.

A partir desse fluxo, conhecemos o papel das principais tecnologias utilizadas no desenvolvimento de páginas Web:

* **HTML** — responsável pela estrutura e pelo conteúdo da página;
* **CSS** — responsável pela aparência, organização e apresentação visual;
* **JavaScript** — responsável pelos comportamentos e pela interatividade.

Também discutimos a relação entre cliente, servidor e navegador durante o acesso a uma aplicação Web.

### 2. Construção de uma página de perfil

Na atividade prática, criamos uma página de perfil utilizando HTML e CSS.

Durante o desenvolvimento, trabalhamos:

* estrutura básica de um documento HTML;
* utilização de títulos, parágrafos, imagens, listas e links;
* aplicação de estilos utilizando CSS;
* organização do conteúdo com classes e contêineres;
* utilização de margens e espaçamentos;
* personalização de cores e fontes;
* aplicação de bordas e sombras;
* organização das pastas do projeto;
* utilização de caminhos relativos para acessar arquivos e imagens.

Também estudamos a criação de links que abrem em uma nova aba:

```html
<a
  href="https://exemplo.com"
  target="_blank"
  rel="noopener noreferrer"
>
  Acessar página
</a>
```

O atributo `rel="noopener noreferrer"` adiciona uma camada de segurança aos links abertos com `target="_blank`, ajudando a proteger a página contra ataques conhecidos como **tabnabbing**.

### 3. Publicação do projeto

Ao final da aula, criamos um repositório no GitHub e enviamos os arquivos do projeto utilizando o fluxo básico do Git:

```bash
git add .
git commit -m "Cria página inicial do projeto"
git push
```

Depois disso, configuramos o **GitHub Pages**, tornando a página acessível publicamente pela internet.

## Resultado da aula

A aula apresentou o ciclo inicial completo de desenvolvimento e publicação de uma aplicação Web:

1. planejamento do conteúdo;
2. criação da estrutura com HTML;
3. estilização da página com CSS;
4. organização dos arquivos do projeto;
5. versionamento do código com Git;
6. armazenamento do repositório no GitHub;
7. publicação da página com GitHub Pages.

Esse projeto servirá como base para as próximas aulas, nas quais ampliaremos a página de perfil e construiremos novas páginas, utilizando elementos semânticos, navegação, Flexbox e responsividade.
