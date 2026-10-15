# SEO Subtopic Research

Automated SEO subtopic research workflow built with n8n, Airtable, and YepAPI. Designed to generate subtopic ideas from a selected long-tail keyword, organize the returned titles, and store the results in Airtable for further content planning.

This workflow is part of a broader SEO content pipeline. It helps bridge the gap between keyword research and article planning by turning a researched keyword into a set of potential subtopics to review.

## What This Workflow Does

This workflow:

- starts when the **Get Subtopics** action is triggered from the Airtable interface
- retrieves the corresponding keyword record from Airtable
- checks the current subtopic research status
- marks the research as in progress
- sends the selected long-tail keyword to YepAPI
- retrieves subtopic suggestions
- extracts subtopic titles from the response
- prepares and aggregates the generated subtopics
- stores the results in Airtable alongside the related keyword record
- updates the subtopic research status when processing is complete

## Features

- Airtable-based keyword selection
- Airtable interface trigger
- Automated subtopic generation
- YepAPI integration
- Subtopic title extraction and processing
- Aggregation of generated subtopics
- Airtable storage for generated results
- Subtopic research status tracking
- A selected-subtopic field for content planning
- n8n-based workflow orchestration

## Workflow Architecture

`Airtable Interface → Get Keyword Record → Check Subtopics Status → Mark In Progress → Generate Subtopics with YepAPI → Extract Titles → Prepare/Aggregate Results → Update Airtable → Mark Complete`

The workflow follows a simple research process:

1. Select a long-tail keyword in Airtable.
2. Trigger **Get Subtopics**.
3. Retrieve the matching keyword record and check its research status.
4. Send the keyword to YepAPI for subtopic suggestions.
5. Extract the returned subtopic titles and prepare the results.
6. Save the generated subtopics in Airtable.
7. Update the research status so the results can be reviewed.

Exact node names and connections may vary by workflow version.

## Tools and Services

- **n8n:** Orchestrates the workflow, API requests, response processing, and Airtable updates.
- **Airtable:** Stores researched keywords, generated subtopics, selected subtopics, and research status.
- **YepAPI:** Provides the subtopic suggestions requested by the workflow.

## Airtable Interface

The workflow is designed to work with an Airtable interface used to manage SEO research.

Relevant fields include:

- **Keyword:** The long-tail keyword used to generate subtopic ideas.
- **Get Subtopics:** The action used to start subtopic research for a selected keyword.
- **Selected Subtopic:** The subtopic chosen for further content planning.
- **Subtopics:** The generated subtopic results.
- **Subtopics Status:** Tracks the state of subtopic research.

Field names and status values should match the actual Airtable base and node configuration.

## How It Works

1. The user selects a keyword and triggers **Get Subtopics** from Airtable.
2. The workflow retrieves the corresponding Airtable record.
3. The workflow checks the current subtopic research status.
4. The record is marked as **In Progress** while the research runs.
5. The selected long-tail keyword is sent to YepAPI.
6. The workflow receives the generated subtopic suggestions.
7. The response is processed to extract the subtopic titles.
8. The generated results are prepared and aggregated into the expected format.
9. The results are saved to the relevant Airtable record.
10. The subtopic research status is updated to **Complete**.
11. The user can review the ideas in Airtable and select a subtopic for the next stage.

## Why Subtopic Research Matters

A long-tail keyword is a useful starting point, but it does not automatically provide a complete content plan. Subtopic research helps identify possible angles and supporting topics to consider before writing an article.

Automating the first pass can reduce repetitive brainstorming and keep research organized, especially when working through many keywords. The generated ideas should still be reviewed for relevance, search intent, overlap with existing content, and whether each idea deserves a separate article.

## What's Next?

This workflow is one stage of a larger SEO content pipeline:

**Competitor Research → Seed Keywords → Long-Tail Keywords → Subtopic Research → Content Planning → Article Generation**

The generated subtopics can be reviewed and selected in Airtable, then used as input for content planning and later article generation. The aim is to connect each stage while keeping the research structured and reviewable.

## Requirements

Depending on your n8n setup, you may need:

- An active n8n instance.
- An Airtable account and configured base.
- An Airtable personal access token with the required permissions.
- An Airtable table containing the keyword records and subtopic fields.
- An Airtable interface or other trigger that initiates the workflow.
- The required Airtable record identifier or input expected by the workflow.
- YepAPI API credentials and access to the endpoint used for subtopic research.
- Correct Airtable field mappings for storing the generated subtopics and updating status.

## Import Workflow

1. Export or download the workflow JSON file from the repository.
2. Open your n8n instance.
3. Select **Import from File**.
4. Choose the workflow JSON file.
5. Configure the Airtable and YepAPI credentials.
6. Verify the Airtable base, table, fields, and node mappings.
7. Configure the Airtable interface action or other trigger with the expected workflow input.
8. Test the workflow using a sample long-tail keyword.
9. Confirm that YepAPI returns subtopic suggestions.
10. Verify that the titles are extracted and saved to the correct Airtable record.
11. Confirm that the subtopic research status updates as expected.
12. Activate the workflow after testing is complete.

## Configuration Notes

- Ensure the trigger passes the correct Airtable record identifier or other required input.
- Verify that the workflow retrieves the intended keyword record.
- Review the status check to confirm how already completed or in-progress records are handled.
- Confirm that the keyword sent to YepAPI is the intended long-tail keyword.
- Configure YepAPI credentials and review the request parameters.
- Verify that the response-processing steps extract the correct title fields.
- Check that aggregation produces the structure expected by the Airtable update step.
- Ensure the generated subtopics are saved to the correct record and field.
- Confirm that the status is updated to the correct value after processing.
- Test with keywords that return different numbers of subtopic suggestions.
- Review how API errors or empty responses affect the status.
- Evaluate generated ideas before using them in a content plan; generated suggestions are not a guarantee of search demand or ranking potential.

## Use Cases

- SEO subtopic research
- Long-tail keyword expansion
- Blog content ideation
- SEO content planning
- Airtable-based research management
- Content pipeline automation
- Preparing topics for article generation
- Reducing repetitive manual brainstorming

## License

MIT License.
