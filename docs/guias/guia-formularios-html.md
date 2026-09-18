# Guia de formulários HTML

Este guia apresenta os principais elementos e atributos utilizados na criação
de formulários HTML. Os exemplos podem ser adaptados para as páginas de
contato, notícias e hobbies do projeto da disciplina.

## Sumário

1. [Para que serve um formulário?](#para-que-serve-um-formulário)
2. [Estrutura mínima](#estrutura-mínima)
3. [GET e POST](#get-e-post)
4. [Label, id e name](#label-id-e-name)
5. [Tipos de input](#tipos-de-input)
6. [Textarea](#textarea)
7. [Select e option](#select-e-option)
8. [Checkbox e radio](#checkbox-e-radio)
9. [Botões](#botões)
10. [Validações nativas](#validações-nativas)
11. [Envio de arquivos](#envio-de-arquivos)
12. [Autocomplete](#autocomplete)
13. [Organização com fieldset e legend](#organização-com-fieldset-e-legend)
14. [Estados no CSS](#estados-no-css)
15. [Acessibilidade](#acessibilidade)
16. [Limites do HTML](#limites-do-html)
17. [Exemplo completo](#exemplo-completo)
18. [Checklist](#checklist)

## Para que serve um formulário?

Um formulário permite que a pessoa forneça dados para uma aplicação. Alguns
exemplos são:

- realizar uma busca;
- entrar em uma conta;
- enviar uma mensagem;
- criar um cadastro;
- avaliar um conteúdo;
- anexar um arquivo;
- escolher opções ou filtros.

O HTML cria a interface e oferece validações básicas. Para armazenar, consultar
ou processar os dados, normalmente será necessário um servidor.

## Estrutura mínima

O elemento `form` delimita os controles que participam do envio:

```html
<form action="/contato" method="post">
  <label for="nome">Nome</label>
  <input type="text" id="nome" name="nome">

  <button type="submit">Enviar</button>
</form>
```

| Atributo | Função |
| --- | --- |
| `action` | Indica o endereço que receberá os dados. |
| `method` | Define o método HTTP utilizado no envio. |
| `enctype` | Define como os dados serão codificados. |
| `autocomplete` | Permite ou restringe sugestões de preenchimento. |
| `novalidate` | Desativa a validação nativa durante o envio. |

> Em exercícios estáticos, `action="#"` pode ser usado temporariamente. Isso
> não armazena nem encaminha os dados.

## GET e POST

### GET

O método `GET` costuma ser utilizado em consultas, buscas e filtros. Os dados
aparecem na URL como parâmetros.

```html
<form action="/buscar" method="get">
  <label for="termo">Buscar</label>
  <input type="search" id="termo" name="q">
  <button type="submit">Buscar</button>
</form>
```

Exemplo de URL:

```text
/buscar?q=html
```

### POST

O método `POST` envia os dados no corpo da requisição. Ele costuma ser usado
para criar registros, enviar mensagens e transmitir arquivos.

```html
<form action="/contato" method="post">
  <!-- campos -->
</form>
```

`POST` não criptografa os dados. A proteção durante o transporte depende do uso
de HTTPS, e o servidor precisa tratar os dados recebidos com segurança.

## Label, id e name

```html
<label for="email">E-mail</label>
<input type="email" id="email" name="email">
```

| Recurso | Função |
| --- | --- |
| `label` | Apresenta o nome ou a instrução do campo. |
| `for` | Indica o `id` do controle associado. |
| `id` | Identifica o elemento no documento. |
| `name` | Define a chave utilizada no envio dos dados. |
| `value` | Representa o valor associado ao controle. |

O valor de um controle sem `name` não participa normalmente dos dados enviados
pelo formulário.

## Tipos de input

O atributo `type` define o comportamento esperado para o campo.

```html
<input type="text" name="nome">
```

Quando `type` não é informado ou possui um valor desconhecido, o navegador
trata o controle como `text`.

### Texto, contato e autenticação

| Tipo | Utilização comum | Comportamento esperado |
| --- | --- | --- |
| `text` | Nome, título ou informação curta | Campo de texto em uma linha. |
| `email` | Endereço de e-mail | Verifica um formato básico de e-mail. |
| `password` | Senha | Oculta visualmente os caracteres digitados. |
| `tel` | Telefone | Pode apresentar teclado telefônico no celular. |
| `url` | Endereço Web | Verifica um formato básico de URL. |
| `search` | Busca e filtros | Campo de texto voltado a pesquisas. |

Exemplo:

```html
<label for="email">E-mail</label>
<input
  type="email"
  id="email"
  name="email"
  autocomplete="email"
  required
>
```

### Números e intervalos

| Tipo | Utilização comum | Atributos relacionados |
| --- | --- | --- |
| `number` | Quantidades e valores numéricos | `min`, `max` e `step`. |
| `range` | Seleção visual em um intervalo | `min`, `max` e `step`. |

```html
<label for="quantidade">Quantidade</label>
<input
  type="number"
  id="quantidade"
  name="quantidade"
  min="1"
  max="10"
  step="1"
>
```

### Datas e horários

| Tipo | Dado esperado |
| --- | --- |
| `date` | Data. |
| `time` | Horário. |
| `datetime-local` | Data e horário local. |
| `month` | Mês e ano. |
| `week` | Semana e ano. |

```html
<label for="data">Data do atendimento</label>
<input type="date" id="data" name="data" required>
```

A interface visual desses campos pode variar entre navegadores e sistemas
operacionais.

### Cores, arquivos e dados ocultos

| Tipo | Utilização comum |
| --- | --- |
| `color` | Seleção de uma cor. |
| `file` | Seleção de um ou mais arquivos. |
| `hidden` | Valor enviado sem controle visível. |

O campo `hidden` não protege informações. A pessoa pode inspecionar e alterar o
HTML pelo navegador.

### Seleções

| Tipo | Utilização comum |
| --- | --- |
| `checkbox` | Zero, uma ou várias escolhas independentes. |
| `radio` | Uma escolha dentro de um grupo. |

### Botões implementados com input

| Tipo | Comportamento |
| --- | --- |
| `submit` | Envia o formulário. |
| `reset` | Restaura os valores iniciais. |
| `button` | Não executa uma ação sozinho. |
| `image` | Envia o formulário por meio de uma imagem. |

Na maioria dos casos, o elemento `button` oferece mais flexibilidade para
conteúdo e estilização.

## Textarea

O elemento `textarea` recebe textos com várias linhas:

```html
<label for="mensagem">Mensagem</label>
<textarea
  id="mensagem"
  name="mensagem"
  rows="6"
  minlength="10"
  maxlength="500"
  required
></textarea>
```

| Atributo | Função |
| --- | --- |
| `rows` | Sugere a quantidade de linhas visíveis. |
| `cols` | Sugere a largura em quantidade de caracteres. |
| `minlength` | Define a quantidade mínima de caracteres. |
| `maxlength` | Define a quantidade máxima de caracteres. |
| `placeholder` | Apresenta uma dica temporária. |

O CSS pode controlar a largura e a altura final do elemento.

```css
textarea {
  width: 100%;
  min-height: 9rem;
  resize: vertical;
}
```

## Select e option

O elemento `select` apresenta uma lista de opções:

```html
<label for="assunto">Assunto</label>

<select id="assunto" name="assunto" required>
  <option value="">Selecione uma opção</option>
  <option value="duvida">Dúvida</option>
  <option value="projeto">Projeto</option>
  <option value="outro">Outro assunto</option>
</select>
```

O conteúdo de `option` aparece para a pessoa, enquanto `value` representa o
dado enviado.

### Seleção de várias opções

```html
<label for="tecnologias">Tecnologias</label>

<select id="tecnologias" name="tecnologias" multiple>
  <option value="html">HTML</option>
  <option value="css">CSS</option>
  <option value="javascript">JavaScript</option>
</select>
```

Ao utilizar `multiple`, forneça instruções claras sobre como selecionar mais de
uma opção.

## Checkbox e radio

### Checkbox

Cada checkbox representa uma escolha independente:

```html
<label>
  <input type="checkbox" name="interesses" value="html">
  HTML
</label>

<label>
  <input type="checkbox" name="interesses" value="css">
  CSS
</label>
```

### Radio

Os controles radio formam um grupo quando compartilham o mesmo `name`:

```html
<fieldset>
  <legend>Qual é o seu interesse pela matéria?</legend>

  <label>
    <input type="radio" name="nota" value="1" required>
    1 estrela
  </label>

  <label>
    <input type="radio" name="nota" value="2">
    2 estrelas
  </label>

  <label>
    <input type="radio" name="nota" value="3">
    3 estrelas
  </label>
</fieldset>
```

## Botões

```html
<button type="submit">Enviar</button>
<button type="reset">Limpar</button>
<button type="button">Abrir ajuda</button>
```

| Tipo | Função |
| --- | --- |
| `submit` | Solicita o envio do formulário. |
| `reset` | Restaura os valores iniciais. |
| `button` | Aguarda uma ação programada, normalmente com JavaScript. |

Declare o `type` explicitamente. Um botão colocado dentro de um formulário pode
assumir o comportamento de envio quando o tipo não é informado.

## Validações nativas

O navegador oferece atributos que ajudam a evitar entradas incompletas ou
incompatíveis.

| Atributo | Aplicação |
| --- | --- |
| `required` | Torna o preenchimento obrigatório. |
| `minlength` | Define a quantidade mínima de caracteres. |
| `maxlength` | Define a quantidade máxima de caracteres. |
| `min` | Define o menor valor permitido. |
| `max` | Define o maior valor permitido. |
| `step` | Define o intervalo entre valores válidos. |
| `pattern` | Define um padrão de texto por expressão regular. |
| `multiple` | Permite informar ou selecionar vários valores. |
| `readonly` | Permite visualizar, mas não editar o valor. |
| `disabled` | Desativa o controle e normalmente o remove do envio. |

Exemplo:

```html
<label for="usuario">Nome de usuário</label>
<input
  type="text"
  id="usuario"
  name="usuario"
  minlength="3"
  maxlength="20"
  pattern="[A-Za-z0-9_-]+"
  title="Use letras, números, hífen ou sublinhado"
  required
>
```

O atributo `title` pode complementar a orientação, mas as instruções essenciais
devem permanecer visíveis na página.

## Envio de arquivos

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

  <button type="submit">Enviar arquivo</button>
</form>
```

| Recurso | Função |
| --- | --- |
| `type="file"` | Abre o seletor de arquivos do dispositivo. |
| `accept` | Indica os formatos de arquivo esperados. |
| `multiple` | Permite selecionar vários arquivos. |
| `enctype="multipart/form-data"` | Codifica o formulário para transportar arquivos. |

Exemplo para várias imagens:

```html
<input
  type="file"
  id="imagens"
  name="imagens"
  accept="image/*"
  multiple
>
```

`accept` orienta a seleção, mas o servidor ainda precisa validar tipo, tamanho,
nome e conteúdo do arquivo.

## Autocomplete

O atributo `autocomplete` ajuda o navegador a reconhecer a finalidade do campo:

```html
<input type="text" name="nome" autocomplete="name">
<input type="email" name="email" autocomplete="email">
<input type="tel" name="telefone" autocomplete="tel">
<input type="text" name="cidade" autocomplete="address-level2">
```

Alguns valores comuns:

| Valor | Informação esperada |
| --- | --- |
| `name` | Nome completo. |
| `given-name` | Nome. |
| `family-name` | Sobrenome. |
| `email` | E-mail. |
| `tel` | Telefone. |
| `street-address` | Endereço. |
| `address-level2` | Cidade. |
| `postal-code` | Código postal. |
| `current-password` | Senha atual. |
| `new-password` | Nova senha. |

## Organização com fieldset e legend

`fieldset` agrupa controles relacionados. `legend` apresenta o nome do grupo.

```html
<fieldset>
  <legend>Forma de contato preferida</legend>

  <label>
    <input type="radio" name="contato" value="email" required>
    E-mail
  </label>

  <label>
    <input type="radio" name="contato" value="telefone">
    Telefone
  </label>
</fieldset>
```

## Estados no CSS

Os controles possuem estados que podem receber estilos específicos:

```css
input:focus,
textarea:focus,
select:focus {
  outline: 3px solid #4db6e8;
  outline-offset: 2px;
}

input:disabled {
  cursor: not-allowed;
  opacity: 0.6;
}

input:checked {
  accent-color: #173b82;
}

input:user-invalid,
textarea:user-invalid {
  border-color: #b83a3a;
}
```

| Seletor | Estado |
| --- | --- |
| `:focus` | Controle que possui foco. |
| `:focus-visible` | Foco que deve receber indicação visual. |
| `:checked` | Checkbox ou radio selecionado. |
| `:disabled` | Controle desativado. |
| `:required` | Controle obrigatório. |
| `:valid` | Valor compatível com as regras. |
| `:invalid` | Valor incompatível com alguma regra. |
| `:user-valid` | Valor válido depois da interação. |
| `:user-invalid` | Valor inválido depois da interação. |

Não remova o `outline` sem criar uma alternativa de foco claramente visível.

## Acessibilidade

Boas práticas:

- associe cada `label` ao controle correspondente;
- mantenha instruções importantes visíveis;
- utilize `fieldset` e `legend` em grupos relacionados;
- informe quais campos são obrigatórios;
- escreva mensagens de erro que expliquem como corrigir o valor;
- preserve um foco visual perceptível;
- utilize uma ordem de navegação coerente no HTML;
- não dependa somente de cores para indicar erro;
- evite usar `placeholder` como único rótulo;
- escolha o tipo de campo adequado ao dado solicitado.

## Limites do HTML

A validação nativa melhora a experiência, mas pode ser ignorada ou alterada no
navegador. O servidor precisa validar novamente todos os dados recebidos.

Uma página publicada somente no GitHub Pages não possui processamento de
backend. O formulário aparecerá e as validações HTML funcionarão, mas os dados
não serão armazenados sem integração com um serviço externo ou uma aplicação de
servidor.

## Exemplo completo

```html
<form class="formulario-contato" action="/contato" method="post">
  <div class="campo">
    <label for="nome">Nome</label>
    <input
      type="text"
      id="nome"
      name="nome"
      minlength="3"
      maxlength="80"
      autocomplete="name"
      required
    >
  </div>

  <div class="campo">
    <label for="email">E-mail</label>
    <input
      type="email"
      id="email"
      name="email"
      autocomplete="email"
      required
    >
  </div>

  <div class="campo">
    <label for="assunto">Assunto</label>
    <select id="assunto" name="assunto" required>
      <option value="">Selecione uma opção</option>
      <option value="duvida">Dúvida</option>
      <option value="projeto">Projeto</option>
      <option value="outro">Outro assunto</option>
    </select>
  </div>

  <div class="campo">
    <label for="mensagem">Mensagem</label>
    <textarea
      id="mensagem"
      name="mensagem"
      rows="6"
      minlength="10"
      maxlength="500"
      required
    ></textarea>
  </div>

  <button type="submit">Enviar</button>
</form>
```

CSS inicial:

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
.campo select,
.campo textarea {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #cbd2dc;
  border-radius: 0.5rem;
  font: inherit;
}
```

## Checklist

- [ ] O formulário possui `action` e `method`?
- [ ] Todos os controles possuem `name`?
- [ ] Cada campo possui um `label` associado?
- [ ] Os valores de `id` são únicos?
- [ ] O tipo de cada `input` corresponde ao dado esperado?
- [ ] Os campos obrigatórios utilizam `required`?
- [ ] Os limites de texto estão documentados?
- [ ] Grupos de opções utilizam `fieldset` e `legend`?
- [ ] Os botões declaram seu `type`?
- [ ] O foco permanece visível?
- [ ] O formulário funciona com a tecla Tab?
- [ ] O layout funciona em telas menores?
- [ ] O servidor validará novamente os dados?

## Referências

- [Formulários Web — MDN](https://developer.mozilla.org/pt-BR/docs/Learn_web_development/Extensions/Forms)
- [`form` — MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/form)
- [`input` — MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/input)
- [`label` — MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/label)
- [`textarea` — MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/textarea)
- [`select` — MDN](https://developer.mozilla.org/pt-BR/docs/Web/HTML/Element/select)
- [Validação de formulários — MDN](https://developer.mozilla.org/pt-BR/docs/Learn_web_development/Extensions/Forms/Form_validation)

