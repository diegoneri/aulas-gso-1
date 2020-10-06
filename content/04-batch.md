# Arquivos de lote (Batch files)

Arquivos em lote ou _batch files_ são arquivos de texto que executam uma série de comandos. Eles podem ser simples o suficiente para que até o usuário doméstico de computador possa tirar proveito deles.

Embora os arquivos em lote possam ser bastante sofisticados e usados para administração de rede e sistema, eles também podem ser extremamente simples e breves.

O objetivo deste conteúdo é dar uma breve noção do que são arquivo em lote e discutirei alguns exemplos simples.

## O que é um arquivo de lote?

São arquivos de texto simples contendo algumas linhas com comandos que são executados em sequência.

Qualquer comando pode ser utilizado, mas não necessariamente seja útil em determinadas situações.

Esses arquivos têm a extensão especial BAT ou CMD. Os arquivos desse tipo são reconhecidos e executados no shell de comandos.

A construção de um arquivo batch consiste em nada mais do que abrir qualquer editor de texto como o "Bloco de Notas" (Notepad), inserir algumas linhas contendo comandos e salvar o arquivo com uma extensão BAT ou CMD. 

🍌 A extensão CMD é limitada a sistemas Windows mais recentes e não é reconhecida em sistemas Windows 9x / Me. No Windows XP, Vista e 7 há pouca diferença prática entre as duas extensões.

🍌 Não use Wordpad ou Word a menos que você seja muito cuidado para salvar todos os arquivos em formato de texto puro.

Os comandos em si são geralmente bastante simples e não há necessidade de aprender uma linguagem de programação. Aqueles que desejarem podem explorar as complexidades disponíveis com decisão e laços.

🧐 Não vamos abordar decisão e laços, mas vocês podem conferir o conteúdo em https://commandwindows.com/batchfiles-branching.htm 

Para executar um arquivo em lote, você pode dar um duplo clique nele no Windows ou citar seu nome no _shell de comandos_.

## Comandos básicos

* `ECHO`: Escreve na tela
* `ECHO OFF`: Oculta informações e o código executado pelo sistema.
* `@ECHO OFF`: Oculta informações e o código executado pelo sistema, inclusive o próprio.
* `ECHO ON`: Exibe informações e o código executado pelo sistema.
* `ECHO.`: Salta uma linha.
* `@ECHO`: Mostra o status do ECHO
* `SET`: Cria variável que pode ser referenciada através de %variável%.
* `SET /A`: Cria variável numérica que pode ser referenciada através de %variável%.
* `SET /P`: Cria variável a partir de uma entrada do usuário, que pode ser referenciada através de %variável%.
* `%1 %2 ... %n`: Referência a parâmetros fornecidos na execução do arquivo em lote.
* `CLS`: Limpa o console.
* `IF e ELSE`: Estruturas condicionais.
* `GOTO`: Avança até determinado trecho do lote.
* `FOR`: Estrutura de repetição.
* `PAUSE`: Faz uma pausa, e exibe: “Pressione qualquer tecla para continuar.”
* `REM`: Utilizado para fazer comentários.
* `START`: Inicializa um aplicativo ou programa.
* `PAUSE`: Pausa a execução do script.

## Construíndo um arquivo

A primeira linha em um arquivo em lote geralmente consiste neste comando:

```bash
@echo off
```

Por padrão, um arquivo em lote exibe seus comandos à medida que é executado. O objetivo deste primeiro comando é desligar esta tela.

O comando `echo off` desativa a exibição da execução de todos os comandos, exceto o próprio comando "echo off".

🍌 As saídas de `echo on` serão exibidas normalmente.

O sinal "arroba" "@" na frente faz com que o comando se aplique a ele mesmo. Essa nuance não é realmente tão importante no contexto aqui, mas eu a menciono porque é freqüentemente vista em scripts.

Os scripts que discutiremos são muito breves e usar esta instrução não fará grande diferença. No entanto, como uma questão de boa prática, vamos inseri-lo em nossos scripts.

### Exemplo 01

Nosso primeiro exemplo de arquivo em lote listará todos os arquivos em uma pasta e colocará a lista em um novo arquivo de texto.

* Use o `copy con listaArquivosProgramas.bat`
* Digite a linha `@echo off`.
* Em seguida, insira outra linha
`dir "C:\Arquivos de programas" > listaDeProgramas.txt`
* Para finalizar, use o `CTRL+Z`

```bash
copy con listaArquivosProgramas.bat
@echo off
dir "C:\Arquivos de programas" > listaDeProgramas.txt
^Z
```

No shell, execute o `listaArquivosProgramas.bat`.

```bash
listaArquivosProgramas.bat
```

Em seguida, use o `type` para exibir o conteúdo do arquivo.

```bash
type listaDeProgramas.txt
```

### Exemplo 02

Hello World

```bash
copy con helloWorld.bat
rem "Hello World"
@echo off
echo.
echo "Olá, mundo!"
^Z
```

```bash
helloWorld.bat
```

### Exemplo 03

Hello World, com valor

```bash
copy con helloWorldComNome.bat
@echo off
rem Hello World, com valor
echo.
set /p nome="Digite seu nome: "
echo.
echo Olá, %nome%!
^Z
```

```bash
helloWorldComNome.bat

Digite seu nome: Diego

Olá, Diego!
```

### Exemplo 04

Parâmetros

```bash
copy con desktopComParametros.bat
@echo off
echo.
echo A lista de arquivos do desktop serão salvas em %1, na pasta Documentos
pause
echo.
dir %userprofile%\Desktop >> %userprofile%\Documents\%1
echo O arquivo %userprofile%\Documents\%1 foi criado
^Z
```

```bash
desktopComParametros.bat listaDesktop.txt

A lista de arquivos do desktop serão salvas em listaDesktop.txt, na pasta Documentos.
Pressione uma tecla para continuar...

 O arquivo C:\Users\dfelix\Documents\listaDesktop.txt foi criado
```

### Exemplo 05

```bash
copy con soma.bat
@echo off
echo.
set /a soma=%1+%2
echo A soma de %1 + %2 = %soma%
^Z
```

```bash
soma.bat 3 4

A soma de 3 + 4 = 7

```

### Exemplo 06

```bash
copy con backupImagens.bat
@echo off
echo.
echo Vamos realizar backup de suas imagens em %1
pause
xcopy %userprofile%\Pictures %1 /d /s

echo Arquivos copiados com sucesso.
^Z
```

## Mas o que pode ser realmente feito com arquivos em lote

Quer ter uma ideia do quão útil pode ser um arquivo de lote? Veja a quantidade de exemplos do link a seguir: <https://www.robvanderwoude.com/batexamples.php>
