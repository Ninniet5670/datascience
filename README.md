Existem 2 passos para se aprender Ciência de Dados (Data Science):

1. Análise de dados (Data Analysis):

   Essencialmente, trata-se de limpar, transformar e modelar os dados, centra-se na ideia de extrair as informações dos dados e tomar a decisão mediante tal análise

2. Visualização de dados (Data Vizualization):

   Representação gráfica das informações e dos dados utilizando-se de elementos visuais por meios mais acessíveis como gráficos



A seguir, as melhores bibliotecas para uso de dados:

- ## NumPy - *Análise de Dados*

É usado para se trabalhar com arrays e no campo de álgebra linear, séries de Fourier, transformações e matrizes



Na realidade, NumPy significa Numerical Python

A maioria das pessoas que usam NumPy é para a funcionalidade de criar arrays

seus arrays possuem 2 tipos:

1. Vetor Dimensional
2. Matriz Dimensional



Para criar um array do NumPy, basta:

```python
import numpy as np

a = [1, 2, 3, 4, 5]

np.array(a)

>>> array([1, 2, 3, 4, 5])
```

Criou-se então um vetor de uma dimensão

```python
b = [[1, 2, 3], [4, 5, 6]]

np.array(b)

>>> array([[1, 2, 3],
           [4, 5, 6]])
```

Sem a função `array()`, a matriz não passa de uma lista composta, contudo, com a função, a mesma transforma-se em uma matriz dimensional

É mais comum criar arrays com seus próprios dados do que converter a partir de listas



Para criar arrays de um número inteiro até outro, usa-se o `arange()`

Um terceiro argumento é possível que seria o intervalo

```python
np.arange(1, 10, 2)

>>> array([1, 3, 5, 7, 9])
```



Para criar um array de tal tamanho somente com zeros, usa-se `zeros()`

é possível criá-lo com várias dimensões

```python
np.zeros(5)

>>> array([0., 0., 0., 0., 0.])

np.zeros((2, 2))

>> array([0., 0.],
		 [0., 0.])
```

A mesma funcionalidade serve com o comando `ones()`, que ao invés de criar arrays com 0, cria com 1



Para criar um array de número até certo número com uma quantidade x de valores e com diferenças distância semelhantes, basta:

```python
np.linspace(2, 4, 5)

>>> array([2. , 2.5, 3. , 3.5, 4. ])
```

No código acima, criou-se um array de 2 até 4 com 5 componentes, componentes estes que incluem números float com porções iguais entre os mesmos



Para criar uma matriz identidade (elementos da diagonal principal igual a um, resto é zero), basta utilizar o `eye()`

seu único parâmetro compartilha as linhas e colunas e são retornados valores float

```python
np.eye(2)

>>> array([[1., 0.],
		   [0., 1.]])
```



É possível criar arrays com números aleatórios, entre 0 e 1 que sejam uniformemente distribuídos, da seguinte forma:

podem ter mais de uma dimensão

```python
np.random.rand(2, 3)

>>> array([[0.0314487 , 0.57989262, 0.30708956],
           [0.85592221, 0.37588996, 0.07690699]])

np.random.randn(2, 3)

>>> array([[ 1.2864043 , -0.24656661,  0.46346839],
           [ 0.19150343, -1.63669499,  0.02939655]])
```

Do mesmo jeito, é possível criar arrays com valores distribuídos por Gorshin *(?)* usando `np.random.randn()`

Os tipos de distribuição serão vistos mais para frente quando o tópico de vizualização de dados for abordado



Da mesma forma, usa-se `np.random.randint()`, tal como da famosa biblioteca random, para gerar um número aleatório inteiro

para transformar em um array, basta passar o terceiro parâmetro de tamanho

```python
np.random.randint(1, 11, 5)

>>> array([4, 7, 8, 5, 9])
```



Para remodelar a matriz sem mudar seus dados, usa-se o método `.reshape()`

```python
a = np.arange(25)
a

>>> array([ 0,  1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12, 13, 14, 15, 16,
       17, 18, 19, 20, 21, 22, 23, 24])

b = a.reshape(5, 5)
b

>>> array([[ 0,  1,  2,  3,  4],
       [ 5,  6,  7,  8,  9],
       [10, 11, 12, 13, 14],
       [15, 16, 17, 18, 19],
       [20, 21, 22, 23, 24]])
```

Para este método funcionar, o produto dos parâmetros deve ser igual ao total de valores dentro do array, caso contrário, um erro será gerado

> Caso seja printado, o print do array sai sem a presença de vírgulas entre um número e outro, contudo, caso seja apenas mostrado no display pelo Jupyter Notebook, as vírgulas se fazem presentes
>
> Do mesmo modo que a explicitação de ser um array apenas aparece na ausência do print



Por ser um array (eu acho que seja por isso), as funções `max()` e `min()` viram métodos da seguinte forma:

```python
b.max()
b.min()

>>> 24
	0
```

para achar o index do maior ou menor número do array, basta adicionar um 'arg' na frente dos métodos anteriores transformando-os assim: `argmax()` e `argmin()`



Para descobrir qual o tamanho de uma matriz, usa-se `.shape`, sem a presença de parênteses

o primeiro argumento é a quantidade de linhas e o segundo é a quantidade de colunas

Já para saber o número de elementos da matriz junto com o seu tipo, usa-se `.dtype`, também sem a presença dos parênteses

```python
b.shape

>>> (5, 5)

b.dtype

>>> dtype('int32')
```



Uma das diferenças entre uma lista e um array NumPy, é que você pode mudar valores em um array de uma vez no NumPy que normalmente não seria possível

```python
a = np.arange(0, 6) #certo
a[2:4] = 6
a

>>> array([0, 1, 6, 6, 4, 5])


a = [0, 1, 2, 3, 4, 5] # errado
a[2:4] = 6
a

>>> TypeError Traceback (most recent call last)
```



Deve-se tomar cuidado ao copiar (ou tentar copiar) um array, pois você pode estar apenas fazendo uma ligação entre o array "a" e o array "b"

> Assim como dizia lá mesmo no CursoemVideo do Guanabara!! :)

Para não ter tal erro de ligação entre arrays, usa-se o método `.copy()` para especificar que é uma cópia

NumPy tenta guardar memória a cada instância possível

```python
a = np.arange(11)
b = a[4:7].copy()
b[:] = 0

a
b

>>> array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
	array([0, 0, 0])
```



Para achar um valor em uma matriz, há 2 formas:

```python
a = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])

a[0,1] #primeiro jeito usando vírgula
a[0][1] # segundo jeito usando dois pares de colchete

>>> 2
```

> É interessante pensar que o primeiro valor seja a linha e o segundo valor seja a coluna

Caso queira ser feito um fatiamento da matriz, faz-se da seguinte forma:

```python
a[:2, 1:]

>>> [[2,3], [5, 6]]
# o código fatiará todos os valores antes da segunda linha e também todos os valores a partir da segunda coluna
```



Caso um vetor seja comparado à um valor inteiro, será retornado outro vetor com valores booleanos

é possível comparar o vetor normal e o booleano para printar somente os valores que satisfazem a condicional imposta

tal processo é chamado de **Indexação Condicional**

```python
a = np.arange(10)
b = a > 5
a[b]

# ou simplesmente

b
a[a>5]

>>> array([False, False, False, False, False, False,  True,  True,  True, True])
array([6, 7, 8, 9])
```



São várias as operações matemáticas que você pode usar utilizando arrays

as operações podem ser tanto feitas entre arrays, quanto feito entre arrays e valores escalares

a operação entre arrays será feita com seus respectivos valores de sua mesma posição no index

```python
a = np.arange(10)
>>> array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])

a + a
>>> array([ 0,  2,  4,  6,  8, 10, 12, 14, 16, 18])

a * a
>>> array([ 0,  1,  4,  9, 16, 25, 36, 49, 64, 81])

a + 2
>>> array([ 2,  3,  4,  5,  6,  7,  8,  9, 10, 11])

```

NumPy as vezes conseguirá executar seu código mesmo que aja um erro, tal como a divisão por 0

claro, uma mensagem de alerta será gerada para tal situação

Há inúmeras outras funções universais que são possíveis usar juntamente com os arrays do NumPy, tais como as neste link: https://numpy.org/doc/stable/reference/ufuncs.html



- ## Pandas - *Análise de dados*

Biblioteca feita para manipulação e análise de dados, oferece estruturas de dados e operações para manipular tabelas numéricas e séries temporais



A séries em Panda são bem similares aos arrays do NumPy, são até na realidade feitos deles

uma das diferenças entre os 2 é que no NumPy, os index inteiros que acessam os dados são implícitos, enquanto que no Panda, os mesmos são explícitos



Para acessar as séries no Panda, usa-se `.Series()`

```python
import pandas as pd

labels = ['a', 'b', 'c']

pd.Series(labels)

labels

>>> 0    a
	1    b
	2    c
	dtype: object
```

Devido ao fato do index agora estar explícito, acessá-los tornou-se muito mais fácil

"Uma versão mais clara e entendível do NumPy"

Use `Shift` + `Tab` para acessar os argumentos disponíveis de uma função no Jupyter Notebook



É possível mudar o nome do index do Panda por meio do argumento `index` na função `Series`:

``` python
data = [1, 2, 3]

pd.Series(data = data, index = labels)

>>> a    1
	b    2
	c    3
	dtype: int64
```

com isso, fica possível referir-se a um valor por meio de tal index mudado, melhorando o acesso aos dados

Como o `data` e o `index` estão em ordem, é possível simplificar seu código da seguinte maneira:

```python
pd.Series(data, labels)
```



O método `Series` pode mostrar não só inteiros e strings, mas também dicionários, listas e etc

Para extrair valores, basta referenciá-los por seu index, tal como em um dicionário



Caso seja feita uma operação matemática entre 2 arrays do `Pandas`, o retorno dos dados será `NaN` caso seus index não sejam os mesmos 

```python
series1 = pd.Series(data = [1, 2, 3, 4], index=["David", 'John', "Aasha", "Victor"])
series2 = pd.Series(data = [1, 2, 5, 6], index=["David", 'John', "Roger", "Natasha"])

series1 + series2

>>> Aasha      NaN
David      2.0
John       4.0
Natasha    NaN
Roger      NaN
Victor     NaN
dtype: float64
```

Os números inteiros são transformados em float depois da operação



Tudo que seja feito na biblioteca Pandas usará DataFrames de uma forma ou de outra

Imagine um DataFrame como um Excel

Para criar uma planilha do Excel, precisa-se dos dados de input, o index e o nome das colunas 

```python
import numpy as np
import pandas as pd
from numpy.random import randn

df = pd.DataFrame(randn(3,3),['A','B','C'],['X','Y','Z'])

>>>
```

![image-20220513040517805](C:\Users\Marco Neto\AppData\Roaming\Typora\typora-user-images\image-20220513040517805.png)

Foi usado o `numpy.random.rand` para gerar os números aleatórios para a planilha acima

DataFrame é importante por isso, o processamento dos dados matemáticos tornam-se bem mais simples

"São um grupo de colunas que compartilham o mesmo index"



Quando se é extraído uma coluna ou uma linha de um DataFrame, ela vira um Series do Panda

Para extrair mais de uma coluna, usa-se a seguinte sintaxe:

```python
df['X']

>>> A    1.331587
B   -0.008384
C    0.265512
Name: X, dtype: float64
```



```python
df[['Y', 'Z']]

>>>
```

![image-20220513041810418](C:\Users\Marco Neto\AppData\Roaming\Typora\typora-user-images\image-20220513041810418.png)



Para criar ou adicionar colunas a um DataFrame, deve-se prover todos os dados necessários, caso contrário, dará erro

```python
df['new'] = df['X'] + df['Y']
df

>>> 
```

![image-20220514112804297](C:\Users\Marco Neto\AppData\Roaming\Typora\typora-user-images\image-20220514112804297.png)

Foi apenas somado um valor com o outro no final



Para apagar colunas, usa-se o método `.drop(axis=1)` 

para apagar linhas, apenas o `.drop()` sem o parâmetro `axis`

Contudo, tais mudanças acima não são permanentes para o DataFrame, necessitando assim de mais um parâmetro, sendo ele o `inplace=True`

```python
df.drop('new', axis=1, inplace=True)
```



Para extrair uma linha, usa-se o método `.loc()` ou o `.iloc()`, os quais também a converte para uma Series

pense no "loc" como "localization", recebe o nome do objeto como parâmetro

e no "i" que poderá vir antes como "index", recebe o index do elemento como parâmetro



Para especificar um item do DataFrame, usa-se 2 parâmetros no método `.loc()`, primeiro a linha depois a coluna

Por fim, para fazer uma submatriz de uma matriz original, basta: 

```python
df.loc([['A', 'B'], ['X', 'Y']])
df

>>>
```

![image-20220515043923105](C:\Users\Marco Neto\AppData\Roaming\Typora\typora-user-images\image-20220515043923105.png)



É possível comparar um DataFrame com outro da seguinte forma:

> comparar pedaços de uma matriz também é possível

```python
newdf = df > 0

df[newdf]

# df[df > 0] ou comparando entre si

>>>
```

![](C:\Users\Marco Neto\AppData\Roaming\Typora\typora-user-images\image-20220515051723719.png)

ele irá retornar os valores originais caso o seu index do comparado seja True, senão, retorna NaN

NaN, convenhamos, não é uma forma sutil de demonstrar um dado, portanto, é possível por meio da comparação, comparar ainda mais, mostrando somente os dados que possuem algo

Método chamado de **Indexação Condicional**

> Saber como se funciona uma lista é perfeito pra esse tipo de trabalho

```python
df[df['X'] > 0]

>>>
```

![](C:\Users\Marco Neto\AppData\Roaming\Typora\typora-user-images\image-20220515051925775.png)

```python
df[df['X'] > 0]['X']

>>> A    0.556989
B    1.536716
E    0.284850
Name: X, dtype: float64
```



Os operadores `and` ou `or` do Python não conseguem comparar 2 Series, precisando utilizar o `&` e o `|`

```python
df[(df["W"]>0) | (df["Y"]>1)]
```



Para resetar o nome do index do DataFrame para o padrão do Python (decimal), usa-se `.reset_index()`

o index antigo será salvo como uma nova coluna

não muda permanentemente o DataFrame original, apenas com `inplace=True`



Para renomear o seu index, usa-se `.set_index()`

é necessário que a quantidade do parâmetro seja igual ao número de linhas

```python
newind = 'PA PR RJ SP BA'.split()

df['Estados'] = newind

df.set_index('Estados')

>>>
```

![image-20220515074106393](C:\Users\Marco Neto\AppData\Roaming\Typora\typora-user-images\image-20220515074106393.png)



Quando for converter um dicionário para um DataFrame, a chave será o nome das colunas e seus valores serão os próprios valores, podendo salientar o nome dos seus index pelo parâmetro de mesmo nome

para permitir a criação de valores `NaN`, usa-se `np.nan`

usa-se `pd.DataFrame()` para tal

```python
pd.DataFrame({"A":[1,2,np.nan],"B":[4,np.nan,np.nan],"C":[1,2,3]}, index= ['oi', 'ola', 'oie'])

>>>
```

![](C:\Users\Marco Neto\AppData\Roaming\Typora\typora-user-images\image-20220516033430472.png)



Para resolver a eventual falta de alguns valores no DataFrame (`NaN` ou `Null`),  pode-se:

- REMOVER

  `.dropna()` - Remove todas as linhas que possuem valor nulo

  para remover as colunas, adiciona-se o parâmetro `axis=1`

  usa-se o parâmetro `thresh` para salientar quantos elementos não nulos a matriz deve ter para não ser excluída

- SUBSTITUIR

  `.fillna()` - Substitui o NaN pelo valor passado no parâmetro



Usa-se o `.mean()` para calcular a média de uma lista



`.groupby()` é usado para juntar linhas de uma coluna para realizar funções de agregação

é possível acessar a localização na memória onde se está sendo guardado os dados apenas o printando

pode-se realizar operações com seus resultados, assim como o `.loc()` para retornar apenas uma parte

Usa-se o `.describe()` para dar informações adicionais da matriz

Para trocar colunas por linhas e vive versa, usa-se `.transpose()`



Há 3 formas de juntar matrizes: Mesclar, Juntando e Concatenando

- `pd.concat()` - CONCATENAR

  As dimensões e o axis devem ser iguais para funcionar

  recebe uma lista dos DataFrames a serem concatenados

  caso o parâmetro `axis` seja 1, a lista será concatenada pelas colunas, senão, pelas linhas

  ```python
  pd.concat([df1,df2,df3], axis=1)
  
  >>>
  ```

  ![image-20220516035626741](C:\Users\Marco Neto\AppData\Roaming\Typora\typora-user-images\image-20220516035626741.png)

  

- `pd.merge()` - MESCLAR

  Funciona mesclando colunas

  Localiza por padrão as chaves comuns e as mescla sem criar outras colunas

  seu parâmetro `on` determina quais chaves não serão repetidas como colunas, caso elas existam em ambas as matrizes, senão dá erro

  ```python
  left = pd.DataFrame({'key1': ['K0', 'K0', 'K1', 'K2'],
                       'key2': ['K0', 'K1', 'K0', 'K1'],
                          'A': ['A0', 'A1', 'A2', 'A3'],
                          'B': ['B0', 'B1', 'B2', 'B3']})
      
  right = pd.DataFrame({'key1': ['K0', 'K1', 'K1', 'K2'],
                        'key2': ['K0', 'K0', 'K0', 'K0'],
                          'C': ['C0', 'C1', 'C2', 'C3'],
                          'D': ['D0', 'D1', 'D2', 'D3']})
  
  pd.merge(left, right, on=['key1', 'key2'])
  ```

![image-20220516042428984](C:\Users\Marco Neto\AppData\Roaming\Typora\typora-user-images\image-20220516042428984.png)



- `.join()` - JUNTAR

  É possível juntas matrizes usando seu index

  pode usar como parâmetro o `how` para diferentes tipos de juntar, como `how='inner'`, negando linhas com valores NaN, ou `how='outer'`, printando valores NaN



`.head()` retorna os primeiros valores e o `.tail()` retorna os últimos valores



`.unique()` retorna os valores únicos de um vetor

`.nunique()` retorna o número de valores únicos (igual em `len()`)



Para criar uma tabela com todos os valores únicos junto com o número de vezes que se repetem,  usa-se o método `.value_counts()`

```python
df["col1"].value_counts()

>>> 4    1
3    1
2    1
1    1
Name: col1, dtype: int64
```



Função poderosíssima é o `.aplly()`, a qual permite que sejam integradas funções diretamente nos valores dos vetores

```python
def times2(x):
    return x*2
    
df['col2'].apply(times2)
# df['col2'].apply(lambda x: x*2) podendo ser feito com lambda também

>>> 0    2
1    4
2    6
3    8
Name: col1, dtype: int64
```



Usa-se `.columns` para retornar as colunas, `.index` para o index e `.isnull()` para salientar os valores nulos



Para sortear os valores de um DataFrame de certa forma, usa-se `.sort_values()`, como parâmetro a coluna e aceitando o `axis` também



Para extrair conteúdo .csv, basta usar `pd.read_csv()` e o nome do arquivo como parâmetro

é importante acrescentar `index_col=[0]`  para não ter problemas de estética 

Já para transformar em conteúdo .csv, basta `.to_csv()` e o nome do novo arquivo como parâmetro

é importante acrescentar `index=False`  para não ter problemas de estética 

> os "read" e "to"  existem para vários tipos de arquivos e funcionam da mesma forma para todos



Para arquivos Excel, é importantíssimo salientar qual o "Sheet" a ser trabalhado para evitar erros

```python
pd.read_excel("Excel_Sample.xlsx", sheet_name="Sheet1")
```



O método `pd.read_html()` procura automaticamente dentro do código html do site a tag `<table>`

É preferível que seja printado a tabela como `data[0]` do que `data` por motivos estéticos



- ## Matplotlib - *Visualização de dados*

É uma biblioteca multiplataforma de visualização de dados e plotagem gráfica para o Python e suas extensões numéricas do NumPy



- ## Seaborn - *Visualização de dados*

Uma biblioteca de visualização de dados baseada no matplotlib, provém interface de altíssimo nível para desenhar informativos e atrativos gráficos estatísticos



A seguir, algumas distribuições do Python próprios para o uso de dados:

- ## Anaconda

  - Visa simplificar a manutenção de pacotes e o seu deploy
  - Várias ferramentas e bibliotecas usados em Data Science e Machine Learning em uma única instalação
  - Tem o seu próprio sistema de ambiente virtual 



- ## Jupyter

  - É uma IDE interativa
  - Você pode combinar seu código com seu output, texto, e vários outros tipos de arquivos multimídia em um único documento
  - É praticamente único devido aos seus recursos



Por si só não possui uma interface, usa portanto a do Google Chrome como tal

não precisa de internet caso inicializado desta forma memso sendo no Google

É possível também abrir o Jupyter pelo prompt de comando, entrando na pasta do Anaconda e digitando o comando `jupyter notebook`



Quando você estiver usando uma função para printar um output, ele não receberá a especificação de tal ação, contanto, caso o mesmo seja feito com uma operação numérica e sem funções de print, a especificação aparece

```python
In [1]: print('Hello World')
		Hello World

In [2]: 100 + 100
Out[2]: 200
```



Pressiona-se `Shift + Enter` como atalho para fazer seu código rodar

e `Alt + Enter` para fazer surgir outra célula de código 

> o de cima também o faz caso não exista código na célula a ser executada

Cada vez que seu código for rodado, o número de execuções, do lado do `In` também irá aumentar

Jupyter Notebook salvará automaticamente seus arquivos em extensão `.ipynb` 

Para sair de um loop infinito, basta reiniciar o programa na interface da IDE

É possível transformar as células em 'markdown', onde pode-se escrever livremente tal como em um comentário

tais células usam a mesma codificação que os arquivos .md, tal qual este mesmo arquivo, com as suas próprias formatações



É possível usar tanto o `pip` quanto o `conda` para realizar instalação de bibliotecas no Python



## Python Revisão Básica

> A maioria da parte básica de Python não será transcrita porque sim :)

O Python possui 5 tipos de dados e alguns possuem subcategorias:

1. Numérico
   1. Inteiros
   2. Números Complexos
   3. Float
2. Dicionário
3. Booleano
4. Set
5. Tipos de Sequência
   1. Strings
   2. Listas
   3. Tuplas



No Jupyter Notebook não é necessário a função print se você quer apenas mostrar um output, tudo que é preciso fazer é digitar o nome da variável e pressionar `Enter`

você não estará o printando, e sim apenas o mostrando no display



Um dicionário é mantido pela sua relação par de chave-valor

O dicionário não aceita valores duplicados



Os operadores relacionais são aqueles de comparação e os operadores lógicos são como `and` e `or`



```python
In [0]: def greet():
			print('Hello!')
	
In [1]: greet()
```

O código acima iria dar erro pois no Jupyter Notebook, a declaração da função ainda não havia sido executada como pode ser visto no `In [0]`, mesmo vindo antes da chamada de sua função
