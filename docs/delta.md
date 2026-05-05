# Delta Lake

## O que é o Delta Lake?

O **Delta Lake** é uma camada de armazenamento de código aberto (open-source) que traz confiabilidade e performance para os _Data Lakes_. Criado originalmente pela Databricks, ele foi desenhado para funcionar perfeitamente com o Apache Spark.

Assim como o Apache Iceberg, o Delta Lake resolve o problema da "falta de regras" nos Data Lakes tradicionais. Em um lago de dados comum, se um processo de gravação falhar na metade, você acaba com arquivos corrompidos ou dados duplicados. O Delta Lake encapsula os arquivos de dados (geralmente no formato Parquet) com um **log de transações** detalhado, garantindo que o ambiente se comporte com a segurança de um banco de dados relacional.

## Principais Funcionalidades

O formato Delta traz recursos essenciais para a Engenharia de Dados moderna:

- **Transações ACID:** Assim como o Iceberg, o Delta garante que múltiplas operações de leitura e escrita ocorram simultaneamente de forma segura. Se o trabalho falhar, a transação sofre _rollback_ (é desfeita) e a tabela permanece intacta.
- **Unificação de Batch e Streaming:** O Delta permite que você leia e grave dados na mesma tabela de forma contínua (em tempo real) ou em grandes lotes diários, sem precisar de arquiteturas separadas.
- **Viagem no Tempo (Time Travel):** O log de transações mantém um histórico das versões dos dados. É possível restaurar a tabela para uma versão anterior ou consultar os dados exatamente como estavam há uma semana.
- **Schema Enforcement e Evolution:** O Delta bloqueia automaticamente a inserção de dados que não correspondam à estrutura da tabela (Enforcement), mas permite a evolução controlada do schema quando novas colunas precisam ser adicionadas (Evolution).

## Aplicação no nosso Cenário (Futebol e VAR)

O Delta Lake se encaixa perfeitamente na dinâmica de atualização dos dados esportivos.

Imagine que estamos processando os eventos de uma partida do Flamengo em tempo real. Um gol é registrado na tabela `fato_evento`. Minutos depois, o Árbitro de Vídeo (VAR) revisa o lance e anula o gol por impedimento.

Utilizando PySpark com Delta Lake, o engenheiro de dados pode disparar um comando `DELETE` ou `UPDATE` especificamente para aquele evento. O log de transações do Delta registrará a exclusão de forma atômica. Quem estiver consultando o painel de estatísticas durante a correção não verá dados pela metade ou erros; a atualização acontecerá de forma transparente, garantindo a integridade do modelo analítico.
