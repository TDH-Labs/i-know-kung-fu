# Practical Guide to Setting Up OpenClaw

This guide provides step-by-step instructions for setting up OpenClaw on a Virtual Private Server (VPS) and configuring integrations with Gmail, Google Drive, and Telegram.

## Setting Up OpenClaw on VPS
1. **Choose a VPS Provider**: Select a VPS provider like Hostinger. Use the provided coupon code for a discount.
2. **Deploy OpenClaw**: Follow the provider’s instructions to deploy OpenClaw on the VPS.
3. **Initial Setup**: Complete the initial bootstrap questions to configure OpenClaw’s personality and settings.

## Configuring Telegram Integration
1. **Create a Bot**: Use the BotFather in Telegram to create a new bot.
2. **Link Bot to OpenClaw**: Copy the bot’s access token and paste it into OpenClaw’s configuration.
3. **Test Integration**: Send a message to the bot and verify OpenClaw responds correctly.

## Integrating Gmail and Google Drive
1. **Enable Two-Factor Authentication**: Go to myaccount.google.com and enable two-step verification.
2. **Create App Passwords**: Generate an app password for OpenClaw to access Gmail.
3. **Configure Google Drive**: Follow the steps to enable Google Drive API and download the JSON file.
4. **Link Google Drive**: Paste the JSON file content into OpenClaw’s configuration.

## Automating Tasks
1. **Sponsorship Emails**: Use OpenClaw to read, filter, and respond to sponsorship emails. Attach media kits from Google Drive automatically.
2. **Meeting Scheduling**: Integrate Google Calendar to allow OpenClaw to schedule meetings autonomously.

For more detailed instructions and best practices, refer to the [Core Concepts](references/core_concepts.md).