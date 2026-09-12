## Aula 2 — Estrutura semântica e navegação entre páginas

Nesta aula, avançamos da página de perfil desenvolvida anteriormente para a construção de um pequeno **Portal de Notícias**.

O objetivo foi compreender como organizar documentos HTML, criar diferentes páginas conectadas por links internos e utilizar elementos semânticos para representar adequadamente cada parte do conteúdo.

### 1. Estrutura semântica do HTML

Estudamos os seguintes elementos:

* `<header>` — representa o cabeçalho de uma página, seção ou publicação;
* `<nav>` — identifica uma área com links de navegação;
* `<main>` — representa o conteúdo principal da página;
* `<section>` — agrupa conteúdos relacionados por assunto;
* `<article>` — representa uma matéria ou publicação independente;
* `<figure>` — agrupa uma imagem ou outro conteúdo ilustrativo;
* `<figcaption>` — apresenta a legenda de uma imagem;
* `<time>` — representa uma data ou um horário;
* `<footer>` — identifica o rodapé de uma página, seção ou publicação.

A utilização desses elementos torna o documento mais organizado, compreensível e acessível, além de facilitar a manutenção do código.

### 2. Navegação entre páginas

Também trabalhamos na criação de páginas conectadas por meio de links internos.

O menu de navegação foi utilizado para permitir que o usuário transitasse entre as diferentes áreas do portal, como:

* Programação;
* Hobbies;
* Sobre Mim.

Essa organização permitiu transformar a página inicial em um projeto composto por diferentes documentos HTML relacionados entre si.

### 3. Organização dos arquivos CSS

Abordamos a separação dos estilos em diferentes arquivos:

* `reset.css` — remove ou normaliza estilos aplicados automaticamente pelo navegador;
* `global.css` — reúne os estilos compartilhados por todas as páginas;
* CSS específico da página — contém os estilos utilizados apenas em uma determinada página ou seção.

Também discutimos a importância da ordem em que esses arquivos são carregados no HTML, pois as regras declaradas posteriormente podem complementar ou substituir estilos anteriores.

Exemplo:

```html
<link rel="stylesheet" href="./css/reset.css" />
<link rel="stylesheet" href="./css/global.css" />
<link rel="stylesheet" href="./css/programacao.css" />
```

### 4. Materiais disponibilizados

Para consulta e revisão, foram disponibilizados:

* PDF com os slides apresentados durante a aula;
* documentação da MDN sobre HTML;
* especificação oficial do padrão HTML mantida pela WHATWG;
* repositório com o código desenvolvido em sala.

O repositório deve ser utilizado como material de apoio e referência para revisar a estrutura construída durante a aula.

Evitem apenas copiar o código. Procurem compreender a função de cada elemento, realizar testes, modificar os exemplos e personalizar os textos, as imagens e os demais conteúdos do portal.

## Continuidade do projeto

O código continuará sendo aprimorado nas próximas aulas, especialmente com:

* desenvolvimento das páginas de Hobbies e Sobre Mim;
* criação de novas seções e conteúdos;
* organização visual utilizando CSS;
* introdução ao Flexbox;
* adaptação do portal para diferentes tamanhos de tela.

Bom final de semana!
