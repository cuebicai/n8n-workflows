# Competitor Seed Keyword Research

Automated competitor seed keyword research workflow built with n8n, Airtable, and YepAPI. Designed to retrieve ranking keyword data from a competitor's domain, extract an initial set of seed keywords, and store them in Airtable for further SEO keyword research.

This workflow:

- receives a competitor keyword research request from an Airtable interface through a webhook
- retrieves the corresponding competitor information from Airtable
- checks the competitor's seed keyword research status
- marks the research as in progress
- prepares the competitor URL for keyword research
- sends the competitor URL to YepAPI's domain keyword research API
- retrieves keyword data for the competitor's domain
- extracts the first 10 seed keywords from the returned results
- splits the seed keywords into individual items
- stores each seed keyword in Airtable
- updates the corresponding competitor record when seed keyword research is complete

## Features

- Airtable-triggered competitor keyword research
- Webhook-based workflow initiation
- Automated competitor information retrieval
- Seed keyword research status tracking
- Competitor domain keyword research
- YepAPI integration
- Competitor ranking keyword discovery
- Keyword position data
- Search volume data
- CPC data
- Ranking landing URL data
- Extraction of 10 initial seed keywords
- Individual seed keyword records
- Automated Airtable record creation
- Automated research status updates
- Airtable interface for managing keyword research
- n8n-based workflow orchestration

## Workflow Architecture

Airtable Interface → Webhook → Get Competitor → Check Seed Keyword Status → Mark Seed Keyword In Progress → Set URL → Get Keywords → Extract Seed Keywords → Store Seed Keywords → Update Seed Keyword Status

The keyword research workflow uses:

- **YepAPI:** SEO data provider used to retrieve keyword data for the competitor's domain.
- **Airtable:** Stores competitor information, research status, and individual seed keyword records.
- **n8n:** Handles the workflow orchestration, API request, keyword extraction, and Airtable updates.

## Airtable Interface

The workflow is triggered and managed through an Airtable interface used for the broader SEO content generation system.

The competitor research section provides the information required for seed keyword research, including:

- **Competitor URL:** Competitor website/domain used for keyword research.
- **Seed Keyword Status:** Tracks the current state of seed keyword research.
- **Generate Seed Keywords:** Button used to trigger the seed keyword research workflow.

The generated seed keywords are stored individually in Airtable and can be used as the foundation for subsequent long-tail keyword research.

## Seed Keyword Research Output

The workflow retrieves keyword data associated with the competitor's domain through YepAPI.

The returned keyword data can include:

- **Keyword:** Search query the competitor is ranking for.
- **Ranking Position:** The competitor's ranking position for the keyword.
- **Search Volume:** Estimated search volume for the keyword.
- **CPC:** Cost-per-click information associated with the keyword.
- **Landing URL:** Page on the competitor's website ranking for the keyword.

The workflow extracts the initial 10 seed keywords from the returned results and stores each keyword as an individual Airtable record.

These seed keywords provide the starting point for deeper long-tail keyword research.

## How It Works

1. A user provides the competitor information through the Airtable interface.

2. The user triggers the **Generate Seed Keywords** action.

3. The Airtable interface triggers the n8n workflow through a webhook.

4. The **Get Competitor** node retrieves the relevant competitor information from Airtable.

5. The **Check Seed Keyword Status** node checks whether seed keyword research has already been completed or is currently in progress.

6. The **Mark Seed Keyword In Progress** node updates the competitor record to indicate that keyword research has started.

7. The **Set URL** node prepares the competitor URL that will be used for the keyword research request.

8. The **Get Keywords** node sends the competitor URL to YepAPI and retrieves keyword data for the domain.

9. The workflow receives the competitor's ranking keyword data, including keyword and associated SEO metrics.

10. The **Extract Seed Keywords** node selects the initial 10 seed keywords from the returned keyword results.

11. The **Split Into Keywords** node converts the selected keywords into individual items.

12. The **Store Seed Keywords** node stores each seed keyword as an individual Airtable record.

13. The **Update Seed Keyword Status** node updates the competitor record to indicate that seed keyword research has been completed.

14. The stored seed keywords are then available for the next stage of the SEO keyword research process.

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

The seed keywords generated by this workflow provide the initial keyword foundation for the subsequent long-tail keyword research process.

## Tech Stack

- **n8n:** Workflow automation and orchestration
- **Airtable:** Competitor database, research status management, seed keyword storage, and user interface
- **Airtable Webhook:** Workflow triggering
- **YepAPI:** Competitor domain keyword research and SEO data
- **Airtable API:** Competitor data retrieval, seed keyword storage, and status updates

## Requirements

Depending on your n8n setup, you may need:

- An active n8n instance
- An Airtable account and configured base
- An Airtable personal access token with the required permissions
- A configured Airtable interface with competitor information and seed keyword fields
- An Airtable webhook or automation configured to trigger the n8n webhook
- YepAPI API credentials
- Access to the YepAPI domain keyword research endpoint
- The required Airtable tables and fields for competitors and seed keywords
- The appropriate Airtable field mappings for storing the generated seed keywords

## Import Workflow

1. Download `workflow.json`.
2. Open your n8n instance.
3. Select **Import from File**.
4. Choose the workflow JSON file.
5. Configure the Airtable and YepAPI credentials.
6. Verify the Airtable base, tables, records, fields, and node mappings.
7. Configure the webhook URL in your Airtable automation or interface trigger.
8. Test the workflow using a sample competitor record.
9. Verify that the competitor's keyword data is retrieved successfully.
10. Verify that 10 seed keywords are extracted and stored as individual Airtable records.
11. Verify that the seed keyword research status is updated correctly.
12. Activate the workflow once testing is complete.

## Configuration Notes

- Configure the Airtable webhook to send the appropriate competitor record identifier or other required input to n8n.
- Ensure the **Get Competitor** node retrieves the correct Airtable competitor record.
- Review the **Check Seed Keyword Status** condition and confirm the intended behavior for records that are already being researched or have completed research.
- Configure the **Mark Seed Keyword In Progress** node to update the correct status field.
- Configure the **Set URL** node with the correct competitor URL field.
- Configure the YepAPI credentials and verify access to the domain keyword research endpoint.
- Review the YepAPI request parameters and ensure the competitor URL/domain is passed correctly.
- Review the **Extract Seed Keywords** node to confirm that the intended 10 keyword results are selected.
- Ensure the **Split Into Keywords** node correctly separates the extracted keywords into individual items.
- Verify that the **Store Seed Keywords** node maps each keyword to the correct Airtable fields.
- Verify that the **Update Seed Keyword Status** node updates the correct competitor record.
- Test the complete workflow from the Airtable interface trigger through keyword retrieval, extraction, storage, and status updates.

## Use Cases

- Competitor keyword research
- SEO content planning
- Seed keyword discovery
- Competitor SEO analysis
- Long-tail keyword research preparation
- Automated SEO research
- Founder-led SEO research
- Startup SEO workflows
- Content strategy development
- Automated content research pipelines

## License

MIT License.
