# Invoice Automation Workflow

Automated invoice generation, storage, email delivery, and status tracking workflow built with n8n.

This workflow automatically:

- receives invoice data through a webhook
- authenticates incoming requests using an API key
- stores invoice details in Google Sheets
- generates invoice PDFs using PDFbro
- uploads generated invoices to Google Drive
- sends invoice PDFs directly to customers by email
- updates the invoice record with the final processing status
- stores the generated PDF link and email timestamp
- returns the final result back to the application that triggered the workflow

## Features

- Webhook-based invoice processing
- API-key authentication
- Invoice data storage and tracking
- Automated PDF invoice generation
- Google Drive invoice storage
- Automated invoice email delivery
- Invoice status management
- PDF link tracking
- Email timestamp tracking
- Webhook response handling
- End-to-end invoice automation

## Workflow Architecture

Webhook → Google Sheets → PDFbro → Google Drive + Resend → Merge → Update Invoice → Webhook Response

## Tech Stack

- n8n
- Google Sheets
- PDFbro (n8n-nodes-pdfbro community node)
- Google Drive
- Resend
- Webhook

## Requirements

This workflow may require external APIs, credentials, accounts, or third-party services depending on your setup.

## Import Workflow

1. Download `workflow.json`
2. Open n8n
3. Click `Import from File`
4. Select the workflow file

## License

MIT License
