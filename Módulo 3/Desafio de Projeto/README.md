
# Desafio Power Bi 2

## Problemas encontrados

Ao instalar o conector my sql connector por algum motivo o Power BI não o reconheceu, depois de várias tentativas de reisntalação que resultaram no mesmo erro, resolvi instalar o MySQL no VSCode, após a instalação o problema foi resolvido e consegui realizar a conecção do Power BI com o banco de dados.

## Transformações realizadas

 Foi realizada a verificação dos cabeçalhos e tipos de dados.
 Modificação dos valores monetários para o tipo decimal fixo.
 Foi localizado um valor nulo, na tabela employees coluna super_ssn, porém ao realizar a análise foi constatado que se tratava de um colaborador numa posição acima de gerente. 
 Não foram encontradoos departamentos sem gerente.
 Ao analisar o número de horas dos projetos foi utilizado uma fórmula DAX no Power Bi e não no Power Query, uma vez que o primeiro não trabalha com  número de horas acima de 24 horas, para realização de cálculos foi mantido o formato decimal.

Fórmula DAX utilizada:

Tempo_Total = 
var hora = INT(SUM('azure_company works_on'[Hours]))
var minuto = INT((SUM('azure_company works_on'[Hours]) - hora) * 60)
var segundo = ROUND((INT(SUM('azure_company works_on'[Hours]) - hora) * 60 - minuto) * 60,0)

var HH = FORMAT(hora, "00")
var MM = FORMAT(minuto, "00")
var SS = FORMAT(segundo, "00")

return

VALUE (HH & MM & SS)

 Foi realizada a divisão da coluna Address em 3 novas colunas, street, number e state.
 Realizada a mescla das tabelas employee e department criando uma nova tabela department_employee.
 Após análise foram eliminadas as colunas desnecessárias.
 Junção dos colaboradores e gerentes utilizando mescla.
 Após a mescla das colunas nome e sobrenome foi utilizado a coluna de exemplos para formatar os nomes dos colaboradores, por fim foram deletadas as colunas orginais.
 Mescla das tabelas departamentos e lozacalização realizada na tabela azure_company dept_location.Porque o mesclar leva em consideração um valor em comum na coluna evitando repetições
 Análise de quantos colaboradores existe por gerente:

[x]Agrupe os dados a fim de saber quantos colaboradores existem por gerente



## Links:

* Fórmula DAX: Canal do Youtube Como usar Power BI
link: https://www.youtube.com/watch?v=cKX4F9DsRoY

* Banco de dados na Azure:
link: desafio-power-bi-dio.mysql.database.azure.com


