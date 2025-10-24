# 5.	Banco de Dados na AWS  

## 5.1 Amazon RDS  

### Amazon RDS  

- O **Amazon Relational Database Service (Amazon RDS)** é um serviço de banco de dados relacional gerenciado da AWS.  
- Ele simplifica tarefas de configuração, operação e escalabilidade de bancos de dados na nuvem, permitindo criar uma instância de banco de dados em poucos minutos.  
- O Amazon RDS é compatível com diversos mecanismos de banco de dados, oferecendo flexibilidade e otimização de desempenho conforme a demanda.  

#### Benefícios  
- <ins>Fácil de gerenciar:</ins> elimina tarefas manuais de administração, como instalação e manutenção de hardware.  
- <ins>Automação:</ins> executa backups automáticos, atualizações de software e monitoração contínua.  
- <ins>Escalabilidade:</ins> permite aumentar ou reduzir capacidade conforme a carga de trabalho.  
- <ins>Alto desempenho:</ins> otimizado para aplicações que exigem respostas rápidas e estabilidade.  
- <ins>Custos controláveis:</ins> modelo de pagamento sob demanda (pay-as-you-go).  

#### Se atentar a: 
- <ins>Custo variável:</ins> depende do tempo de uso e da capacidade provisionada.  
- <ins>Complexidade em cenários avançados:</ins> configurações de replicação ou tunning podem exigir conhecimento técnico adicional.  

### Banco de dados na AWS  

- A AWS oferece várias opções de <ins>bancos de dados gerenciados</ins> — relacionais e não relacionais — que atendem diferentes casos de uso.  
- O Amazon RDS é voltado para bancos de dados **relacionais**, enquanto serviços como DynamoDB e DocumentDB atendem modelos NoSQL.  
- Com o RDS, é possível integrar aplicações web, móveis e corporativas, mantendo alta disponibilidade e segurança dos dados.  

### O que é Amazon RDS  

- O Amazon RDS oferece suporte a <ins>múltiplos mecanismos de banco de dados</ins>:  
  - **Amazon Aurora** — compatível com MySQL e PostgreSQL, combina desempenho de banco comercial com custo reduzido.  
  - **Oracle** — implantação rápida com licenciamento flexível (BYOL ou sob demanda).  
  - **Microsoft SQL Server** — configuração simplificada e compatível com ferramentas nativas.  
  - **MySQL** — sistema amplamente utilizado, compatível com aplicações web existentes.  
  - **PostgreSQL** — banco de dados objeto-relacional robusto e altamente extensível.  
  - **MariaDB** — derivado do MySQL, mantém compatibilidade e desempenho otimizado.  

Essas opções permitem ao usuário escolher o mecanismo mais adequado ao seu ambiente e integrar facilmente com outras soluções AWS, como EC2, Lambda e S3.  

### Criando um banco de dados com Amazon RDS  

- No console da AWS, é possível criar um banco de dados RDS em poucos passos:  
  1. Acessar o serviço Amazon RDS.  
  2. Clicar em <ins>“Criar banco de dados”</ins>.  
  3. Selecionar o mecanismo desejado (ex.: MySQL, PostgreSQL, Aurora).  
  4. Definir o nome, credenciais e configurações de instância.  
  5. Escolher parâmetros de armazenamento, segurança e disponibilidade.  
  6. Concluir a criação e conectar-se à instância via endpoint fornecido.  

Após criado, o Amazon RDS gerencia automaticamente o backup, a manutenção e o monitoramento, permitindo que o usuário se concentre na aplicação, não na infraestrutura.  

*OBS*:
<ins>Banco relacional</ins>: estrutura fixa, ideal para dados com relações e necessidade de consistência.
<ins>Banco não relacional</ins>: estrutura flexível, ideal para alto desempenho e dados não estruturados
 
## 5.2 Amazon DynamoDB  

### Amazon DynamoDB  

- O Amazon DynamoDB é um serviço de banco de dados NoSQL totalmente gerenciado  pela AWS.  
- Foi projetado para oferecer alta escalabilidade, desempenho consistente e baixa latência, independentemente do volume de dados.  
- Ideal para aplicações que exigem respostas em tempo real e grande flexibilidade na estrutura dos dados (como redes sociais, jogos e IoT).  

### O que é Amazon DynamoDB  

- O DynamoDB armazena dados em tabelas, mas sem o modelo fixo de colunas e relações dos bancos relacionais.  
- Cada item é identificado por uma <ins>chave primária</ins> (como `CustomerID`), o que garante rápidas operações de leitura e gravação.  
- Ele trabalha com dados não estruturados ou semiestruturados, permitindo maior liberdade na modelagem.  

#### Benefícios  
- <ins>Gerenciamento automatizado:</ins> sem necessidade de configurar servidores, backups ou atualizações manuais.  
- <ins>Escalabilidade automática:</ins> ajusta capacidade de leitura e gravação conforme a demanda.  
- <ins>Baixa latência global:</ins> resposta inferior a 10 ms, adequada para uso em tempo real.  
- <ins>Integração com outros serviços AWS:</ins> como Lambda, S3, API Gateway e CloudWatch.  

## 5.3 Estratégias de Backup e Recuperação de Dados na AWS  

### Entendendo o backup de dados  

- O <ins>backup de dados</ins> é uma cópia dos dados do sistema, da configuração ou de aplicativos, armazenada separadamente do original.  
- Ele protege contra falhas de sistema, erros humanos, eventos de segurança e desastres naturais, evitando a perda total ou parcial das informações.  
- O backup é parte essencial da proteção e continuidade dos negócios, garantindo que os dados possam ser restaurados rapidamente quando necessário.  

#### Importância do backup  
- <ins>Prevenção de perda de dados:</ins> reduz riscos causados por falhas ou exclusões acidentais.  
- <ins>Continuidade operacional:</ins> mantém os sistemas ativos mesmo após incidentes.  
- <ins>Conformidade e auditoria:</ins> atende a requisitos legais e contratuais de retenção de dados.  
- <ins>Redução de custos:</ins> evita perdas financeiras associadas à indisponibilidade de sistemas.  

### Definindo a estratégia de backup e recuperação de dados  

#### 1. Avaliação e Planejamento  
- Identifique os dados críticos que precisam de maior proteção.  
- Defina os objetivos de:  
  - **RPO (Recovery Point Objective):** quanto de dados pode ser perdido entre backups.  
  - **RTO (Recovery Time Objective):** quanto tempo o sistema pode ficar fora do ar antes da recuperação.  

#### 2. Seleção de Serviços AWS  
- **Amazon S3:** utilizado para armazenar backups de forma durável e escalável.  
- **AWS Backup:** centraliza e automatiza o gerenciamento de backups em diferentes serviços.  
- **Amazon RDS – Automated Backups e Snapshots:** cria cópias automáticas e permite restauração pontual.  
- **Amazon DynamoDB – On-Demand Backup e PITR (Point-In-Time Recovery):** possibilita backups contínuos e sob demanda.  

#### 3. Implementação da Estratégia  
- Configure backups automáticos diários para dados críticos e backups incrementais para otimizar tempo e armazenamento.  
- Utilize cópias de segurança em múltiplas regiões (Multi-Region) para maior resiliência.  
- Automatize o processo com AWS Lambda e monitore com Amazon CloudWatch.  

#### 4. Recuperação e Teste  
- Documente os planos de recuperação para diferentes tipos de falhas.  
- Realize testes periódicos de restauração para validar a eficácia dos backups.  
- Conduza simulações de desastre (Backup Drill) para medir tempo e confiabilidade da recuperação.  

#### 5. Segurança e Conformidade  
- Use criptografia em trânsito e em repouso (TLS, S3 Server-Side Encryption, RDS Encryption).  
- Configure políticas do AWS IAM para restringir o acesso a backups apenas a usuários autorizados.  
- Habilite AWS CloudTrail para registrar todas as atividades de backup e recuperação.  

#### 6. Custo e Otimização  
- Utilize o AWS Cost Explorer para monitorar e otimizar gastos com armazenamento.  
- Implemente políticas de ciclo de vida no S3 para mover backups antigos para classes mais baratas (ex.: S3 Glacier).  
