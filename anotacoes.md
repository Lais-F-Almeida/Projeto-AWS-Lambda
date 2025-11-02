
# Anotações e Explicações do Projeto

## O que o projeto faz?
O projeto automatiza o processamento de arquivos JSON enviados para o Amazon S3.  
Quando o upload ocorre, uma função Lambda é acionada automaticamente para ler, validar e armazenar os dados no DynamoDB.  
Além disso, foi criada uma API que permite inserir e consultar dados remotamente.

---

## Como o fluxo funciona
1. **Upload no S3:** o usuário envia o arquivo *notas_fiscais_2025.json*.  
2. **Evento (Trigger):** o S3 dispara um evento que chama a função Lambda.  
3. **Processamento:** a Lambda lê o conteúdo, extrai campos relevantes (como `id`, `cliente`, `valor` e `data_emissao`) e salva no DynamoDB.  
4. **Persistência:** o DynamoDB mantém os registros de forma escalável e sem necessidade de schema fixo.  
5. **Consulta via API:** a API Gateway permite testar a integração com métodos **POST** e **GET**.  

---

## Detalhes Técnicos

- A função Lambda utiliza **Python 3.9** e o handler `grava_db.lambda_handler`.  
- O LocalStack foi executado localmente, simulando toda a infraestrutura AWS.  
- As permissões e integrações entre serviços foram configuradas usando **AWS CLI** e **awslocal**.  
- O **API Gateway** foi implementado para simular endpoints REST de consulta e inserção.
- Foi criada uma **API Gateway local**  
- Recurso */notas* foi configurado com métodos **POST** e **GET**

**Função dos métodos:**

- **POST:** envia dados para a Lambda  
- **GET:** consulta os dados no DynamoDB  

---

## Configuração do LocalStack

O **LocalStack** é uma ferramenta de desenvolvimento que emula a infraestrutura e serviços da AWS diretamente no seu computador, funcionando como uma mini nuvem local.  

Com o LocalStack, podemos:

- Construir, testar e depurar aplicações que dependem de serviços AWS
- Desenvolver offline, sem necessidade de conexão com a nuvem real
- Reduzir custos de teste e prototipagem
- Garantir maior segurança em testes locais

---


## Benefícios e Aprendizados

- Fluxo **serverless** e orientado a eventos  
- Integração prática: **S3 → Lambda → DynamoDB → API Gateway**  
- Testes seguros e econômicos usando LocalStack  
- Arquitetura escalável e reutilizável  
- Praticar offline ajuda a identificar erros de configuração e permissões  
- Cenários de uso reais: processamento de notas fiscais, logs, manipulação de arquivos  
- Entendimento aprofundado da comunicação entre serviços AWS e automação de processos

