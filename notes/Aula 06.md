# 6. Serviços de Armazenamento e CDN  

## 6.1. Introdução ao Amazon S3  

### O que é o Amazon S3  

- O Amazon Simple Storage Service (S3) é um serviço de armazenamento de objetos em nuvem oferecido pela AWS.  
- Ele permite armazenar, organizar e recuperar grandes volumes de dados de forma segura, escalável e durável.  
- Os dados são armazenados em <ins>buckets</ins>, que funcionam como contêineres — cada bucket possui um nome globalmente único e pode conter qualquer tipo de arquivo (imagens, logs, backups, vídeos etc.).  
- O S3 é amplamente utilizado para:
  - Hospedagem de sites estáticos,  
  - Armazenamento de backups e logs,  
  - Integração com aplicações que precisam de armazenamento de alta disponibilidade,  
  - Entrega de conteúdo via Amazon CloudFront.  

### Características principais  

- **Armazenamento de Objetos:** Cada arquivo é tratado como um *objeto* com seus metadados.  
- **Durabilidade:** Projetado para 99,999999999% (11 noves) de durabilidade.  
- **Disponibilidade:** 99,99% de disponibilidade anual.  
- **Segurança:**  
  - Criptografia de dados em repouso (SSE-S3, SSE-KMS, SSE-C) e em trânsito (HTTPS/TLS).  
  - Controle de acesso granular via IAM Policies e Bucket Policies.  
- **Escalabilidade automática:** Nenhum gerenciamento manual é necessário; o S3 cresce automaticamente conforme a demanda.  

### Classes de armazenamento  

| Classe | Descrição | Caso de uso |
|:--|:--|:--|
| **S3 Standard** | Alta durabilidade e baixa latência | Dados acessados frequentemente |
| **S3 Standard-IA** | Menor custo, acesso ocasional | Backups e dados arquivados |
| **S3 Intelligent-Tiering** | Movimenta automaticamente entre classes conforme uso | Dados com padrão de acesso variável |
| **S3 Glacier / Glacier Deep Archive** | Armazenamento de longo prazo e baixo custo | Arquivamento e retenção de longo prazo |

**Obs:** As classes de armazenamento ajudam a otimizar custos com base na frequência de acesso aos dados.

### Políticas de Acesso no S3  

- Com políticas de bucket (Bucket Policies), é possível controlar quem pode acessar os dados e quais ações podem ser executadas.  
- Essas políticas são escritas em JSON, usando o formato padrão da AWS Identity and Access Management (IAM).  

#### Exemplo – Tornar bucket público
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::meu-bucket-publico/*"
        }
    ]
}
```

### 6.2 Amazon Glacier  

#### O que é o Amazon Glacier
- O **Amazon Glacier** é um dos **tipos de armazenamento do Amazon S3**, projetado para **arquivamento e armazenamento de longo prazo**.  
- Ele oferece **armazenamento durável e de baixo custo** para dados acessados com pouca frequência, como **arquivos antigos, backups e registros históricos**.  
- Ideal quando os dados só precisam ser recuperados **após alguns dias** (geralmente 3 a 5 horas com recuperação padrão).  

#### Usos do AWS Glacier
- Armazenamento digital e arquivamento de longo prazo.  
- Armazenamento de dados científicos e de pesquisa.  
- Arquivamento de informações do setor de saúde.  
- Arquivamento regulatório e de conformidade (exigências legais).  

#### Custos e tempo de retenção
- O custo médio é de **US$ 0,01 por GB** para recuperações padrão.  
- Para **1.000 solicitações**, o custo é de aproximadamente **US$ 0,05**.  
- O tempo mínimo de armazenamento é de:
  - **90 dias** para o **S3 Glacier**.  
  - **180 dias** para o **S3 Glacier Deep Archive**, com estrutura de preços semelhante.  

#### Integração com ciclo de vida do S3
- O Glacier é normalmente usado em conjunto com o **gerenciamento de ciclo de vida** do Amazon S3, que **transfere automaticamente dados raramente acessados** para o armazenamento frio, **reduzindo custos**.  

#### Amazon Glacier na prática
- Usado em cenários onde o tempo de recuperação **não é imediato**, mas a **conservação e durabilidade dos dados** são cruciais.  
- Pode ser integrado com a **família AWS Snow** para transferir grandes volumes de dados físicos para a nuvem:  

  - **AWS Snowball:** migração de dados em larga escala ou uso como armazenamento local temporário.  
  - **AWS Snowball Edge:** transporte de dados em alta velocidade, via dispositivos físicos robustos.  
  - **AWS Snowmobile:** caminhão de transporte de dados capaz de levar até **100 petabytes** de uma só vez.  

> 💡 **Resumo:** O Amazon Glacier é ideal para armazenamento de longo prazo, de baixo custo e com acesso eventual, garantindo alta durabilidade e segurança para dados que não exigem recuperação imediata.


## 6.3. Entendendo a Distribuição de Conteúdo com Amazon CloudFront  

### Amazon CloudFront

O **Amazon CloudFront** é um **serviço de rede de entrega de conteúdo (CDN)** da AWS que distribui **conteúdos estáticos e dinâmicos** (como imagens, vídeos, arquivos CSS e JavaScript) de forma rápida e segura para os usuários finais.

Ele funciona **armazenando cópias em cache** desses conteúdos em **locais estratégicos** ao redor do mundo, chamados de **POPs (Points of Presence)**.  
Esses pontos de presença são responsáveis por **entregar o conteúdo a partir do local mais próximo do usuário**, reduzindo a **latência** e melhorando a **velocidade de carregamento**.

---

### Benefícios principais

- **Baixa latência:** entrega rápida de conteúdo a partir do POP mais próximo.
- **Maior desempenho:** melhora o tempo de resposta e experiência do usuário.
- **Escalabilidade automática:** lida com grandes volumes de acessos simultâneos.
- **Segurança integrada:** integração com AWS Shield e WAF para proteção contra ataques DDoS.
- **Compatibilidade com outros serviços AWS:** pode ser usado junto ao Amazon S3, EC2 e Elastic Load Balancer como origem de conteúdo.

---

### Exemplo prático

> Um site de comércio eletrônico usa o **Amazon CloudFront** para distribuir imagens de produtos.  
> Quando um usuário acessa o site, as imagens são entregues diretamente do **POP mais próximo**, garantindo um carregamento rápido.  
> Caso uma nova imagem seja adicionada, ela é buscada do **servidor de origem** na primeira vez e **armazenada em cache** para as próximas solicitações.

---

### Termos importantes

- **CDN (Content Delivery Network):** rede de servidores distribuídos que entrega conteúdo de forma eficiente.
- **POP (Point of Presence):** local físico onde o CloudFront mantém cópias do conteúdo.
- **Origem (Origin):** local original do conteúdo (ex: bucket S3, instância EC2 ou outro servidor).

---

### Amazon CloudFront na prática

- Configura-se uma **distribuição CloudFront**, definindo o **servidor de origem** (como S3 ou EC2).  
- O conteúdo é entregue automaticamente a partir do **POP mais próximo** de cada usuário.  
- Arquivos estáticos são **cacheados** e atualizados conforme a política de invalidação definida.  
- Ideal para **sites, streaming de vídeo, APIs** e qualquer aplicação que exija **alto desempenho e alcance global**.

---
#### Integração com Amazon S3
- O **Amazon CloudFront** pode usar um **bucket S3 como origem** de conteúdo.
- Essa integração permite **distribuir arquivos estáticos** (imagens, vídeos, documentos, etc.) globalmente, com **baixa latência** e **alta disponibilidade**.
- É amplamente utilizada para **sites estáticos, streaming e aplicações web**.

#### Pontos de Presença (Edge Locations)
- São **locais físicos distribuídos globalmente** usados pelo **Amazon CloudFront** para armazenar **cópias em cache** do conteúdo.
- **Principal vantagem:** reduzir a **latência** e o **tempo de carregamento** para o usuário final.
- Cada requisição é atendida pelo **POP mais próximo**, garantindo **melhor desempenho** e **experiência do usuário**.

#### O que são POPs (Points of Presence)
- São **locais estratégicos distribuídos globalmente** onde o CloudFront **armazena cópias em cache** de conteúdo estático.  
- Esses pontos reduzem a **latência** e melhoram o **tempo de resposta**, entregando o conteúdo a partir do local **mais próximo do usuário**.  
- Cada POP faz parte da **rede de distribuição global (CDN)** da AWS.

### 6.4. Associando Conceitos de Serviços de Armazenamento e CDN  
 - Exercício  

 ---

### 🔧 Políticas e Configurações Importantes nos Serviços de Armazenamento e CDN da AWS

#### **Lifecycle Policy (Política de Ciclo de Vida)**
- Define **regras automáticas** para **mover, arquivar ou excluir objetos** armazenados no Amazon S3 conforme o tempo.
- Exemplo: mover arquivos antigos para o **S3 Glacier** após 90 dias, reduzindo custos de armazenamento.
- Ajuda a automatizar a **gestão do ciclo de vida dos dados**, evitando acúmulo desnecessário de arquivos.

#### **Cross-Region Replication (CRR)**
- Permite **replicar automaticamente objetos do S3** entre buckets em **diferentes regiões da AWS**.
- Garante **alta disponibilidade** e **resiliência** dos dados, além de facilitar a conformidade com normas regionais.
- É configurada no nível do bucket e pode incluir **filtragem por prefixos ou tags**.

#### **Storage Class (Classe de Armazenamento)**
- Define o **tipo de armazenamento** utilizado para cada objeto no S3, de acordo com a frequência de acesso e custo.
- Exemplos:
  - **S3 Standard** → alta disponibilidade e acesso frequente.  
  - **S3 Standard-IA (Infrequent Access)** → menor custo para dados acessados esporadicamente.  
  - **S3 Glacier / Glacier Deep Archive** → ideal para **arquivamento de longo prazo**.
- Permite otimizar custos ao alinhar o tipo de armazenamento com o uso real dos dados.

#### **Cache Behavior (Comportamento de Cache)**
- Configuração usada no **Amazon CloudFront** para definir **como o conteúdo é armazenado, atualizado e entregue**.
- Permite especificar regras por **padrões de URL, headers, cookies ou query strings**.
- Influencia diretamente a **performance** do site ou aplicação ao determinar **quais arquivos são servidos a partir do cache** nos Edge Locations.

---

📘 **Resumo geral**
Essas políticas e configurações permitem automatizar o gerenciamento de dados, **melhorar desempenho**, **reduzir custos** e **aumentar a resiliência** das aplicações na AWS.  
Elas conectam o **Amazon S3**, **Glacier** e **CloudFront**, integrando estratégias de **armazenamento inteligente** e **entrega otimizada de conteúdo**.
