# 🚀 Primeiro projeto de Data Pipeline com ETL + Airflow

Recentemente desenvolvi meu primeiro pipeline de dados estruturado utilizando o conceito de ETL (Extract, Transform, Load).

## 🔹 Extract

Consumi dados meteorológicos da API do OpenWeather para a cidade de São Paulo e armazenei o response JSON bruto como etapa inicial do pipeline.

## 🔹 Transform

Estruturei os dados utilizando pandas:

- Normalização de campos aninhados do JSON
- Remoção de colunas irrelevantes
- Padronização e renomeação de atributos
- Organização em formato tabular pronto para persistência

## 🔹 Load

Modelei uma tabela relacional no PostgreSQL e carreguei os dados transformados para armazenamento estruturado.

Toda a lógica foi organizada em uma função de pipeline, consolidando o fluxo end-to-end.

## 🔄 Orquestração com Apache Airflow

Para automatizar o processo, implementei uma DAG no Airflow, definindo:

- Tasks independentes para cada etapa do ETL
- Dependências entre tarefas
- Agendamento periódico da execução

Essa etapa elevou o projeto de um script isolado para uma pipeline orquestrada.

## 🐳 Arquitetura e desafios

Ao integrar Airflow + Postgres + Docker em ambiente Windows (WSL), enfrentei limitações de memória que afetaram a estabilidade do ambiente.

A solução foi migrar a arquitetura para uma instância EC2 na AWS, utilizando:

- Docker Compose para orquestração dos containers
- PostgreSQL containerizado
- Execução remota via SSM

Essa decisão permitiu:

- Isolamento de ambiente
- Maior estabilidade
- Melhor compreensão de arquitetura distribuída

## 📌 Principais aprendizados:

- Diferença entre ambiente local vs containerizado
- Comunicação entre containers (hostname ≠ localhost)
- Persistência de dados via volumes Docker
- Ajuste de recursos computacionais em ambiente cloud
- Importância da orquestração em pipelines de dados

Esse projeto marcou minha primeira experiência prática com pipelines automatizadas e infraestrutura em nuvem — e consolidou conceitos fundamentais de engenharia de dados.
