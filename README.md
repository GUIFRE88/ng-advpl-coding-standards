# AdvPL Coding Standards

O presente documento tem por objetivo estabelecer um padr�o de boas pr�ticas a serem utilizadas pelas equipes de Desenvolvimento NG que atuam na plataforma Protheus AdvPL. As regras aqui listadas **n�o s�o restritivas**, mas buscam estabelecer uma identidade �nica para os fontes. A ado��o desse padr�o deve naturalmente se tornar um h�bito, aumentando a legibilidade dos fontes e proporcionando mais seguran�a no processo de manuten��o de sistemas.

Novas fun��es devem ser desenvolvidas considerando as boas pr�ticas listadas, e fun��es j� existentes devem ser adequadas gradativamente. Entretanto **n�o se recomenda** a mudan�a de trechos que n�o fazem parte do escopo de altera��o, de forma a n�o comprometer a revis�o t�cnica do fonte nem gerar risco de inser��o de novos bugs acidentalmente.


## Arquivo

- A extens�o deve ser min�scula (exemplo: `.prw`, `.apw`)

 + nomes de arquivo, recomenda��o em min�sculo, exceto para casos que tenha NG (camelcase) ou nome do m�dulo (fontes antigos)
MNTStep
mntstep
MNTSO
MNTSTEP -> errado
(Marcelo)

## Estilo

- Tabs somente para indenta��o, n�o para separa��o

> A tabula��o deve ser utilizada somente � esquerda, antes de iniciar a linha e nunca no meio da linha. O motivo � que quando o arquivo for aberto em diferentes editores (TDS, VSCode, Sublime, etc.), a formata��o ser� respeitada

- Nome de vari�veis devem se basear na nota��o h�ngara

>Iniciar por:
>- n-num�rico
>- c-char/string
>- l-logic/boolean
>- a-array/matriz
>- o-objetos
>- b-bloco de c�digo
>- x-indefinido

- Evite nomes de vari�veis como `nX` ou `nY` (exceto para �ndices). Seja mais descritivo

- Palavras-chave da linguagem devem usar **UpperCamelCase** (exemplos: `If`, `EndIf`, `While`
)

IIf -> certo
IIF -> errado
iif -> errado
Iif -> errado

- Ao terminar uma instru��o `Do While`, prefira `EndDo` ao inv�s de somente `End`

-> pode usar s� While + EndDo (recomendado)
-> tem diferen�a entre while e do while no advpl?

- Ao terminar uma instru��o `For`, prefira `Next <variable>` ao inv�s de somente `Next`

- Nomes de vari�veis locais devem ser em **lowerCamelCase** (exemplos: `cName`, `nAge`)

- Nomes de fun��es em nota��o h�ngara devem usar **lowerCamelCase** (exemplo: `aAdd`)

- Use as vari�veis com nomes iguais em tamanho e caixa (n�o fa�a `thisIsMyVari` e `THISISMYVARI`)

- Nomes de fun��es sem nota��o h�ngara devem usar **UpperCamelCase** (exemplo: `RetSqlName`)

- Evite ultrapassar 120 colunas horizontalmente. Quebre o c�digo com `;` quando necess�rio

- Valores l�gicos devem usar caixa alta (exemplo: `.F.`)

- Espa�o entre operadores. Use `nValue > nExpected` ao inv�s de `nValue>nExpected`

- Idioma padronizado. Evite misturar portugu�s e ingl�s quando poss�vel

- Deixar 1 linha em branco para cada *statement*, exceto conjuntos de *statements*

```
Function Test()

    If Something
        ...
    EndIf

    For nI := 1 To 10
        For nZ := 1 To 10
            ...
        Next nZ
    Next nI

Return
```

+ pular linha ap�s o return, antes da nova fun��o/protheus.doc

- Deixar 1 linha vazia no final de cada arquivo

> Ferramentas de diff se perdem sem linha final e alguns editores j� salvam por padr�o uma linha extra. Alguns compiladores n�o entendem o fim de arquivo (n�o � o caso do AdvPL), por isso � uma boa pr�tica em programa��o.

- Prefira aspas simples `'` ao inv�s de duplas `"`

> Aspas simples facilitam a leitura do c�digo e permitem, por padr�o, o uso de aspas duplas nas strings (ex: cString := 'Verifique o campo "quantidade" na tela.')

- Para acesso de �ndices m�ltiplos, evite `aList[ nI ][ nJ ]`. Use `aList[ nI, nJ ]`

- Fun��es **n�o** devem receber mais que 6 par�metros

> Esse � um padr�o utilizado em praticamente qualquer linguagem de programa��o com fun��es. Fun��es mestras, muito grandes, s�o muito mais dif�ceis de manter e de testar do que fun��es que fazem uma coisa, e a fazem bem feito. Testes unit�rios s�o integr�veis a fun��es simples, mas dif�ceis em fun��es com muitos par�metros. � at� comum que as pessoas se percam com tantos par�metros vazios (ex: TObj:New(100,30,,,,,,.F.)).

> Importante ressaltar que cada fun��o deve ser
exatamente isso: uma fun��o. Quanto a isso, tem dezenas de artigos sobre software engineering de como fun��es com muitos par�metros quebram modularidade e reuso. Normalmente fun��es que precisam de muitos par�metros s�o pass�veis de melhoria para melhor abstra��o em sua arquitetura.

+ acoplamento de fun��es: n�o usar vari�veis de outras fun��es (ex: aVETINR)

- Evite aninhamentos com mais de 3 statements (exemplo: `If` dentro de `If` dentro de `If`)

- Use `!=` ao inv�s de `<>`

- N�o fa�a `== .T.`

- Use `!` ao inv�s de `.Not.`

## Espa�amento

- Deve haver 1 espa�o entre os argumentos de fun��o, blocos e arrays (exemplo: `RetSqlName( 'STJ' )`)

RetSqlName('STJ', 'TJ_CODBEM', .F., lReturn, cMsgAviso)

RetSqlName( 'STJ', 'TJ_CODBEM', .F., lReturn, cMsgAviso )

- Deve haver 1 espa�o ap�s cada v�rgula (exemplo: `{ 1, 2, 3 }`)

- Deve haver espa�o entre par�metros de fun��es (use `Call( 1, 2, 3 )` e n�o `Call(1,2,3)`)

> A recomenda��o � usar espa�amento antes de iniciar o primeiro par�metro, entre cada par�metro e ao final. Entretanto, o primeiro e �ltimo espa�os ficam a crit�rio de cada um.

- **[OFF - PREFERIMOS MANTER � ESQUERDA]** `Return` indentado, j� que faz parte da estrutura da fun��o e **n�o** � um terminador

- Em coment�rios, 1 espa�o ap�s `//`

> Apesar de n�o ser uma obriga��o, o espa�amento antes de come�ar a descrever o coment�rio auxilia na leitura e tamb�m a encontrar e substituir programaticamente padr�es da linguagem.

## Redund�ncia

- Substitua `If` dentro de `If` por `.And.`

## Funcionamento

- Lembre-se de, ao criar uma tabela tempor�ria, fech�-la com `dbCloseArea`

- Lembre-se de fechar o _handler_ para o arquivo com `fClose` ao usar `fOpen`

- Quando deslocar para outro registro utilizando `dbSkip`, garanta estar posicionado na tabela desejada, caso contr�rio utilize `TABLE->( dbSkip() )` ou ent�o utilize `dbSelectArea( TABLE )` antes do `dbSkip()`

## Fun��es

- S�o consideradas **fun��es gen�ricas** aquelas que se aplicam a qualquer m�dulo, normalmente sem tratar de conceitos e regra de neg�cio. Devem ser criadas em fontes gen�ricos como NGUtil e preferencialmente come�ar pelos caracteres `NG`

- S�o consideradas **fun��es gen�ricas do m�dulo** aquelas que atendem regras mais gen�ricas de algum m�dulo, sendo utilizadas em um grupo de rotinas. Devem ser criadas em fontes do m�dulo como MNTUtil ou MDTUtil e preferencialmente come�ar pelos caracteres do m�dulo, ex: `MNT` ou `MDT`

- S�o consideradas **fun��es de rotina** aquelas que atendem regras espec�ficas de alguma rotina, mas que tamb�m podem ser chamadas externamente. Devem ser criadas no fonte que a utiliza e preferencialmente come�ar pelos caracteres da pr�pria rotina, como `MNTA080CAD()`

- S�o consideras **fun��es est�ticas** aquelas que s�o utilizadas apenas por um determinado fonte, sem chamada  externa por outros fontes. Devem ser criadas no fonte que a utiliza e preferencialmente iniciando pelo caracter `f` como `fCalcHora()`


## Refer�ncias

AdvPL Coding Standards - https://github.com/haskellcamargo/advpl-coding-standards by @haskellcamargo
