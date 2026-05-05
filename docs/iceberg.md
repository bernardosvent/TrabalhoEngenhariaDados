# Apache Iceberg

## O que é o Apache Iceberg?

O **Apache Iceberg** é um formato de tabela aberto e de alto desempenho para conjuntos de dados analíticos enormes. Ele não é um motor de processamento (como o Spark) e nem um sistema de armazenamento físico (como o HDFS ou o AWS S3). Em vez disso, ele é uma **camada de metadados** que fica entre o processamento e o armazenamento.

Historicamente, os _Data Lakes_ baseados no ecossistema Hadoop (usando o formato Hive) tinham muitas limitações ao lidar com tabelas gigantes. Atualizar uma única linha ou alterar a estrutura (schema) da tabela era um processo demorado e perigoso, podendo corromper os dados. O Iceberg foi criado originalmente pela Netflix justamente para resolver esses problemas, trazendo a confiabilidade dos bancos de dados tradicionais (SQL) para o mundo do Big Data.

## Principais Funcionalidades

O Iceberg introduz conceitos fundamentais para a nossa arquitetura:

- **Transações ACID:** Garante que operações de leitura e escrita sejam seguras. Se um trabalho de inserção de dados falhar no meio do caminho, a tabela não ficará corrompida com dados parciais.
- **Evolução de Schema (Schema Evolution):** Permite adicionar, renomear ou remover colunas de uma tabela sem a necessidade de reescrever todos os dados antigos.
- **Particionamento Oculto (Hidden Partitioning):** O Iceberg gerencia as partições fisicamente debaixo dos panos, evitando que o usuário precise escrever consultas SQL complexas para filtrar dados de forma eficiente.
- **Viagem no Tempo (Time Travel):** Como o Iceberg rastreia todas as mudanças através de "snapshots" (fotografias do estado da tabela), é possível consultar como a tabela estava exatamente em um dia ou horário anterior.

## Aplicação no nosso Cenário (Futebol e VAR)

No contexto do nosso modelo de estatísticas de partidas de futebol, o Apache Iceberg brilha nas operações críticas.

Se o Árbitro de Vídeo (VAR) anula um gol após a partida já ter encerrado, nós precisamos executar um comando de `DELETE` ou `UPDATE` na tabela `fato_evento`. Em um _Data Lake_ sem Iceberg, teríamos que reescrever todo o arquivo daquela rodada. Com o Iceberg operando em conjunto com o Apache Spark, podemos rodar um simples comando DML (Data Manipulation Language) e a camada de metadados do Iceberg se encarregará de invalidar o registro do gol antigo de forma atômica e segura, sem interromper as análises de quem estiver lendo a tabela naquele exato momento.
