# Guia de depuração de CSS com DevTools

Este guia apresenta uma sequência de investigação para descobrir por que um estilo não foi aplicado, um elemento não está alinhado ou uma página apresenta transbordamento.

## 1. Abrindo o DevTools

Você pode abrir as ferramentas do navegador por meio de:

- clique com o botão direito e **Inspecionar**;
- `F12` em muitos sistemas;
- `Ctrl + Shift + I` no Windows e Linux;
- `Cmd + Option + I` no macOS.

Os nomes e posições dos painéis podem variar entre navegadores.

## 2. Painéis principais

| Painel | Finalidade |
| --- | --- |
| Elements | Inspecionar HTML e regras CSS. |
| Styles | Ver, ativar, alterar e testar declarações. |
| Computed | Consultar o valor final e o Box Model. |
| Layout | Investigar Flexbox e Grid. |
| Console | Observar erros e executar comandos. |
| Network | Verificar carregamento de CSS, imagens e outros arquivos. |

## 3. Selecionando o elemento correto

Use a ferramenta de seleção e clique no elemento visível. Depois confirme:

- nome da tag;
- classes e ID;
- posição no HTML;
- elemento pai;
- filhos diretos.

Um erro de layout frequentemente acontece porque a classe foi aplicada a um nível diferente do esperado.

## 4. Interpretando o painel Styles

O painel mostra todas as regras que atingem o elemento.

Uma propriedade riscada normalmente significa que:

- outra regra venceu pela cascata;
- outra regra possui maior especificidade;
- a mesma propriedade aparece depois;
- o valor não se aplica naquele contexto.

Clique na referência do arquivo para localizar a linha de origem.

## 5. Testando sem alterar o arquivo

No painel Styles, você pode:

- desmarcar uma declaração;
- alterar um valor;
- adicionar uma propriedade;
- testar outra unidade;
- modificar cores e espaçamentos.

Essas alterações são temporárias. Depois de descobrir a solução, faça a correção no arquivo CSS e recarregue a página.

## 6. Quando o Flexbox não funciona

Siga esta sequência:

1. Selecione o elemento pai.
2. Confirme `display: flex` em **Computed**.
3. Identifique os filhos diretos.
4. Verifique `flex-direction`.
5. Observe os eixos principal e transversal.
6. Teste `justify-content` e `align-items`.
7. Confira se `gap` foi aplicado ao pai.
8. Veja se algum filho possui largura ou margem conflitante.

Exemplo incompleto:

```css
.hero-section {
  flex-direction: row;
  align-items: center;
  gap: 2rem;
}
```

Correção:

```css
.hero-section {
  display: flex;
  flex-direction: row;
  align-items: center;
  gap: 2rem;
}
```

## 7. Inspecionando o Box Model

No painel **Computed**, observe:

- conteúdo;
- padding;
- borda;
- margem;
- largura e altura finais.

Se uma caixa com `width: 300px` aparece maior, verifique `box-sizing`, padding e borda.

```css
*,
*::before,
*::after {
  box-sizing: border-box;
}
```

## 8. Descobrindo qual regra venceu

Considere:

```css
p {
  color: blue;
}

.descricao {
  color: green;
}
```

```html
<p class="descricao">Texto</p>
```

A classe possui maior especificidade e o texto fica verde. O painel Styles mostrará `color: blue` riscado.

Quando duas regras têm a mesma especificidade, a última normalmente vence.

## 9. Verificando media queries

Reduza a largura da janela ou utilize o modo responsivo. No painel Styles, confirme se a regra apareceu:

```css
@media (max-width: 768px) {
  .hero-content {
    flex-direction: column;
  }
}
```

Se não aparecer, verifique:

- largura simulada;
- sintaxe da media query;
- fechamento das chaves;
- existência da meta tag de viewport;
- se outra regra posterior está sobrescrevendo o valor.

## 10. Encontrando rolagem horizontal

Possíveis causas:

- elemento com largura fixa;
- `width: 100vw` dentro de um container;
- imagem maior que o pai;
- margem externa excessiva;
- texto longo sem quebra;
- largura percentual somada a `gap` e padding.

Selecione os elementos próximos da borda direita e observe suas dimensões. Uma regra temporária também pode ajudar:

```css
* {
  outline: 1px solid rgba(255, 0, 0, 0.25);
}
```

Remova essa regra após o diagnóstico. Não esconda o problema imediatamente com `overflow-x: hidden`.

## 11. Imagem não carregada

Verifique:

1. o atributo `src`;
2. letras maiúsculas e minúsculas no nome;
3. caminho relativo ao arquivo HTML;
4. extensão correta;
5. erros no Console;
6. resposta da imagem no painel Network.

```html
<img src="./img/perfil/profile.jpeg" alt="Foto de perfil">
```

O servidor do GitHub Pages diferencia maiúsculas de minúsculas, mesmo quando o sistema local pode não diferenciar.

## 12. Imagem deformada ou cortada

Inspecione `width`, `height`, `object-fit` e `object-position`:

```css
.card img {
  display: block;
  width: 100%;
  height: 220px;
  object-fit: cover;
  object-position: center top;
}
```

- deformada: provavelmente falta `object-fit` ou `height: auto`;
- cortada: `cover` está preenchendo uma área com proporção diferente;
- foco incorreto: ajuste `object-position`.

## 13. CSS não carregado

Confira o `link`:

```html
<link rel="stylesheet" href="./css/global.css">
```

Depois:

- abra Network;
- recarregue a página;
- filtre por CSS;
- verifique se houve erro `404`;
- abra o arquivo recebido e confirme se é a versão atual.

## 14. Cache e atualização

Se o arquivo foi alterado, mas a página parece antiga:

- salve o arquivo;
- confirme se editou o arquivo correto;
- recarregue ignorando o cache;
- com o DevTools aberto, desative temporariamente o cache no painel Network.

Não conclua que há cache antes de verificar caminho e arquivo carregado.

## 15. Estados de interação

O painel Styles permite forçar estados como:

- `:hover`;
- `:focus`;
- `:focus-visible`;
- `:active`.

Isso permite testar links e botões sem manter o mouse parado sobre o elemento.

## 16. Sequência de diagnóstico

Quando algo quebrar:

1. **Observe:** descreva exatamente o comportamento incorreto.
2. **Inspecione:** selecione o elemento e confira regras e dimensões.
3. **Isole:** desative declarações até localizar a causa.
4. **Altere:** teste uma propriedade por vez.
5. **Registre:** faça a correção no arquivo CSS.
6. **Teste:** redimensione e recarregue novamente.

Evite alterar várias propriedades simultaneamente, pois isso dificulta entender qual delas resolveu o problema.

## 17. Perguntas úteis

- A classe aparece no HTML?
- O arquivo CSS foi carregado?
- A propriedade está riscada?
- Existe um erro de sintaxe antes dessa regra?
- O elemento correto possui `display: flex`?
- Estou estilizando o pai ou o filho?
- Qual é o tamanho final no Box Model?
- A media query está ativa?
- Qual elemento está causando o overflow?
- O problema continua depois de recarregar?

## 18. Checklist final

- [ ] O elemento correto foi selecionado?
- [ ] A classe esperada está presente?
- [ ] O CSS correto foi carregado?
- [ ] A declaração está válida e não foi sobrescrita?
- [ ] O valor final foi confirmado em Computed?
- [ ] O Box Model foi conferido?
- [ ] O pai e os filhos do Flexbox foram identificados?
- [ ] A media query está ativa na largura esperada?
- [ ] A causa da rolagem horizontal foi encontrada?
- [ ] A correção foi transferida do DevTools para o arquivo?

## Resumo

DevTools não serve apenas para modificar estilos rapidamente. Ele permite descobrir:

- qual elemento está sendo estilizado;
- quais regras chegaram até ele;
- qual declaração venceu;
- qual é o tamanho final da caixa;
- como o layout reage a diferentes larguras.

A sequência mais importante é:

```text
observar → inspecionar → isolar → alterar → testar
```

O objetivo da depuração não é encontrar uma propriedade por tentativa, mas compreender a causa do comportamento apresentado.
