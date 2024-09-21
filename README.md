# Modelando um Dashboard de E-commerce com Power BI Utilizando Fórmulas DAX

## Contexto:
Este projeto tem como objetivo criar um Dashboard de E-commerce no Power BI utilizando Fórmulas DAX para análise de dados. A fonte principal de dados é a tabela Financial Sample, que contém informações sobre vendas de produtos. O modelo de dados foi estruturado em um esquema estrela, criando tabelas de dimensão e uma tabela fato, permitindo uma análise eficiente e escalável de métricas relacionadas a vendas, descontos e performance de produtos.

## Execução:
Depois de configurar o ambiente, siga os seguintes passos para executar o projeto:

**Criar as Tabelas de Dimensão e Fato:**

Utilize a tabela original Financial Sample para criar as tabelas de dimensão e fato. A partir dela, serão extraídos os dados para a construção das dimensões D_Produtos, D_Produtos_Detalhes, D_Descontos, D_Calendário, e D_Detalhes, além da tabela de fato F_Vendas.

**Definir Relacionamentos:**

Acesse a aba de Modelagem e defina os relacionamentos entre as tabelas. Os relacionamentos são do tipo um para muitos entre as dimensões e a tabela fato, com base em campos como ID_Produto e Date.

**Criar Medidas e Colunas Calculadas com DAX:**

Utilize DAX (Data Analysis Expressions) para criar medidas e colunas calculadas que permitem a análise de métricas de vendas, como lucros, descontos aplicados e performance por produto.
Exemplos de medidas incluem a soma de vendas (SUM(Sales)), média de unidades vendidas (AVERAGE(Units Sold)), e lucro total (SUM(Profit)).

**Visualizar o Dashboard:**

Crie visualizações interativas no Power BI utilizando gráficos de colunas, tabelas, e gráficos de linha para representar o desempenho das vendas de e-commerce. Personalize o dashboard para incluir filtros por país, segmento, faixa de desconto e período de tempo.

## Estrutura:

**1. Tabela Fato:**

F_Vendas: Armazena todos os dados transacionais das vendas.
Campos principais: ID_Produto, Sales, Units Sold, Sales Price, Discount Band, Segment, Country, Profit, Date.

**2. Tabelas de Dimensão:**
D_Produtos: Contém dados agregados dos produtos, incluindo médias e valores máximos e mínimos.

**Campos principais:**
Product, Média de Unidades Vendidas, Média do Valor de Vendas, Valor Máximo de Venda, Valor Mínimo de Venda.
D_Produtos_Detalhes: Detalhes específicos dos produtos, como preço de manufatura e unidades vendidas.

**Campos principais:**
Product, Manufacturing Price, Sales Price, Units Sold.
D_Descontos: Armazena informações sobre os descontos aplicados a cada produto.

**Campos principais:**
Discount, Discount Band, ID_Produto.
D_Detalhes: Contém informações complementares sobre as vendas que não foram detalhadas nas demais dimensões.

**Campos principais:**
Sales, COGS, Country, Discount Band, ID_Produto.
D_Calendário: Gerada por DAX para permitir a análise temporal.

**Campos principais:**
Date, Year, Month, Month Number.

### 3. Relacionamentos:
O modelo segue um esquema estrela, onde todas as tabelas de dimensão estão conectadas à tabela fato F_Vendas:

F_Vendas [ID_Produto] → D_Produtos [ID_Produto]
F_Vendas [ID_Produto] → D_Produtos_Detalhes [ID_Produto]
F_Vendas [ID_Produto] → D_Descontos [ID_Produto]
F_Vendas [Date] → D_Calendário [Date]
