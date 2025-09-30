# 2.	Computação na Nuvem com EC2
## 2.1 Amazon EC2 (Elastic Compute Cloud)
### 2.1.1 O que são instâncias EC2
- EC2 (Elastic Compute Cloud) são as **máquinas virtuais** da AWS.
- Podem rodar Windows ou Linux e são compostas por: CPU, memória, disco, rede e sistema operacional
- Pertencem ao modelo **IaaS** (Infraestrutura como Serviço) → a AWS cuida da infraestrutura física, e o usuário gerencia o sistema operacional, dados e aplicativos
- É essencial escolher a instância adequada para equilibrar eficiência, escalabilidade e custos.

### 2.1.2. Tipos de instâncias EC2
- Existem diversos tipos de instâncias, cada uma otimizada para um perfil de uso:  
  - <ins>Sob Demanda (On-Demand)</ins>: pagas por hora/segundo de uso. Boa para testes e workloads irregulares
  - <ins>Reservadas (Reserved Instances)</ins>: mais baratas, mas exigem compromisso de 1 ou 3 anos
  - <ins>Spot Instances</ins>: podem ter até 90% de desconto, mas podem ser encerradas pela AWS com aviso prévio de 2 minutos  
- Além disso, há famílias de instâncias otimizadas para CPU, memória, armazenamento ou GPU.  

### 2.1.3. Otimização de recursos
- <ins>Objetivo principal</ins>: reduzir custos sem perder desempenho
- <ins>Estratégias</ins>:
  - Desligar instâncias não utilizadas em ambientes de teste ou desenvolvimento (ex.: à noite e finais de semana).
  - Remover recursos ociosos que continuam gerando custo, mesmo sem uso.
  - Escalar recursos conforme a demanda:
    - <ins>Verticalmente</ins>: aumentar/reduzir CPU, memória ou disco em uma instância existente.
    - <ins>Horizontalmente</ins>: adicionar mais instâncias ou discos para dividir a carga.
- O uso inteligente dessas práticas garante economia e eficiência operacional.

## 2.2 Armazenamento na Nuvem com Amazon EBS e S3
### 2.2.1. Amazon EBS (Elastic Block Store)
- É um armazenamento em blocos que pode ser anexado a instâncias EC2
- Funciona *como se fosse um HD externo virtual*: você escolhe o tipo e o tamanho e anexa à sua instância.
- Permite expansão rápida do armazenamento, sem precisar reinstalar a máquina
- <ins>Usos comuns</ins>:
  - Armazenar dados de bancos de dados (MySQL, PostgreSQL, Oracle).
  - Armazenar dados de aplicativos web e logs de sistema
- <ins>Principais vantagens</ins>:
  - Alta confiabilidade e desempenho.
  - Persistência dos dados mesmo que a instância EC2 seja desligada.

### 2.2.2 Amazon S3 (Simple Storage Service) -> Bucket/Balde
- É um armazenamento de objetos na nuvem, ideal para grandes volumes de dados
- Permite armazenar, organizar e recuperar dados de forma segura, escalável e durável.
- <ins>Classes de armazenamento</ins> (para otimizar custos):
  - *Standard*: acesso frequente.
  - *Standard-IA (Infrequent Access)*: acesso esporádico, custo mais baixo.
  - *Glacier/Deep Archive*: arquivos raramente acessados, custo muito reduzido
- Regras de ciclo de vida (*Lifecycle*):
  - Automatizam a transição entre classes (ex.: mover arquivos antigos para Glacier).
- <ins>Uso comum</ins>:
  - Guardar backups, imagens, vídeos, documentos.
  - Servir conteúdo estático (ex.: imagens de um site).

## 2.3 Desafio de projeto: Gerenciando Instâncias EC2 na AWS
### 2.3.1 Criação e uso de imagens AMI
- AMI é uma “imagem” que serve como modelo para criar instâncias EC2.
- <ins>Contém</ins>:
  - Sistema operacional.
  - Configurações de rede e segurança.
  - Aplicativos ou pacotes pré-instalados.
- Permite criar várias instâncias iguais, de forma rápida.
  
### 2.3.2. Snapshots EBS
- Snapshot é uma cópia pontual (backup) de um volume EBS.
- Fica armazenado no S3, mas de forma gerenciada pela AWS.
- <ins>Usos comuns</ins>:
  - Backup e recuperação de desastres.
  - Migrar volumes entre diferentes zonas de disponibilidade.
  - Criar novos volumes EBS a partir de snapshots.
- Benefício:
  - <ins>Incrementais</ins> → depois do primeiro snapshot completo, os seguintes só armazenam as mudanças, reduzindo custo.
