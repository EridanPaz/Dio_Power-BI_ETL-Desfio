## Dio_Power-BI_ETL-Desfio

## 1. Feita a Criação da instância Azure/MySql.
	Imagem: Conexão_Wirkbench_Azure.PNG.
## 1.1. Apesar de várias tentativas instalando conectores, não foi possível fazer conexão Power BI x Instância Azure/MySql.
	Imagem: Problema com o conector MySql.PNG.
	
## 2. A solução foi criar um banco local em Firebird, povoá-lo e conectá-lo através do conector ODBC.
  Imagem: ODBC.PNG.
	Arquivo do Banco: AZURE_COMPANY.FDB.
	DER do banco: DER.grc.
	Imagem: DER.PNG.

## 3. Foi feita alteração dos nomes das tabelas para o idioma português para ficar mais legível e amigável.

## 4. Exluídas todas as colunas de metadados.

## 5. Foi criada a tabale DEPTO_FUNCIONÁRIO com a mesclagem da tabela FUNCIONÁRIO x DEPARTAMENTO.
##   5.1. TRANSFORMAR DADOS -> PÁGINA INICIAL -> COMBINAR -> MESCLAR CONSULTAS COMO NOVAS.
##   5.2. Foi gerada a consulta usando como base os campos MGR_SSN (de Departamento) x SSN (de Funcionário).

## 6. Foi criada a tabale FUNCIONÁRIO_DEPTO com a mesclagem da tabela DEPARTAMENTO x FUNCIONÁRIO (mesmo caminho descrito em 3.1).
##   6.1. Criada a coluna DNome para exibir o nome dos Departamentos.
##   6.2. Mescladas as colunas PRIMEIRO_NOME, INÍCIO_NOME_MEIO e ÚLTIMO_NOME.

## 7. Foi relizada a junção entre funcionários e gerentes numa consulta denominada GERENTE_FUNCIONÁRIO, pelo código SQL abaixo:

   SELECT F.FNAME || ' ' || F.MINIT || ' ' || F.LNAME GERENTE,
          G.FNAME || ' ' || G.MINIT || ' ' || G.LNAME FUNCIONARIO
     FROM EMPLOYEE G
     JOIN EMPLOYEE F ON G.SUPER_SSN = F.SSN
	 
## 8. Mescladas as tabelas DEPARTAMENTO x LOCALIZAÇÃO
 	 
## 9. Criado o relatório no Power BI.
## 10. O relatório criado foi publicado no Power BI Service.
