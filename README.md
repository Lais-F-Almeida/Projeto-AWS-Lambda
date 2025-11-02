# Desafio AWS Lambda + S3 + DynamoDB (com LocalStack)

Este laboratório tem como objetivo consolidar os conhecimentos em **tarefas automatizadas utilizando AWS Lambda e Amazon S3**.  
O projeto simula o fluxo completo de processamento de notas fiscais, desde o upload de um arquivo até a gravação e consulta dos dados em um banco **NoSQL (DynamoDB)**.

---

## Objetivo

Criar uma arquitetura localmente com o **LocalStack**, integrando os seguintes serviços:
- **Amazon S3** → Armazenamento dos arquivos JSON com notas fiscais  
- **AWS Lambda** → Processamento automático dos arquivos enviados  
- **Amazon DynamoDB** → Persistência das informações processadas  
- **Amazon API Gateway** → Exposição dos dados via API  
- **IAM** → Controle de permissões simuladas  

---

## Arquitetura do Projeto

Fluxo de execução:
1. O usuário faz upload de um arquivo JSON no bucket S3 (notas-fiscais-upload);
2. O S3 aciona um **trigger** que executa a função Lambda (ProcessarNotasFiscais);
3. A função lê e valida os dados, registrando as informações relevantes no DynamoDB (NotasFiscais);
4. A API Gateway permite consultar ou enviar dados via métodos **POST** e **GET**.

