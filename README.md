# 📡 Monitoramento de Links com n8n e Telegram  

Este projeto foi desenvolvido seguindo o **tutorial do canal Código Fonte TV**, onde aprendi a utilizar o **n8n** para criar uma automação que:  
- Verifica periodicamente o status de uma lista de URLs.  
- Envia alertas via **Telegram** sempre que algum link estiver fora do ar.  

🔗 **Vídeo tutorial:** [https://youtu.be/UDWEAMwS7rg](https://youtu.be/UDWEAMwS7rg)  

---

## 📘 Aprendizados do processo  

Durante o estudo foram abordados:  
- Como configurar o **Docker** e o **Docker Compose** para rodar o n8n.  
- Como preparar variáveis de ambiente em um arquivo `.env`.  
- Como estruturar um **fluxo de trabalho no n8n**, utilizando nós (*nodes*) como **Cron**, **HTTP Request**, **If** e integração com o **Telegram**.  
- Como persistir dados e configurar volumes no Docker.  
- Como importar e ativar fluxos de trabalho no painel do n8n.  

---

## 🔧 Pré-requisitos  

- Docker  
- Docker Compose  
- Conta e Bot no Telegram (**Token**)  
- Chat ID do Telegram para receber os alertas  

---

## 🚀 Instalação  

1. **Clone este repositório**  

   ```bash
   git clone <URL-do-repositorio>
   cd <nome-do-diretorio>

## 📝 Estrutura do Projeto


├── docker-compose.yml                    # Definição do serviço n8n

├── sample.env                            # Exemplo de variáveis de ambiente

├── data/

│   └── meus-links.txt                    # Arquivo com as URLs a monitorar

└── workflows/
    └── check-links-telegram.json         # Workflow exportado do n8n
