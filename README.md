# Desafio-DIO-PowerBI-DAX

Desafio: Modelando um Dashboard de E-commerce com Power BI Utilizando Fórmulas DAX
Descrição do Desafio de Projeto
Utilizaremos a tabela única de Financial Sample para criar as tabelas dimensão e fato do nosso modelo baseado em star schema.

O processo consiste na criação das tabelas com base na tabela original. A partir da cópia serão selecionadas as colunas que irão compor a visão da nova tabela. Sendo assim, a partir da tabela principal serão criadas as tabelas:

Financials_origem (modo oculto – backup)
D_Produtos (ID_produto, Produto, Média de Unidades Vendidas, Médias do valor de vendas, Mediana do valor de vendas, Valor máximo de Venda, Valor mínimo de Venda)
D_Produtos_Detalhes (ID_produto, Discount Band, Sale Price, Units Sold, Manufacturing Price)
D_Descontos (ID_produto, Discount, Discount Band)
D_Detalhes (*)
D_Calendário – Criada por DAX com calendar()
F_Vendas (SK_ID, ID_Produto, Produto, Units Sold, Sales Price, Discount Band, Segment, Country, Sales, Profit, Date)
D_Detalhes deve conter informações adicionais sobre vendas que não foram contempladas nas outras tabelas dimensão.

Passo a Passo
1. Preparação do Ambiente e Criação da Tabela Financials_origem
Importe a tabela Financial Sample no Power BI.
Renomeie a tabela importada para Financials_origem e oculte-a para utilizá-la como backup.
2. Criação das Tabelas Dimensão
D_Produtos:

Criar uma nova tabela com as colunas:
ID_produto (criado usando a função RANKX ou outra lógica para gerar IDs únicos)
Produto
Média de Unidades Vendidas (calculado com AVERAGE)
Média do valor de vendas (calculado com AVERAGE)
Mediana do valor de vendas (calculado com MEDIAN)
Valor máximo de Venda (calculado com MAX)
Valor mínimo de Venda (calculado com MIN)
D_Produtos_Detalhes:

Criar uma nova tabela com as colunas:
ID_produto
Discount Band
Sale Price
Units Sold
Manufacturing Price
D_Descontos:

Criar uma nova tabela com as colunas:
ID_produto
Discount
Discount Band
D_Calendário:

Criar uma nova tabela de calendário usando a fórmula DAX:

D_Calendário = CALENDAR(MIN(Financials_origem[Date]), MAX(Financials_origem[Date]))
D_Detalhes:

Criar uma nova tabela com informações adicionais sobre vendas não contempladas nas outras tabelas dimensão.
3. Criação da Tabela Fato
F_Vendas:

Criar uma nova tabela com as colunas:
SK_ID (chave substituta gerada com RANKX ou outra lógica)
ID_Produto
Produto
Units Sold
Sales Price
Discount Band
Segment
Country
Sales
Profit
Date
Exemplos de Cálculos DAX
ID_Produto:

ID_Produto = RANKX(ALL(Financials_origem), Financials_origem[Produto], , ASC, DENSE)


Média de Unidades Vendidas:

Média_Unidades_Vendidas = AVERAGE(Financials_origem[Units Sold])


Média do valor de vendas:

Média_Valor_Vendas = AVERAGE(Financials_origem[Sales Price])


Mediana do valor de vendas:

Mediana_Valor_Vendas = MEDIAN(Financials_origem[Sales Price])


Valor máximo de Venda:

Valor_Max_Venda = MAX(Financials_origem[Sales Price])


Valor mínimo de Venda:

Valor_Min_Venda = MIN(Financials_origem[Sales Price])


Etapas Finais
Reorganizar as colunas conforme necessário para otimizar a visualização e análise dos dados.
Salvar o projeto .pbix.
Salvar uma imagem do seu esquema em estrela.
Escrever no README do repositório do GitHub o processo de construção do seu diagrama, incluindo as etapas, funcionalidades e funções DAX utilizadas no projeto.
Exemplo de README

# Projeto: Modelagem de Dashboard de E-commerce com Power BI

## Descrição

Este projeto consiste na criação de um modelo dimensional (star schema) para um dashboard de e-commerce utilizando Power BI e fórmulas DAX.

## Etapas do Projeto

1. **Importação dos Dados:**
   - Importamos a tabela `Financial Sample` e renomeamos para `Financials_origem` (modo oculto).

2. **Criação das Tabelas Dimensão:**
   - `D_Produtos` com ID, Produto, Médias e valores de venda.
   - `D_Produtos_Detalhes` com detalhes adicionais do produto.
   - `D_Descontos` com ID, Discount e Discount Band.
   - `D_Calendário` criada com a função `CALENDAR()`.
   - `D_Detalhes` com informações adicionais sobre vendas.

3. **Criação da Tabela Fato:**
   - `F_Vendas` contendo os principais dados de vendas e chaves para as tabelas dimensão.

## Funcionalidades e Fórmulas DAX Utilizadas

- Cálculo de ID de produto usando `RANKX`.
- Cálculos de médias, medianas, valores máximos e mínimos.
- Criação de tabela de calendário com `CALENDAR()`.

## Esquema em Estrela

![Esquema em Estrela](caminho_para_imagem_do_esquema_em_estrela.png)

## Salvamento

- O projeto foi salvo como `nome_do_projeto.pbix`.
- A imagem do esquema em estrela foi salva e incluída no repositório.

## Submissão

O projeto foi submetido ao GitHub. O link do repositório é:

[Link para o repositório do GitHub](URL_do_repositório)

Conclusão
Seguindo essas etapas, conseguiremos criar um modelo dimensional eficaz para um dashboard de e-commerce no Power BI utilizando fórmulas DAX. 
