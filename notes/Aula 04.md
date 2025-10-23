# 4.	Redes na AWS

## 4.1 Amazon VPC  

### Redes na AWS  
- As redes na AWS são a base da comunicação entre todos os serviços na nuvem.  
- Cada recurso implantado — como instâncias EC2, bancos de dados RDS ou funções Lambda — precisa estar conectado a uma rede configurada dentro da Amazon Virtual Private Cloud (VPC).  
- A AWS <ins>permite que cada usuário crie sua própria rede virtual isolada</ins>, chamada VPC, com endereços IP, sub-redes, gateways e regras de segurança personalizadas.  
- Essa estrutura oferece o mesmo controle que um data center tradicional, porém com toda a escalabilidade e flexibilidade da nuvem.  
- Uma rede bem projetada na AWS é composta por:
  - <ins>Subnets</ins> (sub-redes): divisões lógicas da VPC, usadas para separar ambientes públicos e privados.  
  - <ins>Route Tables</ins> tabelas de rotas que determinam para onde o tráfego de rede será enviado.  
  - <ins>Internet Gateway (IGW) e NAT Gateway</ins> permitem a comunicação entre recursos internos e a Internet.  
  - <ins>Security Groups e Network ACLs</ins> mecanismos que controlam o tráfego de entrada (*inbound*) e saída (*outbound*).  

### O que é Amazon VPC  

- A Amazon Virtual Private Cloud (VPC) é uma <ins>rede virtual privada</ins> que você cria dentro da AWS.  
- Ela permite provisionar e gerenciar recursos da nuvem em um ambiente logicamente isolado, semelhante a uma rede física tradicional de data center, mas com recursos altamente escaláveis e gerenciáveis.
- Dentro de uma VPC, você define:
  - o <ins>intervalo de endereços IP (CIDR block)</ins>;  
  - as <ins>subnets</ins> (públicas e privadas) que compõem a rede;  
  - as <ins>regras de roteamento e segurança</ins>que controlam o tráfego;  
  - e a <ins>conectividade com a Internet</ins>ou com redes locais (por VPN ou AWS Direct Connect).  
- Cada conta AWS já possui uma VPC padrão, criada automaticamente em cada região, mas também é possível criar VPCs personalizadas para diferentes projetos ou ambientes (como produção, testes e desenvolvimento).

#### Principais características:  
- <ins>Isolamento de rede</ins> – fornece um ambiente virtual isolado, garantindo que apenas os recursos autorizados possam se comunicar.  
- <ins>Controle de tráfego</ins> – permite definir regras detalhadas de entrada e saída usando Security Groups (nível de instância) e Network ACLs (nível de subnet).  
- <ins>Suporte a sub-redes públicas e privadas</ins> – possibilita segmentar cargas de trabalho de acordo com o nível de exposição necessário.  
- <ins>Controle de endereçamento IP</ins> – o usuário define o intervalo de IPs (CIDR block) que será utilizado dentro da VPC.  
- <ins>Conectividade híbrida</ins> – permite conectar a VPC à rede local via VPN ou AWS Direct Connect, criando um ambiente híbrido.  

-  **Serviços Públicos x Privados**
  - <ins>Serviços Públicos</ins> → são aqueles que não exigem configuração de VPC para funcionar — por exemplo, serviços totalmente gerenciados pela AWS fora da rede do usuário.  
     - Exemplo: Amazon S3 e DynamoDB, que podem ser acessados diretamente pela Internet.  
  - <ins>Serviços Privados</ins> → exigem uma VPC configurada, pois são executados dentro da rede do usuário.  
     - Exemplo: EC2, RDS, EKS e VPC Endpoints, que funcionam dentro de subnets públicas ou privadas.  
  - Alguns serviços, como o AWS Lambda, podem operar tanto em modo público quanto privado, dependendo da configuração de rede escolhida.  

## 4.2 Amazon Subnet  

### O que é Amazon Subnet  

- Uma Subnet (Sub-rede) é uma <ins>faixa de endereços IP dentro de uma VPC (Virtual Private Cloud)</ins>.
 - Ela representa uma subdivisão lógica da rede criada na AWS e serve para organizar, isolar e controlar o tráfego entre os recursos implantados na nuvem.  
- Dentro de uma VPC, você pode criar várias subnets, cada uma com uma função específica (como pública ou privada), permitindo um desenho de rede mais seguro e escalável.  
 - Cada subnet precisa estar totalmente contida em uma única Zona de Disponibilidade (AZ) — ou seja, se a região escolhida tiver múltiplas zonas (como `us-east-1a`, `us-east-1b`), cada subnet será criada dentro de apenas uma delas. Isso garante isolamento físico e resiliência em caso de falhas.  
- Na prática, os recursos da AWS — como instâncias EC2, bancos de dados RDS ou funções Lambda conectadas à VPC — são sempre implantados dentro de uma subnet específica.  
- Além disso, é dentro dessas subnets que configuramos os <ins>grupos de segurança (Security Groups)</ins> e as <ins>regras de rede (inbound e outbound)</ins>, que determinam: 
  - quais endereços IP e protocolos podem acessar os recursos; 
  - e para onde esses recursos podem se conectar.

#### Analogia: o prédio e os apartamentos  
- *Podemos entender a relação entre VPC, Subnet e Endereçamento IP comparando com um prédio de apartamentos:*

| Elemento | Analogia | Função |
|:-----:|:-----:|:-----:|
| **VPC** | É como o <ins>prédio inteiro</ins> — representa a rede principal onde todos os andares e apartamentos existem. | Define o espaço total da rede (ex.: `10.0.0.0/16`). |
| **Subnet** | São os <ins>andares do prédio</ins> — sabemos quantos andares há e quantos apartamentos existem em cada um. | Divide a VPC em partes menores (ex.: `10.0.1.0/24` para um andar). |
| **Endereçamento IP** | É o <ins>número do apartamento</ins> — identifica exatamente onde está cada recurso. | Exemplo: `172.31.0.0 = AP 31`. |  
  
- Além disso, há dois tipos de acesso:
  - <ins>Acesso público:</ins> qualquer pessoa pode entrar (como uma porta aberta para a internet).
  - <ins>Acesso privado:</ins> é necessário liberar o acesso (como um andar ou apartamento com chave ou portaria).

#### Tipos de Subnet

| Tipo de Subnet | Descrição | Exemplo de uso |
|:-----:|:-----:|:-----:|
| **Pública** | Conectada à Internet por meio de um Internet Gateway (IGW). Recursos aqui podem ser acessados de fora da VPC. | Servidores web, balanceadores de carga, endpoints públicos. |
| **Privada** | Não tem acesso direto à Internet; a comunicação externa é feita por um NAT Gateway em uma subnet pública. | Bancos de dados, aplicações internas e serviços sensíveis. |

## 4.3. Amazon Security Group  

### O que é Amazon Security Group  

- O Amazon Security Group (SG) funciona como um <ins>firewall virtual</ins> que controla o tráfego de rede de entrada (*inbound*) e de saída (*outbound*) das instâncias dentro da VPC.  
- Cada instância EC2 deve estar associada a pelo menos um Security Group, que define:
  - Quais portas estarão abertas (ex.: 22 para SSH, 3389 para RDP, 80/443 para HTTP e HTTPS);
  - Quais protocolos podem ser utilizados (ex.: TCP, UDP, ICMP);
  - Quais origens ou destinos de IP têm permissão para enviar ou receber tráfego.  
- O Security Group atua como um filtro de permissões, permitindo o tráfego explícito definido pelo usuário e bloqueando qualquer outro por padrão.  

#### Exemplo:  
- Um servidor web pode ter:
  - <ins>Entrada (Inbound):</ins> porta 22 aberta apenas para o IP do administrador e porta 80 liberada para o público (`0.0.0.0/0`);  
  - <ins>Saída (Outbound):</ins> todas as portas liberadas para atualização e acesso externo.  

#### Principais características:    
- As regras são <ins>stateful</ins>: se o tráfego de entrada é permitido, a resposta de saída correspondente é automaticamente autorizada.  
- As regras podem ser <ins>editadas a qualquer momento</ins>, afetando imediatamente todos os recursos associados.  
- Uma instância pode ter <ins>vários Security Groups</ins> aplicados simultaneamente, e todas as permissões se combinam.  
- O Security Group é aplicado <ins>em nível de instância</ins>, enquanto as <ins>Network ACLs</ins> são aplicadas em nível de subnet.  

#### Analogia:   
*Um Security Group pode ser comparado a um porteiro eletrônico inteligente: Ele permite apenas as pessoas (tráfego) que você autorizou explicitamente. Mesmo que alguém tente entrar por outra porta (porta de rede diferente), ele bloqueia automaticamente. E, quando você permite alguém sair (resposta ao tráfego), ele deixa o retorno passar sem precisar de regras adicionais.*  

## 4.4 Amazon Route 53  

### O que é Amazon Route 53  

- O Amazon Route 53 é um serviço de DNS (Domain Name System) da AWS que faz a conversão de nomes de domínio em endereços IP.  
- Ele permite que os usuários acessem recursos na nuvem por meio de nomes fáceis de lembrar, como `meuservidor.com`, em vez de endereços IP numéricos.  
- Além da resolução de nomes, o Route 53 oferece funcionalidades importantes para o gerenciamento do tráfego e alta disponibilidade das aplicações.

#### Principais funções  
- <ins>Resolução de DNS:</ins> traduz nomes de domínio para os endereços IP correspondentes dentro ou fora da AWS.  
- <ins>Gerenciamento de tráfego:</ins> direciona as requisições de usuários para diferentes recursos (como instâncias EC2 ou balanceadores de carga) com base em políticas configuráveis.  
- <ins>Registro de domínios:</ins> permite comprar e gerenciar domínios diretamente pela AWS.  
- <ins>Verificação de saúde (Health Check):</ins> monitora o status dos endpoints e redireciona o tráfego em caso de falhas, garantindo disponibilidade contínua.

#### Exemplo:   
- Quando um usuário acessa `www.exemplo.com`, o Route 53 converte esse nome em um endereço IP associado ao servidor dentro da VPC.  
- Se houver várias instâncias ou regiões disponíveis, o serviço direciona o tráfego automaticamente para o endpoint mais saudável ou mais próximo, conforme as políticas configuradas.  

## 4.5 Amazon Cloudfront  

### O que é Amazon CloudFront

- O Amazon CloudFront é um serviço de <ins>Content Delivery Network (CDN)</ins> da AWS, responsável por distribuir conteúdo de forma rápida e segura para usuários no mundo todo.  
- Ele reduz a latência (tempo de resposta) ao armazenar cópias do conteúdo em locais chamados Edge Locations — pontos de presença espalhados globalmente.  
- Assim, quando um usuário acessa um site, vídeo ou sistema hospedado na AWS, o conteúdo é entregue a partir do servidor mais próximo, otimizando a velocidade de carregamento.  

#### Principais características:  
- <ins>Entrega global de conteúdo:</ins> distribui arquivos estáticos e dinâmicos (imagens, vídeos, páginas web, APIs, etc.) de forma eficiente.  
- <ins>Integração com outros serviços AWS:</ins> funciona junto com S3, EC2, Elastic Load Balancer e Route 53 para entregar conteúdo com alta disponibilidade.  
- <ins>Segurança:</ins> oferece suporte ao HTTPS, AWS Shield e AWS WAF, protegendo contra ataques e acessos não autorizados.  
- <ins>Cache inteligente:</ins> armazena temporariamente o conteúdo mais solicitado, reduzindo custos e o tráfego direto aos servidores de origem.  

#### Exemplo:  
- Um site hospedado em um bucket S3 pode usar o CloudFront para entregar imagens e vídeos a usuários em diferentes países.  
- O conteúdo é replicado automaticamente nas Edge Locations mais próximas de cada usuário, garantindo acesso rápido mesmo a longas distâncias.  


## 4.6. Amazon Elastic Load Balancer (ELB)  

### O que é Amazon Elastic Load Balancer  

- O Amazon Elastic Load Balancer (ELB) é um serviço da AWS que realiza a <ins>distribuição automática de tráfego</ins> entre múltiplas instâncias de servidores (como EC2) mantendo a operação estável mesmo em picos de acesso.
- Seu objetivo é garantir alta disponibilidade, escalabilidade e desempenho, evitando sobrecarga em um único servidor.  
- O ELB detecta automaticamente quando uma instância está inativa ou sobrecarregada e redireciona o tráfego para outras que estejam saudáveis.  

#### Onde aplicar  
- Em aplicações web com alto volume de acessos, para dividir o tráfego entre várias instâncias EC2.  
- Em arquiteturas distribuídas que precisam de resiliência* e balanceamento dinâmico de carga.  
- Em sistemas híbridos, conectando recursos locais e da nuvem sob um mesmo ponto de entrada.

---

### Tipos de Load Balancer  

| Tipo | Descrição | Uso Ideal |
|:-----:|:-----------|:-----------|
| **Application Load Balancer (ALB)** | Gerencia tráfego HTTP/HTTPS e distribui solicitações com base em regras (como caminhos de URL e cabeçalhos). | Aplicações web que precisam de roteamento avançado e suporte a WebSockets. |
| **Network Load Balancer (NLB)** | Gerencia tráfego TCP/UDP em nível de rede, oferecendo baixa latência e alta taxa de transferência. | Serviços que exigem alta performance e baixa latência, como sistemas financeiros e jogos online. |
| **Gateway Load Balancer (GLB)** | Combina balanceamento de carga com funções de segurança (firewall, detecção de intrusões). | Ambientes que precisam distribuir tráfego e aplicar inspeções de segurança simultaneamente. |
| **Classic Load Balancer (CLB)** | Balanceador legado que distribui tráfego HTTP/HTTPS e TCP entre instâncias EC2. | Aplicações mais antigas, criadas antes dos modelos ALB e NLB. |
