Tarefas Automatizadas com Amazon S3 e AWS Lambda

## Descrição

Este repositório foi desenvolvido como parte do laboratório **Tarefas Automatizadas com Amazon S3 e AWS Lambda**, da DIO. O objetivo desta prática foi compreender o funcionamento de uma arquitetura **Serverless** utilizando serviços da AWS para automatizar o processamento de arquivos, desde o momento em que são enviados para um bucket do Amazon S3 até o armazenamento das informações em um banco de dados NoSQL, utilizando funções Lambda para realizar todo o processamento de forma automática.

Durante o desenvolvimento também foi utilizado o **LocalStack**, uma ferramenta que simula diversos serviços da AWS localmente, permitindo executar e testar toda a aplicação sem a necessidade de utilizar recursos diretamente na nuvem. Essa abordagem facilita o aprendizado e reduz custos durante a fase de desenvolvimento.

---

# Arquitetura da Solução

A arquitetura implementada possui um fluxo simples, porém bastante utilizado em aplicações modernas baseadas em eventos. O usuário realiza o envio de um arquivo JSON para um bucket do Amazon S3. Esse upload gera automaticamente um evento que dispara uma função AWS Lambda escrita em Python. A função é responsável por realizar a leitura do arquivo, interpretar os dados e armazená-los em uma tabela do Amazon DynamoDB.

Além do processamento automático, foi criada uma segunda função Lambda integrada ao Amazon API Gateway. Essa função permite consultar as informações previamente armazenadas no DynamoDB por meio de uma API REST, demonstrando como os serviços da AWS podem ser integrados para criar aplicações escaláveis e desacopladas.

---

# Desenvolvimento

Para a geração dos dados utilizados durante o laboratório foi criado um script em Python responsável por produzir um conjunto de notas fiscais fictícias em formato JSON. Cada registro contém informações como identificador da nota, nome do cliente, valor da compra e data de emissão.

Após a geração do arquivo, o processo de upload para o Amazon S3 inicia automaticamente o fluxo de processamento. A função Lambda recebe a notificação do evento gerado pelo bucket, realiza a leitura do conteúdo e percorre todos os registros presentes no arquivo. Em seguida, cada item é gravado individualmente na tabela do Amazon DynamoDB.

Para demonstrar uma aplicação completa, também foi desenvolvida uma segunda função Lambda destinada à consulta das informações armazenadas. Essa função foi disponibilizada através do Amazon API Gateway, permitindo que qualquer cliente HTTP possa solicitar os dados utilizando uma requisição para o endpoint configurado.

---

# Utilização do LocalStack

Um dos principais recursos utilizados durante o laboratório foi o LocalStack. A ferramenta permitiu simular diversos serviços da AWS diretamente na máquina local, incluindo Amazon S3, AWS Lambda, DynamoDB e API Gateway.

Essa abordagem tornou possível criar toda a infraestrutura necessária para o laboratório sem depender de uma conta AWS ativa, facilitando os testes e permitindo compreender o comportamento dos serviços antes de realizar uma implantação em ambiente real.

Durante a configuração foi necessário criar os recursos simulados, configurar a AWS CLI para utilizar o endpoint do LocalStack e validar o funcionamento da comunicação entre todos os serviços.

---

# Principais Conceitos Estudados

Ao longo das aulas foi possível compreender diversos conceitos importantes relacionados ao desenvolvimento de aplicações Serverless.

O Amazon S3 foi utilizado como serviço de armazenamento de objetos e como responsável por disparar eventos sempre que um novo arquivo fosse enviado ao bucket.

A AWS Lambda foi utilizada para executar código sob demanda, sem a necessidade de gerenciar servidores, realizando automaticamente todo o processamento dos arquivos recebidos.

O Amazon DynamoDB foi empregado como banco de dados NoSQL para armazenar os registros processados pela Lambda, oferecendo alta disponibilidade e baixa latência.

Já o Amazon API Gateway foi utilizado para expor uma API REST capaz de consultar os dados armazenados, permitindo a comunicação entre aplicações clientes e os serviços desenvolvidos.

Por fim, o LocalStack foi essencial para simular toda essa infraestrutura localmente, tornando possível executar o laboratório de forma prática e econômica.

---

# Aprendizados

Este laboratório permitiu compreender na prática como diferentes serviços da AWS podem trabalhar em conjunto para construir soluções modernas baseadas em eventos.

Além da utilização individual de cada serviço, foi possível entender o fluxo completo de uma aplicação Serverless, desde o armazenamento inicial dos arquivos até seu processamento automático e posterior disponibilização por meio de uma API.

Outro ponto importante foi o contato com o LocalStack, que demonstrou ser uma excelente ferramenta para desenvolvimento local, permitindo criar ambientes muito semelhantes aos encontrados na AWS sem gerar custos adicionais.

Também foi possível reforçar conhecimentos em Python, integração entre serviços, automação de processos e documentação técnica utilizando o GitHub.

---


# Conclusão

O desenvolvimento deste laboratório proporcionou uma visão prática sobre a construção de aplicações Serverless utilizando serviços da AWS. A integração entre Amazon S3, AWS Lambda, DynamoDB e API Gateway demonstrou como é possível desenvolver soluções escaláveis, desacopladas e orientadas a eventos.

A utilização do LocalStack complementou a experiência ao permitir que toda a infraestrutura fosse executada localmente, facilitando o aprendizado e tornando o ambiente de desenvolvimento mais acessível.

Ao final da atividade foi possível consolidar conhecimentos sobre computação Serverless, automação de processos, integração entre serviços da AWS e boas práticas de documentação técnica, produzindo um material que poderá servir como referência para estudos e futuras implementações.

---
