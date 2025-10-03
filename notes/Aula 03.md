# 3.	Criando Recursos na AWS
## 3.1. Criando nosso Amazon EC2 - Hands On (prática)
- Lembrando que EC2 é uma máquina virtual de armazenamento na nuvem.  
- *Instruções em vídeo sobre criar uma unidade organizacional*
- *Instruções em vídeo sobre criar uma instância EC2*

### 3.1.1. Configurando o acesso local com MobaXterm
- O MobaXterm é um software usado no Windows para acessar servidores remotos.  
- Ele funciona como um cliente SSH (para Linux) e também suporta conexões de Desktop Remoto (para Windows).  
- Para se conectar a uma instância EC2, usamos chaves criptográficas:  
  - Chave pública: fica registrada na instância durante a criação.  
  - Chave privada: fica com o usuário local, permitindo autenticação segura.  
- Dessa forma, ao iniciar a instância EC2, você pode acessá-la localmente sem precisar de login/senha tradicional, apenas com a chave.  
- *Lembrete*:  
  > - Se não está utilizando desligar a instância (você encontra as opções hibernar, interromper, reiniciar, ...)  
  > - Definir os dados do usuário na criação
  > - *Instruções sobre como conectar acessar as instâncias atravez do MobaX, ambiente de trabalho local*  

### 3.1.2. Comparando o EC2 no Linux e Windows
- EC2 Linux:  
  - Acesso via SSH (Secure Shell).  
  - Normalmente na porta 22.  
  - Usuário conecta usando a chave privada no cliente SSH.  
- EC2 Windows:  
  - Acesso via Remote Desktop Protocol (RDP).  
  - Normalmente na porta 3389.  
  - Também usa chave criptográfica, mas para gerar a senha de administrador que será usada no login remoto.  
- Diferença principal: no Linux você interage pelo terminal (linha de comando), enquanto no Windows você acessa a interface gráfica do servidor.  

### 3.1.3. Criando EC2 com o Windows
- Durante a criação da instância, você define:
  - O tipo de instância (hardware virtualizado).
  - A imagem de sistema operacional (AMI).
  - O Security Group (firewall que libera portas de acesso, como 22 para Linux e 3389 para Windows).
  - O par de chaves (Key Pair), usado para acessar a instância.
- No caso do Windows:
  - Ao lançar a instância, você baixa a chave privada (.pem).
  - Essa chave serve para descriptografar a senha do Administrador do Windows.
  - Depois, abre-se o Remote Desktop no PC local, insere-se o IP público da instância e a senha de administrador gerada.
  - Pronto: você controla a instância Windows na nuvem como se fosse um PC normal.
  
## 3.2. Criando o nosso Amazon S3
### 3.2.1 Planejando nosso Amazon S3  
- Antes de criar um bucket, é preciso planejar qual será o objetivo (armazenar imagens, hospedar site, guardar backups etc.).  
- Escolher a região AWS próxima dos usuários para reduzir a latência.  
- Definir se o bucket será público ou privado. Por padrão, os buckets são privados.  
- Pensar na estrutura de pastas/objetos: cada arquivo dentro do bucket é chamado de objeto, identificado por uma chave (key).  

### 3.2.2 Criando o nosso Amazon S3  
- Criar um bucket no AWS Management Console:  
- Acessar o serviço S3.  
- Escolher o nome único global do bucket.  
- Selecionar a região de armazenamento.  
- Configurar permissões (público/privado).  
- Definir regras adicionais, como versionamento e criptografia.  
- É possível também criar via CLI (Command Line Interface) ou SDKs, mas aqui o foco é via console.  

### 3.2.3 Explicando o exercício prático  
- O exercício consiste em criar um bucket no S3, enviar arquivos e configurar o acesso.  
- É possível usar ferramentas como Git Bash ou o próprio console para manipular arquivos.  
- Em alguns casos, o S3 pode ser configurado para hospedar sites estáticos (HTML, CSS, JS).  
- Passos resumidos:  
  - Criar o bucket.  
  - Subir arquivos (upload).  
  - Definir permissões de acesso.  
  - (Opcional) Ativar hospedagem estática.  

## 3.3. 



