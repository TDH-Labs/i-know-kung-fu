# Practical Guide to Hermes Agent

## Installation
1. Download the Hermes Agent from the official site (hermesagent.newsresearch.com).
2. For Mac, drag the app to your Applications folder. For Windows, run the installer.
3. Open the app and click "Install Hermes" to download dependencies.

## Initial Setup
1. **Model Configuration**:
   - Go to Google AI Studio (aastudio.google.com) and get an API key.
   - In Hermes, select Google as the provider and paste the API key.
   - Choose Gemini 2.5 Flash from the model list.
2. **Agent Context**:
   - Start a chat session and provide context about yourself. Example:
     ```
     Your name is Master Agent. I'm [Your Name]. I run [Your Role]. I'm interested in [Your Interests]. I prefer concise updates. My time zone is [Your Time Zone]. When you're unsure, ask me rather than guessing.
     ```

## Telegram Integration
1. In Telegram, search for @BotFather and create a new bot.
2. Copy the bot token and paste it into Hermes under Messaging > Telegram.
3. Get your Telegram user ID by messaging @userinfobot and paste it into Hermes.
4. Restart the messaging gateway in Hermes.

For more examples and troubleshooting, see [Code Examples](references/code_examples.md).