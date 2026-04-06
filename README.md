
# 🤖 Atendente com IA e Gerador Automático de Contratos

Sistema automatizado criado com **n8n** que realiza o atendimento ao cliente de um evento via Telegram usando Inteligência Artificial, e gera contratos personalizados automaticamente quando o formulário de inscrição é preenchido.

---

## 📌 Visão Geral

Este projeto é composto por **dois fluxos automatizados que se complementam**:

1. **Atendente com IA** — Responde dúvidas dos clientes no Telegram usando um agente de IA com memória e base de conhecimento, e envia o link de inscrição quando o cliente decide participar.

2. **Gerador de Contratos** — Ativado quando o formulário de inscrição é preenchido. Cria automaticamente um contrato personalizado no Google Drive, envia via Telegram e manda um e-mail de confirmação para quem se inscreveu.

---

## 🔁 Fluxo 1 — Atendente com IA (Telegram)

### O que faz
- Recebe mensagens via **Telegram** (texto, imagem ou áudio)
- Identifica o tipo de mídia e direciona corretamente com um **nó Switch**
- Transcreve mensagens de áudio usando **Whisper (OpenAI)**
- Analisa imagens com **OpenAI Vision**
- Usa um **Agente de IA** com memória e base de conhecimento personalizada para responder dúvidas sobre o evento
- Convence a cliente a se inscrever e envia o link do formulário
- Retorna respostas personalizadas via **Telegram**

### Ferramentas e Nós Utilizados
- Telegram Trigger
- Switch (roteamento de mensagens)
- OpenAI (análise de imagem + transcrição de áudio)
- AI Agent com Simple Memory
- Base de Conhecimento (documento personalizado)
- Loop Over Items + Split Out
- Formatter

### Visualização do Fluxo


---

## 🔁 Fluxo 2 — Gerador de Contratos (Formulário → Google Drive → Notificação)

### O que faz
- Ativado pelo **preenchimento de um formulário**
- Copia um **modelo de contrato** do Google Drive
- Atualiza o documento com os **dados personalizados da cliente**
- Faz o download do contrato gerado
- Envia o contrato para o responsável via **Telegram**
- Envia um **e-mail de confirmação** para quem preencheu o formulário

### Ferramentas e Nós Utilizados
- On Form Submission
- Google Drive (Copiar + Baixar)
- Google Docs (Atualizar documento)
- Telegram (Enviar documento)
- Gmail (Enviar e-mail de confirmação)

### Visualização do Fluxo
https://github.com/Jh5611/n8n-ai-attendant-contract-generator.PTBR/blob/main/Workfolw_1.jpeg

---

## 🔗 Como os Fluxos se Conectam


Cliente entra em contato pelo Telegram
        ↓
[Fluxo 1] IA atende e convence o cliente
        ↓
Cliente preenche o formulário de inscrição
        ↓
[Fluxo 2] Contrato é gerado e enviado automaticamente


---

## 🛠 Tecnologias Utilizadas

| Ferramenta | Uso |
|------------|-----|
| n8n | Automação dos fluxos |
| Telegram API | Canal de atendimento ao cliente |
| OpenAI (GPT-4 + Whisper) | Agente de IA, análise de imagem, transcrição de áudio |
| Google Drive | Armazenamento e gestão do modelo de contrato |
| Google Docs | Geração dinâmica de documentos |
| Gmail | E-mail de confirmação para a inscrita |

---

## 💡 Destaques do Projeto

- ✅ Atende mensagens de texto, imagem e áudio automaticamente
- ✅ IA com memória persistente para conversas naturais
- ✅ Base de conhecimento personalizada para o evento
- ✅ Geração de contratos totalmente automatizada com dados personalizados
- ✅ Notificação por múltiplos canais (Telegram + E-mail)
- ✅ Zero intervenção manual após a configuração inicial

## 📲 Outros Canais Suportados

Embora esta implementação utilize o **Telegram**, a mesma lógica de automação pode ser facilmente adaptada para funcionar com **WhatsApp** e **Instagram Direct** — basta trocar os nós de mensagens no n8n. O agente de IA, a memória, a base de conhecimento e o fluxo de geração de contratos permanecem exatamente os mesmos.

---

## 👩‍💻 Autor

Desenvolvido por **Jessé Honório Carvalho** — Apaixonada por automação e Inteligência Artificial.

Me encontre no [LinkedIn](https://www.linkedin.com/in/seuperfil) | [GitHub](https://github.com/seuusuario)
