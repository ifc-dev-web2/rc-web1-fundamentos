# Padronização do ambiente e da formatação do código

## 1. Por que adotaremos esta abordagem?

Durante o desenvolvimento individual, cada pessoa pode configurar seu editor de
código conforme suas preferências. Entretanto, em um projeto desenvolvido por
várias pessoas, diferenças de configuração podem provocar alterações que não
representam mudanças reais no funcionamento do sistema.

Por exemplo, uma pessoa pode utilizar dois espaços para indentar o código,
enquanto outra utiliza quatro espaços ou caracteres de tabulação. Ao editar o
mesmo arquivo, o Git pode interpretar a reformatação como se praticamente todas
as linhas tivessem sido modificadas.

Isso pode causar:

- alterações desnecessárias no histórico do Git;
- dificuldade para identificar o que realmente mudou;
- conflitos durante o `merge` de branches;
- revisões de código mais demoradas;
- arquivos com estilos diferentes dentro do mesmo projeto;
- dependência das configurações particulares de cada computador.

Por esse motivo, a partir de agora, as principais regras de formatação serão
armazenadas no próprio repositório. Assim, o padrão acompanha o projeto e pode
ser utilizado por todos que fizerem seu clone.

> A configuração pessoal prepara a máquina do desenvolvedor. A configuração do
> projeto define como o código daquele repositório deve ser escrito.

## 2. Arquivos que utilizaremos

Cada arquivo possui uma responsabilidade diferente:

| Arquivo | Responsabilidade |
| --- | --- |
| `.editorconfig` | Define regras básicas compartilhadas entre diferentes editores. |
| `.prettierrc.json` | Define como o Prettier deverá formatar o código. |
| `.prettierignore` | Informa quais arquivos e pastas não devem ser formatados. |
| `.vscode/settings.json` | Configura o comportamento do VS Code dentro do projeto. |
| `.vscode/extensions.json` | Recomenda as extensões necessárias para trabalhar no projeto. |

A estrutura ficará semelhante a esta:

```text
projeto/
├── .vscode/
│   ├── extensions.json
│   └── settings.json
├── .editorconfig
├── .prettierignore
├── .prettierrc.json
├── index.html
└── styles.css
```

Esses arquivos devem ser adicionados ao Git para que sejam recebidos por todas
as pessoas que clonarem o repositório.

## 3. Extensões utilizadas

### 3.1 Prettier — Code formatter

- Nome: **Prettier — Code formatter**
- Identificador: `esbenp.prettier-vscode`
- Finalidade: formatar automaticamente arquivos HTML, CSS, JavaScript e outros
  formatos suportados.

O Prettier aplica regras consistentes ao código, como indentação, largura
preferencial das linhas e disposição dos atributos HTML.

### 3.2 Material Icon Theme

- Nome: **Material Icon Theme**
- Identificador: `PKief.material-icon-theme`
- Finalidade: apresentar ícones diferentes de acordo com o tipo de arquivo ou
  pasta.

Essa extensão melhora a identificação visual da estrutura do projeto, mas não
modifica nem formata o código.

## 4. Recomendações de extensões do projeto

Criaremos o arquivo `.vscode/extensions.json`:

```json
{
  "recommendations": [
    "esbenp.prettier-vscode",
    "PKief.material-icon-theme"
  ]
}
```

### Explicação de cada linha

| Linha ou propriedade | O que faz |
| --- | --- |
| `{` | Inicia o objeto de configuração JSON. |
| `"recommendations"` | Define a lista de extensões recomendadas pelo projeto. |
| `[` e `]` | Delimitam a lista de identificadores das extensões. |
| `"esbenp.prettier-vscode"` | Recomenda a instalação do Prettier. |
| `"PKief.material-icon-theme"` | Recomenda a instalação do Material Icon Theme. |
| `}` | Encerra o objeto de configuração. |

Quando o projeto for aberto no VS Code, o editor poderá sugerir a instalação
dessas extensões. A recomendação não instala as extensões automaticamente e não
impede o uso de outro editor.

## 5. Configuração compartilhada do editor

Criaremos o arquivo `.vscode/settings.json`:

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
  "editor.wordWrap": "wordWrapColumn",
  "editor.wordWrapColumn": 80,
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
  },

  "workbench.iconTheme": "material-icon-theme"
}
```

### Explicação das propriedades

| Propriedade | O que faz |
| --- | --- |
| `"editor.tabSize": 2` | Define que cada nível de indentação terá o tamanho visual de dois espaços. |
| `"editor.insertSpaces": true` | Faz a tecla `Tab` inserir espaços em vez de um caractere de tabulação. |
| `"editor.detectIndentation": false` | Impede que o editor substitua as regras do projeto ao tentar detectar a indentação de cada arquivo. |
| `"editor.formatOnSave": true` | Formata automaticamente o arquivo sempre que ele for salvo. |
| `"editor.formatOnPaste": true` | Tenta formatar o conteúdo colado no editor. |
| `"editor.defaultFormatter": "esbenp.prettier-vscode"` | Escolhe o Prettier como formatador padrão do projeto. |
| `"editor.renderWhitespace": "boundary"` | Exibe os espaços relevantes da indentação e das extremidades das linhas. |
| `"editor.renderControlCharacters": true` | Torna visíveis alguns caracteres de controle que normalmente ficam ocultos. |
| `"editor.rulers": [80]` | Mostra uma guia vertical na coluna 80. |
| `"editor.wordWrap": "wordWrapColumn"` | Ativa a quebra visual das linhas na coluna configurada. |
| `"editor.wordWrapColumn": 80` | Define a coluna 80 como ponto da quebra visual. |
| `"editor.guides.indentation": true` | Exibe guias verticais para facilitar a leitura dos níveis de indentação. |
| `"editor.guides.highlightActiveIndentation": true` | Destaca a guia correspondente ao bloco em que o cursor está posicionado. |
| `"[html]"` | Inicia as configurações aplicadas exclusivamente a arquivos HTML. |
| `"[css]"` | Inicia as configurações aplicadas exclusivamente a arquivos CSS. |
| `"[javascript]"` | Inicia as configurações aplicadas exclusivamente a arquivos JavaScript. |
| `"workbench.iconTheme": "material-icon-theme"` | Seleciona o Material Icon Theme como tema de ícones do projeto. |

### Observação sobre a coluna 80

A régua da coluna 80 é uma orientação visual. Ela não impede que o estudante
continue digitando após essa coluna. Da mesma forma, a quebra de linha do editor
é apenas visual e não necessariamente insere uma nova linha no arquivo.

O Prettier tentará reorganizar o código de acordo com a largura configurada,
mas alguns conteúdos indivisíveis, como URLs muito grandes, poderão ultrapassar
esse limite.

## 6. Configuração do EditorConfig

Criaremos o arquivo `.editorconfig` na raiz do projeto:

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

### Explicação das propriedades

| Propriedade | O que faz |
| --- | --- |
| `root = true` | Informa que este é o arquivo EditorConfig principal e interrompe a procura por configurações em diretórios superiores. |
| `[*]` | Aplica as regras seguintes a todos os tipos de arquivo. |
| `charset = utf-8` | Define UTF-8 como codificação dos arquivos. |
| `end_of_line = lf` | Padroniza as quebras de linha no formato LF, evitando diferenças comuns entre sistemas operacionais. |
| `insert_final_newline = true` | Garante uma quebra de linha ao final de cada arquivo. |
| `indent_style = space` | Determina que a indentação deverá utilizar espaços, e não tabs. |
| `indent_size = 2` | Define dois espaços para cada nível de indentação. |
| `trim_trailing_whitespace = true` | Remove espaços desnecessários no final das linhas. |
| `max_line_length = 80` | Registra a largura preferencial de 80 caracteres. O suporte depende do editor ou formatador utilizado. |
| `[*.md]` | Aplica a regra seguinte somente aos arquivos Markdown. |
| `trim_trailing_whitespace = false` | Preserva espaços finais no Markdown, pois eles podem ter significado para a quebra de linha. |

O `.editorconfig` pode ser reconhecido por diversos editores e ferramentas. Isso
permite que uma pessoa utilize VS Code e outra utilize um editor diferente sem
abandonar as regras básicas do projeto.

## 7. Configuração do Prettier

Criaremos o arquivo `.prettierrc.json`:

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

### Explicação de cada propriedade

| Propriedade | O que faz |
| --- | --- |
| `"printWidth": 80` | Orienta o Prettier a organizar o código considerando uma largura preferencial de 80 caracteres. |
| `"tabWidth": 2` | Define dois espaços para cada nível de indentação. |
| `"useTabs": false` | Determina que o Prettier utilize espaços em vez de caracteres de tabulação. |
| `"singleAttributePerLine": true` | Coloca cada atributo de uma tag HTML em uma linha separada quando a tag possui múltiplos atributos. |
| `"bracketSameLine": false` | Mantém o fechamento de tags multilinhas em sua própria linha quando aplicável. |
| `"semi": true` | Insere ponto e vírgula ao final das instruções JavaScript quando necessário. |
| `"singleQuote": true` | Prefere aspas simples em JavaScript. Isso não substitui as aspas duplas exigidas ou adotadas no HTML. |
| `"endOfLine": "lf"` | Faz o Prettier gravar as quebras de linha no padrão LF. |

O `.editorconfig` fornece a base compartilhada. O `.prettierrc.json` complementa
essa base com regras específicas do Prettier. Quando uma propriedade equivalente
existir nos dois arquivos, a configuração do Prettier terá prioridade durante a
formatação realizada por ele.

### Exemplo de formatação HTML

Antes da formatação:

```html
<img class="image-details" src="images/perfil.jpg" alt="Foto do estudante" title="Foto de perfil">
```

Depois da formatação:

```html
<img
  class="image-details"
  src="images/perfil.jpg"
  alt="Foto do estudante"
  title="Foto de perfil"
/>
```

## 8. Arquivos que não devem ser formatados

Criaremos o arquivo `.prettierignore`:

```gitignore
node_modules/
dist/
build/
coverage/
*.min.css
*.min.js
```

Normalmente, dependências, arquivos gerados durante a construção do projeto,
relatórios de cobertura e arquivos já minificados não devem ser alterados pelo
Prettier.

Em projetos iniciais que possuem somente HTML e CSS, algumas dessas pastas ainda
não existirão. Mesmo assim, o arquivo já deixa o repositório preparado para uma
possível evolução.

## 9. Fluxo de configuração para cada estudante

### Primeira preparação da máquina

1. Instalar o VS Code ou outro editor compatível.
2. Instalar a extensão **Prettier — Code formatter**.
3. Instalar a extensão **Material Icon Theme**.
4. Ativar o Material Icon Theme quando solicitado.
5. Clonar o repositório da atividade.
6. Abrir a pasta completa do projeto no editor.
7. Aceitar as extensões recomendadas pelo projeto, caso ainda não estejam
   instaladas.

### Fluxo diário de desenvolvimento

1. Atualizar a branch local antes de começar a atividade.
2. Criar ou selecionar a branch indicada para o trabalho.
3. Editar os arquivos do projeto.
4. Salvar o arquivo e observar a formatação automática.
5. Conferir no Git quais linhas foram realmente alteradas.
6. Testar a página ou aplicação.
7. Criar o commit somente após revisar as alterações.
8. Enviar a branch para o repositório remoto.

## 10. O que acontece quando o projeto é aberto?

O fluxo esperado é:

1. O editor encontra o `.editorconfig` e aplica as regras básicas de indentação
   e final de linha.
2. O VS Code encontra `.vscode/settings.json` e ativa as configurações daquele
   espaço de trabalho.
3. O VS Code lê `.vscode/extensions.json` e recomenda as extensões do projeto.
4. Ao salvar um arquivo, o VS Code chama o Prettier.
5. O Prettier encontra `.prettierrc.json` e aplica as regras de formatação.
6. O `.prettierignore` impede que arquivos gerados ou externos sejam alterados.
7. O Git registra somente o conteúdo final salvo no arquivo.

## 11. Configuração do projeto versus configuração pessoal

As configurações possuem níveis de aplicação:

| Nível | Exemplo | Comportamento |
| --- | --- | --- |
| Pessoal | Configurações gerais do VS Code do estudante | Aplica-se normalmente a todos os projetos abertos naquela máquina. |
| Projeto | Arquivos versionados no repositório | Aplica-se ao projeto e deve representar o padrão definido pela equipe. |

Quando houver uma regra específica no projeto, ela deve prevalecer sobre a
preferência pessoal. Uma pessoa ainda pode escolher o tema de cores, tamanho da
fonte e outros aspectos visuais, mas não deve modificar individualmente as
regras que alteram o conteúdo dos arquivos versionados.

## 12. O que essa estrutura consegue e não consegue garantir?

Esses arquivos reduzem muito as diferenças entre ambientes, mas a configuração
do editor, sozinha, não impede completamente que alguém envie código fora do
padrão. Um estudante ainda pode desativar a extensão ou criar um commit sem
formatar os arquivos.

Em projetos que utilizam Node.js, podemos instalar o Prettier como dependência e
adicionar comandos ao `package.json`:

```json
{
  "scripts": {
    "format": "prettier --write .",
    "format:check": "prettier --check ."
  }
}
```

| Comando | Finalidade |
| --- | --- |
| `npm run format` | Formata os arquivos do projeto. |
| `npm run format:check` | Verifica a formatação sem modificar os arquivos. |

Posteriormente, `npm run format:check` poderá ser executado em uma integração
contínua, como o GitHub Actions. Nesse caso, o repositório poderá rejeitar uma
alteração que não esteja de acordo com o padrão definido.

## 13. Resultado esperado

Com essa abordagem, queremos que os estudantes compreendam que legibilidade e
padronização fazem parte do desenvolvimento de software.

O objetivo não é apenas deixar o código visualmente agradável. Um padrão comum
facilita a leitura, reduz alterações desnecessárias no Git, melhora a colaboração
e permite que a equipe concentre a revisão na lógica realmente desenvolvida.

Portanto, adotaremos a seguinte divisão:

- preferências exclusivamente visuais podem continuar sendo pessoais;
- regras que alteram o conteúdo do código pertencem ao projeto;
- a formatação deverá acontecer automaticamente ao salvar;
- todos deverão revisar as alterações antes de criar um commit;
- o padrão será evoluído junto com as necessidades do projeto.
