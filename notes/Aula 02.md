# 2.	Computação na Nuvem com EC2
## 2.1 Amazon EC2
### 2.1.1 O que são instâncias EC2
- EC2 (Elastic Compute Cloud) são as máquinas virtuais da AWS.
- Podem rodar Windows ou Linux e são compostas por: CPU, memória, disco, rede e sistema operacional
- Pertencem ao modelo IaaS (Infraestrutura como Serviço) → a AWS cuida da infraestrutura física, e o usuário gerencia o sistema operacional, dados e aplicativos
- É essencial escolher a instância adequada para equilibrar eficiência, escalabilidade e custos.
### 2.1.2. Tipos de instâncias EC2
- Existem diversos tipos de instâncias, cada uma otimizada para um perfil de uso:  
  - **Sob Demanda (On-Demand)**: pagas por hora/segundo de uso. Boa para testes e workloads irregulares
  - **Reservadas (Reserved Instances)**: mais baratas, mas exigem compromisso de 1 ou 3 anos
  - **Spot Instances**: podem ter até 90% de desconto, mas podem ser encerradas pela AWS com aviso prévio de 2 minutos  
- Além disso, há famílias de instâncias otimizadas para CPU, memória, armazenamento ou GPU.  

### 2.1.3. Otimização de recursos
- **Objetivo principal**: reduzir custos sem perder desempenho
- **Estratégias**:
  - Desligar instâncias não utilizadas em ambientes de teste ou desenvolvimento (ex.: à noite e finais de semana).
  - Remover recursos ociosos que continuam gerando custo, mesmo sem uso.
  - Escalar recursos conforme a demanda:
    - **Verticalmente**: aumentar/reduzir CPU, memória ou disco em uma instância existente.
    - **Horizontalmente**: adicionar mais instâncias ou discos para dividir a carga.
- O uso inteligente dessas práticas garante economia e eficiência operacional.

## 2.2 Armazenamento na Nuvem com Amazon EBS e S3
### 2.2.1. Amazon EBS
•	É um armazenamento em blocos que pode ser anexado a instâncias EC2
•	Funciona como se fosse um HD externo virtual: você escolhe o tipo e o tamanho e anexa à sua instância.
•	Permite expansão rápida do armazenamento, sem precisar reinstalar a máquina
•	Usos comuns:
o	Armazenar dados de bancos de dados (MySQL, PostgreSQL, Oracle).
o	Armazenar dados de aplicativos web e logs de sistema
•	Principais vantagens:
o	Alta confiabilidade e desempenho.
o	Persistência dos dados mesmo que a instância EC2 seja desligada.

### 2.2.2 Amazon S3

## 2.3 Desafio de projeto: Gerenciando Instâncias EC2 na AWS
### 2.3.1 Criação e uso de imagens AMI

### 2.3.2. Snapshots EBS

