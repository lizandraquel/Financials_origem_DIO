 Power BI – Modelo Estrela com Financial Sample
 Objetivo
Este projeto tem como objetivo transformar a tabela única Financial Sample em um modelo estrela (star schema), criando tabelas dimensão e fato para análises mais organizadas e eficientes no Power BI.


1. Preparação

Importação da tabela Financial Sample.
Renomeada para Financials_origem e marcada como oculta (backup).

2. Criação das Dimensões

D_Produtos → agregações de produto (médias, máximos, mínimos).
D_Produtos_Detalhes → preços, manufatura, unidades vendidas.
D_Descontos → faixas e percentuais de desconto.
D_Detalhes → país, segmento, vendedor.
D_Calendario → criada via DAX com CALENDAR(), contendo Ano, Mês, Trimestre e Dia da Semana.

3. Criação da Fato

F_Vendas → tabela central com vendas, lucro, unidades, preço, descontos e datas.
Inclui chave ID_produto e SK_ID para relacionamentos.

4. Relacionamentos

F_Vendas[ID_produto] → D_Produtos[ID_produto]
F_Vendas[ID_produto] → D_Produtos_Detalhes[ID_produto]
F_Vendas[ID_produto] → D_Descontos[ID_produto]
F_Vendas[ID_produto] → D_Detalhes[ID_produto]
F_Vendas[Date] → D_Calendario[Date]