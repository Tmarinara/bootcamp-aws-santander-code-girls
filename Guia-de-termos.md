# 📖 Guia de Termos  
Este **Guia de Termos** funciona como um glossário prático dos conceitos e palavras que aparecem com frequência nos estudos do bootcamp.  

A ideia é ter um espaço de consulta rápida, onde cada termo é explicado de forma simples e direta, servindo tanto como revisão pessoal quanto como apoio para quem visitar este repositório.  

Aqui você vai encontrar:  
- Definições de termos técnicos relacionados à AWS e computação em nuvem.  
- Palavras-chave que se repetem nos materiais de aula, documentações e diagramas.  
- Breves exemplos ou contextos de uso para facilitar a compreensão.  
> 📌 Este guia será atualizado continuamente, acompanhando o progresso dos estudos e a evolução do repositório.

- **AWS (Amazon Web Services)** → é plataforma de nuvem mais abrangente e amplamente utilizada do mundo

- **Acesso à AWS**
  - <ins>AWS Management Console</ins> → Interface gráfica web para acessar e gerenciar serviços da AWS.  
  - <ins>AWS CloudShell</ins> → Terminal online direto no console AWS para executar comandos sem precisar instalar nada localmente.  
  - <ins>AWS CLI (Command Line Interface)</ins> → Ferramenta de linha de comando que permite gerenciar serviços AWS via scripts ou terminal.  
  
- **Amazon CloudWatch** → Monitora e rastreia a infraestrutura, entregando métricas em tempo real e permitindo criar alertas e respostas automáticas.  

- **Amazon EC2 (Elastic Compute Cloud)** → permite criar e gerenciar máquinas virtuais (instâncias), que podem rodar aplicações, bancos de dados, servidores web etc.
  - <ins>Sob Demanda (On-Demand)</ins>: pagas por hora/segundo de uso.
  - <ins>Reservadas (Reserved Instances)</ins>: mais baratas, mas exigem compromisso de 1 ou 3 anos
  - <ins>Spot Instances</ins>: podem ter até 90% de desconto, mas podem ser encerradas pela AWS com aviso prévio de 2 minutos  

- **Amazon EC2 Auto Scaling** → Ajusta automaticamente a quantidade de instâncias EC2 de acordo com a demanda.  

- **Amazon EBS (Elastic Block Store)** → Serviço de armazenamento em blocos persistente, funciona como um “HD virtual” para instâncias EC2.  

- **Amazon ELS (Elastic File System)** → Sistema de arquivos compartilhado e escalável que pode ser acessado por várias instâncias EC2 ao mesmo tempo.  

- **Amazon ELB (Elastic Load Balancing)** → Balanceador de carga que distribui o tráfego entre múltiplas instâncias EC2. Pode funcionar como único ponto de entrada para os clientes.  

-**Amazon S3 (Simple Storage Service)** → Serviço de armazenamento de objetos, usado para guardar arquivos (imagens, vídeos, backups etc.) em buckets.  
  - <ins>Bucket/Balde</ins> → → Contêiner lógico onde os objetos (arquivos) são armazenados dentro do S3.  

- **Availability Zone (AZ) = Zona de disponibilidade** → um ou mais data centers dentro de uma mesma região.

- **CDN (Content Delivery Network)** → Rede de entrega de conteúdo que utiliza edge locations espalhadas pelo mundo para reduzir a latência.  

- **Cloud**  
  - <ins>Cloud exclusiva</ins> → Nuvem privada dedicada apenas a uma organização.  
  - <ins>Cloud apenas pública</ins> → Uso exclusivo de nuvem pública (AWS, Azure, GCP).  
  - <ins>Cloud on-premises</ins> → Infraestrutura própria da empresa, sem uso de nuvem pública.  
  - <ins>Cloud híbrida</ins> →  Combinação de nuvem pública com infraestrutura privada ou on-premises.  

- **Conta root** → Conta principal da AWS criada no cadastro. Possui acesso total e deve ser usada com cautela (recomenda-se uso mínimo e ativar MFA). 

- **Data center** → Estrutura física que abriga servidores, rede, armazenamento e infraestrutura de TI.  

- **Data warehousing** → Técnica de armazenamento de grandes volumes de dados para análise e geração de relatórios.  

- **Escalabilidade** → Capacidade de aumentar ou reduzir recursos de forma elástica de acordo com a demanda.  

- **IAM (Identity Access Manager)** → Serviço que gerencia usuários, grupos e permissões de acesso aos recursos AWS.  
  - <ins>Usuários IAM</ins> = Identidades individuais com credenciais próprias.
  - <ins>Grupos IAM</ins> = Conjuntos de usuários que compartilham permissões em comum.

- **Imagens AMI (Amazon Machine Image)** → Modelos prontos para criar instâncias EC2, contendo SO, pacotes e configurações.  

- **Infraestrutura como Código (IaC)** → Modelo em que a infraestrutura é criada e gerida com arquivos de configuração (ex.: Terraform, CloudFormation).  

- **Instâncias EC2** → Máquinas virtuais executadas no EC2, podendo rodar diferentes sistemas e aplicações.  

- **Isolamento a falhas** → Estrutura da AWS que separa recursos entre regiões e zonas de disponibilidade para garantir alta disponibilidade.  

- **Latência** → Tempo de resposta entre o envio de uma solicitação e o recebimento da resposta; impacta a experiência do usuário.  

- **MFA (Multi-Factor Authentication)** → Autenticação em múltiplos fatores (senha + token/código) para aumentar a segurança.  

- **MobaXterm** → Ferramenta no Windows para conexões remotas via SSH/RDP; usada para acessar instâncias EC2.  

- **Modelo OPEX** → “Operational Expenditure”, custos operacionais recorrentes (ex.: pagar mensalmente pelos recursos usados).  

- **Modelo CAPEX** → “Capital Expenditure”, custos de capital para compra de infraestrutura física (ex.: comprar servidores).  

- **Modelos de serviço na nuvem**
  - <ins>IaaS (Infrastructure as a Service)</ins>: Infraestrutura como serviço (máquinas virtuais, redes).  
  - <ins>PaaS (Platform as a Service)</ins>: Plataforma pronta para desenvolvimento.  
  - <ins>SaaS (Software as a Service)</ins>: Aplicações prontas para uso via nuvem.  

- **Modelo de responsabilidade compartilhada** → Modelo onde AWS cuida da infraestrutura e o cliente é responsável pela configuração e dados.  

- **Pagamento conforme uso (Pay as you go).** → Modelo de cobrança baseado no consumo real de recursos.  
  -   <ins>Orçamentos (Budgets) </ins> → Definem limite de gasto ou uso de recursos.
  - <ins>Alertas (CloudWatch Alarms)</ins> → Notificam quando custos ou métricas ultrapassam o valor definido.  

- **Region = Região** → Área geográfica que contém múltiplas zonas de disponibilidade (ex.: Virgínia, São Paulo).  

- **Security Groups** → Firewalls virtuais que controlam tráfego de entrada/saída em instâncias EC2.  

- **Serverless** → Modelo em que o desenvolvedor roda código sem precisar gerenciar servidores (ex.: AWS Lambda).  

- **Snapshots EBS** → Cópias de segurança de volumes EBS em um ponto no tempo, armazenadas no S3.  

- **VPC (Virtual Private Cloud)** → Rede virtual isolada onde você pode definir sub-redes, tabelas de rota, gateways e firewalls.  







