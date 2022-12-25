
# Exercícios Básicos ________________________________
B_1 – Retornar nome de peças com peso > 500kg e peso < 700kg. <br>
( tabela: Production.Product - colunas: Weight, Name )
>`SELECT` Name <br>
>`FROM` Production.Product <br>
>`WHERE` Weight > 500 `AND` Weight < 700

<br>
___________________________________________________________________________________________________

B_2 – Retornar relação de empregados casados e assalariados. <br>
( tabela: HumanResources.Employee - colunas: MaritalStatus, SalariedFlag )
> `SELECT` * `FROM` HumanResources.Employee<br>
> `WHERE` MaritalStatus = 'M' `AND` SalariedFlag = 1;

<br>
___________________________________________________________________________________________________

B_3 – Retornar email de usuário chamado Peter Krebs. <br>
( tabela: Person.Person, Person.EmailAdress - colunas: FirstName, LastName ) <br>
( tabela: Person.EmailAddress, Person.EmailAdress - colunas: EmailAddress, BusinessEntityID )

>//acessa nome para descobrir ID <br>
>`SELECT` * `FROM` Person.Person <br>
>`WHERE` FirstName = 'Peter' `AND` LastName = 'Krebs';	

>//acessa o email utilizando o ID= 26, para descobrir email <br>
>`SELECT` EmailAddress `FROM` Person.EmailAddress	<br>
>`WHERE` BusinessEntityID = 26;

<br>
___________________________________________________________________________________________________

B_4 – Retornar quantidade de tamanhos diferentes de produtos cadastrados. <br>
( tabela: Production.Product - colunas: Size )
>`SELECT COUNT` ( Size )<br>
>`FROM` Production.Product;

<br>
___________________________________________________________________________________________________

B_5 – Retornar 100 clientes ordenadamente - nomes ( crescente ) e sobrenomes ( decrescente ) <br>
( tabelas: Person.Person - colunas: FirstName, LastName )
>`SELECT TOP` 100 FirstName,LastName <br>
>`FROM` Person.Person <br>
>`ORDER BY` FirstName `ASC`, LastName `DESC`;

<br>
___________________________________________________________________________________________________

B_6 – Retornar 10 primeiros produtos e valores em ordem decrescente <br>
( tabela: Production.Product - colunas: ProductID, ListPrice )
>`SELECT TOP` 10 ProductID, ListPrice <br>
>`FROM` Production.Product <br>
>`ORDER BY` ListPrice `DESC`;

<br>
___________________________________________________________________________________________________

B_7 - Retornar datas de contratação e departamentos de forma ordenada entre 01/01/2009 - 01/01/2010 <br>
( tabelas: HumanResources.Department, HumanResources.Employee - colunas: GroupName, HireDate )
>`SELECT` `DISTINCT` GroupName,HireDate <br>
>`FROM` HumanResources.Department, HumanResources.Employee <br>
>`WHERE` HireDate `BETWEEN` '2009/01/01' `AND` '2010/01/01' <br>
>`ORDER BY` GroupName `ASC`;

<br>
___________________________________________________________________________________________________

B_8 – Retornar tabela de pessoas que possuem BusinesEntityID de 2, 7, 13 <br>
( tabelas:Person.Person - colunas: BusinessEntityID )
>`SELECT` * `FROM` Person.Person <br>
>`WHERE` BusinessEntityID `IN` (2, 7, 13); 

<br>
___________________________________________________________________________________________________

B_9- Retornar quantidade de produtos cadastrador no sistema custando mais de 1500 dolares.<br> 
( tabela: Production.Product - colunas: ListPrice )
>`SELECT COUNT` ( ListPrice ) `FROM` Production.Product
>`WHERE` ListPrice > 1500;

<br>
___________________________________________________________________________________________________

B_10- Retornar quantidade de pessoas com o sobrenome iniciando com P. <br>
( tabela: Person.Person - colunas: LastName ) 
>`COUNT` e `WHERE` e `LIKE`<br>
>`SELECT COUNT` ( LastName ) `FROM` Person.Person<br>
>`WHERE` LastName `LIKE` 'p%';

<br>
___________________________________________________________________________________________________

B_11- Retornar quantidade de cidades únicas cadastradas pelos clientes. <br>
( tabela: Person.Address - coluna: City )
>`SELECT COUNT` ( `DISTINCT` City )<br>
>`FROM` Person.Address;

<br>
___________________________________________________________________________________________________

B_12- Quantos produtos vermelhos tem preço entre 500 e 100 dolares? <br>
( tabela: Production.Product - colunas: Color, ListPrice )
>`SELECT COUNT` ( Color )			
>`FROM` Production.Product
>`WHERE` Color = 'Red' `AND` ListPrice `BETWEEN` 500 `AND` 1000;

<br>
___________________________________________________________________________________________________

B_13- Calcular o total de todas as vendas e adicionar o nome as colunas.<br>
( tabela: Sales.SalesOrderDetail - coluna: LineTotal )
>`SELECT TOP` 10 `SUM`( LineTotal ) `AS` “NovoNomeColuna”<br>
>`FROM` Sales.SalesOrderDetail

<br>
___________________________________________________________________________________________________

B_14-Retornar quantidade de produtos cadastrados com a palavra ‘road’ no nome. <br>
( tabela: Production.Product - coluna: Name )
>`SELECT COUNT` ( * ) <br>
>`FROM` Production.Product <br>
>`WHERE` Name `LIKE` '%road%'

<br>
___________________________________________________________________________________________________
<br>
<br>

# Exercícios Intermediários ________________________________
___________________________________________________________________________________________________
I_1- Quanto cada produto vendeu ao todo até hoje <br>
( tabela: Sales.SalesOrderDetail - coluna: ProductID )
>`SELECT` * `FROM` Sales.SalesOrderDetail <br>
>`SELECT` ProductID, `COUNT` ( ProductID ) `AS` "CONTAGEM" <br>
>`FROM` Sales.SalesOrderDetail <br>
>`GROUP BY` ProductID

<br>
___________________________________________________________________________________________________

I_2- Retornar a média de preços para produtos que são prateados ( silver )
( tabela: Production.Product )
>`SELECT` Color, `AVG` ( ListPrice ) "PRECO" <br> 
>`FROM` Production.Product <br> 
>`WHERE` Color = 'silver' <br> 
>`GROUP BY`  Color

<br>
___________________________________________________________________________________________________

I_3- Retorne um lista de quantas pessoas tem o mesmo MiddleName. <br> 
( tabela: Person.Person	- coluna: FirstName, MiddleName )
>`SELECT` MiddleName, `COUNT` ( FirstName ) `AS` "Quantidade" <br> 
>`FROM` Person.Person <br> 
>`GROUP BY` MiddleName

<br>
___________________________________________________________________________________________________

I_4- Retorne a quantidade (quantity) que cada produto é vendido na loja <br>
( tabela: Sales.SalesOrderDetail - coluna: ProductID, OrderQty )
>`SELECT` ProductID, `AVG` ( OrderQty ) "Media" <br>
>`FROM` Sales.SalesOrderDetail <br>
>`GROUP BY` ProductID

<br>
___________________________________________________________________________________________________

I_5- Quais os nomes no sistema tem uma ocorrencia mais que 10 vezes ( Tabela (Person.Person)  utilizar (GROUP BY, HAVING ) )
>`SELECT` FirstName, `COUNT` ( FirstName ) `AS` ‘QUANTIDADE’ <br>
>`FROM` Person.Person <br>
>`GROUP BY` FirstName <br>
>`HAVING COUNT` ( FirstName ) > 10

<br>
___________________________________________________________________________________________________
