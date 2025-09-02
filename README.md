# Monitoramento de Links com n8n e Telegram

Este projeto foi desenvolvido seguindo o tutorial do **canal Código Fonte TV**, onde aprendi a utilizar o **n8n** para criar uma automação que verifica periodicamente o status de uma lista de URLs e envia alertas via **Telegram** sempre que algum link estiver fora do ar.  

Durante o processo foi ensinado:  
- Como configurar o **Docker** e o **Docker Compose** para rodar o n8n.  
- Como preparar variáveis de ambiente em um arquivo `.env`.  
- Como estruturar um workflow no n8n utilizando **nós (nodes)** como Cron, HTTP Request, If e integração com o **Telegram**.  
- Como persistir dados e configurar volumes no Docker.  
- Como importar e ativar workflows no painel do n8n.  

**Assista ao vídeo tutorial:** https://youtu.be/UDWEAMwS7rg

---

## 🔧 Pré-requisitos

- Docker  
- Docker Compose  
- Conta e Bot no Telegram (Token)  
- Chat ID do Telegram para receber alertas  

---

## 🚀 Instalação

1. Clone este repositório:

   ```bash
   git clone <URL do repositório>
   cd <nome-do-diretório>
Copie o arquivo de exemplo .env e preencha as variáveis:

bash
Copiar código
cp sample.env .env
Edite o .env com:

DOMAIN_NAME: seu domínio (ex: codigofonte.tv)

SUBDOMAIN: subdomínio para acesso ao n8n (ex: n8n)

GENERIC_TIMEZONE: fuso horário (ex: America/Sao_Paulo)

Edite o arquivo data/meus-links.txt e adicione as URLs que deseja monitorar (uma URL por linha).

##⚙️ Configurando o n8n
Inicie os serviços:

bash
Copiar código
docker-compose up -d
Acesse o painel do n8n em http://localhost:5678 (ou https://<SUBDOMAIN>.<DOMAIN_NAME> se configurado).

Crie uma credencial do tipo Telegram:

Token: fornecido pelo @BotFather

Nome da credencial: Telegram account (deve coincidir com o nome usado no workflow)

Importe o workflow:

Clique em + > Importar > Importar de arquivo

Selecione workflows/check-links-telegram.json

Salve e ative o workflow.

##📝 Estrutura do Projeto

pgsql
Copiar código
.
├── docker-compose.yml              # Definição do serviço n8n
├── sample.env                      # Exemplo de variáveis de ambiente
├── data/
│   └── meus-links.txt              # Arquivo com as URLs a monitorar
└── workflows/
    └── check-links-telegram.json   # Workflow exportado do n8n
    
##📊 Uso
O workflow é executado a cada minuto (configurado no node Cron).

Se algum link retornar statusCode diferente de 200, uma mensagem de alerta é enviada para o chat do Telegram configurado.

Logs podem ser visualizados com:

bash
Copiar código
docker-compose logs -f n8n

##🌐 Hospedagem Recomendada
Para um ambiente de produção mais estável e seguro, recomendo hospedar o n8n em um VPS.

O Código Fonte TV sugere a Hostinger, que possui planos de VPS já com n8n pré-instalado.

Use o cupom CODIGOFONTE para desconto.

Link: https://codigofonte.click/hostingern8n

