# Guia de fundamentos e organização do CSS

Este guia apresenta seletores, cascata, especificidade, pseudo-classes, pseudo-elementos, variáveis e uma forma organizada de estruturar folhas de estilo.

## 1. Anatomia de uma regra CSS

```css
.card {
  color: #212529;
  background-color: #fff;
}
```

- `.card` é o seletor;
- `color` e `background-color` são propriedades;
- os valores aparecem depois de `:`;
- cada declaração termina com `;`.

## 2. Seletor de elemento

Seleciona todos os elementos daquele tipo:

```css
p {
  line-height: 1.6;
}
```

É adequado para estilos gerais, mas não para diferenciar componentes específicos.

## 3. Seletor de classe

Uma classe pode ser reutilizada:

```html
<section class="card">...</section>
<article class="card">...</article>
```

```css
.card {
  border: 1px solid #dee2e6;
}
```

Para estilização de componentes, classes normalmente oferecem o melhor equilíbrio entre reutilização e especificidade.

## 4. Seletor de ID

Um ID identifica um elemento único na página:

```html
<section id="perfil">...</section>
```

```css
#perfil {
  scroll-margin-top: 2rem;
}
```

IDs são úteis para identificação, links internos e JavaScript. Para estilos reutilizáveis, prefira classes.

## 5. Seletores de relação

### Descendente

Seleciona elementos em qualquer nível interno:

```css
.card h2 {
  color: var(--cor-primaria);
}
```

### Filho direto

Seleciona somente filhos imediatos:

```css
.hero-content > img {
  border-radius: 50%;
}
```

### Irmão adjacente

Seleciona o próximo irmão:

```css
h2 + p {
  margin-top: 0;
}
```

### Irmãos posteriores

```css
h2 ~ p {
  color: #495057;
}
```

## 6. Seletores de atributo

```css
input[type="email"] {
  border-color: #173b82;
}

a[target="_blank"] {
  text-decoration-style: dotted;
}
```

## 7. Pseudo-classes

Pseudo-classes representam estado ou posição:

```css
a:hover {
  color: var(--cor-destaque);
}

a:focus-visible {
  outline: 3px solid var(--cor-destaque);
  outline-offset: 3px;
}

li:first-child {
  font-weight: 700;
}
```

Não remova o indicador de foco sem oferecer uma alternativa visível.

## 8. Pseudo-elementos

Pseudo-elementos estilizam ou criam uma parte visual:

```css
.titulo::after {
  display: block;
  width: 3rem;
  height: 0.25rem;
  margin-top: 0.5rem;
  background-color: var(--cor-destaque);
  content: "";
}
```

Conteúdo essencial não deve existir apenas em `::before` ou `::after`.

## 9. Cascata

Quando várias declarações atingem o mesmo elemento, o navegador decide qual vence considerando, de forma simplificada:

1. origem e importância da regra;
2. camada da cascata, quando utilizada;
3. especificidade do seletor;
4. ordem de declaração.

Se duas regras possuem a mesma especificidade, a última normalmente vence:

```css
.card {
  color: blue;
}

.card {
  color: green;
}
```

O texto será verde.

## 10. Especificidade

Uma forma didática de comparar seletores é usar três grupos:

```text
(IDs, classes/atributos/pseudo-classes, elementos/pseudo-elementos)
```

| Seletor | Especificidade |
| --- | --- |
| `p` | `(0, 0, 1)` |
| `.card` | `(0, 1, 0)` |
| `.card h2` | `(0, 1, 1)` |
| `a:hover` | `(0, 1, 1)` |
| `#perfil` | `(1, 0, 0)` |
| `#perfil .card h2` | `(1, 1, 1)` |

Cada grupo é comparado da esquerda para a direita. Uma classe vence qualquer quantidade de seletores de elemento; um ID vence qualquer quantidade de classes quando as demais condições da cascata são equivalentes.

O seletor universal `*` e combinadores como `>`, `+` e `~` não acrescentam especificidade.

## 11. Estilo inline e `!important`

Evite estilo inline:

```html
<p style="color: red;">Texto</p>
```

Ele mistura estrutura e apresentação e possui prioridade elevada na cascata.

`!important` altera a prioridade de uma declaração:

```css
.card {
  color: red !important;
}
```

Não o utilize como correção automática. Primeiro verifique:

- se o seletor está correto;
- se outra regra é mais específica;
- se a ordem do arquivo está adequada;
- se a propriedade está sendo herdada.

## 12. Herança

Algumas propriedades, como `color` e `font-family`, normalmente são herdadas:

```css
body {
  color: #252525;
  font-family: Arial, sans-serif;
}
```

Outras, como `margin`, `padding`, `border` e `width`, normalmente não são herdadas.

## 13. Variáveis CSS

Variáveis transformam valores repetidos em decisões nomeadas:

```css
:root {
  --cor-primaria: #173b82;
  --cor-destaque: #4db6e8;
  --cor-fundo: #f4f6f8;
  --cor-texto: #252525;
  --cor-borda: #dddddd;
  --espacamento-md: 1rem;
  --raio-card: 1rem;
}
```

Uso:

```css
.card {
  padding: var(--espacamento-md);
  color: var(--cor-texto);
  border: 1px solid var(--cor-borda);
  border-radius: var(--raio-card);
}
```

Nomeie variáveis pelo papel no projeto, não apenas pelo valor. `--cor-primaria` comunica melhor a intenção que `--azul`.

## 14. Valor de fallback

```css
.card {
  color: var(--cor-texto, #252525);
}
```

O segundo valor será usado se a variável não estiver definida.

## 15. Organização sugerida do CSS

```css
/* 1. Variáveis */
:root { }

/* 2. Base global e Box Model */
*,
*::before,
*::after { }

body { }
img { }

/* 3. Layout */
.container { }
.header { }
.main { }

/* 4. Componentes */
.hero { }
.card { }
.menu { }

/* 5. Utilitários pontuais */
.visually-hidden { }

/* 6. Ajustes responsivos */
@media (max-width: 768px) { }
```

Agrupe regras por responsabilidade e mantenha a media query depois da regra que ela modifica ou em uma seção responsiva consistente.

## 16. Evitando seletores frágeis

Evite depender de muitos níveis do HTML:

```css
/* Frágil e difícil de reutilizar */
main section div article h2 {
  color: blue;
}
```

Prefira uma classe relacionada ao componente:

```css
.card-title {
  color: var(--cor-primaria);
}
```

## 17. Erros comuns

- utilizar ID para todos os estilos;
- aumentar a especificidade até a regra funcionar;
- adicionar `!important` sem investigar a cascata;
- criar nomes como `.texto-azul` quando a cor representa uma função;
- depender de uma estrutura HTML excessivamente específica;
- retirar o foco visível dos links e controles;
- repetir valores que poderiam ser variáveis.

## 18. Checklist

- [ ] O seletor representa corretamente o elemento ou componente?
- [ ] Uma classe reutilizável seria melhor que um ID?
- [ ] A regra vencedora pode ser explicada pela cascata?
- [ ] A especificidade continua simples?
- [ ] `!important` foi evitado?
- [ ] Estados de `hover` e foco estão visíveis?
- [ ] Valores repetidos foram transformados em variáveis?
- [ ] O arquivo segue uma ordem previsível?

## Resumo

```css
:root {
  --cor-primaria: #173b82;
  --cor-texto: #252525;
}

.card {
  color: var(--cor-texto);
}

.card h2 {
  color: var(--cor-primaria);
}

.card a:hover,
.card a:focus-visible {
  text-decoration: underline;
}
```

Seletores identificam o alvo; a cascata determina qual declaração vence; a especificidade desempata regras concorrentes; e as variáveis mantêm decisões reutilizáveis.
