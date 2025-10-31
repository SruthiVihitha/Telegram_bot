# 🤖 Multi-AI Telegram Bot (Gemini & Claude)

This project, developed by the **AIMER Society - Indian Servers**, implements a powerful Telegram chatbot capable of leveraging multiple Large Language Models (LLMs) from Google (Gemini) and Anthropic (Claude) for advanced conversational capabilities.

## ⚠️ Security Warning & Critical Setup

**DO NOT** run this code with the hardcoded API keys provided in the source file (`.py`). Exposing these tokens compromises your accounts.

The project requires three sensitive credentials to be set as **Environment Variables** before execution.

### 1. Environment Variable Setup

| Variable Name | Required Key | Purpose | 
| ----- | ----- | ----- | 
| `TELEGRAM_BOT_TOKEN` | Your Telegram Bot Token (`71566...`) | Connects the script to the Telegram network. | 
| `GEMINI_API_KEY` | Your Google Gemini API Key (`AIzaS...`) | Authenticates calls to the Gemini model. | 
| `ANTHROPIC_API_KEY` | Your Anthropic API Key (`sk-ant...`) | Authenticates calls to the Claude model. | 

**How to set variables (Windows PowerShell):**

```

$env:TELEGRAM\_BOT\_TOKEN="YOUR\_BOT\_TOKEN"
$env:GEMINI\_API\_KEY="YOUR\_GEMINI\_KEY"
$env:ANTHROPIC\_API\_KEY="YOUR\_ANTHROPIC\_KEY"

```

### 2. Code Correction: Replacing Hardcoded Keys

You must update the Python file to retrieve these variables using `os.getenv()` and delete the hardcoded strings:

| Section | Old Code (Hardcoded) | New Code (Secure) | 
| ----- | ----- | ----- | 
| **Telegram Token** | `TelegramBOT_TOKEN = '...'` | `TelegramBOT_TOKEN = os.getenv('TELEGRAM_BOT_TOKEN')` | 
| **Gemini Key** | `genai.configure(api_key="...")` | `genai.configure(api_key=os.getenv('GEMINI_API_KEY'))` | 
| **Anthropic Key** | `client = anthropic.Anthropic(api_key="...")` | `client = anthropic.Anthropic(api_key=os.getenv('ANTHROPIC_API_KEY'))` | 

## 🛠️ Installation and Execution

### 1. Dependencies

Install all necessary Python packages:

```

\!pip install pyTelegramBotAPI openai google-generativeai anthropic

```

### 2. Code Structure Note (Important!)

Your provided file defines and starts **two separate bots** sequentially:

1. The first definition connects to **Gemini** and calls `bot.polling()`.

2. The second definition connects to **Anthropic (Claude)** and calls `bot.polling()`.

Since `bot.polling()` is a blocking function, **only the second bot (Anthropic/Claude) will run.**

To use both, you must restructure the code to have a single bot instance where handlers route messages to the desired AI.

### 3. Execution

Assuming you have corrected the key usage and chosen which bot handler you wish to run (or merged them):

1. Save the Python file (e.g., as `multi_ai_bot.py`).

2. Set the environment variables (see above).

3. Run the script:

```

python multi\_ai\_bot.py

```

## 📊 Results and Demonstration

This section is for documenting the bot's functionality and performance.

| Feature | Description | Status | 
| ----- | ----- | ----- | 
| **Model Used** | The active LLM in the current deployment (e.g., Claude-3 Opus). | `[Specify Active Model Here]` | 
| **Functionality** | Confirms the bot is responding to user messages. | `[Working / Troubleshooting]` | 
| **Error Handling** | Confirms the `try...except` block catches API errors gracefully. | `[Working / Troubleshooting]` | 

### ⏯️ Video Demonstration

A video demonstration is the best way to showcase the real-time interaction with the bot on Telegram.
```
C:\Users\sruth\OneDrive\Desktop\projects\vids_aimer\telegram_bot.mp4
```
<img width="1383" height="846" alt="image" src="https://github.com/user-attachments/assets/8c30138b-0687-4e96-a9f0-4250569e1c9e" />
<img width="934" height="874" alt="image" src="https://github.com/user-attachments/assets/dec57a49-bff4-4d3c-98ac-d5e2cda69969" />
