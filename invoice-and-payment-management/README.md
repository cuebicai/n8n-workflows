# Invoice & Payment Management Workflow

Complete invoice, payment, and refund management workflow built with n8n.

This workflow automatically:

- receives invoice, payment, and refund events through a webhook
- validates incoming requests and required fields
- routes each event to the appropriate flow
- checks for existing records to prevent duplicate processing
- stores invoice details in Google Sheets
- generates invoice PDFs using PDFbro
- uploads generated invoices to Google Drive
- sends invoice PDFs directly to customers by email
- records and tracks payment information
- updates invoice payment status and remaining balance
- sends payment receipts or final payment confirmations
- records and tracks refund information
- updates invoice refund information and remaining balance
- sends refund confirmation emails
- updates processing statuses
- returns the final result back to the application that triggered the workflow

## Features

- Webhook-based event processing
- Request validation
- Invoice creation and management
- Duplicate invoice protection
- Automated PDF invoice generation
- Google Drive invoice storage
- Automated invoice email delivery
- Payment processing and tracking
- Invoice balance management
- Payment receipt generation
- Full payment confirmation
- Refund processing and tracking
- Duplicate payment and refund protection
- Automated refund confirmation
- Invoice status management
- Webhook response handling
- End-to-end invoice, payment, and refund automation

## Workflow Architecture

Webhook → Validate Request → Route Event → Invoice / Payment / Refund Flow → Update Records → Email Notification → Webhook Response

## Tech Stack

- n8n
- Google Sheets
- PDFbro (`n8n-nodes-pdfbro` community node)
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
