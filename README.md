# 🤖 Bot de WhatsApp com Node.js e Express

Este projeto é um **bot do WhatsApp** desenvolvido com [`whatsapp-web.js`](https://github.com/pedroslopez/whatsapp-web.js) e [`Express`](https://expressjs.com/). Ele permite:

✅ **Enviar mensagens em massa para múltiplos contatos**  
✅ **Receber e armazenar respostas automaticamente**  
✅ **Responder automaticamente a mensagens inválidas**  
✅ **Encerrar conversas após a resposta**  

---

## 🚀 Tecnologias Utilizadas

- [Node.js](https://nodejs.org/)
- [Express](https://expressjs.com/)
- [whatsapp-web.js](https://github.com/pedroslopez/whatsapp-web.js)
- [qrcode-terminal](https://www.npmjs.com/package/qrcode-terminal)

---

## 📂 Estrutura do Projeto

```
/whatsapp-bot
│── package.json
│── README.md
│── server.js
│── src/
│   │── config/
│   │   ├── whatsappClient.js        <-- Configuração do cliente WhatsApp
│   │── controllers/
│   │   ├── messageController.js     <-- Lógica de envio de mensagens
│   │   ├── responseController.js    <-- Lógica para capturar respostas
│   │── routes/
│   │   ├── messageRoutes.js         <-- Rotas para envio de mensagens
│   │   ├── responseRoutes.js        <-- Rotas para consultar respostas
│   │── database/
│   │   ├── responses.js             <-- Banco de dados em memória
│── server.js                        <-- Inicia a API
```

---

## 🔧 Instalação e Configuração

### 1️⃣ Clonar o Repositório

```bash
git clone https://github.com/seu-usuario/whatsapp-bot.git
cd whatsapp-bot
```

### 2️⃣ Instalar Dependências

```bash
npm install
```

### 3️⃣ Iniciar o Bot

```bash
node server.js
```

📌 **Escaneie o QR Code exibido no terminal** para conectar o bot ao seu WhatsApp.

---

## 🌐 Uso da API

### 📩 Enviar Mensagens

**Endpoint:** `POST /api/messages/send`

**Body (JSON):**

```json
{
    "contatos": ["5500000000000", "5500000000000"],
    "mensagem": "Você deseja uma marmita hoje? Responda com: 1 - Frango, 2 - Carne, 3 - Não quero."
}
```

**Resposta esperada (JSON):**

```json
{
    "success": true,
    "message": "Mensagens processadas",
    "enviados": ["5500000000000@c.us", "5500000000000@c.us"],
    "erros": []
}
```

---

### 📥 Consultar Respostas Recebidas

**Endpoint:** `GET /api/responses`

**Resposta esperada (JSON):**

```json
[
    { "telefone": "5500000000000", "resposta": "1", "timestamp": "2025-03-20T12:30:45.000Z" },
    { "telefone": "5500000000000", "resposta": "2", "timestamp": "2025-03-20T12:32:10.000Z" }
]
```

---

## ✅ Funcionalidades

- 📩 Envio de mensagens em massa para múltiplos contatos  
- 📥 Captura de respostas e armazenamento  
- 🚀 Respostas automáticas para mensagens inválidas  
- 🔒 Encerramento automático de conversas após resposta  

---

## ⚠️ Possíveis Erros e Soluções

| Erro                  | Causa Provável                        | Solução                                                  |
|-----------------------|----------------------------------------|-----------------------------------------------------------|
| QR Code não aparece   | Sessão anterior ainda está ativa       | Remova a pasta `.wwebjs_auth` e reinicie o bot            |
| Erro ao enviar mensagem | Número inválido ou não está no WhatsApp | Verifique se o número está correto (com código do país)   |
| Servidor não inicia   | Porta ocupada                          | Altere a porta no arquivo `server.js`                     |

---

## 💡 Dicas Finais

🛠️ Se precisar de persistência de dados, substitua `responses.js` por um banco de dados real como MongoDB, SQLite, etc.  
🛡️ Para rodar em produção, utilize o **pm2** para manter o bot ativo:

```bash
npm install -g pm2
pm2 start server.js
```

🚀 Para adicionar novas funcionalidades, crie novos módulos dentro de `controllers/` e `routes/`.

---
