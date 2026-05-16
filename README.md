# 📧 n8n Workflow — Alerta de Ações com IA + Gmail

> Workflow n8n que monitora ações da B3, detecta variações relevantes, busca notícias via SerpAPI, analisa sentimento com Groq LLaMA 3.3 (gratuito) e envia alertas por e-mail via Gmail.  
> Desenvolvido por **Rodrigo Salgado** — Analista de Dados & IA em transição para Engenheiro de Dados.

---

## 📋 Workflow

| # | Workflow | Descrição | Tecnologias |
|---|----------|-----------|-------------|
| 01 | [Alerta de Ações com IA](./workflows/01-resumo-noticias-email/) | Monitora cotações da B3, detecta variações ±3%, busca notícias e envia alerta com análise de sentimento por e-mail | Alpha Vantage · SerpAPI · Groq LLaMA · Gmail · Google Sheets |

---

## 🔁 Fluxo

```
⏰ Schedule (19h Seg–Sex)
    └─▶ 📊 Ler Tickers (Google Sheets)
            └─▶ 🔁 Loop por Ticker
                    └─▶ 📈 Buscar Cotação (Alpha Vantage)
                            └─▶ 🧮 Calcular Variação %
                                    └─▶ ⚖️ Variação > ±3%?
                                           │
                                    ✅ SIM └─▶ 📰 Buscar Notícias (SerpAPI)
                                                    └─▶ ✏️ Preparar Prompt
                                                            └─▶ 🦙 Groq LLaMA 3.3 (gratuito)
                                                                    └─▶ 📋 Formatar Alerta
                                                                            └─▶ 📤 Gmail
                                                                                    └─▶ 📁 Histórico (Sheets)
                                           │
                                    ❌ NÃO └─▶ 😴 Sem Alerta
```

---

## ⚙️ Configuração

### Credenciais necessárias

| Credencial | Como obter | Custo |
|---|---|---|
| **Alpha Vantage API Key** | [alphavantage.co](https://www.alphavantage.co/support/#api-key) | ✅ 25 req/dia grátis |
| **SerpAPI Key** | [serpapi.com](https://serpapi.com/) | ✅ 100 req/mês grátis |
| **Groq API Key** | [console.groq.com/keys](https://console.groq.com/keys) | ✅ 100% gratuito |
| **Gmail OAuth2** | n8n → Credentials → Gmail OAuth2 | ✅ Gratuito |
| **Google Sheets OAuth2** | n8n → Credentials → Google Sheets | ✅ Gratuito |

### Planilha Google Sheets — aba `Tickers`

| ticker | preco_referencia |
|--------|-----------------|
| PETR4.SAO | 38.50 |
| VALE3.SAO | 68.20 |
| ITUB4.SAO | 32.00 |

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

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/r9drig-power-bi)
[![GitHub](https://img.shields.io/badge/GitHub-100000?style=flat&logo=github&logoColor=white)](https://github.com/r9drig-tech)

---

⚠️ **Aviso:** Os workflows de análise financeira são para fins educacionais. Não constituem recomendação de investimento.

⭐ Se este repositório foi útil, deixe uma estrela!
