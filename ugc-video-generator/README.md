# AI UGC Video Ad Generator

AI-powered UGC video ad generation workflow built with n8n.

This workflow automatically:

- receives product images from Telegram
- analyzes products using AI vision
- extracts product details and visual characteristics
- generates marketing-ready product images
- creates detailed video production scripts
- generates UGC-style video ads using Veo 3
- monitors generation progress automatically
- sends finished videos back to Telegram

## Features

- AI product analysis
- AI image generation
- AI video script generation
- UGC-style video creation
- Telegram bot integration
- Automated workflow orchestration
- End-to-end ad generation

## Workflow Architecture

Telegram → Product Analysis → AI Image Generation → AI Video Script → Veo 3 Video Generation → Telegram Delivery

## Tech Stack

- n8n
- OpenAI
- Nano Banana
- Veo 3
- Telegram Bot
- Google Sheets

## Requirements

This workflow may require external APIs, credentials, accounts, or third-party services depending on your setup.

## Import Workflow

1. Download `workflow.json`
2. Open n8n
3. Click `Import from File`
4. Select the workflow file

## License

MIT License
