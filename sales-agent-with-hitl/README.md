# AI-Powered Sales Agent with Human-in-the-Loop (HITL)

AI-powered sales outreach workflow built with n8n, Airtable, Gmail, and Google Gemini 2.5 Pro. Designed to automate lead management, generate personalized sales emails using previous project experience, and introduce human approval before sending emails to prospects.

This workflow:

- collects project inquiries through an n8n form
- stores incoming leads in Airtable
- updates lead processing status
- uses an AI Sales Agent to generate personalized emails
- searches previous projects through an Airtable database tool
- uses Gemini 2.5 Pro for email generation
- structures email output using an Output Parser
- sends generated drafts through Gmail for human review
- routes approval and rejection decisions
- uses a separate Revision Agent to improve rejected emails
- sends approved emails to prospects
- updates Airtable records after successful delivery

## Features

- Automated lead collection and CRM management
- AI-powered personalized sales emails
- Previous project research and retrieval
- Gemini 2.5 Pro integration
- Structured JSON email generation
- Gmail-based Human-in-the-Loop approval
- Automated approval and rejection routing
- AI-powered email revision
- Repeated review and approval cycle
- Automated email delivery
- Airtable lead status management

## Workflow Architecture

Lead Form → Store Lead → Update Status: In Progress → Sales Agent → Draft Email → HITL - Wait for Response → Check Feedback

**Approved Path:**

Check Feedback → Send Email → Update Status: Done

**Declined Path:**

Check Feedback → Revision Agent → Draft Email → HITL - Wait for Response

The Sales Agent is connected to:

- **Gemini 2.5 Pro:** Primary AI model for generating personalized sales emails.
- **Project Database:** Airtable search tool for retrieving previous projects and client outcomes.
- **Output Parser:** Structures generated emails into JSON containing subject and email properties.

The Revision Agent is connected to:

- **Gemini 2.5 Pro:** Revises emails based on human feedback.
- **Output Parser1:** Structures revised email output.

## Lead Form

The n8n Form Trigger collects:

- **Name:** Prospect's full name.
- **Company Name:** Business or company name.
- **Email:** Prospect's email address.
- **Intent:** Requested AI solution or automation.
- **Budget:** Estimated project budget.
- **Project Description:** Project requirements and expectations.
- **Timeline:** Expected project completion timeline.

Submitted information is stored in Airtable for further processing.

## AI Sales Agent

The Sales Agent uses Gemini 2.5 Pro to understand lead requirements and generate personalized sales emails.

It connects to the Project Database tool to retrieve relevant previous projects and verified client outcomes.

The generated email includes:

- Personalized greeting.
- Understanding of project requirements.
- Relevant previous project experience.
- Proposed solution.
- Booking calendar link.
- Cuebic AI email signature.

The agent returns structured JSON containing:

- **subject:** Email subject line.
- **email:** Complete email body.

## Human-in-the-Loop (HITL)

The Gmail Send and Wait for Response node sends the generated email draft to a human reviewer.

The reviewer can approve or reject the email.

The Check Feedback node evaluates the response and routes the workflow accordingly.

**Approved:** The email proceeds to Gmail for delivery.

**Declined:** The email is sent to the Revision Agent for improvements.

## Revision Agent

The Revision Agent uses Gemini 2.5 Pro to revise rejected email drafts based on human feedback.

It receives the original email and review feedback, generates an improved version, and returns it to the email review process.

This creates a revision cycle until the email is approved.

## How It Works

1. A prospect submits project information through the Lead Form.
2. Store Lead creates a new Airtable record.
3. Update Status: In Progress marks the lead as being processed.
4. Sales Agent analyzes the prospect's requirements using Gemini 2.5 Pro.
5. Project Database retrieves relevant previous projects and client outcomes.
6. Sales Agent generates a personalized email using the Output Parser.
7. Draft Email prepares the generated email for review.
8. HITL - Wait for Response sends the draft through Gmail and waits for human feedback.
9. Check Feedback evaluates the approval decision.
10. Approved emails are sent to the prospect through Gmail.
11. Update Status: Done updates the Airtable lead record.
12. Rejected emails are passed to the Revision Agent.
13. Revision Agent improves the email using Gemini 2.5 Pro and the review feedback.
14. The revised email returns to the human approval process.

## Tech Stack

- **n8n:** Workflow automation and orchestration.
- **Airtable:** Lead management and project database.
- **Google Gemini 2.5 Pro:** AI model for email generation and revision.
- **AI Agent:** Sales email generation and revision.
- **Gmail:** Human approval and email delivery.
- **Output Parser:** Structured JSON email output.
- **Human-in-the-Loop:** Human review and approval mechanism.

## Requirements

- Active n8n instance.
- Airtable account and configured base.
- Airtable API credentials.
- Project Database containing previous project information.
- Google Gemini API credentials.
- Gmail credentials with required permissions.
- Configured booking calendar URL.
- Required AI Agent and Output Parser nodes.

## Import Workflow

1. Download `workflow.json`.
2. Open your n8n instance.
3. Select **Import from File**.
4. Import the workflow JSON.
5. Configure Airtable, Gemini, and Gmail credentials.
6. Verify database tables and field mappings.
7. Configure the booking calendar URL in the Sales Agent system prompt.
8. Review AI Agent instructions and output schemas.
9. Test both approval and rejection scenarios.
10. Activate the workflow.

## Configuration Notes

- **Booking Calendar Link:** Before activating the workflow, replace `[REPLACE WITH YOUR BOOKING CALENDAR LINK]` in the Sales Agent system prompt with your own appointment booking URL (Google Calendar, Calendly, Cal.com, etc.). This link will be included in AI-generated sales emails to allow prospects to schedule a discovery call.
- Verify Airtable record IDs and status mappings.
- Ensure the Project Database retrieves relevant project information.
- Configure both AI agents with the correct system instructions.
- Verify structured output schemas for both agents.
- Configure Gmail approval and rejection options.
- Ensure rejected emails return to the review process.
- Verify approved emails are delivered to the correct recipient.
- Test the complete workflow before activation.

## Use Cases

- AI-powered sales outreach.
- Automated lead management.
- Personalized email generation.
- AI agency client acquisition.
- Human-supervised email automation.
- Automated email revision and approval.
- B2B sales communication.

## License

MIT License.
