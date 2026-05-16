# 📧 n8n Workflow — Resumo de Notícias por E-mail

> Workflow n8n que resume notícias diariamente com ChatGPT (GPT-4o) e envia por e-mail via Gmail.  
> Desenvolvido por **Rodrigo Salgado** — Analista de Dados & IA em transição para Engenheiro de Dados.

---

## 📋 Workflow

| # | Workflow | Descrição | Tecnologias |
|---|----------|-----------|-------------|
| 01 | [Resumo de Notícias por E-mail](./workflows/01-resumo-noticias-email/) | Acessa lista de sites, resume com ChatGPT e envia e-mail HTML diariamente ao meio-dia | Schedule · HTTP Request · ChatGPT GPT-4o · Gmail |

---

## 🔁 Fluxo

```
⏰ Schedule (12h)
    └─▶ 📋 Lista de Links
            └─▶ 🔀 Separar Links
                    └─▶ 🌐 HTTP Request (busca HTML)
                            └─▶ 🧹 Limpar HTML
                                    └─▶ 🤖 ChatGPT GPT-4o
                                            └─▶ 📝 Formatar Resultado
                                                    └─▶ 📧 Montar E-mail
                                                            └─▶ 📤 Gmail
```

---

## ⚙️ Configuração

### Credenciais necessárias

| Credencial | Como obter | Custo |
|---|---|---|
| **OpenAI API Key** | [platform.openai.com](https://platform.openai.com/api-keys) | Pago por uso |
| **Gmail OAuth2** | n8n → Credentials → Gmail OAuth2 | ✅ Gratuito |

### Personalizar os links
No node **"Lista de Links"**, edite o array com seus sites:
```json
["https://www.bbc.com/portuguese", "https://g1.globo.com", "https://tecnoblog.net"]
```

### Destinatário
No node **"Enviar E-mail Gmail"**, altere o campo `sendTo` para seu e-mail.

---

## 📧 Exemplo de E-mail Gerado

```
📰 Resumo de Notícias — quinta-feira, 15 de maio de 2026

🔗 Fonte: g1.globo.com

TÍTULO: Banco Central mantém Selic em 10,5%
RESUMO: O Comitê de Política Monetária...
```

---

## 📁 Estrutura

```
n8n-workflows-email/
├── README.md
└── workflows/
    └── 01-resumo-noticias-email/
        ├── workflow.json
        └── README.md
```

---

## 👨‍💻 Sobre o Autor

**Rodrigo Salgado**  
Analista de Power BI, Dados & IA | Em transição para Engenheiro de Dados & IA

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/SEU-PERFIL)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=flat&logo=github&logoColor=white)](https://github.com/r9drig-tech)

---

⭐ Se este repositório foi útil, deixe uma estrela!
