# AI 3D Anatomy Visualization Generator

AI-powered 3D anatomy visualization workflow built with n8n.

This workflow automatically:

- receives an anatomy subject from Telegram
- validates that the input contains a single anatomical subject
- extracts the requested anatomy part
- combines the subject with a structured Master Prompt
- uses OpenAI GPT-4.1 to compile the final image prompt
- generates realistic 3D medical anatomy visualizations
- maintains consistent visual style across different anatomy subjects
- preserves anatomical accuracy and rendering specifications
- monitors image generation progress automatically
- sends finished anatomy visualizations back to Telegram

## Features

- AI anatomy subject validation
- Anatomy subject extraction
- Structured Master Prompt system
- AI image prompt compilation
- 3D medical visualization generation
- Consistent visual style across organs
- Anatomical accuracy constraints
- Lighting and composition control
- Automated generation status monitoring
- Telegram bot integration
- End-to-end image generation

## Workflow Architecture

Telegram → Subject Validation → Anatomy Extraction → Master Prompt → AI Prompt Compilation → 3D Anatomy Generation → Status Monitoring → Telegram Delivery

## Tech Stack

- n8n
- OpenAI GPT-4.1
- Nano Banana 2
- Telegram Bot

## Requirements

This workflow may require external APIs, credentials, accounts, or third-party services depending on your setup.

## Import Workflow

1. Download `workflow.json`
2. Open n8n
3. Click `Import from File`
4. Select the workflow file

## License

MIT License
