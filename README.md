# TeleNanoAgent 🚀

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Telegram](https://img.shields.io/badge/Telegram-Bot-purple)](https://t.me/your_bot_username) <!-- Replace with live bot link after deploy -->

**TeleNanoAgent** is an ML-powered Telegram bot for AI image tasks. Users send text prompts (e.g., "Generate a cyberpunk cat") or images for edits, and the bot classifies intents with a fine-tuned BERT model, generates/edits via Google's Gemini Nano (free tier), and automates workflows (e.g., save to Drive) using n8n. Built for real-time multi-modal AI—combines NLP, computer vision, and automation.

Perfect for devs into Gen AI and bots; sharpens core ML skills like transformer fine-tuning. Ties into my other projects like [n8n-Task-Agent](https://github.com/superuser303/n8n-Task-Agent) for automation and [Visionflow](https://github.com/superuser303/Visionflow) for vision tasks.

## 🎯 Features
- **Intent Classification**: Fine-tuned BERT for detecting "generate image," "edit image," or "other" from user prompts.
- **Image Gen/Editing**: Powered by Gemini 2.5 Flash Image API (Nano Banana)—text-to-image or edit uploads (e.g., "Add a hat to this photo").
- **Task Automation**: n8n workflows for saving results to Google Drive, notifications, or chaining tasks.
- **Cloud-Ready**: Deployed on Vercel (bot) + Render/AWS (n8n/ML)—free tiers for prototyping.
- **ML Eval**: 90%+ accuracy on intents; lightweight for real-time use.

## 🛠 Tech Stack
- **ML**: Hugging Face Transformers (BERT fine-tuning), PyTorch, FAISS embeddings.
- **Bot**: Node.js + Telegraf.js for Telegram integration.
- **Gen AI**: Google Gemini API (free: 500 reqs/day).
- **Automation**: n8n (self-hosted).
- **Deployment**: Vercel, Render.com, Google Colab (for training).
- **Other**: Axios for API calls, Docker for n8n.

try it live: [t.me/TeleNanoAgentBot](https://t.me/your_bot_username) <!-- Add after deploy -->

## Architecture
Here's the high-level flow (built with draw.io—export as PNG):

![Workflow Diagram](architecture.png)
<!-- Telegram Input → BERT Intent API (HF) → Gemini Nano Gen/Edit → n8n Workflow (Save/Notify) → Bot Reply-->
## 🚀 Quick Start
### Prerequisites
- Node.js 18+ for bot.
- Python 3.8+ for ML (use Google Colab for free training).
- Free accounts: Telegram BotFather, Google AI Studio (Gemini key), Hugging Face (for BERT hosting), Vercel/Render.

### Installation
1. **Clone Repo**: git clone https://github.com/superuser303/TeleNanoAgent.git

2. **ML Model (BERT Training)**:
- Open `/ml/bert_intent_classifier.ipynb` in Google Colab.
- Run cells to fine-tune on CLINC150 dataset (~10 mins on free GPU).
- Push model to Hugging Face: `model.push_to_hub("superuser303/TeleNanoBERT")`.
- Get inference URL for bot integration.

3. **Bot Setup**:
- `cd bot`
- `npm install` (installs Telegraf, Axios, dotenv).
- Create `.env`
