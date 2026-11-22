# Vida Verde Chatbot

## 1. Sobre o projeto

O Vida Verde Chatbot é um assistente virtual desenvolvido para realizar o primeiro atendimento de clientes pelo WhatsApp e auxiliar no pré-cadastro de potenciais compradores da empresa Vida Verde.

O objetivo é coletar informações dos interessados, apresentar as condições comerciais e registrar os dados para facilitar o atendimento da equipe de vendas.

A Vida Verde comercializa vasos e produtos para jardinagem, não plantas.

## 2. Tecnologias utilizadas

- **n8n:** automação e gerenciamento do fluxo de atendimento.
- **Evolution API:** integração com o WhatsApp.
- **Google Gemini:** inteligência artificial para interpretar mensagens e conduzir conversas.
- **Google Sheets:** armazenamento e consulta dos cadastros.
- **Docker:** execução dos serviços em containers.

## 3. Funcionamento do chatbot

O fluxo de atendimento contempla:

1. Recebimento de mensagens pelo WhatsApp.
2. Identificação de clientes e consulta de cadastros existentes.
3. Coleta de nome, CPF ou CNPJ, empresa, cidade e estado.
4. Identificação da preferência por atendimento presencial ou remoto.
5. Definição do responsável pelo atendimento conforme a região e a preferência.
6. Apresentação do pedido mínimo e prazo estimado de entrega conforme o estado.
7. Identificação do interesse do cliente.
8. Registro ou atualização das informações no Google Sheets.

Os cadastros são identificados pelo CPF ou CNPJ, evitando duplicidade de registros.

## 4. Regras comerciais

O chatbot informa o pedido mínimo e o prazo estimado de entrega de acordo com o estado informado pelo cliente.

Os valores e prazos são definidos pelas condições comerciais da empresa. O chatbot não deve inventar preços, produtos, estoque ou condições comerciais.

## 5. Estrutura do repositório

```text
VidaVerde-Chatbot/
├── .gitignore
├── docker-compose.yml
├── README.md
└── workflows/
    └── Vida-Verde-Pre-Cadastro.json
```

## 6. Como executar

### Requisitos

- Windows.
- Docker Desktop.
- Acesso ao GitHub.
- Conta e credenciais do Google.
- Credencial de acesso à API do Google Gemini.
- Evolution API configurada e conectada ao WhatsApp.

### Iniciar o n8n

Na pasta do projeto, execute:

```powershell
docker compose up -d
```

O n8n estará disponível em:

http://localhost:5678

O arquivo `docker-compose.yml` deste repositório configura o n8n na versão 2.44.6.

A Evolution API é um serviço separado e deve estar configurada antes de realizar os testes de integração com o WhatsApp.

## 7. Importação do workflow

1. Acesse o n8n.
2. Abra o menu de workflows.
3. Selecione a opção de importar workflow de arquivo.
4. Escolha `workflows/Vida-Verde-Pre-Cadastro.json`.
5. Configure as credenciais do Google Sheets e do Google Gemini.
6. Configure a autenticação da Evolution API no nó de envio de mensagens.
7. Confira a URL do webhook e a conexão com a instância do WhatsApp.
8. Salve e ative o workflow.

**Atenção:** o arquivo disponibilizado no GitHub possui um marcador no lugar da chave da Evolution API. É necessário configurar uma chave válida no ambiente de execução. As credenciais não são disponibilizadas neste repositório.

## 8. Banco de dados e armazenamento

O Google Sheets é utilizado para armazenar os dados dos clientes cadastrados.

O projeto também utiliza o armazenamento do n8n para manter os dados necessários à execução e continuidade das conversas.

## 9. Segurança

- Não publicar chaves de API, senhas ou credenciais.
- Não publicar arquivos de banco de dados.
- Não compartilhar arquivos `.env` com informações privadas.
- Configurar as credenciais diretamente nos serviços utilizados.

## 10. Objetivo acadêmico

O projeto demonstra a aplicação de inteligência artificial e automação no atendimento comercial, utilizando interpretação de linguagem natural, extração de informações, integração entre APIs e armazenamento estruturado de dados.

Desenvolvido como projeto acadêmico por:

- Aline Pertille Pereira
- Arthur Ziani Moraes
- Eduardo Lopes
