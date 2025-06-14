Relatório de evasão de clientes
Autor: Matheus Pereira Costa

Data: 14/06/2025

Contextualização
De acordo com os ultimos dados obtidos foram percebidos um aumento no número de evasões de clientes devido a esse mótivo foi solicitado um estudo sobre as possíveis causas e se haveriam alguma relação entre elas.

Metodologia
A metodologia aplicada para obter os dados foi através da biblioteca requests onde foi feito uma consulta do tipo get na API que se encontra em GitHub.

Após trazer esses dados para dentro do projeto de análise, foi verificado que ele havia 7267 linhas e 6 colunas. Foi transformado em dataframe com a biblioteca do pandas e posteriormente expandidas as colunas que estavam com dados em formato de dicionário usando pd.json_normalize, resultando em um dataframe com 7267 linhas e 22 colunas.

Validação dos Dados
Não foram encontrados dados nulos ou duplicados
Padronização de colunas binárias (Yes/No transformado para formato binominal numérico 1/0)
Padronização de dados com mais de uma forma de escrita, exemplo (No/No phone service)
Identificados e removidos 224 casos com espaços em branco na coluna Churn
Análise Exploratória
Taxa de evasão (Churn): 26.54% do total
Tabelas de apoio
Ressalta-se que como os dados binários foram transformados para númericos então em colunas com 0 significa não/não evadiu e 1 sim/evadiu

Categóricas
+--------------------------+
|          gender          |
+-------+----------+-------+
| Churn | Category | Value |
+-------+----------+-------+
|   0   |  Female  |  2549 |
|   0   |   Male   |  2625 |
|   1   |  Female  |  939  |
|   1   |   Male   |  930  |
+-------+----------+-------+
+--------------------------+
|      SeniorCitizen       |
+-------+----------+-------+
| Churn | Category | Value |
+-------+----------+-------+
|   0   |    0     |  4508 |
|   0   |    1     |  666  |
|   1   |    0     |  1393 |
|   1   |    1     |  476  |
+-------+----------+-------+
+--------------------------------+
|            Contract            |
+-------+----------------+-------+
| Churn |    Category    | Value |
+-------+----------------+-------+
|   0   | Month-to-month |  2220 |
|   0   |    One year    |  1307 |
|   0   |    Two year    |  1647 |
|   1   | Month-to-month |  1655 |
|   1   |    One year    |  166  |
|   1   |    Two year    |   48  |
+-------+----------------+-------+
+-------------------------------------------+
|               PaymentMethod               |
+-------+---------------------------+-------+
| Churn |          Category         | Value |
+-------+---------------------------+-------+
|   0   | Bank transfer (automatic) |  1286 |
|   0   |  Credit card (automatic)  |  1290 |
|   0   |      Electronic check     |  1294 |
|   0   |        Mailed check       |  1304 |
|   1   | Bank transfer (automatic) |  258  |
|   1   |  Credit card (automatic)  |  232  |
|   1   |      Electronic check     |  1071 |
|   1   |        Mailed check       |  308  |
+-------+---------------------------+-------+
Numéricas
+------------------------------------------------------------+
|                      Charges.Monthly                       |
+-------+-----------+-------------------+--------------------+
| Churn |    Sum    |        Mean       |        Std         |
+-------+-----------+-------------------+--------------------+
|  0.0  | 316985.75 | 61.26512369540008 | 31.09264811934529  |
|  1.0  | 139130.85 | 74.44133226324237 | 24.666053259397444 |
+-------+-----------+-------------------+--------------------+
+--------------------------------------------------------------+
|                        Charges.Total                         |
+-------+------------+--------------------+--------------------+
| Churn |    Sum     |        Mean        |        Std         |
+-------+------------+--------------------+--------------------+
|  0.0  | 13193241.8 | 2555.344141003293  | 2329.4569835604348 |
|  1.0  | 2862926.9  | 1531.7960941680042 | 1890.8229944644058 |
+-------+------------+--------------------+--------------------+
+----------------------------------------------------------------------+
|                            Charges.Daily                             |
+-------+--------------------+--------------------+--------------------+
| Churn |        Sum         |        Mean        |        Std         |
+-------+--------------------+--------------------+--------------------+
|  0.0  | 10566.191666666668 | 2.0421707898466694 | 1.036421603978175  |
|  1.0  |      4637.695      | 2.481377742108079  | 0.8222017753132481 |
+-------+--------------------+--------------------+--------------------+
+------------------------------------------------------------+
|                           tenure                           |
+-------+----------+--------------------+--------------------+
| Churn |   Sum    |        Mean        |        Std         |
+-------+----------+--------------------+--------------------+
|  0.0  | 194387.0 | 37.56996521066873  | 24.113776690704086 |
|  1.0  | 33603.0  | 17.979133226324237 | 19.531123054519544 |
+-------+----------+--------------------+--------------------+
Gráficos


![Distribuição de evasão](image-1.png)
![Matriz de Correlação](image-2.png)



Conclusão
Ao avaliar os dados, é possível compreender que entre os clientes que deixaram a empresa estão aqueles que possuem o contrato de Month-to-Month representam 88.55% do total que deixaram a empresa.

Outra categoria que trâs dados importantes sobre o caso é o metodo de pagamento ou PaymentMethod, que os que optaram pela modalidade Electronic check representam 57.30% do total que deixaram a empresa.

A correlação é fraca entre os elementos ao compara-los com a coluna de evasão/Churn.

Portanto, para solucionar o problema sugiro uma revisão nos contratos e na forma de pagemnto sendo eles como causadores principais de tais efeitos.