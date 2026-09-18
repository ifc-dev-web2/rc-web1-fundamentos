# Guias de Desenvolvimento Web I

Este diretório reúne os guias complementares utilizados na disciplina de
**Desenvolvimento Web I**.

Os materiais foram organizados para auxiliar na revisão dos conceitos
apresentados em aula e servir como referência durante o desenvolvimento
das atividades e dos projetos.

> Os guias não substituem as explicações, demonstrações e atividades
> realizadas em sala. Utilize-os para revisar conceitos, consultar exemplos
> e esclarecer dúvidas durante o desenvolvimento.

## Sumário

- [Ambiente e padronização](#ambiente-e-padronização)
- [Fundamentos do CSS](#fundamentos-do-css)
- [Layout e responsividade](#layout-e-responsividade)
- [Imagens e tipografia](#imagens-e-tipografia)
- [Formulários HTML](#formulários-html)
- [Diagnóstico e correção de problemas](#diagnóstico-e-correção-de-problemas)
- [Ordem sugerida de leitura](#ordem-sugerida-de-leitura)
- [Como utilizar os guias](#como-utilizar-os-guias)
- [Retornar ao repositório](#retornar-ao-repositório)

## Ambiente e padronização

### [Padronização do ambiente e do código](./guia-padronizacao-codigo.md)

Apresenta os arquivos e as configurações utilizados para manter a
formatação do código consistente entre os projetos.

Conteúdos abordados:

- EditorConfig;
- Prettier;
- configurações do Visual Studio Code;
- extensões recomendadas;
- formatação automática;
- padronização do ambiente de desenvolvimento.

## Fundamentos do CSS

### [Fundamentos e organização do CSS](./guia-fundamentos-css.md)

Apresenta os conceitos fundamentais para escrever e organizar regras CSS.

Conteúdos abordados:

- anatomia de uma regra CSS;
- seletores de elementos e classes;
- cascata;
- herança;
- especificidade;
- pseudoclasses;
- pseudoelementos;
- variáveis CSS;
- organização dos estilos.

### [Box Model no CSS](./guia-box-model-css.md)

Explica como o navegador calcula o espaço ocupado por cada elemento da
página.

Conteúdos abordados:

- conteúdo;
- `padding`;
- borda;
- margem;
- largura e altura;
- `content-box`;
- `border-box`;
- propriedade `box-sizing`.

## Layout e responsividade

### [Flexbox no CSS](./guia-flexbox-css.md)

Apresenta o funcionamento do Flexbox e sua utilização na construção de
layouts.

Conteúdos abordados:

- contêiner e itens flexíveis;
- eixos principal e transversal;
- alinhamento;
- distribuição de espaço;
- espaçamento com `gap`;
- quebra de linha;
- crescimento e redução dos elementos;
- exemplos de layouts responsivos.

### [Layout responsivo no CSS](./guia-layout-responsivo-css.md)

Explica como adaptar uma página para diferentes tamanhos de tela.

Conteúdos abordados:

- layouts fixos, fluidos e responsivos;
- configuração da viewport;
- unidades de medida;
- contêineres flexíveis;
- `max-width`;
- breakpoints;
- media queries;
- identificação e prevenção de overflow.

## Imagens e tipografia

### [Imagens no HTML e CSS](./guia-imagens-html-css.md)

Apresenta boas práticas para inserir, organizar e adaptar imagens dentro
das páginas.

Conteúdos abordados:

- elemento `<img>`;
- atributo `alt`;
- caminhos relativos;
- imagens responsivas;
- proporção;
- `display: block`;
- `object-fit`;
- `object-position`;
- imagens de capa;
- avatares e imagens utilizadas em cartões.

### [Tipografia no CSS](./guia-tipografia-css.md)

Apresenta os principais conceitos relacionados à organização visual dos
textos.

Conteúdos abordados:

- tamanho da fonte;
- hierarquia visual;
- unidades `px` e `rem`;
- peso da fonte;
- altura da linha;
- espaçamento;
- legibilidade;
- criação de escalas tipográficas.

## Formulários HTML

### [Formulários HTML](./guia-formularios-html.md)

Apresenta os elementos, controles, atributos e validações utilizados na
criação de formulários para a Web.

Conteúdos abordados:

- elemento `<form>`;
- atributos `action`, `method` e `enctype`;
- diferenças entre os métodos `GET` e `POST`;
- associação entre `<label>` e os controles;
- atributos `for`, `id`, `name` e `value`;
- tipos de `<input>`;
- elementos `<textarea>`, `<select>` e `<option>`;
- controles `checkbox` e `radio`;
- botões de envio, limpeza e ação;
- atributos de validação nativa;
- preenchimento automático com `autocomplete`;
- envio de arquivos;
- organização com `<fieldset>` e `<legend>`;
- estados dos controles no CSS;
- acessibilidade em formulários;
- limites da validação realizada pelo navegador.

## Diagnóstico e correção de problemas

### [Depuração de CSS com DevTools](./guia-devtools-css.md)

Apresenta uma sequência de investigação para identificar e corrigir
problemas de layout e estilização utilizando as ferramentas do navegador.

Conteúdos abordados:

- abertura do DevTools;
- seleção e inspeção de elementos;
- identificação das regras aplicadas;
- Box Model;
- Flexbox;
- dimensões e espaçamentos;
- imagens;
- responsividade;
- overflow;
- teste temporário de propriedades CSS.

## Ordem sugerida de leitura

Para acompanhar a progressão dos conteúdos, recomenda-se a seguinte ordem:

1. [Padronização do ambiente e do código](./guia-padronizacao-codigo.md);
2. [Fundamentos e organização do CSS](./guia-fundamentos-css.md);
3. [Box Model no CSS](./guia-box-model-css.md);
4. [Tipografia no CSS](./guia-tipografia-css.md);
5. [Imagens no HTML e CSS](./guia-imagens-html-css.md);
6. [Flexbox no CSS](./guia-flexbox-css.md);
7. [Layout responsivo no CSS](./guia-layout-responsivo-css.md);
8. [Depuração de CSS com DevTools](./guia-devtools-css.md);
9. [Formulários HTML](./guia-formularios-html.md).

Essa sequência acompanha a progressão dos conteúdos trabalhados na
disciplina. Os guias também podem ser consultados individualmente,
conforme as necessidades encontradas durante o desenvolvimento.

## Como utilizar os guias

Ao consultar um material:

1. leia a explicação do conceito;
2. observe os exemplos apresentados;
3. reproduza os exemplos no próprio projeto;
4. altere valores e propriedades para observar os resultados;
5. utilize o DevTools para investigar o comportamento dos elementos;
6. registre e envie as mudanças realizadas no repositório.

Evite apenas copiar os exemplos. Procure compreender a função de cada
elemento, atributo e propriedade antes de incorporá-los ao projeto.

## Retornar ao repositório

- [Voltar ao README principal](../../README.md);
- [Consultar os materiais das aulas](../aulas/).
