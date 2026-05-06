# Trabalho de Pesquisa: Apache Spark com Delta Lake e Apache Iceberg

## Descrição

Este projeto é referente ao trabalho da disciplina de Engenharia de Dados (Arquitetura de Dados). O objetivo é implementar um ambiente utilizando Apache Spark (PySpark) e demonstrar o funcionamento prático dos formatos de tabela Delta Lake e Apache Iceberg. O projeto inclui a modelagem de dados (modelo ER), códigos DDL, e a demonstração prática de comandos de `INSERT`, `UPDATE` e `DELETE` em ambos os formatos.

## Disclaimer ou alertas/avisos

Este é um projeto acadêmico desenvolvido para fins de avaliação. O ambiente foi configurado e testado em um sistema Linux (Ubuntu/WSL) para garantir a total compatibilidade e estabilidade das ferramentas de Engenharia de Dados, conforme recomendado nas aulas.

## 🛠️ Tecnologias e Pré-requisitos

Para garantir a reprodutibilidade, utilizamos o gerenciador **UV** para travar as dependências exatas do projeto:

- **Java (OpenJDK 11 ou 17)**: Necessário para a execução do motor Spark.
- **Python**: Versão 3.12.1.
- **UV**: Gerenciador de pacotes e ambientes virtuais (substituindo Pip/Poetry).
- **PySpark**: 3.5.1.
- **Delta Lake**: 3.2.0.
- **Apache Iceberg**: 1.6.1 (Runtime 3.5_2.12).

## Instalação

Siga o roteiro passo a passo abaixo para reproduzir a configuração exata do ambiente:

1. **Clone o repositório do projeto:**

   ```bash
   git clone https://github.com/bernardosvent/TrabalhoEngenhariaDados.git
   cd TrabalhoEngenhariaDados
   ```

2. **Garanta que o gerenciador UV está instalado:**
   Caso não tenha o UV, instale-o globalmente utilizando o `pipx`:

   ```bash
   pipx install uv
   ```

3. **Instale as dependências e crie o ambiente virtual:**
   Como estamos utilizando o padrão do UV, as bibliotecas já estão mapeadas no projeto. Para instalar tudo e gerar o ambiente virtual automaticamente, execute:

   ```bash
   uv sync
   ```

4. **Ative o ambiente virtual:**
   Sempre que for trabalhar no projeto, ative o ambiente com o comando:
   ```bash
   source .venv/bin/activate
   ```

## Howto

Para utilizar o projeto e visualizar as implementações práticas:

1. Com o ambiente virtual ativado, inicie o servidor do Jupyter Labs executando:

```bash
   jupyter lab
```

2. No navegador, acesse a interface do Jupyter e navegue até a pasta `src/` (ou diretório principal onde os notebooks foram salvos).
3. Abra os arquivos `.ipynb` referentes à implementação do **Delta Lake** e do **Apache Iceberg** para rodar os blocos de código contendo o passo a passo das operações DML (Insert, Update, Delete) e visualização dos dados.

## Testes

Para rodar a suíte de testes do projeto utilizando o framework Pytest, execute no terminal (com o ambiente ativado):

```bash
pytest -v
```

## Documentação

A documentação teórica completa do projeto foi construída utilizando o **MkDocs**, contendo:

- Contextualização do trabalho e cenário dos dados (Modelo ER, Fonte de dados).
- Explicação teórica sobre o Apache Spark (PySpark).
- Explicação teórica sobre o Apache Iceberg.
- Explicação teórica sobre o Delta Lake.

**Acesse a documentação web:**
[https://bernardosvent.github.io/TrabalhoEngenhariaDados/iceberg/]
