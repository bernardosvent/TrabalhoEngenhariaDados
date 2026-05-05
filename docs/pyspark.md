# Apache Spark e PySpark

## O que é o Apache Spark?

O **Apache Spark** é um mecanismo (framework) unificado de processamento de dados distribuído e ultrarrápido, projetado para lidar com grandes volumes de dados (Big Data). Diferente de sistemas mais antigos que liam e gravavam dados no disco a cada pequena etapa do processo, o Spark realiza o processamento primariamente **em memória** (in-memory). Isso o torna excepcionalmente rápido para análises complexas.

Na arquitetura de dados moderna, ele atua como o "motor" principal, permitindo a ingestão, transformação e análise de dados em grande escala, suportando tanto processamento de dados históricos em lote (Batch) quanto dados contínuos em tempo real (Streaming).

## O que é o PySpark?

O **PySpark** é a interface (API) oficial do Apache Spark para a linguagem Python. Como o Python é a linguagem mais utilizada no cenário de Engenharia de Dados, o PySpark permite que os desenvolvedores escrevam scripts que, nos bastidores, são traduzidos e executados de forma distribuída em um cluster (um conjunto de vários computadores trabalhando juntos).

### Principais Vantagens do PySpark na Engenharia de Dados:

- **Acessibilidade:** Permite usar Python para orquestrar Big Data sem a necessidade de aprender linguagens nativas da máquina virtual Java (JVM), como Scala ou Java.
- **Integração:** Facilita a união do processamento distribuído com o rico ecossistema de bibliotecas analíticas do Python.
- **Processamento Paralelo (DataFrames):** O PySpark utiliza DataFrames que distribuem automaticamente arquivos gigantes (como arquivos CSV contendo milhões de eventos esportivos) em pequenos pedaços processados simultaneamente.

## Como o PySpark interage com Delta e Iceberg

É importante ressaltar que o Spark é estritamente um motor de processamento, e não um banco de dados de armazenamento. Ele lê arquivos crus e precisa gravá-los em algum lugar.

É exatamente neste ponto de gravação que tecnologias como **Delta Lake** e **Apache Iceberg** entram. O PySpark utiliza os drivers desses formatos para estruturar como os arquivos são salvos no armazenamento em nuvem, garantindo que o motor consiga executar comandos transacionais, como corrigir ou deletar um dado específico, sem corromper o _Data Lake_.
