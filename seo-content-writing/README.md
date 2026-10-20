# AI SEO Blog Content Generation

Automated SEO blog content generation workflow built with n8n, Airtable, Gemini, and Perplexity. Designed to turn structured SEO inputs into researched blog articles by creating a content plan, researching the topic, writing the article section by section, and generating an accompanying image.

This workflow is part of a broader SEO content pipeline. It uses keyword and subtopic data alongside company information, audience details, and writing-style instructions to prepare content for review.

## What This Workflow Does

This workflow:

- retrieves article and subtopic inputs from the content system
- checks whether the article is ready for processing
- retrieves company, ICP, and writing-style information
- prepares the inputs for content generation
- creates a content plan using Gemini
- researches the topic using a research agent with access to Perplexity
- splits the plan into sections
- writes and updates the article section by section
- generates article imagery
- updates the article record and completion status
- removes temporary article data according to the configured workflow

Exact inputs and behavior depend on the connected Airtable base and n8n node configuration.

## Features

- Airtable-based article and content management
- SEO keyword and subtopic inputs
- Company and ideal customer profile (ICP) context
- Configurable writing style and content instructions
- AI-assisted content planning
- Topic research with Perplexity
- Section-by-section article writing
- Progressive article updates
- Blog image generation
- Article status tracking
- Temporary article data cleanup
- n8n workflow orchestration

## Workflow Architecture

`SEO Inputs → Prepare Article Data → Content Planning → Topic Research → Split Plan into Sections → Write Sections → Generate Image → Update Article → Mark Complete`

The workflow follows these main steps:

1. Retrieve the selected article and its related inputs.
2. Load company, audience, and writing-style context.
3. Generate the content plan and research the topic.
4. Split the plan into individual sections.
5. Write the article incrementally, updating the accumulated content.
6. Generate an image and update the article record.
7. Mark the article complete and clean up temporary data.

Exact node names and connections may vary by workflow version.

## Tools and Services

- **n8n:** Orchestrates the workflow, model calls, data processing, and Airtable updates.
- **Airtable:** Stores article inputs, company details, writing instructions, and article records.
- **Gemini 2.5 Pro:** Used for content planning in the observed configuration.
- **Gemini 2.5 Flash:** Used by the research agent in the observed configuration.
- **Perplexity:** Provides research capability to the research agent.
- **Image-generation tool:** Generates article imagery through the configured node.

## Content Inputs

Depending on the Airtable base and node mappings, the workflow can use:

- **SEO topic data:** Selected article, keyword, and subtopic.
- **Company information:** Brand details and relevant URLs.
- **ICP:** Intended audience and customer context.
- **Writing style:** Tone and formatting preferences.
- **Global instructions:** Requirements for the generated article.
- **Internal links:** Links requested for inclusion where relevant.
- **Image preferences:** Visual style and brand color.
- **Existing article content:** Content accumulated during section-by-section writing.

Field names and mappings should match the actual Airtable base and workflow configuration.

## How It Works

1. An article or subtopic is selected through the configured content system.
2. The workflow retrieves the relevant records and checks readiness.
3. Company, ICP, and writing-style details are prepared.
4. Gemini creates a structured content plan.
5. The research agent investigates the topic using Perplexity.
6. The plan is split into sections for the writing loop.
7. Each section is generated and added to the article content.
8. The article record is updated as writing progresses.
9. The image-generation step creates article imagery.
10. The workflow updates the article status and removes temporary data according to its configuration.

## Test Execution

One displayed test execution reported:

- **Total execution time:** 28 minutes, 1.649 seconds
- **Reported token usage:** 636,964 tokens
- **Image Generation node duration:** 55.767 seconds
- **Tokens reported for Image Generation node:** 34,610 tokens

These figures describe one execution and are not guaranteed benchmarks. Reported token usage is not necessarily the exact billable usage, and it should not be used to calculate cost without checking model-level usage and provider billing data.

## Requirements

Depending on your setup, you may need:

- an active n8n instance
- an Airtable account, base, and required tables and fields
- Airtable credentials configured in n8n
- Gemini API access and credentials
- Perplexity access configured for the research agent
- credentials for the configured image-generation service
- article and subtopic records in the expected format
- the required trigger or Airtable interface action
- correct record IDs, field mappings, and status values

## Import Workflow

1. Export or download the required n8n workflow JSON files.
2. Open your n8n instance.
3. Select **Import from File** and choose the workflow JSON.
4. Configure the Airtable, Gemini, Perplexity, and image-generation credentials.
5. Verify the Airtable base, tables, fields, and record mappings.
6. Review the prompts and model settings.
7. Test with a sample article record.
8. Check the generated content, image output, and Airtable updates.
9. Confirm that status updates and temporary-data cleanup work as expected.
10. Activate the workflow after testing is complete.

If the pipeline uses multiple connected workflows, import and configure all required workflows before testing the full process.

## Configuration Notes

- Verify that each stage uses the correct article ID.
- Ensure each section belongs to the article being updated.
- Check that generated sections are added without duplication.
- Review the research process and verify important factual claims before publishing.
- Confirm that the image-generation node receives the intended article title and content.
- Check how API errors and incomplete model responses affect the workflow status.
- Review the final article for relevance, repetition, formatting, and working links.
- Check provider usage and billing data before estimating cost per article.

## Use Cases

- SEO blog article generation
- Research-assisted writing
- Structured content planning
- Long-form article generation
- Brand-aware content workflows
- Airtable-based content management
- Blog image generation
- SEO content pipeline automation

## License

MIT License.
