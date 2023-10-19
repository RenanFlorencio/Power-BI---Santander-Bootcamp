# Santander Bootcamp Power BI Analiyst

## Desafio Módulo 2

Criação de um relatório utilizando PowerBI a partir de banco dados fornecido. Análises de vendas, lucro e gastos foram feitos com o auxilio de diversos elementos visuais.

A página modelada e inserida por mim está mostrada abaixo:

![image](https://github.com/RenanFlorencio/Power-BI---Santander-Bootcamp/assets/122649765/58ad792c-6c6e-4b94-bc99-2674eb46b830)

## Desafio Módulo 3

Nesse desafio foi utilizada uma conexão do Power BI ao MySQL para a obtenção dos dados. A trasnformação dos dados foi feita a partir do Power Query.

O primeiro passo para a transformação é a verificação dos cabeçalhos e dos tipos de dados de cada coluna para todas as tabelas.

* Remover colunas desnecessárias. 

* Separar os endereços dos employees de modo que número, rua, cidade e estado estejam separados usando delimitador de colunas e corrigindo casos individuais. Aqui percebemos que todos os
empregados são do Texas, então não precisamos de uma coluna para estado.

* Preencher valores nulos baseados no contexto em que estavam inseridos.

* Concatenar local e nome do departamento para criar uma chave única para os departamentos.

Também foi criada uma nova tabela mesclada com trabalhadores e seus respectivos departamentos e gerentes de departamento, além dos nomes dos gerentes de cada um deles.

Por fim, as colunas de nome foram concatenadas de forma a obter uma informação mais completa.

Depois de já importados, criei uma nova tabela a partir da seguinte consulta SQL que retorna a quantidade de funcionários de cada gerente:

```
SELECT CONCAT(Fname, ' ', Lname) AS FullName, Funcionarios FROM employee AS e,
(
    SELECT Mgr_ssn, count(*) AS Funcionarios FROM departament AS d 
    INNER JOIN employee AS e ON e.Super_ssn = d.Mgr_ssn GROUP BY Mgr_ssn
) AS cont
WHERE (e.Ssn = cont.Mgr_ssn);
```

Assim temos um banco de dados pronto para ser visualizado com PowerBI. 

![imagem_2023-10-17_163435858](https://github.com/RenanFlorencio/Power-BI---Santander-Bootcamp/assets/122649765/68ed941b-b633-4112-93be-706f79cae485)

