# AI 360° Ghost Mannequin Apparel Video Generator

AI-powered 360° apparel video generation workflow built with n8n.

This workflow automatically:

- receives front and back garment images from Telegram
- collects the selected body type for men's or women's fit
- uploads and stores garment reference images
- extracts image metadata automatically
- analyzes garment characteristics using AI vision
- identifies apparel type, colors, graphics, typography, construction, and proportions
- builds a structured garment master specification
- generates optimized AI video prompts
- reconstructs realistic intermediate garment views
- creates photorealistic 360° ghost mannequin apparel videos
- preserves front and back garment artwork with high fidelity
- monitors video generation progress automatically
- sends finished videos back to Telegram

## Features

- AI garment analysis
- Front and back reference image processing
- Structured master specification generation
- AI video prompt compilation
- 360° ghost mannequin video generation
- Garment structure preservation
- Artwork and typography preservation
- Realistic intermediate view reconstruction
- Men's and women's body type support
- Automated generation status monitoring
- Telegram bot integration
- End-to-end video generation

## Workflow Architecture

Telegram → Front & Back Garment Images → Image Metadata Extraction → AI Garment Analysis → Master Specification → AI Prompt Compiler → 360° Video Generation → Status Monitoring → Telegram Delivery

## Tech Stack

- n8n
- OpenAI GPT-4.1
- Seedance 2 mini
- Kie AI
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
