# AI SEO Content Generation Pipeline

An automated SEO content generation pipeline built with n8n, Airtable, YepAPI, Gemini, and Perplexity. Designed to connect company research, keyword discovery, subtopic generation, content planning, and blog writing into a structured content production process.

The pipeline is divided into separate workflows, with each workflow responsible for a specific stage. Research results and content records are stored and passed between stages, allowing the process to move from initial SEO research to a blog article ready for review.

## What This Pipeline Does

This pipeline:

- researches company information and generates an Ideal Customer Profile (ICP)
- collects keyword data and extracts seed keywords
- generates long-tail keyword opportunities
- creates related subtopic ideas from selected keywords
- collects and prepares blog research data
- develops a content strategy and article structure
- researches topics using AI research tools
- writes blog articles section by section
- generates accompanying blog images
- stores research results and article data in Airtable
- tracks processing status across individual workflows
- manages article updates and temporary data cleanup where configured

The exact inputs, outputs, and execution behavior depend on the connected Airtable base, workflow configuration, and API integrations.

## Features

- Modular n8n workflow architecture
- Company and Ideal Customer Profile (ICP) research
- Automated keyword research
- Seed keyword extraction
- Long-tail keyword discovery
- Subtopic idea generation
- Structured blog research
- AI-assisted content strategy
- Article outline and section generation
- Section-by-section blog writing
- AI-assisted topic research
- Blog image generation
- Airtable-based content management
- Processing status tracking
- Data transformation between workflow stages
- Temporary data cleanup where configured

## Workflow Architecture

`Company Research → Keyword Research → Long-tail Keywords → Subtopic Ideas → Blog Data Collection → Content Strategy → Blog Writing → Image Generation → Article Update`

The pipeline follows these main stages:

1. **ICP Generator:** Collects company information and uses AI research to develop an Ideal Customer Profile.
2. **Keyword Research:** Retrieves keyword data, extracts seed keywords, and stores the results for further processing.
3. **Long-tail Keyword Research:** Processes seed keywords and generates more specific keyword opportunities.
4. **Subtopic Ideas:** Generates related subtopics from selected long-tail keywords and stores the results.
5. **Blog Data Collection:** Retrieves relevant subtopic information and prepares the inputs required for content planning.
6. **Blog Content Strategy:** Uses AI research and content planning to develop an article structure and organize it into sections.
7. **Blog Writing:** Processes the planned sections, generates article content and images, and updates the corresponding blog records.

Each stage handles a specific responsibility, making the pipeline easier to maintain, test, and improve independently.

## Tools and Services

- **n8n:** Orchestrates the workflows, AI operations, data processing, and connections between stages.
- **Airtable:** Stores company information, ICP data, keywords, subtopics, research records, and blog content.
- **YepAPI:** Provides keyword research data for keyword discovery and expansion.
- **Gemini:** Supports AI-assisted research, content planning, and writing tasks, depending on the configured workflow.
- **Perplexity:** Provides research capabilities to the configured AI research workflow.
- **HTTP Request nodes:** Connect external APIs and retrieve data from supported services.
- **Data transformation nodes:** Process, split, merge, and structure data between workflow stages.
- **Image-generation service:** Generates accompanying blog imagery through the configured integration.

Model versions, API credentials, and individual node configurations may vary.

## Data Inputs

Depending on the workflow stage and Airtable configuration, the pipeline can use:

- **Company information:** Website URL, company details, and relevant business context.
- **ICP data:** Target audience and customer information.
- **Seed keywords:** Initial keywords used to discover further SEO opportunities.
- **Long-tail keywords:** More specific search terms used for subtopic discovery.
- **Subtopic records:** Topic ideas used to prepare article inputs.
- **Content instructions:** Article requirements, writing style, and relevant context.
- **Research data:** Information collected for article planning and writing.
- **Article records:** Existing article information and accumulated content.
- **Image instructions:** Visual requirements for the blog image generation stage.

Input field names, record relationships, and mappings must match the configured Airtable base and n8n workflows.

## How It Works

1. Company information is retrieved and processed to develop an ICP.
2. Keyword research collects relevant keyword data and extracts seed keywords.
3. The long-tail keyword workflow processes the seed keywords and stores keyword suggestions.
4. The subtopic workflow generates related topic ideas from selected keywords.
5. Blog data collection prepares the relevant information for article planning.
6. The content strategy workflow develops an article plan and splits it into sections.
7. The writing workflow generates article sections and updates the blog record as content progresses.
8. The image-generation stage creates accompanying article imagery.
9. The workflow updates article records and processing status according to its configuration.
10. Temporary data is cleaned up where configured.

The full pipeline depends on the required records and workflow connections being configured correctly. Individual stages may also be executed and tested independently.

## Requirements

Depending on the stages you want to run, you may need:

- an active n8n instance
- an Airtable account and configured base
- the required Airtable tables and fields
- YepAPI access and credentials
- Gemini API access and credentials
- Perplexity access configured for the research workflow
- credentials for the configured image-generation service
- the required workflow exports and connected workflows
- valid input records and expected field mappings
- the appropriate API permissions and usage limits

## Import Workflows

1. Export or download all required n8n workflow JSON files, including the image-generation sub-workflow.
2. Open your n8n instance.
3. Select **Import from File** and import each workflow JSON file.
4. Configure the required Airtable, YepAPI, Gemini, Perplexity, and image-generation credentials.
5. Verify the Airtable base, tables, fields, and record mappings.
6. Configure the image-generation sub-workflow and verify its connection to the main blog-writing workflow.
7. Check connections between all workflows and verify any required workflow IDs.
8. Review prompts, model settings, status conditions, and API configurations.
9. Test each workflow independently using sample records.
10. Verify that keywords, subtopics, article content, and generated images are stored correctly.
11. Test the complete pipeline to ensure all workflows execute as expected before enabling production execution.

Importing the workflows does not automatically configure external credentials, Airtable schemas, or connections between separate workflows.

## Configuration Notes

- Ensure each workflow uses the correct Airtable record IDs and field mappings.
- Verify that keyword and subtopic records are associated with the intended research inputs.
- Check status conditions before running downstream stages.
- Confirm that AI outputs are structured as expected by subsequent nodes.
- Review article section processing to prevent missing or duplicated content.
- Validate research results and factual claims before publishing.
- Check that generated images are associated with the correct article.
- Verify error handling for failed API requests and incomplete AI responses.
- Review temporary-data cleanup to ensure required article data is preserved.
- Monitor API usage, rate limits, and provider billing when running the pipeline at scale.

## Use Cases

- SEO keyword research automation
- Long-tail keyword discovery
- Content topic and subtopic research
- Ideal Customer Profile research
- SEO content strategy development
- Research-assisted blog writing
- AI-generated blog imagery
- Airtable-based content management
- Repeatable SEO content production
- Marketing workflow automation

## Limitations

- Generated keywords and subtopics require validation for relevance and search intent.
- AI-generated research and article content may contain inaccuracies and require review.
- API availability, rate limits, and model usage affect execution.
- Results depend on the quality of the input data and configuration.
- The pipeline does not guarantee search rankings, organic traffic, or business outcomes.
- Publishing and additional SEO quality checks depend on the configured workflow.

## License

MIT License.
