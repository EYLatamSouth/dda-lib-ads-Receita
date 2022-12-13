# dda-lib-ads-Receita
Framework de dados e dashboards para análise de receita de varejo (KPIs de negócio e auditoria)


# Acelerador: Framework de Dados e Power BI para análise da Receita


Atualizado por: Camilo Jose
Última Versão: 23-11-2022

## 1-	Descrição
Modelo de Dados (Framework) e Formulas em DAX (Power BI) para análise da Receita e KPIs de Auditoria.

**Lista de Visualizações de Negócios:**
1) Top 10 Lojas com maior receita (Vendas);
2) Receita por modalidade de pagamento;
3) Evolução de Vendas Anual;
4) Distribuição Percentual das Vendas por mês;
5) Venda Total;
6) Volume de Vendas Demografico (Por Estados do Brasil);
7) Densidade de Filiais por Estados;
8) Distribuição das Vendas por Bandeira (Varejo);
9) Análise de Evolução das Vendas (Semana x Final de Semana);
10) Receita por m² por Filial e Estado;
11) Top 10 Lojas com maior receita por m²;
12) Média das vendas por m² por estado;

**Lista de Visualizações de KPIs de Auditoria:**
1) Conciliação das vendas por fonte de origem (PDV, Razão, CAR);
2) Análise de Resumo de Débitos x Créditos;
3) Análise de Volume de Lançamentos (Débitos x Créditos);
4) Tabela de Lançamentos Contábeis (Analítico);
5) Resumo da Validação Contábil (Conciliação por Conta);
6) Analítico da Validação Contábil (Lançamentos);
7) Análise de Dispersão de Lançamentos Manuais (Razão Contábil);
8) Correlação dos Grupos de Receita x Contas a Receber x Caixa/Banco;
9) Análise de Adquirente x Extratos Bancários;

## 2-	Pré Requisitos

Para gerar as visualizações, é necessário trabalhar os dados de acordo com as bases modelo (framework) dos dados. Importante considerar que os dados podem ser alterados, desde que se mantenham o mesmo layout e tipo de dados;

ARQUIVO: ADQUIRENTE X EXTRATOS

|#|Nome do Campo | Descrição
| ------------ | ------------ |
|1|NUM_PERIODO| Número do Período de Análise
|2|PERIODO| Nome do Mês em Análise
|3|RECEBIMENTOS - ADQUIRENTE| Valores repassados da Adquirente
|4|EXTRATOS BANCARIOS| Valores identificado no extrato bancário da companhia
|5|ANTECIPAÇÃO| Valores de Antecipação
|6|EXTRATO + ANTECIPACAO| Valor de Extrato + Antecipação
|7|DIFERENÇARECEBIMENTOS x EXTRATOS| Diferença Apurada entre Adquirente x Extratos
|8|Saldo dev.per.relat.|
|9|Crédito período apurado|
|10|Saldo acum|

ARQUIVO: PBI_CAR_SUMARIZADO

|#|Nome do Campo | Descrição
| ------------ | ------------ |
|1|CtaRazão| Conta do Razão (Contas a Receber)
|2|Loc_neg_| Código da Filial
|3|EY_VALOR_CR_OK| Valor Apurado de Contas a Receber
|4|COUNT1| Quantidae de Lançamentos (CAR)


ARQUIVO: PBI_PDV_SUM_SEMANA_FDS

|#|Nome do Campo | Descrição
| ------------ | ------------ |
|1|CD_FILIAL| Código da Filial (PDV)
|2|PERIODO| Período de Análise
|3|EY_SEMANA_FDS| Semana ou Final de Semana
|4|EY_VL_MOVTO| Valor Apurado (PDV)
|5|COUNT| Quantidade de Lançamentos (PDV)


ARQUIVO: PBI_RAZAO_SUMARIZADO_SALDO

|#|Nome do Campo | Descrição
| ------------ | ------------ |
|1|HKONT| Conta do Razão Contábil
|2|BUPLA| Código da Filial (Razão)
|3|VALOR_RAZAO_DXC| Valor Apurado (Razão)
|4|COUNT1| Quantidade de Lançamentos (Razão)

ARQUIVO: PDV_COMPLETO_SUMARIZADO

|#|Nome do Campo | Descrição
| ------------ | ------------ |
|1|CD_FILIAL| Código da Filial (PDV)
|2|PERIODO| Período de Análise (PDV)
|3|DS_FORMA_PAGTO| Modalidade de Pagamento (PDV)
|4|EY_VL_MOVTO| Valor Apurado (PDV)
|5|COUNT| Quantidade de Lançamentos (PDV)


ARQUIVO: TB_CONCILIACAO_ANALITICO

|#|Nome do Campo | Descrição
| ------------ | ------------ |
|1|ANALISE_EY| Classificação da Conciliação Contábil
|2|CONTA_CONTABIL| Conta Contábil
|3|CLASSE_DE_CONTA| Classe de Conta Contábil
|4|CONTA_ARQUIVO_JE| Conta Contábil (Razão)
|5|TOTAL_DE_CREDITOS_NO_ARQUIVO| Total de Créditos no Arquivo Razão
|6|TOTAL_DE_DEBITOS_NO_ARQUIVO| Total de Débitos no Arquivo Razão
|7|MOVIMENTACAO_DO_ARQUIVO| Movimentação Contábil no Arquivo Razão 
|8|SALDO_DO_BALANCETE_EM_MESINICIAL| Saldo contábil no balancete do mês inicial
|9|SALDO_DO_BALANCETE_EM_MESFINAL| Saldo contábil no balancete do mês final
|10|MOVIMENTACAO_BALANCETE| Movimentação de Saldo do Balancete
|11|EY_DIF_ARQ_BALANCETE| Diferença entre a movimentação do arquivo (razão) e movimentação do balancerte


ARQUIVO: TB_CONCILIACAO_RESUMO

|#|Nome do Campo | Descrição
| ------------ | ------------ |
|1|ANALISE_EY| Classificação da Conciliação Contábil
|2|QUANTIDADE| Quantidade de Contas
|3|EY_DIF_ARQ_BALANCETE| Valor apurado de diferenças


ARQUIVO: TB_DXC_ANALITICO

|#|Nome do Campo | Descrição
| ------------ | ------------ |
|1|COD_EMPRESA| Código da Empresa (Razão)
|2|PERIODO_CONTABIL| Período Contábil (Razão)
|3|CONTA| Conta Contábil (Razão)
|4|CLASSE_DE_CONTA| Classe da Conta (Razão)
|5|TIPO_DE_OPERACAO| Tipo da Operação, C = Crédito, D = Débito (Razão)
|6|MOEDA| Moeda
|7|QUANTIDADE| Quantidade de Lançamentos (Razão)
|8|VALOR_CONTABIL| Valor Contábil Apurado (Razão)
|9|PERIODO| Período Contábil (Razão)
|10|LENGHT| Tamanho da Cadeia de String do Período (Razão)
|11|MONTH_NR| Número do Mês de Análise


ARQUIVO: TB_DXC_RESUMO

|#|Nome do Campo | Descrição
| ------------ | ------------ |
|1|COD_EMPRESA| Código da Empresa (Razão)
|2|PERIODO_CONTABIL| Período Contábil (Razão)
|3|TIPO_DE_OPERACAO| Tipo da Operação, C = Crédito, D = Débito (Razão)
|4|MOEDA| Moeda
|5|QUANTIDADE| Quantidade de Lançamentos (Razão)
|6|VALOR_CONTABIL| Valor Contábil Apurado (Razão)
|7|EY_DIFERENCA| Valor apurado de diferenças
|8|PERIODO| Período Contábil (Razão)
|9|LENGHT| Tamanho da Cadeia de String do Período (Razão)
|10|MONTH_NR| Número do Mês de Análise


ARQUIVO: TB_ESTADOS

|#|Nome do Campo | Descrição
| ------------ | ------------ |
|1|ESTADOS| Nome do Estado
|2|SIGLA| UF, Unidade Federativa



ARQUIVO: TB_FILIAIS

|#|Nome do Campo | Descrição
| ------------ | ------------ |
|1|C.Custo| Centro de Custo
|2|JAVA| Código da Loja no Sistema de PDV
|3|Loja| Localização Abreviada da Loja
|4|BANDEIRA| Bandeira (Varejo)
|5|ÁREA DE VENDAS (m²)| Área de Vendas da Loja
|6|Cidade| Cidade em que a loja está situada
|7|UF| Unidade Federativa
|8|COD_LOJA| Código da Loja (Razão)



ARQUIVO: TB_PLANO_DE_CONTAS


|#|Nome do Campo | Descrição
| ------------ | ------------ |
|1|Conta| Número da Conta Contábil
|2|GL_Account_Name| Descrição da Conta
|3|ACCOUNT_CLASS| Classificação da Conta
|4|ACCOUNT_TYPE| Tipo da Conta
|5|ACCOUNT_SUBTYPE| Subtipo da Conta


ARQUIVO: TB_RAZAO_DISPERSAO


|#|Nome do Campo | Descrição
| ------------ | ------------ |
|1|COD_EMPRESA| Código da Empresa
|2|NOME_EMPRESA| Nome da Empresa
|3|FILIAL| Código da Filial
|4|DATA_CONTABIL| Data Contábil (Razão)
|5|DATA_LANCAMENTO| Data Lançamento (Razão)
|6|TIPO_DE_DOCUMENTO| Tipo do Documento (Razão)
|7|CLASSE_DE_CONTA| Classe de Conta (Razão)
|8|TIPO_DE_OPERACAO| Tipo de Operação(Razão)
|9|CONTA| Número da Conta Contábil (Razão)
|10|HISTORICO_LANCAMENTO| Histórico do Lançamento (Razão)
|11|USNAM| Usuário (Razão)
|12|PERIODO_CONTABIL| Período Contábil (Razão)
|13|MOEDA| Moeda (Razão)
|14|TIPO_DE_LANCAMENTO| Tipo do Lançamento (Razão)
|15|NUMERO_DOCUMENTO| Número do Documento (Razão)
|16|VALOR_CONTABIL| Valor Contábil Apurado (Razão)




ARQUIVO: xCORRELATION_BAR


|#|Nome do Campo | Descrição
| ------------ | ------------ |
|1|PERIODO_FINAL_TRAT| Período da Correlação
|2|B_AR_activity_posting_to_Receita| B - Valor apurado de Contas a Receber na correlação com Receitas
|3|D_AR_activity_posting_to_Caixa| D - Valor apurado de Contas a Receber na correlação com Caixa e Banco
|4|E_AR_activity_NOT_posting_to_Receita_AND_Caixa| D - Valor apurado de Contas a Receber não identificado em receita e caixa e banco na correlação
|5|Running_Balance| Evolução do Balanço
|6|ORDER_SEQUENCE| Sequencia (ordenada)
|7|Column| Verifica se o primeiro digito do período é número ou letra
|8|SORTED_SEQUENCE| Ajuste de sequencia para que o Beg Balance seja o 1 na ordenação
|9|EY_B| Saldo B
|10|EY_D| Saldo D
|11|EY_E| Saldo E


ARQUIVO: xCORRELATION_STATUS


|#|Nome do Campo | Descrição
| ------------ | ------------ |
|1|CORRELAÇÃO| Classificação da Correlação
|2|VALOR_RECEITA| Valor Apurado em Receita
|3|VALOR_CR| Valor Apurado em Contas a Receber
|4|VALOR_CAIXA| Valor Apurado em Caixa e Banco
|5|VALOR_CR_ABS| Valor Apurado em Receita (Absoluto)


ARQUIVO: xCORRELATION_TABLE_CHART


|#|Nome do Campo | Descrição
| ------------ | ------------ |
|1|CORRELAÇÃO| Classificação da Correlação
|2|JAN| Valor Apurado em Janeiro
|3|FEB| Valor Apurado em Fevereiro
|4|MAR| Valor Apurado em Março
|5|APR| Valor Apurado em Abril
|6|MAY| Valor Apurado em Maio
|7|JUN| Valor Apurado em Junho
|8|JUL| Valor Apurado em Julho
|9|AUG| Valor Apurado em Agosto
|10|SEP| Valor Apurado em Setembro
|11|OCT| Valor Apurado em Outubro
|12|NOV| Valor Apurado em Novembro
|13|DEC| Valor Apurado em Dezembro
|14|TOTAL| Valor Apurado Total




## 3-	Passo a Passo

1)	Crie um diretório (pasta) para armazenamento das bases de modelo;
2)	Crie um diretório (pasta) para armazenamento do executável do Power BI (.pbix);
3)	Baixe do GitHub o pacote com as bases modelo e armazene-as no diretório criado no passo 1;
4)	Faça replace dos dados das Bases de Modelo por dados do seu projeto;
5)	Baixe do GitHub o PBIX (projeto do Power BI) e salve no diretório criado no passo 2;
6)	Abra o Power BI "Acelerador DASH - Receita v3.pbix";
7)	Vá em Data > Home > Refresh

