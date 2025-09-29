# 1.	Introdução à AWS e Conceitos Básicos
## 1.1.	Visão geral da AWS: história, infraestrutura global, e modelo de negócios
### 1.1.1 História da AWS
A Amazon começou em 1994 como uma livraria online, fundada por Jeff Bezos. O nome inicial pensado era “Cadabra”, mas foi trocado para “Amazon”, inspirado no rio Amazonas (o maior do mundo). A AWS (Amazon Web Services) foi lançada em 2006, para fornecer serviços de infraestrutura em nuvem.
### 1.1.2.	Infraestrutura Global
A AWS tem a infraestrutura de nuvem mais abrangente e confiável do mundo. Essa infraestrutura é organizada em:
- Regions (Regiões): áreas geográficas.
- Availability Zones (Zonas de Disponibilidade): data centers independentes dentro de cada região.
  
Atualmente: 33 regiões e 105 zonas de disponibilidade, com planos de expansão.
### 1.1.3.	Modelo de Negócio da AWS
Diferente dos data centers tradicionais, o modelo é baseado em OPEX (pagar pelo uso), não em CAPEX (investimento inicial pesado em infraestrutura física).

Características:
- Pagamento conforme uso (Pay as you go).
- 	Variedade enorme de serviços: computação, bancos de dados, machine learning, IoT etc.
### 1.1.4.	Modelos de Serviço na Nuvem
IaaS (Infrastructure as a Service): infraestrutura (máquinas virtuais, redes).  
PaaS (Platform as a Service): plataforma pronta para desenvolver apps.  
SaaS (Software as a Service): aplicativos prontos para uso via nuvem.  

## 1.2.	Conceitos fundamentais: regiões, zonas de disponibilidade, serviços gerenciados

### 1.2.1.	Regiões (Regions)
Cada região é uma área geográfica que contém duas ou mais zonas de disponibilidade.  
São isoladas umas das outras, o que aumenta a tolerância a falhas e a estabilidade.  
Ao escolher uma região, você deve considerar:
-	Compliance (regras legais do país/mercado)
-	Disponibilidade de serviços (nem todos estão em todas as regiões)
-	Custo (os preços variam por região)
-	Latência (a proximidade dos usuários impacta a velocidade).

### 1.2.2.	Zonas de Disponibilidade (AZ – Availability Zones)
Uma AZ é um conjunto de data centers redundantes que funcionam de forma independente.  
Dentro de uma região, existem várias AZs conectadas logicamente para garantir alta disponibilidade.  
Caso uma falhe, as outras mantêm o sistema funcionando.  
Exemplo: a região US-West (Norte da Califórnia) tem as AZs us-west-1a, us-west-1b e us-west-1c.

### 1.2.3.	Serviços Gerenciados
A AWS é conhecida pela alta escalabilidade e robustez, atendendo sistemas enormes como Netflix e bancos.  
Serviço gerenciado significa que a AWS cuida da infraestrutura, atualização e segurança do serviço, e você só se preocupa com o uso.  
Isso permite que empresas foquem em seus negócios sem precisar administrar servidores e bancos de dados manualmente.  

## 1.3.	Configuração da conta AWS e práticas de segurança
### 1.3.1.	Conta Root
Ao criar uma conta AWS, é gerada a conta root, que tem todas as permissões sobre o ambiente.  
Essa conta deve ser criada e guardada com segurança, não utilizada para o dia a dia.

### 1.3.2.	Dados necessários para criar a conta AWS
E-mail válido  
Número de telefone  
Cartão de crédito (para verificação, não necessariamente para cobrança inicial).  

### 1.3.3.	Práticas de Segurança
- Não compartilhar os dados da conta root.  
- Ativar MFA (autenticação multifator) para proteção extra.  
- Criar usuários IAM para uso cotidiano em vez de usar a conta root.  
- Monitorar e-mails de notificações de cobrança.  
- Estabelecer barreiras de permissões (princípio do menor privilégio).  
- Sempre seguir as best practices da AWS IAM (conforme documentação oficial).

## 1.4.	Seja bem vindo a AWS  
### 1.4.1.	IAM (Identity and Access Management)
É o serviço que controla quem pode fazer o quê na AWS.  
Permite criar usuários, grupos e políticas de permissão.  
Exemplo: um grupo “Desenvolvedores” pode ter acesso somente ao S3 e EC2, mas não a outros serviços.  
**Boa prática**: aplicar o princípio do menor privilégio → cada pessoa só recebe a permissão necessária para sua função.  
IAM também pode ser automatizado com scripts (ex.: scriptIAM.sh) usando o AWS CLI.

### 1.4.2.	Controle de Gastos e Alertas
A AWS funciona no modelo **pay as you go** (pagar pelo uso).  
Para evitar surpresas, é essencial configurar:  
- Orçamentos (Budgets) → definem um limite de gasto.  
- Alertas (CloudWatch Alarms) → notificam quando o limite está sendo alcançado ou ultrapassado.  
Isso é fundamental para quem está em aprendizado (free tier) ou começando projetos.  

### 1.4.3.	Formas de Acesso à AWS

- 1.4.3.1.	AWS Management Console (Portal Web)  
  - É a forma mais intuitiva e usada por iniciantes.
  - Interface gráfica acessada pelo navegador: [console amazon](https://console.aws.amazon.com)
  - Permite clicar, navegar e configurar serviços como EC2, S3, RDS etc.
  - Ideal para quem está começando ou quer visualizar os recursos de forma mais clara.
     
- 1.4.3.2.	AWS CloudShell  
  - É um terminal integrado dentro do console AWS.
  - Já vem configurado com a AWS CLI e outras ferramentas.
  - Não precisa instalar nada localmente.
  - Bom para testar comandos rapidamente sem se preocupar com configuração no seu computador.
  - Link direto: [cloudshell amazon](https://console.aws.amazon.com/cloudshell)

-  1.4.3.3.	AWS CLI (Command Line Interface)  
   - Instalada no seu computador.
   - Permite criar, configurar e excluir recursos usando comandos de texto.
   - Muito útil para automação e integração em scripts (ex.: criar vários usuários IAM de uma vez).
   - Guia oficial de instalação: [doc amazon cli userguide](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)
   
- 1.4.3.4.	Infraestrutura como Código (IaC)  
   - Para cenários mais avançados, você pode usar:
     - AWS CloudFormation: cria recursos a partir de modelos em YAML/JSON.
     - Terraform (HashiCorp): ferramenta externa muito usada para automação multi-cloud.
   - É a forma mais profissional e escalável, usada em grandes projetos.


