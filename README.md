## Projeto de Big Data: Cadastro Ambiental Rural

### Descrição
Este projeto visa a criação de uma arquitetura eficiente para gerenciar e analisar o conjunto de dados do Cadastro Ambiental Rural, que contém informações sobre propriedades rurais no Brasil. Utilizando tecnologias modernas de Big Data e computação em nuvem, buscamos otimizar o processamento e a análise desses dados volumosos.

### Problema
O Cadastro Ambiental Rural é um conjunto de dados volumoso, tornando desafiador o gerenciamento e a realização de consultas rápidas. O objetivo do projeto é projetar uma arquitetura que permita o gerenciamento eficiente desses dados, facilitando consultas e análises rápidas.

### Dados
Os dados utilizados no projeto estão disponíveis aqui,
[Cadastro Ambiental Rural](https://dados.gov.br/dados/conjuntos-dados/cadastro-ambiental-rural1).


### Arquivos
No repositório do projeto, você encontrará os seguintes arquivos importantes:

* *Sugestao Grandes Volumes.pdf*: Este documento contém o enunciado do projeto e as informações detalhadas sobre as exigências a serem cumpridas durante o desenvolvimento do projeto.

* *dicionario-temas-ambientais.pdf*: Este documento apresenta uma listagem dos atributos existentes na base de dados, descrevendo o que cada campo armazena e as informações que representam.

### Implementação
Utilizamos o Databricks para implementar todo o projeto, dividindo o processo em 7 notebooks para organizar cada etapa da arquitetura de dados:

1. Santander_Coders_Projeto_BD_01_Criação_diretorios_schemas: Definição dos diretórios e arquivos, além dos bancos de dados e tabelas para cada etapa da arquitetura Medallion.

2. Santander_Coders_Projeto_BD_02_Ingestao_Raw_Zone: Importação dos dados do arquivo .csv para a tabela na arquitetura raw_zone, importando todos os dados como string.

3. Santander_Coders_Projeto_BD_03_Ingestao_Bronze_Zone: Importação dos dados da tabela na camada Raw, realizando o processo de tipagem correta baseado nos dados contidos nas colunas.

4. Santander_Coders_Projeto_BD_04_Profiles_Bronze_Zone: Geração de relatório para definir as melhorias necessárias na camada bronze para silver.

5. Santander_Coders_Projeto_BD_05_Missing_Zone: Consulta e armazenamento de todos os registros com valores nulos em alguma coluna.

6. Santander_Coders_Projeto_BD_06_Silver_Zone: Importação dos dados da camada bronze, checando a validade dos dados e garantindo a qualidade dos mesmos.

7. Santander_Coders_Projeto_BD_07_Gold_Zone: Apresentação da estruturação dos insights gerados, respondendo questões importantes com cálculos precisos sobre os dados estruturados.

### Ferramentas e Tecnologias Utilizadas
* Databricks: Plataforma utilizada para análise de dados baseada em nuvem que facilita a colaboração entre equipe.

* Apache Spark: Utilizado para processamento de dados em grande escala.

* Formato de Arquivo Delta: Formato de armazenamento otimizado para o processamento de Big Data, que permite a leitura e escrita eficiente.

* Tabelas Externas: Tabelas que permitem a organização e gerenciamento eficiente dos dados, facilitando o acesso e a manipulação.

### Utilização no Projeto
Neste projeto, a combinação de Databricks e Apache Spark, juntamente com o formato de arquivo Delta, aproveita ao máximo os benefícios da computação em nuvem e da computação distribuída. Foi utilizado várias elementos que proporcionaram benefícios para o seu desenvolvimento:

* Paralelismo: Permitiu a execução de múltiplas operações simultaneamente, reduzindo significativamente o tempo de processamento. Isso foi especialmente eficaz para trabalhar com várias tabelas ao mesmo tempo, agilizando as etapas de importação, transformação e análise dos dados.

* Resiliência: Oferece alta disponibilidade e tolerância a falhas, garantindo que o sistema continue a operar mesmo em caso de falhas em componentes individuais. Essa característica é fundamental no cenário de múltiplos notebooks do projeto, assegurando que a execução não seja interrompida por problemas isolados.

* Jobs múltiplos: Melhorou a eficiência no processamento de grandes volumes de dados ao distribuir as tarefas entre vários nós de computação. Isso acelerou a execução de scripts em grande volume de dados, representando um ganho significativo na performance e na capacidade de lidar com a escala dos dados do Cadastro Ambiental Rural.

* Particionamento de arquivos: Garante separar os dados por atributo, permitindo assim, consultas mais rápidas, acelerando o processo de encontrar informações relevantes dentro do conjunto de dados.


### Dificuldades.
Lidar com grandes bases de dados não é uma tarefa fácil. Para facilitar o armazenamento e processamento desses dados no Databricks, foi necessário realizar uma manipulação prévia dos dados. Isso envolveu um pré-processamento eficiente, onde a base de dados original foi dividida em partes menores antes do upload para a nuvem no Databricks.

Além disso, a base de dados continha muitos registros duplicados que precisaram ser tratados com critérios precisos. Para abordar os registros duplicados, foram definidos dois critérios específicos:

* Data de Retificação Mais Recente: Seleciona o registro com a última data de retificação mais recente.

* Quantidade de Dados Não Nulos: Seleciona o registro que contém a maior quantidade de informações não nulas, priorizando registros mais completos.

Esses critérios ajudaram a eliminar duplicidades de forma sistemática e a garantir que os dados armazenados fossem os mais recentes e completos possíveis, melhorando a qualidade geral do conjunto de dados.