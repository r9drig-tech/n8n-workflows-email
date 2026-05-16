# 📧 Workflow 01 — Resumo de Notícias por E-mail com ChatGPT

Workflow que acessa uma lista de sites de notícias diariamente ao meio-dia, extrai o conteúdo, resume com ChatGPT GPT-4o (título + 3 linhas) e envia tudo consolidado em um único e-mail HTML formatado.

---

## 🔁 Fluxo

```
⏰ Schedule (12h)
    └─▶ 📋 Lista de Links (Set)
            └─▶ 🔀 Separar Links (Code)
                    └─▶ 🌐 HTTP Request
                            └─▶ 🧹 Limpar HTML (Code)
                                    └─▶ 🤖 ChatGPT GPT-4o
                                            └─▶ 📝 Formatar Resultado (Set)
                                                    └─▶ 📧 Montar E-mail (Code)
                                                            └─▶ 📤 Gmail
```

---

## ⚙️ Configuração

### 1. Credenciais

| Credencial | Onde obter |
|---|---|
| **OpenAI API Key** | [platform.openai.com/api-keys](https://platform.openai.com/api-keys) |
| **Gmail OAuth2** | n8n → Settings → Credentials → Add → Gmail OAuth2 |

### 2. Personalizar links
No node **"Lista de Links"**:
```json
["https://www.bbc.com/portuguese", "https://g1.globo.com", "https://tecnoblog.net"]
```

### 3. Destinatário
No node **"Enviar E-mail Gmail"** → campo `sendTo` → seu e-mail.

---

## 💡 Dicas

- Sites com anti-bot: use `https://r.jina.ai/SUA_URL` no lugar da URL direta
- O prompt usa `temperature: 0.4` para respostas objetivas
- Adicione quantos links quiser no array

---

## 📄 Arquivo

- [`workflow.json`](./workflow.json) — Importe diretamente no n8n
