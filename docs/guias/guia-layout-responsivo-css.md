# Guia de layout responsivo no CSS

Este guia explica como criar páginas que permanecem legíveis e organizadas em diferentes tamanhos de tela. O objetivo não é montar uma página diferente para cada aparelho, mas permitir que o mesmo conteúdo se adapte ao espaço disponível.

## 1. Layout fixo, fluido e responsivo

Um layout fixo utiliza uma largura que não acompanha a tela:

```css
.container {
  width: 960px;
}
```

Em uma tela menor que `960px`, esse conteúdo pode provocar rolagem horizontal.

Um layout fluido combina uma largura relativa com um limite de crescimento:

```css
.container {
  width: 90%;
  max-width: 1200px;
  margin: 0 auto;
}
```

- `width: 90%` acompanha a largura do elemento pai;
- `max-width: 1200px` impede que o conteúdo cresça indefinidamente;
- `margin: 0 auto` centraliza o container horizontalmente.

Um layout responsivo acrescenta mudanças condicionais quando a adaptação natural não é suficiente.

## 2. Configuração da viewport

Inclua esta configuração dentro do `head`:

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

- `width=device-width` utiliza a largura real do dispositivo;
- `initial-scale=1.0` define a escala inicial;
- a viewport não cria responsividade sozinha: o CSS também precisa ser adaptável.

## 3. Unidades de medida

| Unidade | Referência | Uso frequente |
| --- | --- | --- |
| `px` | valor fixo em pixels CSS | bordas e detalhes controlados |
| `%` | normalmente o tamanho do elemento pai | larguras fluidas |
| `rem` | fonte do elemento `html` | tipografia e espaçamento global |
| `em` | tamanho da fonte do contexto | componentes que escalam localmente |
| `vw` | 1% da largura da viewport | efeitos ligados à janela |
| `vh` | 1% da altura da viewport | seções relacionadas à altura da tela |

Medida relativa não significa ausência de limites. Podemos combinar unidades:

```css
.hero-cover {
  width: 100%;
  height: 20vh;
  min-height: 150px;
  max-height: 240px;
}
```

## 4. `width`, `min-width` e `max-width`

```css
.container {
  width: 90%;
  max-width: 1200px;
}
```

- `width` define o tamanho desejado;
- `max-width` estabelece um limite máximo;
- `min-width` estabelece um limite mínimo.

Em imagens, uma configuração comum é:

```css
img {
  display: block;
  max-width: 100%;
  height: auto;
}
```

## 5. Adaptação natural antes da media query

Primeiro, permita que o layout se ajuste naturalmente:

```css
.lista-cards {
  display: flex;
  flex-wrap: wrap;
  gap: 1.5rem;
}

.card {
  flex: 1 1 250px;
}
```

Os cartões passam para outra linha quando deixam de caber. A media query deve ser acrescentada apenas quando houver uma mudança de composição necessária.

## 6. Media queries

Uma media query aplica regras quando uma condição é atendida:

```css
@media (max-width: 768px) {
  .hero-content {
    flex-direction: column;
    text-align: center;
  }
}
```

A regra original continua existindo. Dentro da condição, apenas as propriedades necessárias são sobrescritas.

## 7. Como escolher um breakpoint

Não escolha um breakpoint apenas pelo nome de um aparelho. Reduza a largura da janela e observe quando:

- textos ficam apertados;
- imagem e conteúdo deixam de caber;
- o menu começa a transbordar;
- os cartões ficam estreitos demais;
- surge rolagem horizontal.

Esse é o ponto em que o conteúdo pede uma mudança.

Valores como `480px`, `600px`, `768px` e `1024px` são referências comuns, não regras obrigatórias.

## 8. Desktop-first e mobile-first

### Desktop-first

As regras gerais descrevem telas maiores e `max-width` adapta telas menores:

```css
.hero-content {
  display: flex;
}

@media (max-width: 768px) {
  .hero-content {
    flex-direction: column;
  }
}
```

### Mobile-first

As regras gerais descrevem telas menores e `min-width` amplia o layout:

```css
.hero-content {
  display: flex;
  flex-direction: column;
}

@media (min-width: 769px) {
  .hero-content {
    flex-direction: row;
  }
}
```

As duas estratégias funcionam. O importante é adotar um padrão consistente no projeto.

## 9. Menu responsivo

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

@media (max-width: 600px) {
  .menu {
    flex-direction: column;
    align-items: center;
  }
}
```

## 10. Perfil responsivo

```css
.hero-content {
  display: flex;
  align-items: center;
  gap: 2rem;
}

.hero-image {
  flex-shrink: 0;
}

.hero-about {
  min-width: 0;
}

@media (max-width: 768px) {
  .hero-content {
    flex-direction: column;
    gap: 1rem;
    text-align: center;
  }
}
```

## 11. Evitando rolagem horizontal

Causas frequentes:

- largura fixa maior que a tela;
- `100vw` dentro de um container;
- imagem sem `max-width: 100%`;
- duas colunas de `50%` somadas a um `gap`;
- conteúdo longo que não pode quebrar;
- uso excessivo de `flex-shrink: 0`.

Para textos muito longos dentro de itens Flexbox:

```css
.conteudo {
  min-width: 0;
  overflow-wrap: anywhere;
}
```

Não utilize isto antes de identificar a causa:

```css
body {
  overflow-x: hidden;
}
```

Essa regra pode apenas esconder o problema.

## 12. Testes no DevTools

1. Abra o inspetor do navegador.
2. Ative o modo de simulação de dispositivos.
3. Arraste a largura lentamente.
4. Observe em que ponto o conteúdo perde legibilidade.
5. Verifique se alguma largura ultrapassa o container.
6. Confirme se a media query foi ativada.
7. Teste também alturas diferentes e zoom do navegador.

## 13. Checklist

- [ ] A página possui a meta tag de viewport?
- [ ] O container combina largura fluida e limite máximo?
- [ ] As imagens respeitam o elemento pai?
- [ ] O layout se adapta naturalmente antes das media queries?
- [ ] Os breakpoints foram escolhidos pelo conteúdo?
- [ ] Textos e botões continuam legíveis?
- [ ] Não existe rolagem horizontal indesejada?
- [ ] O layout funciona com zoom e tamanhos de fonte maiores?

## Resumo

```css
.container {
  width: 90%;
  max-width: 1200px;
  margin: 0 auto;
}

.conteudo {
  display: flex;
  flex-wrap: wrap;
  gap: 1.5rem;
}

@media (max-width: 768px) {
  .conteudo {
    flex-direction: column;
  }
}
```

Responsividade acontece em três etapas: permitir a adaptação natural, observar onde o conteúdo deixa de funcionar e aplicar uma mudança condicional somente nesse ponto.
