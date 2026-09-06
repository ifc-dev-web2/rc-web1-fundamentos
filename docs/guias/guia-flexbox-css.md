# Guia de Flexbox no CSS

Este guia apresenta os principais conceitos do CSS Flexbox e mostra como utilizá-lo para organizar elementos, criar espaçamentos, distribuir áreas e adaptar layouts para diferentes tamanhos de tela.

## 1. O que é Flexbox?

Flexbox é um modelo de layout do CSS criado para organizar elementos em uma dimensão por vez:

- em uma linha; ou
- em uma coluna.

Ele é especialmente útil para:

- alinhar elementos verticalmente ou horizontalmente;
- distribuir espaço entre elementos;
- criar menus de navegação;
- organizar imagens e textos lado a lado;
- criar grupos de cartões;
- alterar o layout em telas menores.

## 2. Elemento pai e elementos filhos

Para utilizar Flexbox, primeiro é necessário identificar o elemento pai e seus filhos diretos.

```html
<div class="container">
  <div class="item">Item 1</div>
  <div class="item">Item 2</div>
  <div class="item">Item 3</div>
</div>
```

Nesse exemplo:

- `.container` é o elemento pai;
- cada `.item` é um filho direto;
- os itens serão controlados pelo Flexbox aplicado ao pai.

Para ativar o Flexbox:

```css
.container {
  display: flex;
}
```

> Propriedades como `flex-direction`, `justify-content`, `align-items` e `gap` dependem de `display: flex` ou `display: inline-flex` no elemento pai.

## 3. O que muda com `display: flex`?

Antes do Flexbox, elementos de bloco normalmente aparecem um abaixo do outro:

```text
Item 1
Item 2
Item 3
```

Depois de aplicar `display: flex`, os filhos diretos aparecem em linha por padrão:

```text
Item 1  Item 2  Item 3
```

Isso ocorre porque o valor inicial de `flex-direction` é `row`.

## 4. Eixo principal e eixo transversal

O Flexbox trabalha com dois eixos:

- **eixo principal:** definido por `flex-direction`;
- **eixo transversal:** perpendicular ao eixo principal.

Quando usamos:

```css
flex-direction: row;
```

o eixo principal é horizontal e o transversal é vertical.

Quando usamos:

```css
flex-direction: column;
```

o eixo principal é vertical e o transversal é horizontal.

Essa distinção é essencial porque:

- `justify-content` atua no eixo principal;
- `align-items` atua no eixo transversal.

## 5. Direção com `flex-direction`

### Elementos em linha

```css
.container {
  display: flex;
  flex-direction: row;
}
```

Resultado:

```text
Item 1  Item 2  Item 3
```

### Elementos em coluna

```css
.container {
  display: flex;
  flex-direction: column;
}
```

Resultado:

```text
Item 1
Item 2
Item 3
```

Também existem `row-reverse` e `column-reverse`, mas inverter visualmente os elementos pode criar uma ordem diferente da leitura do HTML. Prefira organizar o HTML na ordem correta sempre que possível.

## 6. Alinhamento com `justify-content`

`justify-content` distribui os itens ao longo do eixo principal.

```css
.container {
  display: flex;
  justify-content: center;
}
```

Valores frequentes:

| Valor | Comportamento |
| --- | --- |
| `flex-start` | Posiciona os itens no início. |
| `center` | Centraliza os itens. |
| `flex-end` | Posiciona os itens no final. |
| `space-between` | Coloca o espaço disponível entre os itens. |
| `space-around` | Distribui espaço ao redor de cada item. |
| `space-evenly` | Distribui espaços iguais entre itens e extremidades. |

Exemplo de navegação:

```css
.menu {
  display: flex;
  justify-content: center;
  gap: 2rem;
}
```

## 7. Alinhamento com `align-items`

`align-items` posiciona os itens no eixo transversal.

```css
.container {
  display: flex;
  align-items: center;
}
```

Valores frequentes:

| Valor | Comportamento |
| --- | --- |
| `stretch` | Estica os itens no eixo transversal quando possível. É o valor inicial. |
| `flex-start` | Alinha os itens ao início. |
| `center` | Centraliza os itens. |
| `flex-end` | Alinha os itens ao final. |
| `baseline` | Alinha os itens pela linha de base do texto. |

Exemplo com imagem e texto:

```css
.hero-content {
  display: flex;
  align-items: center;
  gap: 2rem;
}
```

## 8. Centralização completa

Para centralizar um item horizontal e verticalmente:

```css
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
}
```

Nesse caso:

- `justify-content: center` centraliza no eixo principal;
- `align-items: center` centraliza no eixo transversal.

Se `flex-direction` mudar para `column`, os eixos também mudarão.

## 9. Espaçamento com `gap`

`gap` cria espaço entre os filhos de um container Flexbox:

```css
.container {
  display: flex;
  gap: 1.5rem;
}
```

O `gap` não cria espaço nas bordas externas do container. Para isso, utilize `padding` no pai.

```css
.container {
  display: flex;
  gap: 1.5rem;
  padding: 2rem;
}
```

É possível controlar linhas e colunas separadamente:

```css
.container {
  display: flex;
  gap: 1rem 2rem;
}
```

O primeiro valor representa o espaço entre linhas e o segundo, entre colunas.

> Evite somar `gap` no pai e margens laterais nos filhos sem necessidade, pois o espaçamento final pode ficar maior que o planejado.

## 10. Quebra de linha com `flex-wrap`

Por padrão, o Flexbox tenta manter todos os itens na mesma linha:

```css
flex-wrap: nowrap;
```

Para permitir que os itens passem para a linha seguinte:

```css
.lista-cards {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}
```

Esse recurso é útil para:

- cartões;
- etiquetas de competências;
- galerias;
- botões;
- itens de navegação.

Exemplo com competências:

```css
.lista-competencias {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
  margin: 0;
  padding: 0;
  list-style: none;
}
```

## 11. `align-content` não é `align-items`

`align-items` alinha os itens dentro de cada linha.

`align-content` distribui o conjunto de linhas no eixo transversal e só produz efeito quando:

- existe mais de uma linha;
- `flex-wrap: wrap` está ativo;
- há espaço disponível no eixo transversal.

```css
.container {
  display: flex;
  flex-wrap: wrap;
  align-content: center;
  min-height: 400px;
}
```

Para a maioria dos layouts iniciais, `align-items` será usado com mais frequência.

## 12. Propriedades aplicadas aos itens

Algumas propriedades são definidas no container pai:

```css
.container {
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
}
```

Outras são aplicadas diretamente aos filhos:

```css
.item {
  flex: 1;
  align-self: center;
  order: 1;
}
```

Resumo:

| No elemento pai | Nos elementos filhos |
| --- | --- |
| `display` | `flex` |
| `flex-direction` | `flex-grow` |
| `justify-content` | `flex-shrink` |
| `align-items` | `flex-basis` |
| `align-content` | `align-self` |
| `flex-wrap` | `order` |
| `gap` |  |

## 13. Crescimento com `flex-grow`

`flex-grow` determina quanto um item pode crescer para ocupar o espaço disponível.

```css
.item {
  flex-grow: 1;
}
```

Se todos os itens tiverem `flex-grow: 1`, eles dividirão o espaço igualmente.

```css
.principal {
  flex-grow: 2;
}

.lateral {
  flex-grow: 1;
}
```

Nesse exemplo, a área principal recebe duas partes e a lateral recebe uma parte do espaço livre. Isso não significa obrigatoriamente `66,66%` e `33,33%`, porque o tamanho inicial do conteúdo e o `flex-basis` também participam do cálculo.

## 14. Redução com `flex-shrink`

`flex-shrink` determina se um item pode diminuir quando falta espaço:

```css
.item {
  flex-shrink: 1;
}
```

O valor inicial é `1`, portanto os itens normalmente podem encolher.

Para impedir que uma foto de perfil diminua:

```css
.hero-image {
  flex-shrink: 0;
}
```

Use essa regra com cuidado: se vários elementos forem impedidos de encolher, eles poderão ultrapassar o container.

## 15. Tamanho inicial com `flex-basis`

`flex-basis` define o tamanho inicial do item no eixo principal antes da distribuição do espaço:

```css
.card {
  flex-basis: 250px;
}
```

Com quebra de linha, podemos criar cartões flexíveis:

```css
.lista-cards {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

.card {
  flex-grow: 1;
  flex-shrink: 1;
  flex-basis: 250px;
}
```

## 16. Atalho `flex`

A propriedade `flex` representa, nesta ordem:

```text
flex: flex-grow flex-shrink flex-basis;
```

Exemplo:

```css
.card {
  flex: 1 1 250px;
}
```

Isso equivale a:

```css
.card {
  flex-grow: 1;
  flex-shrink: 1;
  flex-basis: 250px;
}
```

Atalhos comuns:

| Declaração | Significado prático |
| --- | --- |
| `flex: 1` | Permite crescer e encolher, partindo de uma base de `0`. |
| `flex: auto` | Permite crescer e encolher, considerando o tamanho inicial do conteúdo. |
| `flex: none` | Impede crescimento e redução. |
| `flex: 1 1 250px` | Cria um item flexível com base de `250px`. |

## 17. Proporção entre colunas

Para criar uma área principal maior e uma barra lateral menor:

```html
<div class="conteudo">
  <main class="coluna-principal">Conteúdo principal</main>
  <aside class="coluna-lateral">Conteúdo lateral</aside>
</div>
```

```css
.conteudo {
  display: flex;
  align-items: stretch;
  gap: 1.5rem;
}

.coluna-principal {
  flex: 2;
}

.coluna-lateral {
  flex: 1;
}
```

Como alternativa mais explícita, podemos definir bases percentuais:

```css
.coluna-principal {
  flex: 1 1 65%;
}

.coluna-lateral {
  flex: 1 1 35%;
}
```

O `gap` também ocupa espaço, por isso não é recomendável combinar duas larguras rígidas que totalizem `100%` com um espaço adicional entre elas.

## 18. Alinhamento individual com `align-self`

`align-self` altera o alinhamento de apenas um filho:

```css
.item-destacado {
  align-self: flex-end;
}
```

Ele sobrescreve, para aquele item, o alinhamento definido por `align-items` no pai.

## 19. Espaço automático com `margin: auto`

Margens automáticas absorvem o espaço disponível dentro de um layout flexível.

Exemplo de menu com um item empurrado para a direita:

```css
.menu {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.menu-login {
  margin-left: auto;
}
```

Esse recurso é útil quando apenas um elemento precisa ser separado do restante do grupo.

## 20. Alterando a ordem visual

A propriedade `order` altera a ordem visual dos itens:

```css
.primeiro-visualmente {
  order: -1;
}
```

Entretanto, ela não altera a ordem do HTML nem necessariamente a ordem utilizada por teclado e tecnologias assistivas.

> Prefira escrever o HTML em uma ordem lógica. Use `order` apenas quando a mudança visual não prejudicar a leitura e a navegação.

## 21. Flexbox dentro de Flexbox

Um item flexível também pode se transformar em outro container Flexbox.

```html
<section class="hero-section">
  <img class="hero-image" src="./img/perfil.jpg" alt="Foto de perfil">

  <div class="hero-about">
    <h1>Cristofer Sousa</h1>
    <h2>Estudante de Redes de Computadores</h2>
    <p>Araquari, Santa Catarina</p>
  </div>
</section>
```

```css
.hero-section {
  display: flex;
  align-items: center;
  gap: 2rem;
}

.hero-about {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}
```

Nesse exemplo:

- `.hero-section` coloca imagem e texto lado a lado;
- `.hero-about` coloca título, subtítulo e parágrafo um abaixo do outro.

O Flexbox afeta somente os filhos diretos. Por isso, cada nível do layout pode precisar de seu próprio `display: flex`.

## 22. Exemplo: navegação

### HTML

```html
<nav aria-label="Navegação principal">
  <ul class="menu">
    <li><a href="./programacao.html">Programação</a></li>
    <li><a href="./hobbies.html">Hobbies</a></li>
    <li><a href="./sobre.html">Sobre mim</a></li>
  </ul>
</nav>
```

### CSS

```css
.menu {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 1rem 2rem;
  margin: 0;
  padding: 1rem;
  list-style: none;
}
```

## 23. Exemplo: cartões responsivos

### HTML

```html
<section class="lista-cards">
  <article class="card">Hóquei</article>
  <article class="card">Música</article>
  <article class="card">Cinema</article>
</section>
```

### CSS

```css
.lista-cards {
  display: flex;
  flex-wrap: wrap;
  gap: 1.5rem;
}

.card {
  flex: 1 1 250px;
  padding: 1.5rem;
  border: 1px solid #dee2e6;
  border-radius: 1rem;
}
```

Cada cartão:

- começa com uma base de `250px`;
- pode crescer para ocupar espaço livre;
- pode diminuir quando necessário;
- passa para outra linha quando não cabe.

## 24. Responsividade com media queries

Flexbox pode alterar a direção do layout conforme o espaço disponível:

```css
.hero-content {
  display: flex;
  align-items: center;
  gap: 2rem;
}

@media (max-width: 768px) {
  .hero-content {
    flex-direction: column;
    text-align: center;
  }
}
```

Em telas maiores, imagem e texto ficam lado a lado. Em telas de até `768px`, ficam um abaixo do outro.

Um breakpoint não deve ser escolhido apenas porque corresponde a um aparelho específico. Ele deve representar o ponto em que o conteúdo deixa de caber ou de ser legível.

## 25. Conteúdo que não encolhe corretamente

Um item flexível pode parecer não respeitar o espaço disponível por causa do tamanho mínimo automático do conteúdo.

Textos longos, links e conteúdos sem espaços podem provocar transbordamento. Uma correção frequente é:

```css
.conteudo-textual {
  min-width: 0;
}
```

Para permitir a quebra de palavras ou endereços muito longos:

```css
.conteudo-textual {
  min-width: 0;
  overflow-wrap: anywhere;
}
```

Essa regra é especialmente útil em cards, colunas e componentes com textos extensos.

## 26. Flexbox ou Grid?

Flexbox é indicado principalmente para organização em uma dimensão:

- uma linha de navegação;
- uma coluna de textos;
- imagem e descrição;
- conjunto de botões;
- cartões que podem quebrar para outras linhas.

CSS Grid é indicado quando linhas e colunas precisam ser controladas ao mesmo tempo:

- galerias com posições bem definidas;
- dashboards;
- layouts bidimensionais;
- tabelas visuais complexas.

Não existe competição entre eles. Um projeto pode utilizar Grid na estrutura externa e Flexbox no conteúdo interno dos componentes.

## 27. Erros comuns

### Esquecer `display: flex`

```css
/* As outras propriedades não ativam o Flexbox sozinhas. */
.container {
  flex-direction: row;
  align-items: center;
  gap: 2rem;
}
```

Correção:

```css
.container {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 2rem;
}
```

### Aplicar as propriedades no elemento errado

`justify-content`, `align-items`, `flex-direction`, `flex-wrap` e `gap` devem ser aplicados ao pai.

`flex`, `align-self` e `order` devem ser aplicados aos filhos.

### Esperar que Flexbox afete todos os descendentes

Flexbox controla somente os filhos diretos do container.

```html
<div class="pai">
  <div class="filho">
    <p>Descendente</p>
  </div>
</div>
```

O Flexbox de `.pai` controla `.filho`, mas não controla diretamente o elemento `p`.

### Confundir os eixos

Se `flex-direction` mudar, o significado visual de `justify-content` e `align-items` também muda.

### Usar largura total junto com `gap`

Dois itens com `width: 50%` mais um `gap` podem ultrapassar o container:

```css
/* Pode provocar transbordamento. */
.coluna {
  width: 50%;
}
```

Prefira:

```css
.coluna {
  flex: 1;
}
```

### Usar `100vw` dentro de um container

`100vw` representa a largura da janela inteira. Para acompanhar a largura do elemento pai, utilize:

```css
.elemento {
  width: 100%;
}
```

### Impedir toda redução

Aplicar `flex-shrink: 0` a vários itens pode gerar rolagem horizontal. Use-o apenas quando um elemento realmente precisar conservar seu tamanho.

### Utilizar `order` para corrigir um HTML desorganizado

A ordem visual não substitui uma estrutura HTML lógica e acessível.

## 28. Como investigar um problema no navegador

Ao inspecionar um layout no DevTools:

1. selecione o elemento que deveria ser o container;
2. confirme se `display: flex` está aplicado;
3. identifique os filhos diretos destacados pelo navegador;
4. verifique o valor de `flex-direction`;
5. observe os eixos principal e transversal;
6. ative e desative `justify-content`, `align-items`, `gap` e `flex-wrap`;
7. reduza a largura da janela e observe quando o conteúdo deixa de caber;
8. procure regras sobrescritas ou riscadas no painel de estilos.

O inspetor de layout dos navegadores também pode desenhar os limites e espaçamentos do Flexbox sobre a página.

## 29. Configuração-base para o perfil

```css
.container {
  width: 90%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem 0;
}

.hero-content {
  display: flex;
  align-items: center;
  gap: 2rem;
}

.hero-image {
  flex-shrink: 0;
}

.hero-about {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  min-width: 0;
}

.hero-skills {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.profile-content {
  display: flex;
  align-items: stretch;
  gap: 1.5rem;
}

.profile-main {
  display: flex;
  flex: 2;
  flex-direction: column;
  gap: 1.5rem;
  min-width: 0;
}

.profile-sidebar {
  display: flex;
  flex: 1;
  flex-direction: column;
  gap: 1.5rem;
  min-width: 0;
}

@media (max-width: 768px) {
  .hero-content,
  .profile-content {
    flex-direction: column;
  }

  .hero-content {
    text-align: center;
  }

  .hero-skills {
    justify-content: center;
  }
}
```

## 30. Checklist de Flexbox

Antes de considerar o layout concluído, verifique:

- [ ] O `display: flex` foi aplicado ao elemento pai correto?
- [ ] Os elementos que devem ser organizados são filhos diretos?
- [ ] A direção deve ser `row` ou `column`?
- [ ] O alinhamento no eixo principal está correto?
- [ ] O alinhamento no eixo transversal está correto?
- [ ] O espaçamento pode ser feito com `gap`?
- [ ] Os itens precisam quebrar com `flex-wrap`?
- [ ] Algum item precisa crescer, diminuir ou ter uma base definida?
- [ ] O conteúdo continua legível quando a janela diminui?
- [ ] É necessário mudar a direção em uma media query?
- [ ] Existe algum texto longo que exija `min-width: 0`?
- [ ] A ordem visual continua coerente com a ordem do HTML?

## Resumo

As propriedades fundamentais do container são:

```css
.container {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: stretch;
  flex-wrap: nowrap;
  gap: 1rem;
}
```

As propriedades fundamentais dos itens são:

```css
.item {
  flex: 1 1 auto;
  align-self: auto;
  order: 0;
}
```

O raciocínio principal pode ser resumido em quatro perguntas:

1. Qual é o elemento pai?
2. Quem são seus filhos diretos?
3. Eles devem ficar em linha ou em coluna?
4. Como devem ser alinhados, espaçados e redimensionados?

Ao responder essas perguntas antes de escrever o CSS, torna-se mais fácil escolher as propriedades corretas e identificar problemas no layout.
