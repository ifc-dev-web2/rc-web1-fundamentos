# Guia de Box Model no CSS

Todo elemento HTML é representado pelo navegador como uma caixa. Compreender como essa caixa é calculada ajuda a evitar larguras inesperadas, desalinhamentos e rolagem horizontal.

## 1. As quatro áreas da caixa

Da parte interna para a externa, o Box Model possui:

1. **content:** conteúdo do elemento;
2. **padding:** espaço interno entre conteúdo e borda;
3. **border:** contorno da caixa;
4. **margin:** espaço externo que separa a caixa das demais.

```css
.card {
  width: 300px;
  padding: 20px;
  border: 2px solid #adb5bd;
  margin: 16px;
}
```

## 2. `content-box`

`content-box` é o valor inicial de `box-sizing`:

```css
.card {
  box-sizing: content-box;
  width: 300px;
  padding: 20px;
  border: 2px solid;
}
```

Nesse modelo, `width` representa apenas o conteúdo.

```text
largura final = conteúdo + padding horizontal + borda horizontal
largura final = 300 + 40 + 4
largura final = 344px
```

A margem não participa do tamanho da caixa, mas ocupa espaço ao redor dela.

## 3. `border-box`

Com `border-box`, a largura declarada já inclui conteúdo, padding e borda:

```css
.card {
  box-sizing: border-box;
  width: 300px;
  padding: 20px;
  border: 2px solid;
}
```

A largura externa da caixa permanece em `300px`. O navegador reduz a área do conteúdo para acomodar padding e borda.

## 4. Regra global recomendada

```css
*,
*::before,
*::after {
  box-sizing: border-box;
}
```

Essa regra torna o cálculo das dimensões mais previsível e inclui também caixas criadas por pseudo-elementos.

## 5. Padding e margin

`padding` cria espaço dentro da borda:

```css
.card {
  padding: 2rem;
}
```

`margin` cria espaço fora da borda:

```css
.card {
  margin-bottom: 2rem;
}
```

Para espaçar os filhos de Flexbox ou Grid, prefira `gap`:

```css
.lista-cards {
  display: flex;
  gap: 1.5rem;
}
```

## 6. Formas abreviadas

Um valor aplica-se aos quatro lados:

```css
padding: 1rem;
```

Dois valores representam vertical e horizontal:

```css
padding: 1rem 2rem;
```

Quatro valores seguem o sentido horário:

```css
padding: 1rem 2rem 3rem 4rem;
```

Ordem:

```text
top → right → bottom → left
```

## 7. Largura, altura e limites

```css
.elemento {
  width: 90%;
  max-width: 1200px;
  min-height: 200px;
}
```

- `width` define a largura desejada;
- `height` define uma altura explícita;
- `min-*` impede que o elemento fique menor que o limite;
- `max-*` impede que ultrapasse o limite.

Evite alturas fixas em blocos com texto quando o conteúdo pode crescer:

```css
/* Mais seguro para conteúdo variável */
.card {
  min-height: 220px;
}
```

## 8. Centralização com margem automática

```css
.container {
  width: 90%;
  max-width: 1200px;
  margin: 0 auto;
}
```

As margens horizontais automáticas absorvem igualmente o espaço restante. O elemento precisa possuir uma largura menor que a área disponível para a centralização ser percebida.

## 9. Colapso de margens

Margens verticais de elementos de bloco podem se combinar em vez de serem somadas. Por isso, dois elementos com margens verticais não necessariamente produzirão a soma esperada.

Em componentes, `gap` costuma ser mais previsível:

```css
.grupo {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.grupo > * {
  margin: 0;
}
```

## 10. `overflow`

Quando o conteúdo ultrapassa os limites da caixa, `overflow` define seu comportamento:

```css
.caixa {
  overflow: visible;
}
```

| Valor | Comportamento |
| --- | --- |
| `visible` | O conteúdo pode aparecer fora da caixa. |
| `hidden` | O excedente é recortado. |
| `auto` | Cria rolagem quando necessária. |
| `scroll` | Mantém uma área de rolagem. |

Para fazer uma imagem respeitar os cantos de um card:

```css
.card {
  overflow: hidden;
  border-radius: 1rem;
}
```

Não use `overflow: hidden` apenas para esconder um erro de largura.

## 11. Box Model e imagens

```css
.foto-perfil {
  display: block;
  width: 160px;
  height: 160px;
  object-fit: cover;
  border: 6px solid #fff;
  border-radius: 50%;
}
```

Com a regra global de `border-box`, a borda está incluída nos `160px` declarados.

## 12. Inspeção no DevTools

O painel **Computed** apresenta um diagrama do Box Model. Utilize-o para verificar:

- tamanho do conteúdo;
- padding aplicado;
- espessura da borda;
- margem externa;
- tamanho final renderizado.

Quando um elemento fica maior que o esperado, confira primeiro `width`, `padding`, `border` e `box-sizing`.

## 13. Erros comuns

### Somar padding a uma largura sem `border-box`

```css
.caixa {
  width: 100%;
  padding: 2rem;
}
```

Com `content-box`, essa caixa pode ultrapassar o pai.

### Usar `height` fixa em textos

Se o texto quebrar em mais linhas, poderá sair da caixa. Prefira `min-height` ou deixe a altura automática.

### Confundir margem com padding

- espaço interno: `padding`;
- espaço externo: `margin`;
- espaço entre filhos de um layout: `gap`.

### Usar `100vw` dentro de um container

Prefira `width: 100%` para acompanhar a largura do pai.

## 14. Checklist

- [ ] A regra global de `box-sizing` foi aplicada?
- [ ] A largura precisa incluir padding e borda?
- [ ] O espaço é interno, externo ou entre itens?
- [ ] Uma altura fixa é realmente necessária?
- [ ] O conteúdo pode crescer sem ser recortado?
- [ ] O tamanho final foi conferido no DevTools?
- [ ] `overflow` está corrigindo uma necessidade real?

## Resumo

```css
*,
*::before,
*::after {
  box-sizing: border-box;
}

.card {
  width: 100%;
  max-width: 600px;
  padding: 2rem;
  border: 1px solid #dee2e6;
  margin: 0 auto;
}
```

Com `border-box`, a dimensão declarada inclui conteúdo, padding e borda. Essa decisão torna a construção de layouts mais previsível.
