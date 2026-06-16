# AI 3D Apparel Mockup Generator

AI-powered apparel mockup generation workflow built with n8n.

This workflow automatically:

- receives t-shirt design images from Telegram
- analyzes artwork using AI vision
- extracts typography, graphics, colors, and design characteristics
- generates specialized apparel mockup prompts
- creates premium 3D t-shirt mockups
- preserves artwork with high fidelity
- applies designs as realistic garment prints
- monitors generation progress automatically
- sends finished mockups back to Telegram

## Features

- AI artwork analysis
- AI apparel prompt generation
- 3D t-shirt mockup creation
- Artwork preservation
- Realistic garment rendering
- Telegram bot integration
- Automated workflow orchestration
- End-to-end mockup generation

## Workflow Architecture

Telegram → Artwork Analysis → AI Mockup Prompt Generation → 3D Mockup Generation → Status Monitoring → Telegram Delivery

## Tech Stack

- n8n
- OpenAI 4.1
- Nano Banana 2
- Telegram Bot
- ImgBB

## Requirements

This workflow may require external APIs, credentials, accounts, or third-party services depending on your setup.

## Import Workflow

1. Download `workflow.json`
2. Open n8n
3. Click `Import from File`
4. Select the workflow file

## License

MIT License
