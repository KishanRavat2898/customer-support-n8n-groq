# 🤖 WhatsApp AI Agent for Adidas Customer Support Chatbot

An intelligent AI-powered customer support chatbot for Adidas, built using **n8n**, **Google Gemini 2.5 Flash**, and **WhatsApp** integration. This agent can handle customer queries, look up order records, and provide real-time support — all through WhatsApp.

---

## 🏗️ Technical Architecture

```
WhatsApp (Customer)
       ↓
    Twilio
       ↓
   n8n Webhook
       ↓
   AI Agent (Gemini 2.5 Flash)
    ↙     ↓       ↘
Memory  Airtable  Return Policy
        (Orders)    Tool
       ↓
  Reply via Twilio → WhatsApp
```



- 💬 **WhatsApp Integration** — Customers interact directly via WhatsApp
- 🧠 **AI-Powered Responses** — Uses Groq LLM (LLaMA 3.3) for fast, intelligent replies
- 📦 **Order Record Lookup** — Searches order database to answer order-related queries
- 🔁 **Session Memory** — Maintains conversation context across messages
- ⚡ **Low Latency** — Groq's ultra-fast inference for near-instant responses

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| [n8n](https://n8n.io/) | Workflow automation & agent orchestration |
| [Google Gemini 2.5 Flash](https://deepmind.google/technologies/gemini/) | AI chat model (Gemini 2.5 Flash) |
| [Twilio](https://www.twilio.com/) | WhatsApp messaging integration |
| [Airtable](https://airtable.com/) | Order records database |
| Return Policy Tool | Custom agent tool for return/refund queries |
| n8n Memory Node | Session-based conversation memory |

---

## 📋 Prerequisites

- [n8n](https://n8n.io/) instance (self-hosted or cloud)
- Google Gemini API key → [Get it here](https://aistudio.google.com/app/apikey)
- Twilio account with WhatsApp sandbox → [Get it here](https://www.twilio.com/)
- Airtable account with an Orders base → [Get it here](https://airtable.com/)

---

## ⚙️ Setup

### 1. Clone the repo
```bash
git clone https://github.com/YOUR_USERNAME/adidas-customer-support-bot.git
cd adidas-customer-support-bot
```

### 2. Import the workflow into n8n
- Open your n8n instance
- Go to **Workflows** → **Import from file**
- Select `workflow.json`

### 3. Configure credentials
Add the following credentials in n8n:

- **Google Gemini API Key** → Settings → Credentials → New → Google Gemini
- **Twilio** → Add your Twilio Account SID + Auth Token
- **Airtable** → Add your Airtable Personal Access Token

### 4. Set the correct model
In the **Google Gemini Model** node, make sure you're using:
```
gemini-2.5-flash
```

### 5. Activate the workflow
Click **Publish** in n8n to activate the webhook and go live.

---

## 🧪 Testing

You can test locally using n8n's built-in **Chat** panel:
1. Open the workflow in n8n
2. Click **Execute Workflow**
3. Use the chat window to send test messages like:
   - `"Where is my order?"`
   - `"I want to return my shoes"`
   - `"What are your store timings?"`

---

## 📁 Project Structure

```
adidas-customer-support-bot/
│
├── workflow.json        # n8n workflow export
└── README.md            # Project documentation
```

---

## 🔐 Environment Variables / Secrets

> ⚠️ **Never commit your API keys!**

Make sure the following are set as credentials in n8n and NOT hardcoded:

- `GEMINI_API_KEY`
- `TWILIO_ACCOUNT_SID`
- `TWILIO_AUTH_TOKEN`
- `AIRTABLE_API_KEY`

---

## 📸 Workflow Preview

> *(Add a screenshot of your n8n workflow here)*

---

## 🙌 Built By

Made with ❤️ using n8n + Groq

---

## 📄 License

MIT License — feel free to use, modify, and share.
