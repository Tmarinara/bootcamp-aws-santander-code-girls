# 7.	Serviços Intermediários e Avançados  

# 7. Serviços Intermediários e Avançados  

## 7.1. Entendendo como Funciona o AWS Lambda  

### O que é AWS Lambda  

- O **AWS Lambda** é um serviço de **computação sem servidor (serverless)** que executa código em resposta a eventos, **sem a necessidade de gerenciar servidores**.  
- Ele cuida automaticamente de toda a infraestrutura: **provisionamento, manutenção, escalabilidade e monitoramento**.  
- Essa abordagem permite que o desenvolvedor foque apenas na **lógica da aplicação**, e não na administração da infraestrutura.  
- O Lambda é amplamente utilizado para **automatizar processos**, **responder a eventos em tempo real**, e **construir aplicações modernas e modulares**.  

#### Características principais
- **Execução sob demanda:** o código é executado apenas quando há um evento disparador, e o custo é calculado **somente pelo tempo de execução**.  
- **Escalabilidade automática:** adapta-se automaticamente ao número de eventos recebidos, sem necessidade de configuração manual.  
- **Alta disponibilidade:** executa o código em uma infraestrutura distribuída e tolerante a falhas da AWS.  
- **Custo-benefício:** preço base de aproximadamente **0,20 USD por 1 milhão de solicitações** (podendo variar conforme região).  
- **Integração nativa:** funciona com diversos serviços da AWS, como **S3**, **API Gateway**, **DynamoDB**, **SNS**, **SQS** e **CloudWatch**.  

---

### Amazon Lambda na prática  

#### Exemplo de uso real

> Um cenário comum é usar o **AWS Lambda** para processar dados automaticamente quando um arquivo é enviado a um bucket do **Amazon S3**.  
> Outro exemplo é executar uma função Lambda quando uma mensagem chega a uma fila **SQS** ou quando uma API é chamada via **API Gateway**.

#### Exemplo de código (consulta à API ViaCEP)

```python
import json
import requests

def lambda_handler(event, context):
    url = 'https://viacep.com.br/ws/01001000/json/'
    resultado = requests.get(url, verify=False)
    
    numeros = json.loads(resultado.text)['ibge']
    
    return {
        'statusCode': 200,
        'body': json.dumps(numeros)
    }

```

### Vantagens do AWS Lambda  

| Benefício | Descrição |
|:-----------|:-----------|
| <ins>Sem servidor (Serverless)</ins> | Elimina a necessidade de configurar e gerenciar servidores. |
| <ins>Escalabilidade automática</ins> | Ajusta automaticamente o número de execuções conforme a demanda. |
| <ins>Cobrança sob demanda</ins> | Você paga apenas pelo tempo em que o código é executado. |
| <ins>Alta integração</ins> | Integra-se facilmente com outros serviços AWS (S3, SNS, DynamoDB, API Gateway, etc.). |
| <ins>Resiliência</ins> | Executa sobre uma infraestrutura altamente disponível e redundante. |


## 7.2. Entendendo o que são Amazon ECS e EKS na Orquestração de Containers  

### 🧭 Introdução ao Amazon ECS e Amazon EKS
O **Amazon ECS (Elastic Container Service)** e o **Amazon EKS (Elastic Kubernetes Service)** são serviços da AWS voltados à **orquestração de contêineres**, permitindo o gerenciamento automatizado e escalável de aplicações baseadas em **microserviços**.

Esses serviços possibilitam a execução, escalonamento, monitoramento e integração de aplicações containerizadas sem a necessidade de configurar manualmente a infraestrutura.

---

### 🐳 ECS – Amazon Elastic Container Service
O **Amazon ECS** é um serviço **gerenciado de orquestração de contêineres** que simplifica a execução e administração de contêineres em um cluster AWS.

#### ⚙️ Principais características:
- **Gerenciamento simples:** automatiza o controle de clusters e tarefas.  
- **Escalabilidade automática:** aumenta ou reduz contêineres conforme a demanda.  
- **Integração nativa:** conecta-se facilmente com **IAM**, **VPC**, **CloudWatch** e outros serviços AWS.  
- **Segurança:** aplica políticas de acesso e controle detalhadas.  
- **Monitoramento:** usa o **CloudWatch** para métricas, logs e análise de desempenho.

#### 🧩 Casos de uso:
- Aplicações compostas por **microserviços** (ex: catálogo, carrinho, pagamentos).  
- Cada microserviço é empacotado em um **contêiner Docker**, e o ECS gerencia suas **tarefas** e **serviços** para manter a disponibilidade.  
- Utilização de **escalabilidade automática** para ajustar recursos durante picos de uso (como promoções).

#### 🗃️ Componentes relacionados:
- **ECS:** serviço de orquestração dos contêineres Docker.  
- **ECR (Elastic Container Registry):** repositório gerenciado para armazenar e versionar imagens de contêiner.

#### 💡 Quando usar:
Ideal para workloads com duração superior a 15 minutos e para quem busca simplicidade no gerenciamento sem precisar manter infraestrutura Kubernetes.

---

### ☸️ EKS – Amazon Elastic Kubernetes Service
O **Amazon EKS** é o serviço **gerenciado de Kubernetes da AWS**, que permite rodar clusters Kubernetes sem precisar instalar, configurar ou manter manualmente a infraestrutura.

#### ⚙️ Principais características:
- **Execução gerenciada:** a AWS cuida da disponibilidade, atualização e escalabilidade do cluster Kubernetes.  
- **Escalabilidade automática:** ajusta o número de nós e contêineres conforme a demanda.  
- **Alta segurança e confiabilidade:** integra-se ao ecossistema AWS, mantendo as práticas recomendadas do Kubernetes.  

#### 🧩 Casos de uso:
- Organizações que **já utilizam Kubernetes** ou desejam adotá-lo com o suporte da infraestrutura AWS.  
- Projetos complexos que demandam **controle granular, automação e compatibilidade multiplataforma.**

---

### ⚖️ Amazon ECS vs Amazon EKS

| Aspecto | **ECS (Elastic Container Service)** | **EKS (Elastic Kubernetes Service)** |
|----------|------------------------------------|--------------------------------------|
| **Tipo** | Serviço proprietário da AWS | Serviço baseado em Kubernetes (open source) |
| **Complexidade** | Menor — configuração e uso simplificados | Maior — exige familiaridade com Kubernetes |
| **Infraestrutura** | Usa **Fargate** (serverless) para eliminar o gerenciamento de servidores | Gerencia clusters Kubernetes completos |
| **Ideal para** | Iniciantes em containers e aplicações de média complexidade | Ambientes corporativos complexos e distribuídos |
| **Integração** | Totalmente integrado com o ecossistema AWS | Compatível com ferramentas nativas do Kubernetes |
| **Custos** | Mais simples e previsível | Mais flexível, mas pode ser mais caro |

#### 🧠 Conclusão:
- O **ECS** é ideal para **organizações que estão começando** a usar contêineres ou possuem arquiteturas simples/médias.  
- O **EKS** é mais adequado para **empresas com experiência em Kubernetes** e que lidam com **aplicações complexas e distribuídas**.  
- Ambos oferecem alta escalabilidade, segurança e integração com os serviços AWS — a escolha depende do **nível de maturidade e necessidade de controle** do ambiente.

---

📘 **Resumo geral:**
> ECS e EKS são soluções AWS para orquestração de contêineres.  
> ECS oferece simplicidade e integração total com a AWS, enquanto EKS entrega flexibilidade e controle via Kubernetes.



## 7.3.Entendendo como Funcionam o Amazon SNS e SQS na Comunicação   



## 7.4. Explorando Workflows Automatizados com AWS Step Functions  
