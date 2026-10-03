# AI-Powered ICP Generator

AI-powered Ideal Customer Profile (ICP) research workflow built with n8n, Airtable, Gemini 2.5 Pro, and Perplexity. Designed to automate company research and generate structured customer profiles using AI.

This workflow:

- receives company research requests from an Airtable interface through a webhook
- retrieves company information from Airtable
- checks the company's research status
- marks the research as in progress
- sends company information to an AI research agent
- uses Gemini 2.5 Pro as the primary AI model
- connects Perplexity as a research tool for gathering additional company information
- uses memory to provide contextual information to the AI agent
- structures the generated research using an output parser
- generates a detailed Ideal Customer Profile (ICP)
- updates the corresponding Airtable record with the generated results

## Features

- Airtable-triggered company research
- Webhook-based workflow initiation
- Automated company information retrieval
- Research status tracking
- AI-powered ICP generation using Gemini 2.5 Pro
- Perplexity research tool integration
- AI agent with memory
- Structured output parsing
- Ideal Customer Profile generation
- Customer pain point identification
- Customer goals and objectives analysis
- Target industry and company size identification
- Decision-maker and buyer persona identification
- Existing solutions and alternatives research
- Automated Airtable record updates
- Airtable interface for managing company research
- n8n-based workflow orchestration

## Workflow Architecture

Airtable Interface → Webhook → Get Company → Check Research Status → Mark Research In Progress → ICP Research Agent → Update ICP Record

The ICP Research Agent is connected to:

- **Gemini 2.5 Pro:** Primary AI model for analyzing company information and generating ICP research.
- **Perplexity:** Research tool for gathering additional information about the company and its market.
- **Memory:** Provides contextual information to the AI agent.
- **Output Parser:** Structures the generated research into a predefined format for Airtable.

## Airtable Interface

The workflow is triggered and managed through an Airtable interface called **SEO Content Generation**.

The Company Information section includes:

- **Website URL:** Company's official website.
- **Company LinkedIn:** Company's LinkedIn profile.
- **Product Description:** Information about the company's products, services, features, and business model.
- **Generate Info:** Button to trigger the ICP research workflow.

The interface also displays the generated ICP research and provides additional sections for the broader SEO content generation process.

## ICP Research Output

The workflow generates structured company research covering the following areas:

- **Ideal Customer Profile:** Target industries, company sizes, geographical locations, organizational structures, and potential customer characteristics.
- **Decision Makers:** Relevant job titles, seniority levels, and buyer personas involved in purchasing decisions.
- **Pain Points:** Challenges and problems faced by potential customers.
- **Key Goals:** Business objectives, desired outcomes, and improvements customers want to achieve.
- **Currently Solving Problems:** Existing tools, platforms, alternatives, and manual processes customers use to address their challenges.

The generated research is saved to the corresponding Airtable company record for review and further use.

## How It Works

1. A user enters the company's website, LinkedIn profile, and product description in the Airtable interface.

2. The user clicks the **Generate Info** button to initiate the ICP research process.

3. The Airtable interface triggers the n8n workflow through a webhook.

4. The **Get Company** node retrieves the relevant company information from Airtable.

5. The **Check Research Status** node evaluates the company's research status and controls the workflow's execution path.

6. The **Mark Research In Progress** node updates the Airtable record to indicate that research has started.

7. The **ICP Research Agent** receives the company information and begins analyzing the business.

8. The agent uses **Gemini 2.5 Pro** as its primary AI model and **Perplexity** as a research tool to gather additional information.

9. The agent uses its connected memory and structured output parser to support contextual processing and organize the generated research.

10. The AI agent generates a structured Ideal Customer Profile, including target customers, decision-makers, pain points, goals, and existing solutions.

11. The **Update ICP Record** node saves the generated research to the corresponding Airtable company record.

12. The user can review the generated ICP directly in the Airtable interface and use it as a foundation for subsequent SEO and content generation workflows.

## SEO Content Generation Interface

The Airtable interface is part of a larger SEO content generation system.

It includes additional sections for:

- Company Information
- Competitor Research
- Blog Style Configuration
- Seed Keyword Generation
- Long-Tail Keyword Generation
- Keyword Overview
- SEO Article Generation
- Blog Article Review
- Article Scheduling

The generated ICP serves as foundational company and customer research for subsequent marketing and SEO workflows.

## Tech Stack

- **n8n:** Workflow automation and orchestration
- **Airtable:** Company database, research status management, and user interface
- **Airtable Webhook:** Workflow triggering
- **Google Gemini 2.5 Pro:** Primary AI model
- **Perplexity:** AI-powered company research tool
- **AI Agent:** Research analysis and ICP generation
- **Memory:** Contextual information for the AI agent
- **Structured Output Parser:** Structured ICP output
- **Airtable API:** Company data retrieval and generated research updates

## Requirements

Depending on your n8n setup, you may need:

- An active n8n instance
- An Airtable account and configured base
- An Airtable personal access token with the required permissions
- A configured Airtable interface with company information fields and a Generate Info button
- An Airtable webhook or automation configured to trigger the n8n webhook
- Google Gemini API credentials with access to Gemini 2.5 Pro
- Perplexity API credentials and a configured research tool
- The required n8n AI Agent, memory, and output parser nodes
- The appropriate Airtable field mappings for storing the generated ICP

## Import Workflow

1. Download `workflow.json`.
2. Open your n8n instance.
3. Select **Import from File**.
4. Choose the workflow JSON file.
5. Configure the Airtable, Gemini, and Perplexity credentials.
6. Verify the Airtable base, table, record fields, and node mappings.
7. Configure the webhook URL in your Airtable automation or interface trigger.
8. Test the workflow using a sample company record.
9. Verify that the generated ICP is correctly saved to Airtable.
10. Activate the workflow once testing is complete.

## Configuration Notes

- Configure the Airtable webhook to send the appropriate company record identifier or other required input to n8n.
- Ensure the **Get Company** node retrieves the correct Airtable record.
- Review the research status condition and confirm the intended behavior for records that are already being researched or have completed research.
- Configure the **Mark Research In Progress** node to update the correct status field.
- Review the AI Agent's system instructions to define the research methodology, ICP criteria, and expected output.
- Configure Gemini 2.5 Pro and verify that the model is accessible through your API credentials.
- Ensure the Perplexity tool is properly configured and available to the AI agent.
- Configure memory according to your desired contextual research strategy.
- Define and validate the structured output schema to match the Airtable fields.
- Verify that the **Update ICP Record** node writes the generated research to the correct company record.
- Test the complete workflow, including the Airtable interface trigger, research process, status updates, and final output.
- Review and validate AI-generated research before using it for business or marketing decisions.

## Use Cases

- Founder-led customer research
- Startup ICP development
- B2B customer profiling
- Buyer persona research
- Marketing strategy development
- SEO content planning
- Lead generation research
- Automated company analysis
- Agency client research and onboarding

## License

MIT License.
