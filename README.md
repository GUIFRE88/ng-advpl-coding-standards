# AdvPL Coding Standards

### Arquivo

- A extens�o deve ser min�scula (exemplo: `.prw`, `.apw`)

### Estilo

- Tabs somente para indenta��o, n�o para separa��o (ou seja, usar tabs somente � esquerda, antes de iniciar a linha, nunca no meio da linha)
- Nome de vari�veis devem se basear na nota��o h�ngara (iniciar por `n-n�meros`, `c-char/string`, `l-boolean`, `a-array/matriz`, `o-objetos` e `x-indefinido`)
- Evite nomes de vari�veis como `nX` ou `nY` (exceto para �ndices). Seja mais descritivo
- Palavras-chave da linguagem devem usar **UpperCamelCase** (exemplos: `If`, `EndIf`, `While`)
- Ao terminar uma instru��o `Do While`, prefira `EndDo` ao inv�s de somente `End`
- Ao terminar uma instru��o `For`, prefira `Next <variable>` ao inv�s de somente `Next`
- Nomes de vari�veis locais devem ser em **lowerCamelCase** (exemplos: `cName`, `nAge`)
- Nomes de fun��es em nota��o h�ngara devem usar **lowerCamelCase** (exemplo: `aAdd`)
- Use as vari�veis com nomes iguais em tamanho e caixa (n�o fa�a `thisIsMyVariable` e `THISISMYVARI`)
- Nomes de fun��es sem nota��o h�ngara devem usar **UpperCamelCase** (exemplo: `RetSqlName`)
- Deve haver 1 espa�o entre os argumentos de fun��o, blocos e arrays (exemplo: `RetSqlName( 'STJ' )`)
- Deve haver 1 espa�o ap�s cada v�rgula (exemplo: `{ 1, 2, 3 }`)
- Deve haver espa�o entre par�metros de fun��es (use `Call( 1, 2, 3 )` e n�o `Call(1,2,3)`)
- Evite ultrapassar 80 colunas horizontalmente. Quebre o c�digo com `;` quando necess�rio
- Valores l�gicos devem usar caixa alta (exemplo: `.F.`)
- Espa�o entre operadores. Use `nValue > nExpected` ao inv�s de `nValue>nExpected`
- `Return` indentado, j� que faz parte da estrutura da fun��o e **n�o** � um terminador
- Em coment�rios, 1 espa�o ap�s `//`
- Idioma padronizado. Evite misturar portugu�s e ingl�s quando poss�vel
- Deixar 1 linha em branco para cada *statement*, exceto conjuntos de *statements*
- Deixar 1 linha vazia no final de cada arquivo
- Prefira aspas simples `'` ao inv�s de duplas `"`
- Para acesso de �ndices m�ltiplos, evite `aList[ nI ][ nJ ]`. Use `aList[ nI, nJ ]`
- Fun��es **n�o** devem receber mais que 6 par�metros
- Evite aninhamentos com mais de 3 statements (exemplo: `If` dentro de `If` dentro de `If`)
- Use `!=` ao inv�s de `<>`
- N�o fa�a `== .T.`
- Use `!` ao inv�s de `.Not.`

## Redund�ncia

- Substitua `If` dentro de `If` por `.And.`

## Funcionamento

- Lembre-se de, ao criar uma tabela tempor�ria, fech�-la com `dbCloseArea`
- Lembre-se de fechar o _handler_ para o arquivo com `fClose` ao usar `fOpen`
- Quando deslocar para outro registro utilizando `dbSkip`, garanta estar posicionado na tabela desejada, caso contr�rio utilize `TABLE->( dbSkip() )` ou ent�o utilize `dbSelectArea( TABLE )` antes do `dbSkip()`
