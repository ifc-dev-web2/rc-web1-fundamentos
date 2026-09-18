# Aula 6 — Formulários HTML

**Data:** 18 de setembro de 2026  
**Disciplina:** Desenvolvimento Web I  
**Curso:** Tecnologia em Redes de Computadores

## Apresentação

Nesta aula, estudamos como criar formulários para coletar informações em uma
página Web.

O conteúdo foi aplicado ao Portal de Notícias desenvolvido durante as aulas
anteriores. Foram criadas novas possibilidades de interação para as páginas do
projeto, incluindo busca de publicações, avaliação de notícias, comentários
sobre hobbies e uma página de contato.

O HTML foi utilizado para definir a estrutura, os campos e as validações
iniciais. O CSS foi aplicado em uma segunda etapa para organizar e estilizar os
controles do formulário.

## Objetivos da aula

Ao final da aula, espera-se que o estudante consiga:

- compreender a função de um formulário em uma página Web;
- criar formulários utilizando o elemento `<form>`;
- associar corretamente `<label>` e campos de entrada;
- escolher o tipo de `input` adequado ao dado solicitado;
- utilizar `<textarea>`, `<select>` e `<option>`;
- diferenciar `checkbox` e `radio`;
- configurar botões de envio e limpeza;
- aplicar atributos de validação nativa;
- selecionar arquivos com `input type="file"`;
- organizar formulários com Flexbox;
- criar campos adaptáveis para diferentes tamanhos de tela;
- testar o formulário utilizando o navegador e o DevTools.

## Conteúdos abordados

### Estrutura de um formulário

Estudamos o elemento `<form>` e os atributos responsáveis por configurar o
envio:

```html
<form action="#" method="post">
  <!-- controles do formulário -->
</form>
```

| Recurso | Função |
| --- | --- |
| `action` | Informa o endereço que receberá os dados. |
| `method` | Define o método utilizado no envio. |
| `GET` | Utilizado normalmente em buscas, filtros e consultas. |
| `POST` | Utilizado normalmente para enviar ou criar informações. |
| `enctype` | Define a codificação dos dados enviados. |

Nesta etapa do projeto, os formulários possuem finalidade didática. Uma página
publicada somente no GitHub Pages não possui um servidor para armazenar os
dados enviados.

### Label, id e name

Cada campo deve possuir um rótulo que informe qual dado precisa ser preenchido:

```html
<label for="email">E-mail</label>

<input
  type="email"
  id="email"
  name="email"
>
```

O atributo `for` do `<label>` precisa possuir o mesmo valor do atributo `id` do
campo.

| Recurso | Função |
| --- | --- |
| `label` | Apresenta o nome ou a instrução do campo. |
| `for` | Associa o rótulo ao `id` do controle. |
| `id` | Identifica o elemento dentro do documento. |
| `name` | Define a chave utilizada no envio dos dados. |
| `value` | Representa o valor associado ao controle. |

### Tipos de input

Foram apresentados diferentes valores para o atributo `type`:

```html
<input type="text">
<input type="email">
<input type="password">
<input type="tel">
<input type="url">
<input type="search">
<input type="number">
<input type="date">
<input type="time">
<input type="color">
<input type="checkbox">
<input type="radio">
<input type="file">
```

O tipo escolhido ajuda o navegador a compreender qual informação será
recebida. Em dispositivos móveis, ele também pode influenciar o teclado
apresentado durante o preenchimento.

### Textarea

O elemento `<textarea>` é utilizado para textos maiores e com várias linhas:

```html
<label for="mensagem">Mensagem</label>

<textarea
  id="mensagem"
  name="mensagem"
  rows="6"
  maxlength="500"
></textarea>
```

### Select e option

O elemento `<select>` permite escolher uma opção dentro de uma lista:

```html
<label for="assunto">Assunto</label>

<select id="assunto" name="assunto" required>
  <option value="">Selecione</option>
  <option value="duvida">Dúvida</option>
  <option value="projeto">Projeto</option>
</select>
```

O texto da `<option>` aparece para a pessoa. O atributo `value` representa o
valor enviado.

### Checkbox e radio

O `checkbox` permite escolhas independentes:

```html
<label>
  <input type="checkbox" name="interesses" value="html">
  HTML
</label>
```

O `radio` permite uma escolha dentro de um grupo. As opções do grupo precisam
compartilhar o mesmo `name`:

```html
<label>
  <input type="radio" name="nota" value="1" required>
  1 estrela
</label>

<label>
  <input type="radio" name="nota" value="2">
  2 estrelas
</label>
```

### Fieldset e legend

Os elementos `<fieldset>` e `<legend>` organizam controles relacionados:

```html
<fieldset>
  <legend>Qual é o seu interesse pela matéria?</legend>

  <!-- opções de avaliação -->
</fieldset>
```

### Botões

Foram apresentados três comportamentos principais:

```html
<button type="submit">Enviar</button>
<button type="reset">Limpar</button>
<button type="button">Abrir ajuda</button>
```

| Tipo | Comportamento |
| --- | --- |
| `submit` | Solicita o envio do formulário. |
| `reset` | Restaura os valores iniciais. |
| `button` | Aguarda uma ação programada, normalmente com JavaScript. |

### Validações nativas

O navegador pode verificar algumas regras antes do envio:

```html
<input
  type="text"
  name="nome"
  minlength="3"
  maxlength="80"
  required
>
```

| Atributo | Aplicação |
| --- | --- |
| `required` | Torna o campo obrigatório. |
| `minlength` | Define a quantidade mínima de caracteres. |
| `maxlength` | Define a quantidade máxima de caracteres. |
| `min` | Define o menor valor permitido. |
| `max` | Define o maior valor permitido. |
| `step` | Define o intervalo entre valores numéricos. |
| `pattern` | Define um padrão de texto. |
| `placeholder` | Apresenta uma dica temporária. |
| `autocomplete` | Ajuda o navegador a sugerir valores. |

A validação realizada pelo navegador melhora a experiência de preenchimento,
mas o servidor ainda precisa validar todos os dados recebidos.

### Envio de arquivos

O campo `file` abre o seletor de arquivos do dispositivo:

```html
<form
  action="/arquivos"
  method="post"
  enctype="multipart/form-data"
>
  <label for="anexo">Arquivo complementar</label>

  <input
    type="file"
    id="anexo"
    name="anexo"
    accept=".png,.jpg,.jpeg,.pdf"
  >
</form>
```

O atributo `accept` indica os formatos esperados. O atributo `multiple` permite
selecionar vários arquivos:

```html
<input type="file" name="imagens" accept="image/*" multiple>
```

Esses atributos orientam a seleção, mas o servidor ainda precisa verificar o
tipo, o tamanho e o conteúdo de cada arquivo.

## Aplicação no Portal de Notícias

Os formulários foram relacionados às páginas já construídas no projeto.

### Página principal

Na página `index.html`, foi proposta uma área de consulta com:

- campo de busca;
- filtro por categoria;
- filtro por tecnologia;
- botão para filtrar as publicações.

Como se trata de uma consulta, o formulário utiliza `method="get"`.

### Página completa da notícia

Foi criada uma página interna para apresentar o conteúdo completo de uma
publicação. No rodapé da notícia, o formulário permite informar:

- nome;
- comentário;
- nota de interesse pela matéria;
- arquivo complementar opcional.

### Página de hobbies

Na página `hobbies.html`, o formulário permite:

- identificar a pessoa visitante;
- escolher o hobby que mais chamou sua atenção;
- atribuir uma nota;
- marcar outras atividades de interesse;
- escrever um comentário.

### Página de contato

Foi criada a página `contato.html` com os campos:

- nome;
- e-mail;
- mensagem;
- botão de envio.

O desenvolvimento visual ocorreu em duas etapas:

1. organização estrutural do formulário com Flexbox;
2. estilização de rótulos, campos, estados de foco e botão.

## Organização do CSS

Os estilos específicos da página de contato devem permanecer em um arquivo
próprio:

```html
<link rel="stylesheet" href="./css/reset.css">
<link rel="stylesheet" href="./css/global.css">
<link rel="stylesheet" href="./css/styles.css">
<link rel="stylesheet" href="./css/contato.css">
```

Exemplo de organização inicial:

```css
.formulario-contato {
  display: flex;
  flex-direction: column;
  gap: 1.25rem;
}

.campo {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.campo input,
.campo textarea,
.campo select {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #cbd2dc;
  border-radius: 0.5rem;
  font: inherit;
}
```

## Atividade prática

Cada estudante deverá criar ou aprimorar uma página de formulário dentro do
próprio projeto.

O formulário deverá possuir:

1. pelo menos três campos diferentes;
2. labels associados corretamente;
3. atributos `id` e `name`;
4. pelo menos dois tipos de `input`;
5. pelo menos uma validação nativa;
6. botão com `type="submit"`;
7. organização visual com CSS;
8. foco visível durante a navegação pelo teclado;
9. adaptação para telas menores.

## Resultado esperado

Ao final da atividade, o projeto deverá possuir uma página de formulário:

- conectada ao menu de navegação;
- organizada semanticamente;
- visualmente integrada às demais páginas;
- adaptável a diferentes tamanhos de tela;
- capaz de utilizar as validações nativas do navegador.

## Checklist

- [ ] A página está conectada ao menu?
- [ ] O link da página atual possui `aria-current="page"`?
- [ ] O formulário possui `action` e `method`?
- [ ] Todos os campos possuem `name`?
- [ ] Cada label está associado ao campo correto?
- [ ] Os valores de `id` são únicos?
- [ ] Os tipos de `input` são adequados aos dados solicitados?
- [ ] Os campos obrigatórios utilizam `required`?
- [ ] Os botões declaram o atributo `type`?
- [ ] O foco permanece visível?
- [ ] O formulário pode ser percorrido com a tecla Tab?
- [ ] O layout funciona em telas menores?
- [ ] As alterações foram registradas no Git?
- [ ] A versão mais recente foi enviada ao GitHub?

## Material complementar

- [Consultar o guia de formulários HTML](../../guias/guia-formularios-html.md)
- [Consultar os demais guias](../../guias/README.md)

## Navegação

- [Aula anterior](../aula5/README.md)
- [Voltar para as aulas](../)
- [Voltar ao README principal](../../../README.md)

