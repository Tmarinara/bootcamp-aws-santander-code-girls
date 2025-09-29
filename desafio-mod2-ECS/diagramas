# Diagramas de Arquitetura AWS – Módulo 2

## Diagrama 1 – EC2 + EBS
![Diagrama 1](./images/Diagramas-D1.drawio.png)

**Síntese:**  
Uma instância **EC2** roda a aplicação e está conectada a um volume **EBS**, que mantém os dados mesmo que a máquina seja desligada.

**Caso aplicado – Blog WordPress**  
Um blog simples é hospedado em uma instância EC2.  
O WordPress roda no EC2, enquanto o EBS guarda banco de dados, arquivos e sistema, garantindo persistência mesmo após reinicializações.

---

## Diagrama 2 – EC2 + EBS + S3
![Diagrama 2](./images/Diagramas-D2.drawio.png)

**Síntese:**  
O **EC2** roda o site. O **EBS** guarda os dados internos (banco e sistema). O **S3** armazena arquivos enviados pelos usuários, como imagens e documentos.

**Caso aplicado – Loja Virtual**  
Uma loja online roda no EC2, que processa as páginas da aplicação.  
O EBS armazena dados críticos da loja e o S3 recebe imagens enviadas pelos vendedores, com escalabilidade e baixo custo.

---

## 🔹 Diagrama 3 – Automação com Lambda
![Diagrama 3](./images/Diagramas-D3.drawio.png)

**Síntese:**  
O **S3** recebe arquivos. Sempre que um novo upload acontece, dispara uma função **Lambda**, que processa o arquivo sem precisar de servidor dedicado.

**Caso aplicado – Processamento de Imagens**  
Um usuário envia uma foto para a loja.  
O EC2 roda a aplicação, o EBS guarda banco e dados internos, e o S3 armazena a foto.  
A Lambda é acionada automaticamente e cria uma miniatura para o catálogo, deixando o sistema mais ágil e automatizado.

---

## Diagrama 4 – Auto Scaling com várias instâncias EC2
![Diagrama 4](./images/Diagramas-D4.drawio.png)

**Síntese:**  
Várias instâncias **EC2** são criadas automaticamente (auto scaling).  
Cada instância tem seu próprio **EBS**, mas todas compartilham o mesmo **S3**, que centraliza os arquivos.

**Caso aplicado – Plataforma de Streaming**  
Um serviço de vídeos precisa atender milhares de usuários.  
O auto scaling cria várias instâncias EC2 conforme a demanda aumenta.  
Os vídeos ficam no S3, acessíveis por todas as instâncias, garantindo escalabilidade e eficiência no uso dos recursos.

---

