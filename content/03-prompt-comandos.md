# Shell de comandos (Prompt de comandos)

O shell de comandos é um programa que reproduz uma interface de usuário baseada em texto na interface gráfica do usuário (GUI) do Windows.

Ele pode ser usado para executar comandos inseridos, básicos e avançados e realizar funções administrativas em um computador. O _shell_ muitas vezes é utilizado na resolução de muitos problemas de uso do Windows, sejam eles a nível de operacionalização, automação, desenvolvimento e outras características de um Técnico em Informática.

## Primeiros passos: como abrir

### Opção 01

1. Clique no botão Iniciar do Windows
1. Na caixa de pesquisa e digite uma das opções abaixo:
   * prompt

   ![prompt](./image/001a.png)

   * cmd

   ![cmd](./image/001b.png)

### Opção 02

1. Pressione a sequência de teclas ![Tecla Windows](./icon/001.png) + R
1. Na caixa de diálogo `Executar`, digite `cmd` e clique em OK:

![Executar](./image/003.png)

Todas as opções levam à janela a seguir:

![Shell de Comandos](./image/004.png)

## Prompt: o que é

Importante diferenciarmos o que é um prompt e o que é um shell.

Um shell é uma interface que nos possibilite a interação com o Sistema Operacional. Neste caso, estamos interagindo via interface de linha de comando.

O prompt nada mais é que a estrutura exibida pelo shell, independente do Sistema Operacional:

![Prompt](image/005.png)

Ele pode ser alterado para exibir o que você desejar, como o nome do diretório atual, data e hora do sistema. O valor padrão é o caminho do diretório atual (_path_), seguido do colchete angular ">"

### Sintaxe

```sh
prompt <opções>
```

#### Valor padrão

```sh
prompt
```

ou

```sh
prompt $p$g
```

ou

```sh
prompt $m$p$g
```

#### Opções - prompt

<https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/prompt>

* `$M` --> nome remoto associado a pasta, no caso de ser um diretório de rede;
* `$P` --> caminho completo da pasta atual;
* `$G` --> caracter ">";
* `$C` --> caracter "(";
* `$F` --> caracter ")";
* `$S` --> caracter " ";
* `$_` --> retorno de carro ou quebra de linha.

Outras opções úteis:

* `%username%` --> nome do usuário logado;
* `%computername%`--> nome do computador.

## Comandos básicos de ajuda

### help

Exibe a ajuda do shell de comandos.

### Parâmetro `? (/?)`

Boa parte dos comandos aceitam o parâmetro `?` para consultar a ajuda de um determinado comando. Isto se torna muito útil quando você precisa realizar uma operação e não possui acesso a internet.

## Arquivos, diretórios e caminhos (_paths_)

Aqui são demonstrados os conceitos básicos de arquivo e diretório (pasta) no contexto de computação.

### Arquivos

Conjunto de dados que se relacionam de alguma forma, descrevendo uma ou mais informações.

Para a computação, os arquivos são formados por _bytes_, organizados seguindo algum tipo de estrutura ou formato.

Um arquivo pode representar informações das mais diversas naturezas, como um texto ou imagem, por exemplo.

Cada arquivo precisa de uma identificação. No ponto de vista do Sistema Operacional, ele possui uma identificação de endereço no disco secundário. Abordaremos detalhes quando falarmos de __Sistema de Arquivos__.

No ponto de vista do usuário, um arquivo possui um nome.

### Diretórios

É uma subdivisão lógica que indica o caminho virtual de um arquivo ou diretório no seu disco secundário, permitindo a organização e o agrupamento dos mesmos.
> Uma pasta ou diretório é um artefato virtual no sistema operacional: serve para te ajudar a organizar seus arquivos e não ocupa espaço
> Diretórios são chamados de pastas em função da analogia utilizada em sistemas Windows e que é adotada até os anos atuais.

#### Diretório raiz

É o primeiro diretório na hierarquia. Em sistemas Windows, é representado geralmente por `\` (`C:\`) e em sistemas Unix, por `/`.

### Caminhos (_Paths_)

Um caminho ou _path_ é o que determina a localização única a nível de usuário de um arquivo ou diretório em uma árvore de diretórios.

Eles são utilizados em diversas situações, quando para referenciar arquivo ou diretório.

A depender do sistema operacional, podemos ter os seguintes caracteres delimitadores:

`:` - dois pontos --> utilizado para expressar uma unidade de disco em sistemas Windows.

`\`- contrabarra --> utilizado para expressar a hierarquia entre um diretório e um subdiretório ou arquivo contido, em Sistemas Windows.

`\\` - dupla contrabarra --> utilizado para expressar a hierarquia entre uma localização remota, acessível pelo computador e um subdiretório ou arquivo contido, em Sistemas Windows.

`/`- barra --> utilizado para expressar a hierarquia entre um diretório e um subdiretório ou arquivo contido, em Sistemas Unix.

Os caminhos podem ser classificados em caminhos absolutos ou relativos.

#### Caminho absoluto

```bash
C:\Users\Diego
C:\Users\Diego\Desktop
\Users\Diego\Desktop
```

Caminho __absoluto__ ou __completo__ determina o caminho exato de um arquivo ou diretório, independente da localização atual.

Deve-se incluir o diretório raiz (`\`).  

#### Caminho relativo

O caminho __relativo__ é determinado a partir da localização atual.

Então, utiliza-se as referências para se determinar caminhos relativos:

* **acima** da localização atual. Quanto mais acima, mais distante da raiz.

```bash
C:\Users\Diego>cd Pictures\Screenshots

#É uma referência relativa para o diretório C:\Users\Diego\Pictures\Screenshots
```

* **abaixo** da localização atual. Quanto mais abaixo, mais próximo da raiz. Cada nível é determinado por `..`:

```bash
C:\Users\Diego\Pictures\Screenshots>cd ..\..

#É uma referência relativa para o diretório C:\Users\Diego.
```

Para `C:\Users\Diego\Pictures\Screenshots`:

* `..` --> C:\Users\Diego\Pictures
* `..\..` --> C:\Users\Diego
* `..\..\..` --> C:\Users
* `..\..\..\..` --> C:\

**Obs: Não há anterior para a raiz.**

Ainda há a referência `.`, que indica a localização atual.

## Comandos básicos - Diretório

### dir (_directory_)

Exibe o conteúdo de um diretório. Quando não especificado um, exibe o conteúdo do diretório atual.

Parâmetros:

* `/A` - Exibe conteúdo com atributos especificados

   | Atributo  | Descrição                    |
   |-----------|------------------------------|
   | D         | Diretórios                   |
   | R         | Arquivos somente leitura     |
   | H         | Arquivos ocultos             |
   | S         | Arquivos de sistema          |
   | -         | Prefixo significando negação |

* `/B` - Usa formatação básica (sem informações de cabeçalho ou resumo).
* `/W` - Exibe os resultados em coluna, classificados por linha.
* `/D` - Exibe os resultados em coluna, classificados por coluna.
* `/O` - Determina uma ordenação, a partir de uma classificação

   | Ordenação  | Classificação                |
   |------------|------------------------------|
   | N          | Alfabética por nome          |
   | E          | Alfabética por extensão      |
   | G          | Diretórios primeiro          |
   | S          | Tamanho                      |
   | D          | Data e hora                  |
   | -          | Prefixo significando negação |

* `/X` - Exibe um formato curto de arquivo, muito utilizado em sistemas Windows até o 98 SE.

### cd ou chdir (_change directory_)

Altera o diretório corrente. Quando não especificado um, exibe o _path_ atual.

#### Sintaxe - cd

```bash
CD [caminho relativo]
```

```bash
CD [caminho absoluto]
```

### md ou mkdir (_make directory_)

Cria um ou mais diretórios.

#### Sintaxe - md

```bash
MD [<novoDir1 novoDir2 ...>]
```

### rd ou rmdir (_remove directory_)

Remove um ou mais diretórios.

```bash
RD [dir1 <dir2 ...>]
```

### tree

Exibe graficamente a estrutura de diretório do path atual ou de um especificado.

#### Sintaxe - tree

```bash
TREE [unidade:][caminho] [/F] [/A]
```

#### Opções - tree

* `/F` --> Exibir também o nome dos arquivos;
* `/A` --> Usa os caracteres da Tabela ASCII ao invés de caracteres estendidos (recomendado);

## Saída do shell

A saída do shell ou console é um evento de impressão das informações em tela.
Além da saída padrão no próprio console, é possível __redirecionar__ a saída para outros locais:

* Arquivo;
* Área de transferência.

Isto é útil quando você precisa salvar as informações de processamento do console em um arquivo a ser enviado em um relatório, por exemplo.

### Redirecionar para a área de transferência

#### Sintaxe - clip

```bash
[COMANDO] | clip
```

Exemplo

```bash
C:\Users\Diego> tree /A | clip
```

### Redirecionar para um arquivo

#### Criando um novo (ou substituindo) um arquivo

```bash
[COMANDO] > meuArquivo.txt
```

Exemplo

```bash
C:\Users\Diego> tree Desktop /A > arquivosAreaTrabalho.txt
```

Obs: se o arquivo existir, ele será substituído.

#### Concatenando informações em um arquivo

```bash
[COMANDO] >> meuArquivo.txt
```

Exemplo

```bash
C:\Users\Diego> dir /w Documents >> C:\Users\Diego\Desktop\listaMeusArquivos.txt
C:\Users\Diego> dir /w Desktop >> C:\Users\Diego\Desktop\listaMeusArquivos.txt
```

#### Redirecionando erros

```bash
[COMANDO] 1> meuArquivo.txt 2> erros.txt
```

##### Exemplo - saída de erro para arquivo diferente

```bash
C:\Users\Diego> dir programa.exe 1> relatorio.txt 2> erros.txt
```

##### Exemplo - saída de erro para o mesmo arquivo

```bash
C:\Users\Diego> dir programa.exe 1> relatorio.txt 2>&1
```

Obs: da mesma forma, pode-se usar o operador `>>` caso queira que a saída do comando seja concatenada em arquivo existente.

##### Concatenando saída e erro:

```bash
C:\Users\Diego> dir programa.exe 1>> relatorio.txt 2>>&1
```

ou

```bash
C:\Users\Diego> dir programa.exe 1>> relatorio.txt 2>> erros.txt
```

##### Concatenando __somente__ saída:

```bash
C:\Users\Diego> dir programa.exe 1>> relatorio.txt 2> erros.txt
```

##### Concatenando __somente__ erro:

```bash
C:\Users\Diego> dir programa.exe 1> relatorio.txt 2>> erros.txt
```
