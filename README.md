# DataMart de Vendas com PySpark


Este projeto demonstra a construção de um DataMart de vendas utilizando PySpark no ambiente Google Colab. A modelagem adota o formato estrela (_star schema_), com separação entre tabelas de dimensões e fato, e os resultados são exportados em arquivos CSV, organizados para suporte a análises e exploração futuras.

## Visão Geral

Este projeto implementa um pipeline de dados em PySpark para construção de um DataMart de vendas, estruturado em quatro etapas principais:

-   **Ingestão de dados:** leitura do arquivo CSV bruto contendo registros de vendas.
    
-   **Processamento e modelagem:** transformação dos dados, tratamento de tipos e criação de tabelas normalizadas (dimensões e fato) seguindo o modelo estrela.
    
-   **Armazenamento:** exportação dos DataFrames modelados em arquivos CSV individuais, com opção de geração de um pacote compactado (.zip).
    
-   **Análises exploratórias:** criação de _views_ temporárias no Spark SQL para realização de consultas analíticas, respondendo perguntas de negócio relevantes sobre o dataset.

## Funcionalidades

### Ingestão de Dados

-   Leitura do arquivo `dados_brutos.csv` enviado manualmente no ambiente Colab.
    

### Processamento e Modelagem

-   Criação das seguintes tabelas:
    
    -   **Dimensão Cliente** (`dimensao_cliente`)
        
    -   **Dimensão Produto** (`dimensao_produto`)
        
    -   **Dimensão Tempo** (`dimensao_tempo`)
        
    -   **Fato Vendas** (`fato_vendas`)
        
-   Aplicação de transformações:
    
    -   Conversão e tratamento de tipos de dados.
        
    -   Criação de identificadores únicos.


### Exportação

-   Geração de arquivos CSV para cada tabela.
    
-   Disponibilização opcional de todos os arquivos compactados em um único `.zip`.
    

## Modelagem de Dados



### dimensao_cliente

| Coluna      | Descrição                 |
|-------------|----------------------------|
| cliente_id  | ID único do cliente         |
| nome        | Nome do cliente             |
| email       | E-mail do cliente           |
| cidade      | Cidade do cliente           |
| estado      | Estado do cliente           |

### dimensao_produto

| Coluna        | Descrição                |
|---------------|---------------------------|
| produto_id    | ID único do produto        |
| nome_produto  | Nome do produto            |
| categoria     | Categoria do produto       |

### dimensao_tempo

| Coluna        | Descrição                 |
|---------------|----------------------------|
| data_id       | ID único da data            |
| data_pedido   | Data do pedido              |
| ano           | Ano do pedido               |
| mes           | Mês do pedido               |
| dia           | Dia do pedido               |
| dia_semana    | Dia da semana do pedido     |

### fato_vendas

| Coluna         | Descrição                                          |
|----------------|----------------------------------------------------|
| pedido_id      | ID do pedido                                        |
| cliente_id     | Chave estrangeira para `dimensao_cliente`           |
| produto_id     | Chave estrangeira para `dimensao_produto`           |
| data_id        | Chave estrangeira para `dimensao_tempo`             |
| quantidade     | Quantidade vendida                                 |
| preco_unitario | Preço unitário do produto                          |
| valor_total    | Valor total bruto (quantidade × preço unitário)     |
| desconto       | Valor do desconto aplicado                         |
| valor_final    | Valor final da venda após o desconto                |
## Como Executar

### Ambiente: Google Colab

1.  Acesse o [Google Colab](https://colab.research.google.com/) no seu navegador de preferência.
    
2.  Faça upload do notebook `datamart_vendas_pyspark.ipynb`.
    
3.  Realize o upload do arquivo `dados_brutos.csv` na célula indicada.
    
4.  Execute as células em sequência.
        
5.  Baixe os arquivos exportados conforme necessário.

6. Execute as células da seção de análise para conferir o resultado para algumas perguntas de negócio. (opcional)
    

## Requisitos

-   **Google Colab** (ambiente baseado em nuvem, gratuito).
    
-   **Bibliotecas necessárias**:
    
    -   [PySpark](https://spark.apache.org/docs/latest/api/python/) — processamento de dados distribuído.
        
    -   **os**, **datetime** — manipulação de arquivos e datas.
