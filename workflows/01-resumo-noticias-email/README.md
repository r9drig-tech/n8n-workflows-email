# 📊 Workflow 01 — Alerta de Ações com Análise de Sentimento por IA

Workflow que monitora automaticamente uma lista de ações da B3, detecta variações relevantes de preço (±3%), busca notícias via SerpAPI, analisa sentimento com Groq LLaMA 3.3 (gratuito) e envia alertas detalhados por e-mail. Histórico registrado no Google Sheets.

---

## ⚙️ Configuração

### Credenciais

| Credencial | Como obter | Custo |
|---|---|---|
| **Alpha Vantage** | [alphavantage.co](https://www.alphavantage.co/support/#api-key) | ✅ Grátis |
| **SerpAPI** | [serpapi.com](https://serpapi.com/) | ✅ 100 req/mês |
| **Groq API Key** | [console.groq.com/keys](https://console.groq.com/keys) | ✅ 100% Gratuito |
| **Gmail OAuth2** | n8n → Credentials | ✅ Gratuito |
| **Google Sheets OAuth2** | n8n → Credentials | ✅ Gratuito |

### Planilha — aba `Tickers`

| ticker | preco_referencia |
|--------|-----------------|
| PETR4.SAO | 38.50 |
| VALE3.SAO | 68.20 |

> Use sufixo `.SAO` para ações da B3

### Planilha — aba `Histórico de Alertas`
Crie com cabeçalhos:
```
Data | Hora | Ticker | Preço Referência | Preço Atual | Variação (%) | Sentimento IA | Confiança (%) | Resumo Notícias | Correlação Preço | Principais Fatores
```

---

## 💡 Dicas

- Limite de variação (±3%) ajustável no node **IF**
- Groq LLaMA 3.3: 14.400 req/dia gratuitas
- Alpha Vantage gratuito: 25 req/dia

---

## 📄 Arquivo

- [`workflow.json`](./workflow.json) — Importe diretamente no n8n
