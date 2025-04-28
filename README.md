# DataMart de Vendas com PySpark


Este projeto contém um notebook em PySpark que realiza a criação de um Datamart de vendas a partir de um arquivo CSV. O notebook processa essas informações, cria dimensões e fatos modeladas no formato estrela e exporta o resultado em arquivos CSV e ZIP.

## Funcionalidades

### Ingestão de dados

-   Leitura de arquivo CSV enviado manualmente no ambiente Colab:
    
    -   dados_brutos.csv
        

### Processamento e Transformação

-   Criação de tabelas:
    
    -   Dimensão Cliente
        
    -   Dimensão Produto
        
    -   Dimensão Data
        
    -   Fato Vendas
        
-   Tratamento de dados:
    
    -   Conversão de tipos
        
    -   Criação de IDs únicos
        
        

### Armazenamento

-   Exportação dos DataFrames resultantes em formato CSV:
    
    -   dimensao_cliente
        
    -   dimensao_produto
        
    -   dimensao_tempo
        
    -   fato_vendas
        

Os arquivos CSV gerados podem ser baixados individualmente diretamente do ambiente do Colab ou zipados.

## Estrutura de Tabelas

-   **dimensao_cliente**:
    
    -   cliente_id (ID único do cliente)
        
    -   nome (Nome do cliente)
        
    -   email (E-mail do cliente)
        
    -   cidade (Cidade do cliente)
        
    -   estado (Estado do cliente)
        
-   **dimensao_produto**:
    
    -   produto_id (ID único do produto)
        
    -   nome_produto (Nome do produto)
        
    -   categoria (Categoria do produto)
        
-   **dimensao_tempo**:
    
    -   data_id (ID único de data)
        
    -   data_pedido (Data do pedido)
        
    -   ano
        
    -   mes
        
    -   dia
        
    -   dia_semana
        
-   **fato_vendas**:
    
    -   pedido_id (ID do pedido)
        
    -   cliente_id (Chave estrangeira para dimensão cliente)
        
    -   produto_id (Chave estrangeira para dimensão produto)
        
    -   data_id (Chave estrangeira para dimensão tempo)
        
    -   quantidade
        
    -   preco_unitario
        
    -   valor_total
        
    -   desconto
        
    -   valor_final
        

## Como Usar

### Rodando no Google Colab:

1.  Acesse Google Colab (gratuito).
    
2.  Faça upload do notebook `datamart_vendas_pyspark.ipynb`.
    
3.  No Colab:
    
    -   Execute o código como preferir, célula a célula ou tudo de uma vez.
    -   Faça upload do arquivos CSV de entrada manualmente via interface do Colab (célula 2)
    -  Ao final, baixe os arquivos CSV gerados (célula 7).
    -  Se preferir baixar todos os arquivos zipados, rode a célula 8.
    

## Requisitos

-   Google Colab (ambiente gratuito baseado em nuvem).
    
-   Bibliotecas:
    
    -   **PySpark** para processamento de dados.
    -   **os** e **datetime** para manipulação de caminhos e datas.
