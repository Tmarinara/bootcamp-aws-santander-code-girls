# Desafio – Gerenciamento de Instâncias EC2 na AWS

Este desafio faz parte do **Módulo 2 – Computação na Nuvem com EC2** do Bootcamp **AWS – Santander Code Girls 2025**.  
O objetivo é consolidar os conhecimentos em **gerenciamento de instâncias EC2** na AWS, documentando de forma clara os passos e aprendizados obtidos.

---

## Objetivos de Aprendizagem
- Aplicar conceitos de criação e gerenciamento de instâncias **EC2.**
- Representar arquiteturas em nuvem com uso de **S3**, **EBS** e **Lambda Functions**.  
- Compreender a integração com recursos como **EBS (Elastic Block Store)** e boas práticas de configuração.  
- Documentar processos técnicos de forma clara e organizada no GitHub.   
  
   
---

## O que foi feito
1. Estudo das vídeo-aulas sobre EC2 e conceitos relacionados (instâncias, snapshots, tipos de armazenamento).  
2. Anotações estruturadas sobre diferenças entre armazenamento **EBS** e **armazenamento efêmero (Instance Store)**.  
3. Criação de diagramas de arquitetura no [**draw.io**](https://www.drawio.com/) representando como o autor (usuário) pode enviar arquivos para a nuvem e como esses dados podem ser processados/armazenados pelos serviços da AWS;
4. Organização do repositório no GitHub com README, anotações e pasta de imagens para diagramas.  
                                         
---

## Anotações relevantes
-  **O que são** EC2, EBS, S3 e Lambda
  -- **EC2 (Elastic Compute Cloud)** → serviço de máquinas virtuais na nuvem. É como se fosse o “computador” onde você instala sistema operacional e roda suas aplicações.
  -- **EBS (Elastic Block Store)** → serviço de armazenamento em blocos. É o “HD/SSD” persistente que você conecta ao seu EC2 para que os dados não se percam ao desligar a instância.
  -- **S3 (Simple Storage Service)** → serviço de armazenamento de objetos. Ótimo para guardar arquivos como fotos, PDFs, backups, vídeos. Não é um disco de sistema, é um “balde (bucket)” na nuvem.
  -- **Lambda** → serviço serverless. Você escreve funções que rodam sem precisar criar/gerenciar servidores. O código é executado “sob demanda”, por exemplo, quando um arquivo chega no S3.
                                         
- **Como se relacionam normalmente**
  -- O **EC2** é a base → hospeda sistemas, aplicações e bancos.
  -- O **EBS** dá persistência ao EC2 → sem ele, os dados se perdem ao desligar a máquina.
  -- O **S3** complementa → usado para guardar arquivos de longo prazo, estáticos ou grandes volumes.
  -- O **Lambda** entra como automação → integra S3 e EC2. Exemplo: ao subir uma foto no S3, uma função Lambda pode processar essa foto e salvar resultado em outro bucket.
