# Analise de dados de Transações Imobiliárias no Rio de Janeiro

## 1.  Dataset

- **Resumo do dataset:** Dados de transações imobiliárias da Cidade do Rio de Janeiro. Contém a informação sobre a compra e venda de imóveis Residenciais e Não Residenciais.

- **Origem do dataset:** [DATA RIO](https://www.data.rio/datasets/PCRJ::itbi-transa%C3%A7%C3%B5es-por-logradouro-e-m%C3%AAs-im%C3%B3veis-residenciais-e-n%C3%A3o-residenciais/explore) - base de dados oficial da Prefeitura da Cidade do Rio de Janeiro
### 1.2 Descrição do Problema

O conjunto de dados de **Transações Imobiliárias** possui informações sobre o Logradouro segundo a Natureza de Compra e Venda e de Promessa e Compra e Venda a partir de 2011.

O foco dessa análise será nos imóveis do tipo residencial, para isso será excluídos os imóveis 'Não Residenciais' da análise.

O objetivo principal desta análise é preparar os dados para realizar um modelo de regressão que permite inferir um valor médio de compra e venda para um imovel com base no bairro , tipo de imóvel e metragem.

### 1.3 Hipóteses do Problema

As hipóteses que tracei são as seguintes:

1. **Bairros com maior volume de transações aumentam o valor médio da transação no ano seguinte?**
2. **Em quais bairrros há maior discrepância entre o valor médio da trasação e o valor médio do imóvel?**
3. **A sazonalidade afeta o volume de vendas na cidade de uma maneira geral?**
4. **Há diferença entre o preço do metro quadrado entre imóveis de tipologias diferentes?**

### 1.4 Tipo de problema
Este é um problema de regressão supervisionada. O Objetivo deste modelo é prever o valor de um imóvel com base no metro quadrado, tipo de imóvel e bairro.

### 1.5 Seleção de Dados

O dataset escolhido é  **ITBI - Transações Imobiliárias por Divisão Administrativa e Ano - Imóveis Residenciais e Não Residenciais** que está disponível no DATARIO, base de dados oficial da cidade do Rio de Janeiro. O dataset foi escolhido devido a relevância dos dados para o Mercado Imobiliário e para a cidade do Rio de Janeiro e por percenter a um banco de dados oficial da cidade.

### 1.6 Atributos do Dataset

O **ITBI - Transações Imobiliárias por Divisão Administrativa e Ano - Imóveis Residenciais e Não Residenciais contém 95.584 linhas** contém 95.584 linhas, com 16 atributos e são eles:

- **cl:** código do logradouro
- **logradouro:** nome do logradouro
- **codbairro:** código do bairro
- **bairro:** nome do bairro
- **total_transações:** quantidade de transações
- **uso:** tipo do uso, seja ele RESIDENCIAL ou NAO RESIDENCIAL
- **principais_tipologias:** tipologia do imovel, como "APARTAMENTO', 'CASA', 'GALPAO', LOJA SHOPPING', 'ARMAZEM/DEPOSITO', 'VAGA DE GARAGEM', 'GARAGEM/ESTACIONAMENTO', 'APARTAMENTO (PROLETARIO)'
- **média_percentual_transferido:** percentual médio do imovel que foi transferido na transação
- **média_área_construída:** metragem média do imóvel
- **média_valor_transação:** valor realizado na venda do imóvel
- **média_valor_imóvel:** valor médio do imóvel com base nos registros da prefeitura (valor venal do imóvel)
- **principal_transação_mercado:** informa em qual estagio jurídico da transação imobiliária foi realizado o pagamento do ITBI, seja na "COMPRA E VENDA" ou na "PROMESSA DE COMPRA E VENDA"
- **ano_transação:** ano em que a transação foi realizada
- **cd_utilizacao:** códido referente ao uso (RESIDENCIAL ou NAO RESIDENCIAL)
- **mês_transação:** mês da transação

## 2. Análise de Dados

Nesta estapa iremos avilar e entender as informações apresentadas neste dataset. Aas análises realizadas serão:
- Quantos atributos e instâncias existem;
- Quais são os tipos de dados dos atributos;
- O que se destaca ao análisar as primeiras linhas do dataset;
- Verificar se há a presença valores nulos, duplicados, outliers ou inconsistentes;
- Realizar resumo estatístico dos atributos numéricos (mínimo, máximo, mediana, média, desvio-padrão, primeiro quartil, terceiro quartil e moda).
- Visualizações:
    - Análise de balanceamento do dataset das categorias de de contagem
    - Histograma com a distribuição  das variáveis numéricas
    - Boxplots para identificar outliers.

  Toda essa etapa está documentada no notebook: https://github.com/daniellerms/Analise-de-Dados-e-Boas-Praticas/blob/main/MVP_Analise_de_Dados_e_Boas_Praticas.ipynb
 
## 3. Pré-processamento de dados
  - Filtragem e limpeza do dataset
  - Tratamento de valores nulos
  - Verificando as Primeiras e as Últimas linhas do Dataset Filtrado e Limpo
  - Tramento de Outliers
  - Enconding: Transformando as colunas categóricas em números
  - Separando o dataset em conjuntos de treino e teste
  - Normalização
  - Padronização
  - Outras Transformações e Etapas de Pré-Processamento: Matriz de correlação com o dataset limpo
  - 
Toda essa etapa está documentada no notebook: https://github.com/daniellerms/Analise-de-Dados-e-Boas-Praticas/blob/main/MVP_Analise_de_Dados_e_Boas_Praticas.ipynb
 

## 4. Respondendo as Hipóteses
A análise e o pré-processamento dos dados de transações imobiliárias demonstraram a importância de tratar e filtrar o dataset antes de qualquer interpretação. O conjunto de dados original apresentava ruídos, como imóveis comerciais e registros com áreas irreais, que foram saneados para permitir uma análise focada no mercado residencial. A exploração revelou correlações claras entre a área construída e o valor de mercado, além de expor distorções fiscais em bairros de alto padrão. As etapas de limpeza e categorização por tipologia foram fundamentais para entender que o mercado não é homogêneo, garantindo que as conclusões reflitam a realidade das transações na cidade.

A partir da análise realizada, as hipóteses levantadas foram validadas:
1. **Bairros com maior volume de transações aumentam o valor médio da transação no ano seguinte?** Não, os dados mostraram que a correlação entre o aumento do volume de vendas e o aumento do preço do imóvel no ano seguinte é baixa.
2. **Em quais bairrros há maior discrepância entre o valor médio da trasação e o valor médio do imóvel?**  Identificamos que, em bairros nobres (como a Urca), existe uma sobrevalorização fiscal, onde o valor de avaliação para imposto é consideravelmente maior que o valor real de venda, diferente do que ocorre em bairros mais populares.
3. **A sazonalidade afeta o volume de vendas na cidade de uma maneira gera?** Sim. Os dados mostraram um ciclo de mercado que começa em baixa no verão e Carnaval, apresenta um pico de recuperação em Março e cresce de forma consistente no segundo semestre, atingindo o ápice em Outubro.
4. **Há diferença entre o preço do metro quadrado entre imóveis de tipologias diferentes?** Sim. O metro quadrado de um apartamento padrão é quase o triplo do valor de uma casa. Além disso, o padrão construtivo (popular/proletário vs. padrão) influencia o preço tanto quanto a localização.

Toda essa etapa está documentada no notebook: https://github.com/daniellerms/Analise-de-Dados-e-Boas-Praticas/blob/main/MVP_Analise_de_Dados_e_Boas_Praticas.ipynb
 

## 5. Conclusão
  ### 4.1 Revisão do MVP
      O objetivo desse trabalho foi realizar uma análise exploratória e pré-processamento em um dataset sobre dados de transações imobiliárias no Rio de Janeiro. Os dados foram preparados com o objetivo de prever o valor de um imóvel com base no metro quadrado, tipo de imóvel e bairro.
      Durante a análise exploratória, percebemos alguns valores nulos, e uma forte presença de outliers, que foram evidênciados pelas análises estatíticas e visualizados pelo histograma com assimetria à direita e pelos outiliers no boxplot.
      No pré processamento, foi necessário limitar a amostra a ser análisada, filtrando metro quadrado mínimo e máximo, valor de transação mínimo e máximo, tratamento de valores nulos e de outliers.
      
  ### 4.2 Possíveis melhorias:
     1 - Além do modelo de regressão para a previsão para prever o valor de um imóvel com base em suas característica, esse dataset poderia ser usado para realizar um modelo de clusterização para identificar diferentes áreas da cidade com características semelhantes.
     2 - Poderiamos ter sido testadas outras hipóteses como:
     
  ### 4.3 Conclusão
  
    


 



