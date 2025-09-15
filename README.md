---

# 🚀 Desafio DIO – Gerenciamento de Instâncias EC2 na AWS

## 📘 Descrição do Projeto

Este repositório documenta minha prática no laboratório da DIO sobre EC2, AMIs e Snapshots EBS. O objetivo foi aplicar os conceitos aprendidos em aula, criar recursos na AWS, acessar via terminal com segurança e registrar todo o processo como material de apoio para estudos e futuras implementações.

---

## 🎯 Objetivos de Aprendizagem

- Criar e gerenciar instâncias EC2 na AWS  
- Criar AMIs personalizadas a partir de instâncias configuradas  
- Utilizar Snapshots EBS para backup e restauração de volumes  
- Acessar instâncias via SSH com chave segura  
- Encerrar recursos corretamente para evitar cobranças  
- Documentar processos técnicos de forma clara e organizada  
- Utilizar o GitHub como ferramenta de portfólio técnico

---

## 🛠️ Tecnologias e Ferramentas Utilizadas

- AWS EC2  
- Amazon EBS  
- AMI (Amazon Machine Image)  
- AWS Console  
- Git & GitHub  
- Markdown  
- Terminal (PowerShell / Bash)  
- Par de chaves SSH (.pem)

---

## 📂 Estrutura do Repositório

```
📁 desafio-ec2-dio/
├── README.md
├── /images
│   ├── ec2-criacao.png
│   ├── ami-criada.png
│   ├── snapshot-ebs.png
└── /scripts
    └── comandos-utilizados.txt
```
---

## ⚙️ Como funciona

Este projeto simula o ciclo completo de uma instância EC2 na AWS, desde a criação até a geração de uma AMI personalizada. Abaixo, o diagrama simplificado representa o fluxo de ações:

![Diagrama Simplificado EC2](images/diagrama-simplificado.png)

### 🔍 Etapas explicadas:

- **Usuário (Você):** Inicia o processo via terminal
- **PowerShell / Terminal:** Interface para enviar comandos
- **Chave SSH (.pem):** Autenticação segura para acesso à instância
- **Ambiente EC2:** Instância com Apache e Git instalados
- **Snapshot EBS:** Backup do volume principal
- **AMI personalizada:** Imagem reutilizável da instância configurada

---

---

## 🧪 Etapas Realizadas

### 1. Criação da Instância EC2
- Tipo escolhido: `t2.micro` (uso geral, gratuito no plano Free Tier)  
- Sistema operacional: Ubuntu Server 22.04  
- Configuração de rede e segurança: criação de Security Group com porta 22 liberada para SSH  
- Criação do par de chaves `key-desafio-dio.pem` para acesso seguro

### 2. Acesso via SSH
- Acesso realizado via terminal com o comando:
  ```bash
  ssh -i "key-desafio-dio.pem" ubuntu@ec2-18-116-61-89.us-east-2.compute.amazonaws.com
  ```
- Permissões ajustadas com:
  ```bash
  chmod 400 key-desafio-dio.pem
  ```
- Instalação de pacotes básicos:
  ```bash
  sudo apt update && sudo apt upgrade -y
  sudo apt install apache2 git -y
  ```

### 3. Criação da AMI
- Após personalização da instância, foi criada uma imagem personalizada:
  ```bash
  aws ec2 create-image --instance-id i-xxxxxxxx --name "MinhaAMI" --no-reboot
  ```

### 4. Gerenciamento de Volumes EBS
- Criação de Snapshot do volume principal:
  ```bash
  aws ec2 create-snapshot --volume-id vol-xxxxxxxx --description "Backup do volume principal"
  ```
- Teste de restauração em nova instância  
- Verificação de integridade dos dados após restauração

### 5. Encerramento do Projeto
- Encerramento da instância EC2 (`terminate`) após conclusão do desafio  
- Verificação e exclusão de volumes EBS não utilizados  
- Manutenção segura da chave `.pem`  
- Revisão do painel de faturamento para garantir que não há recursos ativos fora do Free Tier

---

## 📸 Capturas de Tela

As imagens estão disponíveis na pasta `/images` e ilustram:

- Criação da instância EC2  
- Processo de criação da AMI  
- Criação e visualização de Snapshots EBS  
- Configurações de segurança e rede  
- Acesso via terminal com chave SSH

---

## 💭 Reflexões Pessoais

- Durante o desafio, percebi como a criação de AMIs pode acelerar a replicação de ambientes e facilitar testes.  
- Snapshots são uma ferramenta poderosa para garantir segurança e continuidade, especialmente em ambientes de produção.  
- Aprendi a importância de encerrar corretamente os recursos para evitar cobranças e manter o ambiente limpo.  
- Documentar cada etapa me ajudou a consolidar o aprendizado e entender melhor o fluxo de trabalho na nuvem.

---

## 📚 Aprendizados e Insights

- A escolha correta da instância impacta diretamente no custo e desempenho  
- AMIs são ótimas para replicar ambientes com rapidez  
- Snapshots são essenciais para garantir segurança dos dados  
- O uso de chave SSH e permissões corretas é fundamental para segurança  
- A documentação técnica é uma ferramenta poderosa para aprendizado e compartilhamento  
- O uso do GitHub como portfólio técnico é uma excelente forma de mostrar evolução profissional

---

## 🔗 Recursos Complementares

- [Documentação oficial EC2 – AWS](https://docs.aws.amazon.com/pt_br/AWSEC2/latest/UserGuide/concepts.html)  
- [Guia de Markdown no GitHub](https://guides.github.com/features/mastering-markdown/)  
- [GitHub Quick Start](https://github.com/git-guides)

---

## 📬 Contato

- Projeto desenvolvido por **Patrícia Silva** como parte da formação na DIO.  
- Para dúvidas ou sugestões, entre em contato via [LinkedIn](https://www.linkedin.com/in/patricia-silva-714750140) ou abra uma issue neste repositório.
```
