# Guia de padronização do código

Este documento apresenta as configurações utilizadas no template de projetos
HTML e CSS do curso técnico.

## Por que padronizar o código?

Cada pessoa pode configurar seu editor de acordo com suas preferências.
Entretanto, em projetos desenvolvidos por várias pessoas, essas diferenças
podem causar inconsistências.

Algumas pessoas podem utilizar:

* dois ou quatro espaços para indentação;
* espaços ou caracteres de tabulação;
* aspas simples ou duplas;
* diferentes formas de organizar atributos HTML;
* diferentes padrões de quebra de linha;
* espaços desnecessários ao final das linhas.

Embora algumas dessas diferenças não alterem o funcionamento da página, elas
podem fazer o Git interpretar a reformatação como uma grande alteração no
arquivo.

Isso pode provocar:

* alterações desnecessárias no histórico;
* dificuldade para identificar o que realmente mudou;
* conflitos durante o `merge`;
* revisões de código mais demoradas;
* arquivos com estilos diferentes;
* dependência das configurações pessoais de cada computador.

Por isso, as principais regras de formatação estão armazenadas no próprio
repositório.

> A configuração pessoal prepara o editor do desenvolvedor. As configurações do
> repositório determinam o padrão que deve ser utilizado no projeto.

## Arquivos de configuração

O template possui os seguintes arquivos:

```text
.
├── .vscode/
│   ├── extensions.json
│   └── settings.json
├── .editorconfig
├── .prettierignore
├── .prettierrc.json
└── .gitignore
```

Cada arquivo possui uma responsabilidade.

| Arquivo                   | Responsabilidade                              |
| ------------------------- | --------------------------------------------- |
| `.editorconfig`           | Define regras básicas dos arquivos            |
| `.prettierrc.json`        | Define como o Prettier formata o código       |
| `.prettierignore`         | Informa o que não deve ser formatado          |
| `.vscode/settings.json`   | Configura o VS Code para o projeto            |
| `.vscode/extensions.json` | Recomenda as extensões necessárias            |
| `.gitignore`              | Define arquivos que não devem ser versionados |

Esses arquivos devem permanecer versionados para que as configurações
acompanhem o projeto.

## EditorConfig

O EditorConfig define regras básicas que podem ser reconhecidas por diferentes
editores de código.

As configurações estão no arquivo:

```text
.editorconfig
```

Conteúdo utilizado:

```ini
root = true

[*]
charset = utf-8
end_of_line = lf
insert_final_newline = true
indent_style = space
indent_size = 2
trim_trailing_whitespace = true
max_line_length = 80

[*.md]
trim_trailing_whitespace = false
```

### Explicação das regras

| Propriedade                       | Finalidade                                            |
| --------------------------------- | ----------------------------------------------------- |
| `root = true`                     | Indica que este é o arquivo principal de configuração |
| `charset = utf-8`                 | Define a codificação utilizada nos arquivos           |
| `end_of_line = lf`                | Padroniza as quebras de linha                         |
| `insert_final_newline = true`     | Adiciona uma linha ao final do arquivo                |
| `indent_style = space`            | Utiliza espaços em vez de tabulações                  |
| `indent_size = 2`                 | Define dois espaços para cada indentação              |
| `trim_trailing_whitespace = true` | Remove espaços desnecessários                         |
| `max_line_length = 80`            | Indica a largura recomendada das linhas               |

A propriedade `max_line_length` não bloqueia a digitação depois da coluna 80.
Ela funciona como uma orientação para as ferramentas compatíveis.

Nos arquivos Markdown, a remoção automática de espaços ao final das linhas é
desabilitada:

```ini
[*.md]
trim_trailing_whitespace = false
```

Isso acontece porque espaços ao final de uma linha podem ter significado
específico em documentos Markdown.

## Prettier

O Prettier é responsável pela apresentação visual do código.

As regras utilizadas pelo projeto estão em:

```text
.prettierrc.json
```

Configuração:

```json
{
  "printWidth": 80,
  "tabWidth": 2,
  "useTabs": false,
  "singleAttributePerLine": true,
  "bracketSameLine": false,
  "semi": true,
  "singleQuote": true,
  "endOfLine": "lf"
}
```

### Explicação das propriedades

| Propriedade              | Finalidade                                     |
| ------------------------ | ---------------------------------------------- |
| `printWidth`             | Define 80 caracteres como largura preferencial |
| `tabWidth`               | Define dois espaços para indentação            |
| `useTabs`                | Impede a utilização de caracteres de tabulação |
| `singleAttributePerLine` | Organiza os atributos HTML em linhas separadas |
| `bracketSameLine`        | Posiciona o fechamento da tag em outra linha   |
| `semi`                   | Adiciona ponto e vírgula no JavaScript         |
| `singleQuote`            | Utiliza aspas simples no JavaScript            |
| `endOfLine`              | Utiliza o padrão de quebra de linha `LF`       |

O `printWidth` representa uma largura preferencial. Em algumas situações, o
Prettier pode manter uma linha com mais de 80 caracteres quando não for possível
quebrá-la com segurança.

### Exemplo de formatação HTML

Antes:

```html
<img class="image-details" src="img/exemplo.jpg" alt="Descrição da imagem" title="Imagem de exemplo">
```

Depois:

```html
<img
  class="image-details"
  src="img/exemplo.jpg"
  alt="Descrição da imagem"
  title="Imagem de exemplo"
/>
```

Essa organização facilita a leitura, a manutenção e a identificação dos
atributos.

### Formatar um arquivo

O projeto está configurado para aplicar o Prettier quando o arquivo for salvo.

Também é possível utilizar:

```text
Format Document
```

Atalhos:

* Windows e Linux: `Shift + Alt + F`;
* macOS: `Shift + Option + F`.

## Prettier Ignore

O arquivo `.prettierignore` informa quais arquivos e diretórios não devem ser
formatados pelo Prettier.

```text
node_modules/
dist/
build/
coverage/
*.min.css
*.min.js
```

Esses diretórios normalmente contêm dependências, arquivos compilados,
relatórios ou arquivos minificados.

Arquivos com extensões como `.min.css` e `.min.js` já foram preparados para
ocupar menos espaço e não devem ser reformatados.

## Configurações do VS Code

As configurações compartilhadas pelo projeto estão em:

```text
.vscode/settings.json
```

Configuração utilizada:

```json
{
  "editor.tabSize": 2,
  "editor.insertSpaces": true,
  "editor.detectIndentation": false,
  "editor.formatOnSave": true,
  "editor.formatOnPaste": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.renderWhitespace": "boundary",
  "editor.renderControlCharacters": true,
  "editor.rulers": [80],
  "editor.guides.indentation": true,
  "editor.guides.highlightActiveIndentation": true,

  "[html]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },

  "[css]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },

  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  }
}
```

### Principais comportamentos

Essas configurações:

* definem dois espaços para indentação;
* utilizam espaços no lugar de tabulações;
* impedem a detecção automática de outra indentação;
* formatam o arquivo ao salvar;
* formatam conteúdos colados;
* definem o Prettier como formatador;
* exibem uma régua visual na coluna 80;
* mostram espaços importantes;
* exibem guias de indentação;
* aplicam o Prettier em HTML, CSS e JavaScript.

A régua na coluna 80 é apenas uma referência visual. Ela não impede que uma
linha ultrapasse esse limite.

## Extensões recomendadas

As extensões recomendadas estão registradas em:

```text
.vscode/extensions.json
```

Conteúdo:

```json
{
  "recommendations": [
    "esbenp.prettier-vscode",
    "PKief.material-icon-theme",
    "ritwickdey.LiveServer"
  ]
}
```

### Prettier — Code Formatter

Identificador:

```text
esbenp.prettier-vscode
```

Responsável por formatar automaticamente os arquivos HTML, CSS e JavaScript.

### Material Icon Theme

Identificador:

```text
PKief.material-icon-theme
```

Apresenta ícones diferentes para cada tipo de arquivo ou diretório.

Essa extensão altera apenas a aparência do VS Code e não modifica o código.

### Live Server

Identificador:

```text
ritwickdey.LiveServer
```

Cria um servidor local para visualizar páginas HTML no navegador.

Para utilizar:

1. abra o arquivo `index.html`;
2. clique com o botão direito;
3. selecione **Open with Live Server**.

O navegador será atualizado quando os arquivos forem salvos.

## Configuração pessoal e configuração do projeto

É importante diferenciar os dois tipos de configuração.

### Configuração pessoal

Pode definir:

* tema claro ou escuro;
* família da fonte;
* tamanho da fonte;
* zoom do editor;
* minimapa;
* salvamento automático;
* aparência dos ícones.

Essas preferências pertencem ao perfil pessoal do estudante.

### Configuração do projeto

Define:

* indentação;
* largura preferencial das linhas;
* organização dos atributos;
* padrão de quebra de linha;
* formatador utilizado;
* extensões recomendadas;
* arquivos ignorados.

Essas configurações ficam versionadas e acompanham o repositório.

## Relação entre as ferramentas

As ferramentas atuam em etapas diferentes:

1. o EditorConfig define as regras básicas;
2. o VS Code aplica as configurações do projeto;
3. o Prettier organiza visualmente o código;
4. o Live Server apresenta a página no navegador;
5. o Git registra as alterações realizadas.

Nenhuma dessas ferramentas substitui o conhecimento de HTML e CSS. Elas
ajudam a manter o ambiente organizado enquanto o código é desenvolvido.

## Impacto no Git

A padronização evita que diferenças de editor apareçam como alterações
desnecessárias.

Antes de criar um commit, utilize:

```bash
git status
git diff
```

O comando `git status` mostra quais arquivos foram alterados.

O comando `git diff` permite conferir exatamente quais linhas foram
modificadas.

Depois da verificação:

```bash
git add .
git commit -m "feat: descreva a alteração realizada"
git push
```

## Tipos de commit

Alguns prefixos ajudam a organizar o histórico:

| Prefixo    | Utilização                                 |
| ---------- | ------------------------------------------ |
| `feat`     | Inclusão de uma funcionalidade             |
| `fix`      | Correção de um problema                    |
| `docs`     | Alteração na documentação                  |
| `style`    | Alteração visual ou de formatação          |
| `refactor` | Reorganização sem mudança de comportamento |
| `chore`    | Configurações e manutenção                 |

Exemplos:

```bash
git commit -m "feat: adiciona página de perfil"
git commit -m "fix: corrige alinhamento do cabeçalho"
git commit -m "docs: atualiza instruções do projeto"
```

## Fluxo recomendado

Ao iniciar o desenvolvimento:

1. clone o repositório;
2. abra a pasta do projeto no VS Code;
3. instale as extensões recomendadas;
4. abra o `index.html` com o Live Server;
5. desenvolva os arquivos HTML e CSS;
6. salve e observe a formatação;
7. teste a página no navegador;
8. confira as alterações no Git;
9. crie o commit;
10. envie o código ao GitHub.

## Problemas comuns

### O Prettier não formata ao salvar

Verifique se:

1. a extensão Prettier está instalada;
2. o projeto foi aberto pela pasta raiz;
3. o arquivo `.prettierrc.json` existe;
4. o Prettier está definido como formatador;
5. a opção `editor.formatOnSave` está habilitada.

Também é possível utilizar o comando:

```text
Format Document With...
```

Selecione:

```text
Prettier — Code formatter
```

### Os atributos não ficam em linhas separadas

Confirme se o arquivo `.prettierrc.json` contém:

```json
"singleAttributePerLine": true
```

Depois salve ou formate novamente o documento.

### A indentação aparece com quatro espaços

Verifique no canto inferior direito do VS Code se aparece:

```text
Spaces: 2
```

Se aparecer outro valor:

1. clique sobre a indicação;
2. selecione **Indent Using Spaces**;
3. selecione **2**;
4. formate novamente o documento.

### O Live Server não aparece

Verifique se a extensão está instalada e habilitada.

Depois abra o arquivo `index.html`, clique com o botão direito e selecione:

```text
Open with Live Server
```

### O VS Code não recomenda as extensões

Confirme se:

* o projeto foi aberto pela pasta raiz;
* o arquivo `.vscode/extensions.json` existe;
* a pasta `.vscode` foi versionada pelo Git.

## Checklist de validação

Antes de enviar uma atividade, confirme:

* [ ] o projeto foi aberto pela pasta raiz;
* [ ] as extensões recomendadas foram instaladas;
* [ ] o Prettier está configurado;
* [ ] os atributos HTML estão organizados;
* [ ] a indentação utiliza dois espaços;
* [ ] a régua aparece na coluna 80;
* [ ] os espaços da indentação estão visíveis;
* [ ] o Live Server abre a página;
* [ ] a página foi testada no navegador;
* [ ] as alterações foram conferidas com o Git;
* [ ] o código foi enviado ao repositório remoto.

## Referências

* [HTML — MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/HTML);
* [CSS — MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Web/CSS);
* [EditorConfig](https://editorconfig.org/);
* [Prettier](https://prettier.io/);
* [Visual Studio Code](https://code.visualstudio.com/);
* [Live Server](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer);
* [Git](https://git-scm.com/);
* [GitHub](https://github.com/).
