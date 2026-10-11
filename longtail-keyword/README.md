# Long-Tail Keyword Research

Automated long-tail keyword research workflow built with n8n, Airtable, and YepAPI. Designed to discover related keywords, keyword ideas, and autocomplete suggestions from a seed keyword, retrieve available SEO keyword data, and store the results in Airtable for further SEO research and content planning.

This workflow:

- receives a seed keyword research request through a webhook
- retrieves the corresponding seed keyword record from Airtable
- checks the long-tail keyword research status
- marks the research as in progress
- prepares the seed keyword for keyword research
- retrieves related keywords through YepAPI
- retrieves keyword ideas through YepAPI
- retrieves autocomplete suggestions through YepAPI
- sends autocomplete-derived keywords to YepAPI for additional keyword data
- splits keyword responses into individual items
- prepares and standardizes keyword data from the different research paths
- stores the resulting keyword records in Airtable
- updates the original seed keyword record when the research process is complete

## Features

- Airtable-based seed keyword management
- Webhook-based workflow initiation
- Automated seed keyword record retrieval
- Long-tail keyword research status tracking
- Related keyword discovery
- Keyword idea generation
- Autocomplete suggestion discovery
- YepAPI integration
- Keyword data retrieval for autocomplete-derived keywords
- Search volume data where available
- Competition data where available
- Keyword difficulty data where available
- CPC data where available
- Automated keyword response processing
- Individual keyword record creation
- Airtable keyword storage
- Automated research status updates
- Airtable interface for managing keyword research
- n8n-based workflow orchestration

## Workflow Architecture

Webhook → Get Keyword Record → Check Longtail Status → Mark Longtail In Progress → Set Seed KW → [Related Keywords / Keyword Ideas / Autocomplete → Keyword Data] → Store Longtail Keywords → Update Longtail Keyword Status

The workflow uses three primary keyword discovery paths:

- **Related Keywords:** Retrieves related keyword suggestions from YepAPI.
- **Keyword Ideas:** Retrieves additional keyword ideas associated with the seed keyword.
- **Autocomplete:** Retrieves autocomplete suggestions and passes them through an additional keyword-data request.

The workflow uses:

- **n8n:** Workflow orchestration, API requests, response processing, and Airtable updates.
- **Airtable:** Seed keyword storage, research status tracking, long-tail keyword records, and the research interface.
- **YepAPI:** Keyword discovery and SEO keyword data retrieval.

## Airtable Interface

The workflow is part of a broader SEO content research system managed through Airtable.

The interface provides a workspace for managing seed keywords, reviewing discovered keywords, and initiating subsequent research stages.

The long-tail keyword research process uses the following information:

- **Company:** Associates keyword research with the relevant company.
- **Seed Keyword:** Stores the original keyword used to initiate research.
- **Longtail Status:** Tracks the current state of long-tail keyword research.
- **Keyword:** Stores the discovered keyword phrase.
- **Competition:** Stores the available keyword competition metric.
- **Volume:** Stores the available search volume estimate.
- **KW Difficulty:** Stores the available keyword difficulty metric.
- **CPC:** Stores the available cost-per-click estimate.

Additional Airtable fields support subtopic research:

- **Get Subtopics:** Action used to initiate the next stage of research.
- **Selected Subtopic:** Stores the selected subtopic.
- **Subtopics:** Stores subtopic research results.
- **Subtopics Status:** Tracks the status of subtopic research.

Field names and status values should match the actual Airtable base and node configurations.

## Keyword Research Sources

### Related Keywords

The workflow sends a request to YepAPI to retrieve keywords related to the seed keyword.

The response is processed using the following nodes:

`Get Related Keyword → Split Out → Set Related`

- **Get Related Keyword:** Requests related keyword data from YepAPI.
- **Split Out:** Separates the returned keyword collection into individual items.
- **Set Related:** Prepares the keyword fields for downstream processing and Airtable storage.

### Keyword Ideas

The workflow uses a separate YepAPI request to retrieve additional keyword ideas.

The response is processed using:

`Get Keyword Ideas → Split Out1 → Set Ideas`

- **Get Keyword Ideas:** Requests keyword ideas associated with the seed keyword.
- **Split Out1:** Separates the returned keyword collection into individual items.
- **Set Ideas:** Prepares the keyword data for downstream processing and Airtable storage.

### Autocomplete Suggestions

The workflow retrieves autocomplete suggestions to discover additional keyword variations.

The response is processed using:

`Get Auto Complete → Split Out2 → Aggregate`

- **Get Auto Complete:** Requests autocomplete suggestions through YepAPI.
- **Split Out2:** Separates the returned suggestions into individual items.
- **Aggregate:** Collects the processed suggestions into a structure for the subsequent keyword-data request.

### Keyword Data Retrieval

The aggregated autocomplete-derived keywords are sent through an additional YepAPI request.

The response is processed using:

`Get Keyword Data → Split Out3 → Set Keyword`

- **Get Keyword Data:** Requests keyword data for the supplied keywords.
- **Split Out3:** Separates the returned keyword data into individual items.
- **Set Keyword:** Prepares the keyword fields for Airtable storage.

The exact metrics returned depend on the YepAPI endpoint, request parameters, and availability of the underlying data.

## Long-Tail Keyword Research Output

The workflow stores the resulting keyword records in Airtable.

Available fields can include:

- **Company:** Company associated with the research.
- **Seed Keyword:** Original keyword used to discover keyword variations.
- **Keyword:** Discovered keyword phrase.
- **Competition:** Keyword competition metric.
- **Volume:** Estimated search volume.
- **KW Difficulty:** Keyword difficulty metric.
- **CPC:** Cost-per-click estimate.

The available metrics depend on the response and field mappings configured in the workflow.

Keywords from different research paths may overlap. The number of output items should not be interpreted as the number of unique keyword opportunities unless deduplication has been performed.

## How It Works

1. A seed keyword research request is submitted through the configured webhook.
2. The **Get Keyword Record** node retrieves the corresponding seed keyword record from Airtable.
3. The **Check Longtail Status** node checks the current research status and determines the appropriate processing path.
4. The **Mark Longtail In Progress** node updates the seed keyword record to indicate that research has started.
5. The **Set Seed KW** node prepares the seed keyword for the research requests.
6. The **Get Related Keyword** node requests related keywords from YepAPI.
7. The **Split Out** node separates the related keyword response into individual items.
8. The **Set Related** node prepares the related keyword data.
9. The **Get Keyword Ideas** node requests additional keyword ideas from YepAPI.
10. The **Split Out1** node separates the keyword ideas into individual items.
11. The **Set Ideas** node prepares the keyword idea data.
12. The **Get Auto Complete** node retrieves autocomplete suggestions from YepAPI.
13. The **Split Out2** node separates the autocomplete suggestions into individual items.
14. The **Aggregate** node collects the autocomplete results into the structure required by the next request.
15. The **Get Keyword Data** node requests keyword data for the autocomplete-derived keywords.
16. The **Split Out3** node separates the returned keyword data into individual items.
17. The **Set Keyword** node prepares the keyword data for storage.
18. The **Store Longtail Keywords** node creates the resulting keyword records in Airtable.
19. The **Update Longtail Keyword Status** node updates the original seed keyword record to reflect the research result.
20. The stored keywords become available for review and subsequent SEO research.

## Example Execution

In one displayed workflow execution, the research paths produced the following item counts:

- Related keywords: 7 items
- Keyword ideas: 6 items
- Autocomplete-derived keywords: 13 items

**Total: 26 output items.**

These counts describe the displayed execution and are not guaranteed for every seed keyword. They also do not establish that all returned keywords are unique.

## SEO Content Generation Interface

The long-tail keyword workflow is part of a broader SEO content generation system managed through Airtable.

The system includes sections for:

- Company Information
- Competitor Research
- Blog Style Configuration
- Seed Keyword Generation
- Long-Tail Keyword Generation
- Keyword Overview
- SEO Article Generation
- Blog Article Review
- Article Scheduling

The seed keyword research workflow establishes an initial keyword foundation. This workflow expands that foundation with related keywords, keyword ideas, and autocomplete-derived results.

The resulting keywords can then be used for further keyword analysis, subtopic discovery, and content planning.

## Tech Stack

- **n8n:** Workflow automation and orchestration.
- **Airtable:** Seed keyword management, keyword records, research status tracking, and user interface.
- **Airtable API:** Seed keyword retrieval, keyword record creation, and status updates.
- **Webhook:** Receives the research request and starts the workflow.
- **YepAPI:** Related keyword discovery, keyword idea retrieval, autocomplete suggestions, and keyword data retrieval.

## Requirements

Depending on your n8n setup, you may need:

- An active n8n instance.
- An Airtable account and configured base.
- An Airtable personal access token with the required permissions.
- The required Airtable tables and fields for seed keywords and long-tail keywords.
- A configured Airtable interface or other trigger that initiates the webhook.
- The correct Airtable record identifier or other required input in the webhook payload.
- YepAPI API credentials.
- Access to the YepAPI endpoints used for related keywords, keyword ideas, autocomplete, and keyword data.
- Correct Airtable field mappings for the generated keyword records.
- Appropriate status fields for tracking long-tail keyword research.

## Import Workflow

1. Download `workflow.json`.
2. Open your n8n instance.
3. Select **Import from File**.
4. Choose the workflow JSON file.
5. Configure the Airtable and YepAPI credentials.
6. Verify the Airtable base, tables, fields, and node mappings.
7. Configure the webhook URL in your Airtable automation or other trigger.
8. Test the workflow using a sample seed keyword.
9. Verify that the related keyword request returns the expected data.
10. Verify that the keyword ideas request returns the expected data.
11. Verify that autocomplete suggestions are retrieved and processed correctly.
12. Verify that the keyword-data request processes the autocomplete-derived keywords.
13. Confirm that the results are stored in the correct Airtable records.
14. Confirm that the original seed keyword's research status is updated correctly.
15. Activate the workflow once testing is complete.

## Configuration Notes

- Configure the webhook to receive the correct seed keyword record identifier or other required input.
- Ensure the **Get Keyword Record** node retrieves the intended Airtable record.
- Review the **Check Longtail Status** condition and confirm the intended behavior for records that are already being researched or have completed research.
- Configure the **Mark Longtail In Progress** node to update the correct status field.
- Ensure the **Set Seed KW** node maps the correct seed keyword into the request parameters.
- Configure the YepAPI credentials and verify access to all required endpoints.
- Review the request parameters in **Get Related Keyword**, **Get Keyword Ideas**, and **Get Auto Complete**.
- Verify that the **Aggregate** node produces the input structure expected by **Get Keyword Data**.
- Review the **Set Related**, **Set Ideas**, and **Set Keyword** field mappings.
- Ensure the **Store Longtail Keywords** node creates records in the correct Airtable table.
- Verify that the Company and Seed Keyword fields are associated with the correct parent research record.
- Review the **Update Longtail Keyword Status** node to ensure it updates the correct seed keyword record and status value.
- Test the workflow with keywords that return different numbers of results.
- Check how failed API requests and incomplete responses affect the research status.
- Consider adding normalization, deduplication, source tracking, and keyword intent clustering before treating the output as a final list of content opportunities.

## Use Cases

- Long-tail keyword research
- SEO keyword discovery
- Related keyword research
- Keyword idea generation
- Autocomplete-based keyword discovery
- Search volume and CPC data collection
- SEO content planning
- Seed keyword expansion
- Automated keyword research pipelines
- Airtable-based SEO research management
- Startup SEO workflows
- Automated content research systems

## License

MIT License.
