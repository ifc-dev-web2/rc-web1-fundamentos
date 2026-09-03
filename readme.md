# Desenvolvimento Web I — Fundamentos

Repositório acadêmico da disciplina **Desenvolvimento Web I**, ofertada para o curso de **Tecnologia em Redes de Computadores** do **Instituto Federal Catarinense — Campus Araquari**.

Este espaço reúne exemplos, materiais, atividades, projetos e registros utilizados durante as aulas. O conteúdo acompanha a evolução da turma desde os fundamentos de HTML e CSS até a introdução à programação com JavaScript.

## Identificação da disciplina

| Informação                         | Descrição                                                      |
| ---------------------------------- | -------------------------------------------------------------- |
| **Curso**                          | Tecnologia em Redes de Computadores                            |
| **Disciplina**                     | Desenvolvimento Web I                                          |
| **Carga horária**                  | 60 horas                                                       |
| **Tecnologias**                    | HTML, CSS, JavaScript e introdução a Web Components            |
| **Dia e horário das aulas**        | Sexta-feira, das 19h às 22h30                                  |
| **Professor**                      | [Cristofer Sousa](https://www.linkedin.com/in/cristofersousa/) |
| **Plantão de dúvidas/atendimento** | Sexta-feira, das 18h às 19h                                    |
| **Instituição**                    | Instituto Federal Catarinense — Campus Araquari                |

> O atendimento deve ser previamente combinado com o professor, especialmente quando houver necessidade de acompanhamento individual ou revisão de atividades.

## Sumário

- [Proposta da disciplina](#proposta-da-disciplina)
- [Importância para Redes de Computadores](#importância-para-redes-de-computadores)
- [Benefícios e desafios para o estudante](#benefícios-e-desafios-para-o-estudante)
- [Objetivos de aprendizagem](#objetivos-de-aprendizagem)
- [Conteúdos abordados](#conteúdos-abordados)
- [Metodologia](#metodologia)
- [Projeto orientador](#projeto-orientador)
- [Avaliação da aprendizagem](#avaliação-da-aprendizagem)
- [Cronograma](#cronograma)
- [Uso de Inteligência Artificial](#uso-de-inteligência-artificial)
- [Como utilizar este repositório](#como-utilizar-este-repositório)
- [Orientações para as entregas](#orientações-para-as-entregas)
- [Referências](#referências)

## Proposta da disciplina

A disciplina apresenta os fundamentos necessários para compreender como páginas e aplicações Web são estruturadas, estilizadas e executadas no navegador.

Mais do que reproduzir interfaces, a proposta é permitir que o estudante compreenda o caminho percorrido entre uma requisição realizada pelo navegador e a apresentação de uma página ao usuário. Para isso, serão estudados:

- A estrutura de documentos com HTML;
- A organização visual e a adaptação de layouts com CSS;
- A criação de comportamentos e interações com JavaScript;
- A comunicação entre páginas, navegadores, servidores e serviços Web;
- A organização e o versionamento de projetos com Git e GitHub;
- A publicação de páginas para acesso pela internet;
- A introdução ao desenvolvimento baseado em componentes.

As aulas combinam explicação conceitual, demonstração, desenvolvimento orientado, exercícios, análise de erros e evolução progressiva de projetos.

## Importância para Redes de Computadores

O funcionamento da Web está diretamente relacionado aos conhecimentos desenvolvidos no curso de Redes de Computadores. Ao acessar uma página, diferentes tecnologias e serviços participam do processo: navegador, DNS, protocolos HTTP e HTTPS, servidor Web, endereço IP, portas, certificados, arquivos estáticos, APIs e mecanismos de segurança.

Compreender desenvolvimento Web ajuda o profissional de Redes a:

- Entender o modelo cliente-servidor na prática;
- Interpretar requisições e respostas HTTP;
- Configurar e administrar servidores Web;
- Publicar páginas, painéis e serviços internos;
- Criar interfaces para ferramentas de infraestrutura;
- Consumir e testar APIs;
- Identificar problemas de conectividade entre navegador e servidor;
- Analisar cabeçalhos, códigos de resposta e tráfego Web;
- Compreender certificados, HTTPS e políticas de segurança;
- Dialogar com equipes de desenvolvimento, infraestrutura, segurança e suporte;
- Automatizar ou apresentar informações coletadas de dispositivos e serviços de rede.

Um profissional de Redes não precisa necessariamente atuar como desenvolvedor de interfaces. Entretanto, conhecer os fundamentos da Web amplia sua autonomia e sua capacidade de investigar, integrar, documentar e entregar soluções.

## Benefícios e desafios para o estudante

### Benefícios

| Benefício              | Relação com a formação                                                                 |
| ---------------------- | -------------------------------------------------------------------------------------- |
| Compreensão da Web     | Permite visualizar como navegador, protocolos e servidores trabalham em conjunto       |
| Maior autonomia        | Ajuda na criação de páginas, painéis administrativos e ferramentas internas            |
| Integração com APIs    | Facilita o consumo e a apresentação de dados de serviços e equipamentos                |
| Diagnóstico técnico    | Melhora a capacidade de identificar falhas na aplicação, no servidor ou na comunicação |
| Visão interdisciplinar | Aproxima desenvolvimento, infraestrutura, segurança e experiência do usuário           |
| Portfólio profissional | Possibilita publicar projetos que demonstrem conhecimentos técnicos                    |
| Trabalho em equipe     | Melhora a comunicação com profissionais de outras áreas da tecnologia                  |

### Desafios

| Desafio                                | Como será trabalhado                                                         |
| -------------------------------------- | ---------------------------------------------------------------------------- |
| Aprender diferentes linguagens         | Os conteúdos serão apresentados progressivamente, com aplicação prática      |
| Organizar arquivos e responsabilidades | Serão adotados padrões simples de pastas, nomes e separação de estilos       |
| Relacionar teoria e prática            | Cada conceito será utilizado na construção ou evolução de uma página         |
| Identificar erros                      | Serão utilizados console, DevTools, leitura de mensagens e testes orientados |
| Desenvolver autonomia                  | O estudante deverá explicar, modificar e corrigir o código que entregar      |
| Evitar dependência de código pronto    | Exemplos externos e ferramentas de IA deverão ser analisados e compreendidos |

O principal desafio é não tratar HTML, CSS e JavaScript apenas como comandos que precisam ser copiados. O estudante precisa compreender o papel de cada tecnologia e as consequências das decisões adotadas.

## Objetivos de aprendizagem

Ao final da disciplina, espera-se que o estudante seja capaz de:

- Explicar o funcionamento básico da Web e do modelo cliente-servidor;
- Criar documentos HTML bem estruturados;
- Utilizar elementos semânticos de acordo com a finalidade do conteúdo;
- Criar navegação entre diferentes páginas;
- Organizar formulários e seus campos;
- Aplicar estilos utilizando seletores, classes e propriedades CSS;
- Compreender box model, fluxo dos elementos e tipos de `display`;
- Criar layouts com Flexbox;
- Utilizar medidas absolutas e relativas;
- Adaptar páginas para diferentes tamanhos de tela;
- Escrever comandos básicos em JavaScript;
- Utilizar variáveis, operadores, condicionais, funções e arrays;
- Selecionar e modificar elementos com o DOM;
- Responder a eventos realizados pelo usuário;
- Integrar JavaScript a formulários HTML;
- Organizar e versionar projetos com Git e GitHub;
- Documentar projetos por meio de um arquivo `README.md`;
- Publicar páginas utilizando o GitHub Pages;
- Ler, testar, explicar e corrigir o próprio código.

## Conteúdos abordados

### Fundamentos da Web

- Internet e Web;
- Modelo cliente-servidor;
- Navegadores e servidores Web;
- Endereços, URLs e recursos;
- Introdução aos protocolos HTTP e HTTPS;
- Ferramentas de desenvolvimento do navegador.

### HTML

- Estrutura básica de um documento;
- Títulos, parágrafos, listas e links;
- Imagens e caminhos de arquivos;
- Elementos em bloco e inline;
- Elementos `div` e `span`;
- Semântica com `header`, `nav`, `main`, `section`, `article` e `footer`;
- Elementos `figure`, `figcaption` e `time`;
- Formulários, campos, rótulos, botões e validações nativas;
- Acessibilidade básica.

### CSS

- Seletores, classes e propriedades;
- Cascata, herança e especificidade;
- CSS Reset;
- Estilos globais e específicos;
- Cores, tipografia, bordas e espaçamentos;
- Box model e `box-sizing`;
- Elementos em bloco e inline;
- Flexbox, eixos, alinhamento, quebra e espaçamento;
- Medidas `px`, `%`, `em`, `rem`, `vw` e `vh`;
- Containers fluidos, `max-width` e `margin: 0 auto`;
- Imagens responsivas e propriedade `object-fit`;
- Viewport, breakpoints e media queries;
- Identificação e correção de overflow.

### JavaScript

- Inclusão de scripts;
- Console do navegador;
- Variáveis com `let` e `const`;
- Tipos de dados;
- Operadores aritméticos, relacionais e lógicos;
- Estruturas condicionais;
- Funções, parâmetros e retorno;
- Arrays e métodos básicos;
- Introdução ao DOM;
- Seleção e alteração de elementos;
- Eventos;
- Captura e validação básica de formulários.

### Web Components

- Motivação para a criação de componentes reutilizáveis;
- Separação de responsabilidades;
- Introdução a Custom Elements;
- Relação entre HTML, CSS, JavaScript e componentes.

> Web Components serão apresentados de maneira introdutória, de acordo com o desenvolvimento da turma e a disponibilidade do cronograma.

### Git e publicação

- Repositório local e remoto;
- Alterações, commits e histórico;
- Envio do código para o GitHub;
- Organização do repositório;
- Documentação com Markdown;
- Publicação pelo GitHub Pages.

## Metodologia

A disciplina será desenvolvida por meio de:

- Aulas expositivas dialogadas;
- Demonstrações realizadas pelo professor;
- Desenvolvimento de código em conjunto com a turma;
- Exercícios de acompanhamento;
- Atividades práticas individuais;
- Análise e correção de erros;
- Evolução progressiva de projetos;
- Revisão e refatoração de código;
- Utilização do Git e do GitHub;
- Apresentação e explicação das soluções desenvolvidas.

O erro será tratado como parte do processo de aprendizagem. O estudante será incentivado a observar o comportamento da aplicação, interpretar mensagens, formular hipóteses, testar alterações e registrar o processo realizado.

## Projeto orientador

Durante o primeiro ciclo, os conteúdos serão demonstrados por meio da construção progressiva de um **Portal de Notícias**.

O projeto parte de uma página pessoal e evolui para um pequeno portal com páginas interligadas, conteúdo semântico, imagens, categorias, formulários, Flexbox e responsividade.

O portal funciona como exemplo orientado. Para o trabalho individual N2, cada estudante desenvolverá um projeto próprio de **tema livre**, aplicando os conhecimentos construídos durante as aulas.

## Avaliação da aprendizagem

A avaliação será contínua, diagnóstica, formativa e somativa, considerando o desenvolvimento do estudante ao longo da disciplina.

### Instrumentos avaliativos

| Instrumento                          | Data prevista | Descrição                                                                              |
| ------------------------------------ | :-----------: | -------------------------------------------------------------------------------------- |
| **N1 — Avaliação individual**        |  02/10/2026   | Avaliação teórica e/ou prática envolvendo os conteúdos desenvolvidos no primeiro ciclo |
| **N2 — Trabalho prático individual** |  16/10/2026   | Entrega e apresentação de um projeto Web individual de tema livre                      |
| **Recuperação semestral**            |  11/12/2026   | Atividade individual teórica e/ou prática sobre os objetivos essenciais da disciplina  |

Os exercícios realizados durante as aulas terão caráter diagnóstico e formativo. Eles permitirão acompanhar a aprendizagem, identificar dificuldades e orientar a retomada dos conteúdos, ainda que não constituam necessariamente instrumentos com atribuição de nota.

### Critérios considerados

- Desenvolvimento das atividades propostas;
- Compreensão e aplicação dos conceitos;
- Organização semântica do HTML;
- Organização e qualidade do CSS;
- Funcionamento da solução;
- Responsividade e acessibilidade básica;
- Capacidade de identificar e corrigir problemas;
- Organização dos arquivos e diretórios;
- Evolução do projeto;
- Uso adequado do Git e do GitHub;
- Documentação no `README.md`;
- Cumprimento dos requisitos e prazos;
- Compreensão demonstrada durante a apresentação.

### N2 — Projeto individual de tema livre

Cada estudante deverá desenvolver e apresentar um projeto Web individual relacionado a um tema de sua escolha.

O projeto deverá demonstrar a aplicação dos conhecimentos do primeiro ciclo, incluindo HTML semântico, CSS, Flexbox, responsividade, formulário, organização dos arquivos, versionamento, documentação e publicação no GitHub Pages.

Durante a apresentação, o estudante deverá:

- Explicar o tema e o objetivo do projeto;
- Demonstrar suas páginas e recursos;
- Justificar as principais decisões técnicas;
- Relatar as dificuldades encontradas;
- Explicar as soluções adotadas;
- Responder a perguntas sobre o código;
- Realizar pequenas alterações, quando solicitado.

A avaliação considerará o resultado final e a compreensão individual demonstrada.

## Cronograma

O cronograma poderá receber ajustes de acordo com o calendário acadêmico, o desenvolvimento da turma e as necessidades identificadas durante as aulas.

| Aula |    Data    | Conteúdo previsto                                                                                                                            |    Status    |
| :--: | :--------: | -------------------------------------------------------------------------------------------------------------------------------------------- | :----------: |
|  —   | 07/08/2026 | Recesso acadêmico                                                                                                                            | ✅ Concluído |
|  1   | 14/08/2026 | Apresentação da disciplina, diagnóstico, introdução à Web, estrutura básica do HTML, CSS inicial, Git, GitHub e publicação pelo GitHub Pages | ✅ Concluído |
|  2   | 21/08/2026 | HTML semântico, estrutura de conteúdo, páginas, menu de navegação, links internos, imagens, legendas e datas                                 | ✅ Concluído |
|  3   | 28/08/2026 | Elementos em bloco e inline, `div`, `span`, Flexbox, medidas, containers, imagens adaptáveis e página de Hobbies                             | ✅ Concluído |
|  4   | 04/09/2026 | Responsividade, viewport, breakpoints, media queries e adaptação do portal para diferentes tamanhos de tela                                  | ⏳ Pendente  |
|  5   | 11/09/2026 | Prática orientada de responsividade, correção do portal, adaptação do menu, perfil, cartões e imagens e utilização do DevTools               | ⏳ Pendente  |
|  6   | 18/09/2026 | Formulários HTML, tipos de campos, rótulos, botões, atributos e validações nativas                                                           | ⏳ Pendente  |
|  7   | 25/09/2026 | Revisão de HTML, CSS, formulários, Flexbox, medidas, responsividade, organização e publicação Web                                            | ⏳ Pendente  |
|  8   | 02/10/2026 | **N1 — Avaliação individual de HTML e CSS**                                                                                                  | ⏳ Pendente  |
|  9   | 09/10/2026 | Correção comentada da N1, retomada dos conteúdos e atividade prática de reforço                                                              | ⏳ Pendente  |
|  10  | 16/10/2026 | **N2 — Entrega e apresentação do projeto Web individual de tema livre**                                                                      | ⏳ Pendente  |
|  11  | 23/10/2026 | Devolutiva dos projetos, correção orientada e aperfeiçoamento das soluções                                                                   | ⏳ Pendente  |
|  12  | 30/10/2026 | Finalização do primeiro ciclo, revisão dos projetos, resultados e preparação para JavaScript                                                 | ⏳ Pendente  |
|  13  | 06/11/2026 | Introdução ao JavaScript, scripts, console, variáveis e primeiros comandos                                                                   | ⏳ Pendente  |
|  14  | 13/11/2026 | Tipos de dados, operadores, comparações, conversões e estruturas condicionais                                                                | ⏳ Pendente  |
|  —   | 20/11/2026 | Feriado Nacional — Dia da Consciência Negra                                                                                                  |  📅 Feriado  |
|  15  | 27/11/2026 | Funções, parâmetros, retorno, arrays, métodos básicos, organização do código e introdução ao DOM                                             | ⏳ Pendente  |
|  16  | 04/12/2026 | DOM, eventos, formulários com JavaScript, integração, revisão e encerramento das atividades regulares                                        | ⏳ Pendente  |
|  17  | 11/12/2026 | **Recuperação semestral da aprendizagem**                                                                                                    | ⏳ Pendente  |

### Legenda do cronograma

| Símbolo | Situação                    |
| :-----: | --------------------------- |
|   ✅    | Concluído                   |
|   🚧    | Em andamento                |
|   ⏳    | Pendente                    |
|   📅    | Feriado ou evento acadêmico |

## Uso de Inteligência Artificial

Ferramentas de Inteligência Artificial podem ser utilizadas como apoio à aprendizagem, mas não substituem o estudo dos fundamentos nem a responsabilidade do estudante sobre o código entregue.

O objetivo da disciplina não é apenas produzir uma página que aparente funcionar. O estudante deve compreender:

- O problema que está resolvendo;
- A estrutura do código utilizado;
- A função dos elementos, propriedades e comandos;
- As decisões tomadas durante o desenvolvimento;
- Os erros encontrados e as soluções adotadas;
- Os impactos das alterações realizadas;
- As limitações e os possíveis erros das respostas produzidas por IA.

### Vibe coding e fundamentos

**Vibe coding**, ou programação por vibração, é uma forma de desenvolvimento na qual a pessoa descreve em linguagem natural o que deseja construir e utiliza uma Inteligência Artificial para gerar parte significativa da aplicação, concentrando-se no resultado final, sem necessariamente escrever ou compreender o código linha por linha.

Essa abordagem pode acelerar experimentações e protótipos. Entretanto, quando utilizada sem conhecimento técnico, pode produzir uma falsa sensação de domínio.

Um projeto funcionar visualmente não significa que esteja correto, seguro, organizado, acessível ou preparado para manutenção. Sem domínio dos fundamentos, o estudante poderá apresentar dificuldades para:

- Identificar por que determinado código funciona;
- Corrigir situações não previstas pela IA;
- Avaliar se a solução atende aos requisitos;
- Reconhecer problemas de semântica, acessibilidade e responsividade;
- Identificar vulnerabilidades ou comportamentos inseguros;
- Modificar funcionalidades sem comprometer outras partes;
- Trabalhar com sistemas existentes e códigos legados;
- Participar de revisões técnicas;
- Explicar e defender suas decisões.

> A Inteligência Artificial pode sugerir o código, mas a responsabilidade pela solução permanece com quem a utiliza.

### Utilização permitida como apoio

A IA poderá ser utilizada para:

- Esclarecer conceitos estudados;
- Solicitar exemplos adicionais;
- Comparar soluções;
- Interpretar mensagens de erro;
- Revisar organização e legibilidade;
- Sugerir melhorias para uma solução inicial;
- Apoiar a documentação;
- Auxiliar pesquisas que posteriormente sejam verificadas.

Toda sugestão deverá ser lida, testada e validada pelo estudante.

### Compreensão e autoria

Durante atividades, projetos e avaliações, o estudante deverá conseguir explicar e modificar o código apresentado. Poderão ser feitas perguntas sobre a função de elementos, propriedades, comandos e decisões utilizadas.

Caso não consiga explicar, adaptar ou corrigir o código entregue, o trabalho poderá não demonstrar adequadamente a aprendizagem esperada, mesmo que o resultado visual esteja funcionando.

### Uso inadequado

Será considerado inadequado:

- Entregar código gerado sem leitura ou compreensão;
- Apresentar como autoral uma solução que não consegue explicar;
- Utilizar conteúdos desconhecidos sem investigar seu funcionamento;
- Solicitar que uma IA realize integralmente uma avaliação individual;
- Copiar respostas sem testar;
- Utilizar a ferramenta para contornar os objetivos de aprendizagem;
- Ocultar seu uso quando a declaração for solicitada.

### Declaração de uso de IA

Quando solicitado, o estudante deverá registrar no `README.md` do projeto:

```markdown
## Uso de Inteligência Artificial

**Ferramenta utilizada:** nome da ferramenta.

**Finalidade:** descreva para que a ferramenta foi utilizada.

**Partes do projeto que receberam auxílio:** informe os arquivos,
páginas ou funcionalidades relacionadas.

**Validação realizada:** explique como o conteúdo foi analisado,
testado e corrigido.

Declaro que revisei o conteúdo gerado e consigo explicar as soluções
incorporadas ao projeto.
```

O princípio adotado na disciplina será:

> Primeiro compreender os fundamentos; depois utilizar a Inteligência Artificial para ampliar a produtividade.


## Como utilizar este repositório

Cada estudante deverá criar uma cópia deste repositório em sua própria conta do GitHub por meio de um **fork**. Depois disso, deverá clonar o próprio fork para o computador.

### 1. Criar o fork

1. Acesse o repositório da disciplina: [ifc-dev-web2/rc-web1-fundamentos](https://github.com/ifc-dev-web2/rc-web1-fundamentos);
2. Clique no botão **Fork**, localizado na parte superior da página;
3. Selecione sua conta pessoal como destino;
4. Mantenha o nome `rc-web1-fundamentos`, salvo orientação diferente do professor;
5. Confirme a criação do fork.

Ao concluir, o estudante terá em sua conta um repositório semelhante a:

```text
https://github.com/seu-usuario/rc-web1-fundamentos
```

### 2. Clonar o próprio fork

No repositório criado em sua conta, clique em **Code** e copie o endereço HTTPS. Em seguida, execute:

```bash
git clone https://github.com/seu-usuario/rc-web1-fundamentos.git
```

> Substitua `seu-usuario` pelo seu nome de usuário no GitHub. O endereço utilizado no clone deve apontar para o fork do estudante, e não para o repositório original da disciplina.

### 3. Acessar o diretório

```bash
cd rc-web1-fundamentos
```

### 4. Abrir no Visual Studio Code

```bash
code .
```

### 5. Conferir o repositório remoto

Para verificar para qual repositório as alterações serão enviadas:

```bash
git remote -v
```

O endereço de `origin` deverá apontar para a conta do estudante:

```text
https://github.com/seu-usuario/rc-web1-fundamentos.git
```

### 6. Registrar e enviar as alterações

Depois de realizar uma atividade, verifique, registre e envie as mudanças:

```bash
git status
git add .
git commit -m "Adiciona atividade da aula"
git push origin main
```

A mensagem do commit deverá descrever de maneira breve e objetiva a alteração realizada.


## 🧹 Padronização e formatação do código

A partir deste projeto, utilizaremos uma configuração compartilhada de
formatação para manter o código organizado e consistente entre todos os
participantes.

As regras do projeto definem:

- indentação com dois espaços;
- utilização de espaços em vez de tabulações;
- formatação automática com Prettier;
- largura preferencial de 80 caracteres;
- atributos HTML organizados em linhas separadas;
- visualização de espaços e níveis de indentação;
- padronização das quebras de linha;
- extensões recomendadas para o VS Code.

Ao abrir o projeto, verifique as extensões recomendadas pelo editor e instale-as
antes de iniciar o desenvolvimento.

> As configurações pessoais do editor podem continuar sendo utilizadas para
> aspectos visuais. Entretanto, as regras de formatação versionadas no
> repositório devem ser respeitadas por todos.

Para compreender a configuração, a função de cada arquivo e o fluxo de
desenvolvimento adotado, consulte:

📖 [Guia de padronização do código](./docs/guia-padronizacao-codigo.md)
---

### Repositório original e fork

| Repositório                        | Responsabilidade                                                                      |
| ---------------------------------- | ------------------------------------------------------------------------------------- |
| Repositório original da disciplina | Disponibiliza materiais, exemplos, orientações e atualizações mantidas pelo professor |
| Fork do estudante                  | Armazena as atividades e modificações realizadas individualmente                      |

O estudante deve confirmar, antes de iniciar uma atividade, que está trabalhando no fork de sua própria conta.

Durante a disciplina, consulte as pastas e os arquivos indicados pelo professor para cada aula. Os exemplos são materiais de estudo e devem ser lidos, executados, modificados e testados.


## Estrutura do Projeto

```text
portal-noticias/
├── .vscode/
│   ├── extensions.json
│   └── settings.json
│
├── css/
│   ├── global.css
│   ├── hobbies.css
│   └── perfil.css
│
├── docs/
│   ├── aulas/
│   │   ├── 01-index.md
│   │   └── 02-hobbies.md
│   └── guia-padronizacao-codigo.md
│
├── img/
│
├── .editorconfig
├── .gitignore
├── .prettierignore
├── .prettierrc.json
├── hobbies.html
├── index.html
├── perfil.html
├── LICENSE
└── README.md
```

---

## Orientações para as entregas

Antes de entregar uma atividade ou projeto, verifique:

- [ ] O repositório está acessível;
- [ ] Os arquivos estão organizados;
- [ ] O menu e os links funcionam;
- [ ] As imagens foram incluídas no repositório;
- [ ] Os caminhos dos arquivos estão corretos;
- [ ] O HTML possui organização semântica;
- [ ] O CSS está separado e organizado;
- [ ] A página se adapta a diferentes larguras;
- [ ] O formulário possui rótulos e campos adequados;
- [ ] O código foi testado no navegador;
- [ ] As alterações foram registradas em commits;
- [ ] O `README.md` explica o projeto;
- [ ] O GitHub Pages está atualizado, quando solicitado;
- [ ] O uso de IA foi declarado, quando aplicável;
- [ ] O estudante consegue explicar o código entregue.

## Conduta acadêmica

Espera-se que todas as atividades sejam realizadas com responsabilidade, respeito e transparência.

O compartilhamento de conhecimento e a colaboração são incentivados durante as práticas. Entretanto, avaliações e trabalhos definidos como individuais deverão representar a aprendizagem e a autoria de cada estudante.

Plágio, cópia integral de projetos, falsificação de autoria ou entrega de código que o estudante não consiga explicar poderão ser considerados incompatíveis com os objetivos da atividade.

## Referências

- [MDN Web Docs](https://developer.mozilla.org/pt-BR/);
- [WHATWG — HTML Living Standard](https://html.spec.whatwg.org/);
- [W3C — Web Standards](https://www.w3.org/standards/);
- [JavaScript.info](https://javascript.info/);
- [Git — Documentação](https://git-scm.com/doc);
- [GitHub Docs](https://docs.github.com/pt).

---

## Licença e uso educacional

Este repositório possui finalidade educacional e foi desenvolvido como material de apoio para a disciplina de Desenvolvimento Web I.

Os estudantes poderão criar forks, estudar, modificar e adaptar os exemplos e projetos para fins de aprendizagem, construção de portfólio e desenvolvimento profissional.

Ao reutilizar este material, recomenda-se manter a referência ao projeto original e ao Instituto Federal Catarinense — Campus Araquari.

Os projetos individuais desenvolvidos pelos estudantes poderão receber suas próprias adaptações, identidades visuais e conteúdos, respeitando a autoria de materiais externos, imagens, bibliotecas e demais recursos utilizados.

Para informações sobre as permissões de uso, modificação e distribuição, consulte o arquivo [`LICENSE`](./LICENSE).

---

**Professor:** [Cristofer Sousa](https://www.linkedin.com/in/cristofersousa/)  
**Disciplina:** Desenvolvimento Web I  
**Curso:** Tecnologia em Redes de Computadores  
**Instituição:** Instituto Federal Catarinense — Campus Araquari
