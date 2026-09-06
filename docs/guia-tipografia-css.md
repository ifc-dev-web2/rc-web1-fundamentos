# Guia de tipografia no CSS

Este guia apresenta os fundamentos necessários para definir tamanhos, pesos e espaçamentos de fontes de maneira consistente em uma página web.

## 1. Tamanho da fonte e hierarquia visual

O tamanho da fonte ajuda a mostrar a importância de cada conteúdo. Normalmente, um título principal é maior que um subtítulo, que por sua vez é maior que um parágrafo.

```text
h1 → título principal
h2 → título de seção
h3 → subtítulo
p  → texto comum
```

O elemento `h1` não precisa obrigatoriamente ter `2rem`. Esse é apenas um valor comum. O importante é criar uma hierarquia visual coerente entre os elementos.

Exemplo:

```css
h1 {
  font-size: 2rem;
}

h2 {
  font-size: 1.5rem;
}

h3 {
  font-size: 1.25rem;
}

p {
  font-size: 1rem;
}
```

## 2. O que é `rem`?

A unidade `rem` é calculada com base no tamanho da fonte do elemento raiz da página, o elemento `html`.

```css
html {
  font-size: 16px;
}
```

Quando o tamanho raiz é `16px`, temos:

| Valor em CSS | Cálculo | Resultado |
| --- | ---: | ---: |
| `0.75rem` | 0,75 × 16 | 12px |
| `0.875rem` | 0,875 × 16 | 14px |
| `1rem` | 1 × 16 | 16px |
| `1.25rem` | 1,25 × 16 | 20px |
| `1.5rem` | 1,5 × 16 | 24px |
| `2rem` | 2 × 16 | 32px |
| `2.5rem` | 2,5 × 16 | 40px |

### Converter `rem` para pixels

A fórmula é:

```text
tamanho em pixels = valor em rem × tamanho da fonte raiz
```

Exemplo:

```text
1.5rem × 16px = 24px
```

### Converter pixels para `rem`

A fórmula inversa é:

```text
valor em rem = tamanho em pixels ÷ tamanho da fonte raiz
```

Exemplo:

```text
24px ÷ 16px = 1.5rem
```

> Os cálculos acima consideram que o elemento `html` utiliza `font-size: 16px`. Se esse valor for alterado, o resultado de todas as medidas em `rem` também será alterado.

## 3. Criando uma escala tipográfica

Uma escala tipográfica define uma relação matemática entre os tamanhos dos textos. Uma fórmula possível é:

```text
tamanho = tamanho-base × proporção elevado ao nível
```

Considerando um tamanho-base de `16px` e uma proporção de `1.25`:

| Nível | Cálculo aproximado | Tamanho |
| --- | ---: | ---: |
| Texto comum | 16 × 1 | 16px |
| Subtítulo | 16 × 1,25 | 20px |
| Título de seção | 20 × 1,25 | 25px |
| Título principal | 25 × 1,25 | 31,25px |

No CSS, podemos arredondar esses valores para tornar a escala mais simples:

```css
:root {
  --font-size-sm: 0.875rem; /* 14px */
  --font-size-md: 1rem;     /* 16px */
  --font-size-lg: 1.25rem;  /* 20px */
  --font-size-xl: 1.5rem;   /* 24px */
  --font-size-2xl: 2rem;    /* 32px */
}
```

As variáveis evitam a repetição de valores e ajudam a manter o padrão visual do projeto.

```css
body {
  font-size: var(--font-size-md);
}

h1 {
  font-size: var(--font-size-2xl);
}

h2 {
  font-size: var(--font-size-xl);
}

h3 {
  font-size: var(--font-size-lg);
}
```

## 4. Peso da fonte

A propriedade `font-weight` controla a espessura dos caracteres. Ela não modifica o tamanho da fonte.

| Peso | Nome comum | Aplicação sugerida |
| ---: | --- | --- |
| `300` | leve | textos decorativos |
| `400` | normal | parágrafos |
| `500` | médio | subtítulos |
| `600` | seminegrito | títulos secundários |
| `700` | negrito | títulos principais |
| `800` ou `900` | extranegrito | chamadas de grande destaque |

Exemplo de hierarquia:

```css
.hero-about h1 {
  font-size: 2rem;
  font-weight: 700;
}

.hero-about h3 {
  font-size: 1.25rem;
  font-weight: 500;
}

.hero-about p {
  font-size: 1rem;
  font-weight: 400;
}
```

Nesse exemplo, a hierarquia é criada por duas características:

- tamanho: `32px → 20px → 16px`;
- peso: `700 → 500 → 400`.

### Disponibilidade dos pesos

A família tipográfica utilizada precisa oferecer os pesos escolhidos. Caso somente o peso `400` seja carregado, o navegador poderá simular os demais pesos.

Exemplo com uma fonte importada do Google Fonts:

```css
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap");

body {
  font-family: "Roboto", sans-serif;
}
```

Nesse caso, foram carregados os pesos `400`, `500` e `700`.

## 5. Altura da linha

A propriedade `line-height` controla a altura de cada linha de texto. Ela influencia diretamente a legibilidade.

```css
h1 {
  line-height: 1.2;
}

h3 {
  line-height: 1.4;
}

p {
  line-height: 1.6;
}
```

Quando usamos um valor sem unidade, o navegador realiza a multiplicação:

```text
altura da linha = tamanho da fonte × line-height
```

Para um parágrafo com `font-size: 16px` e `line-height: 1.6`:

```text
16px × 1.6 = 25.6px
```

Títulos geralmente utilizam uma altura de linha menor. Parágrafos precisam de mais espaço entre as linhas para facilitar a leitura.

## 6. Exemplo aplicado ao perfil

Primeiro, podemos definir os valores gerais do projeto:

```css
:root {
  --font-size-sm: 0.875rem;
  --font-size-base: 1rem;
  --font-size-subtitle: 1.25rem;
  --font-size-section: 1.5rem;
  --font-size-title: 2rem;

  --font-weight-normal: 400;
  --font-weight-medium: 500;
  --font-weight-semibold: 600;
  --font-weight-bold: 700;
}
```

Depois, aplicamos as variáveis aos elementos:

```css
.hero-about h1,
.hero-about h3,
.hero-about p {
  margin: 0;
}

.hero-about h1 {
  color: #212529;
  font-size: var(--font-size-title);
  font-weight: var(--font-weight-bold);
  line-height: 1.2;
}

.hero-about h3 {
  color: #495057;
  font-size: var(--font-size-subtitle);
  font-weight: var(--font-weight-medium);
  line-height: 1.4;
}

.hero-about p {
  color: #6c757d;
  font-size: var(--font-size-base);
  font-weight: var(--font-weight-normal);
  line-height: 1.6;
}
```

## 7. Boas práticas

- Use uma escala limitada de tamanhos, em vez de escolher um valor diferente para cada elemento.
- Use `rem` para permitir que a tipografia acompanhe as preferências de tamanho definidas pelo usuário no navegador.
- Utilize peso, tamanho e cor para criar hierarquia, sem depender de apenas uma dessas características.
- Evite usar pesos muito leves em textos pequenos, pois eles podem dificultar a leitura.
- Prefira `line-height` sem unidade para que a altura da linha acompanhe o tamanho do texto.
- Não escolha títulos apenas pela aparência: mantenha a ordem semântica entre `h1`, `h2` e `h3`.
- Evite definir `html { font-size: 62.5%; }` somente para facilitar cálculos. Isso reduz o tamanho-base para aproximadamente `10px` e pode contrariar a preferência de acessibilidade do usuário.

## Resumo

Uma tipografia consistente combina quatro decisões:

1. **Tamanho:** estabelece a hierarquia do conteúdo.
2. **Peso:** reforça o nível de importância.
3. **Altura da linha:** melhora a legibilidade.
4. **Escala:** mantém uma relação visual coerente entre todos os textos.

Em uma configuração padrão de `16px`:

```text
1rem = 16px
1.25rem = 20px
1.5rem = 24px
2rem = 32px
```

O objetivo não é decorar todos os valores, mas compreender as fórmulas e aplicar uma escala consistente em todo o projeto.
