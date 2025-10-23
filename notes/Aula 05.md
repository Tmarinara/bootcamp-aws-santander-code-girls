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
 
## 5.2. Introdução ao Amazon DynamoDB  

### O que é Amazon DynamoDB  

### Amazon DynamoDB na Prática  

## 5.3. Explorando Estratégias de Backup e Recuperação de Dados na AWS  

### Entendendo o backup de dados  

### Definindo a estratégia de backup e recuperação de dados  


