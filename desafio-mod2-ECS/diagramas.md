# Diagramas de Arquitetura AWS – Módulo 2

## Diagrama 1 – EC2 + EBS
<img width="2285" height="1490" alt="Diagramas-D1 drawio" src="https://github.com/user-attachments/assets/c35d86aa-181c-4f7f-8f64-a33bfaae5e84" />

**Síntese:**  
Uma instância **EC2** roda a aplicação e está conectada a um volume **EBS**, que mantém os dados mesmo que a máquina seja desligada.

**Caso aplicado – Blog WordPress**  
Um blog simples é hospedado em uma instância EC2.  
O WordPress roda no EC2, enquanto o EBS guarda banco de dados, arquivos e sistema, garantindo persistência mesmo após reinicializações.

---

## Diagrama 2 – EC2 + EBS + S3
<img width="2138" height="2265" alt="Diagramas-D2 drawio" src="https://github.com/user-attachments/assets/b2d37c0f-647b-4353-a036-608b5e5b4f20" />

**Síntese:**  
O **EC2** roda o site. O **EBS** guarda os dados internos (banco e sistema). O **S3** armazena arquivos enviados pelos usuários, como imagens e documentos.

**Caso aplicado – Loja Virtual**  
Uma loja online roda no EC2, que processa as páginas da aplicação.  
O EBS armazena dados críticos da loja e o S3 recebe imagens enviadas pelos vendedores, com escalabilidade e baixo custo.

---

## Diagrama 3 – Automação com Lambda
<img width="2138" height="2265" alt="Diagramas-D3 drawio" src="https://github.com/user-attachments/assets/c4ff1c5d-900a-4162-906d-a8ff00f382ff" />

**Síntese:**  
O **S3** recebe arquivos. Sempre que um novo upload acontece, dispara uma função **Lambda**, que processa o arquivo sem precisar de servidor dedicado.

**Caso aplicado – Processamento de Imagens**  
Um usuário envia uma foto para a loja.  
O EC2 roda a aplicação, o EBS guarda banco e dados internos, e o S3 armazena a foto.  
A Lambda é acionada automaticamente e cria uma miniatura para o catálogo, deixando o sistema mais ágil e automatizado.

---

