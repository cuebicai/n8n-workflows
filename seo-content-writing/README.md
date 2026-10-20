# AI SEO Blog Content Generation Pipeline

An n8n-based workflow for turning structured SEO inputs into researched,
structured blog articles. The pipeline connects Airtable, Gemini, and
Perplexity to support content planning, topic research,
section-by-section writing, image generation, and article record
updates.

The workflow is designed to be part of a broader SEO content system. It
uses more than a target keyword: it can also use company information,
ideal customer profile (ICP) details, writing-style configuration,
global instructions, internal-linking requirements, and image
preferences.

## What It Does

The pipeline:

- retrieves article and subtopic inputs from the content system
- checks whether an article is ready to be processed
- retrieves company, audience, and writing-style context
- standardizes inputs for downstream workflow stages
- creates a content plan using Gemini
- researches the topic using a research agent with access to
  Perplexity
- splits the content plan into individual sections
- generates and updates article content iteratively
- generates article imagery
- updates the article record and completion status
- cleans up temporary article data after processing

The exact inputs, outputs, and behavior depend on the connected Airtable
base and the node configurations in the imported workflows.

## Features

- n8n-based workflow orchestration
- Airtable-based content and article management
- Structured SEO inputs and subtopics
- Company and brand context
- Ideal customer profile (ICP) inputs
- Configurable writing style and global content instructions
- AI-assisted content planning
- Topic research through a research agent and Perplexity
- Section-by-section article generation
- Progressive article content updates
- Image generation
- Article status tracking
- Article record updates and temporary-data cleanup
- Support for internal-linking requirements
- A workflow architecture that can be extended with editorial review
  and publishing steps

## Workflow Architecture

The pipeline is organized into three main stages.

```text
SEO Data and Article Inputs
        |
        v
SEO Research & Input Preparation
        |
        |-- Retrieve article/subtopic data
        |-- Check readiness and status
        |-- Get company and ICP inputs
        |-- Get writing-style inputs
        |-- Standardize inputs
        |
        v
Content Planning & Research
        |
        |-- Content Planner (Gemini 2.5 Pro)
        |-- Research Agent (Gemini 2.5 Flash + Perplexity tool)
        |-- Split plan into sections
        |-- Prepare section data
        |
        v
Section-by-Section Blog Writing
        |
        |-- Loop through sections
        |-- Retrieve latest article content
        |-- Generate/update the next section
        |-- Update article content
        |
        v
Image Generation & Finalization
        |
        |-- Generate article imagery
        |-- Mark article complete
        |-- Update blog record
        |-- Delete temporary article data
```

The pipeline separates input preparation, planning and research, and
writing/finalization so each stage has a defined responsibility.

## Workflow Stages

### 1. SEO Research & Input Preparation

The first stage prepares the information needed to generate the article.

Depending on the configuration, this stage can retrieve:

- the selected article or subtopic
- company information
- ideal customer profile (ICP) details
- writing-style settings
- global article instructions
- internal-linking requirements
- image-generation preferences

The workflow checks readiness and updates progress before preparing a
standardized input structure for the next stage.

The style configuration shown in the workflow includes company and blog
information, writing instructions, internal-link requirements, image
style, and a brand color. Example-article fields may also be configured;
whether they influence output depends on how they are mapped into the
prompts.

### 2. Content Planning & Research

The planning and research stage creates the structure and supporting
context for the article.

The observed workflow configuration uses:

- **Gemini 2.5 Pro** for content planning
- **Gemini 2.5 Flash** in the research agent
- **Perplexity** as a research tool available to the agent

The plan is split into individual sections for the writing stage.

Having a research agent does not, by itself, guarantee that every claim
in the finished article is verified. Research quality depends on the
agent's prompt, the queries it makes, the sources it retrieves, and
whether source evidence is preserved and checked during writing.

### 3. Section-by-Section Article Writing

Instead of asking a model to generate the entire article in a single
response, the workflow processes planned sections iteratively.

The observed flow includes:

- looping through section items
- retrieving the latest article content
- using an LLM chain to generate or update the next section
- passing updated content through the workflow
- updating the article record

This design can help manage long articles and lets the workflow build
the article progressively. It also requires careful handling of article
IDs, section data, and accumulated content to prevent duplicate, stale,
or unrelated content from being merged into the article.

### 4. Image Generation & Finalization

After the writing stage, the workflow runs image generation and
finalization steps.

The observed nodes include:

- **Image Generation**
- **Mark Article Complete**
- **Update Blog**
- **Delete Article Data**

The image-generation step uses the article content passed into the node.
Confirm that the title, article ID, and content supplied to this node
all belong to the same article before relying on the generated output.

The finalization steps update the article's status and record, then
clean up temporary data. The exact meaning of "complete" depends on the
status logic configured in Airtable and n8n; it should not be treated as
proof that the article has passed editorial or factual review.

## Data Used by the Pipeline

The workflow is designed to use structured inputs rather than a keyword
alone. Depending on the connected Airtable base and field mappings,
these inputs can include:

- **Company information:** company details and relevant URLs
- **SEO topic data:** keyword, subtopic, and article inputs
- **ICP inputs:** intended audience and customer context
- **Writing style:** tone, structure, and style preferences
- **Global instructions:** requirements and constraints for the
  article
- **Internal links:** requested links to include where relevant
- **Image preferences:** visual style and brand color
- **Existing article content:** content already generated during
  earlier iterations

The exact fields and their names should be checked against the actual
Airtable base and node configuration.

## AI Models and Services

---

Component Role

---

**n8n** Workflow orchestration, looping,
data transformation, and node
execution

**Airtable** Content inputs, article records,
configuration, and status tracking

**Gemini 2.5 Pro** Content planning in the observed
workflow

**Gemini 2.5 Flash** Research-agent model in the
observed workflow

**Perplexity** Research tool available to the
research agent

**Image-generation service/tool** Creates article imagery through the
configured image-generation node

---

The exact model calls, token accounting, image provider, and costs
depend on the current node settings and connected API accounts.

## Test Execution Metrics

One displayed test execution reported the following figures:

Metric Observed value

---

Total workflow execution time 28 minutes
Total reported token usage 636,964 tokens
Image Generation node duration 55.767 seconds
Tokens reported for the Image Generation node 34,610 tokens

These are observations from one execution, not guaranteed performance
benchmarks.

The reported token count should not be treated as the exact billable
usage or monetary cost without checking model-level usage and provider
billing data. The Image Generation node's reported tokens and duration
also should not automatically be interpreted as image-generation-only
cost or latency, since the node may include model and tool activity.

To calculate the cost per article accurately, inspect the usage and
billing data for each model/API call, including repeated calls and
image-generation requests.

## How It Works

At a high level, the workflow proceeds as follows:

1.  An article or subtopic is selected through the configured content
    system.
2.  The workflow retrieves the corresponding inputs and checks
    readiness.
3.  Company, ICP, writing-style, and other configuration inputs are
    retrieved.
4.  Inputs are standardized for the content-generation stages.
5.  The content planner creates an article plan.
6.  The research agent investigates the topic using its configured
    research tool.
7.  The plan is separated into individual sections.
8.  The writing workflow loops through the sections.
9.  The latest article content is retrieved and used when
    generating/updating the next section.
10. Updated article content is passed through the workflow and stored.
11. The image-generation node creates article imagery from the supplied
    input.
12. The workflow updates the article record and marks it complete.
13. Temporary article data is deleted according to the configured
    cleanup logic.

Node names, branching behavior, and the precise order of operations
should be verified against the exported workflow JSON.

## Airtable and Content Management

Airtable acts as the content-management layer for the broader pipeline.
It can be used to manage company information, competitor research,
writing-style configuration, keyword research, article inputs, article
review, and scheduling.

The workflow updates article records and status fields as it progresses.
Ensure that the configured record identifiers and field mappings
consistently point to the intended article throughout all stages.

## Requirements

Depending on the workflow configuration, you may need:

- an active n8n instance
- an Airtable account and configured base
- the required Airtable tables, fields, and permissions
- Airtable credentials configured in n8n
- Gemini API credentials and access to the configured models
- Perplexity credentials or access configured for the research tool
- credentials for the configured image-generation service/tool
- article and subtopic records in the expected format
- the required input trigger, webhook, or Airtable interface action
- correct node mappings for article IDs, section content, and status
  updates

Credentials, Airtable table names, field names, and API settings are not
provided by this README and must be configured for your environment.

## Import and Setup

1.  Export or obtain the relevant n8n workflow JSON files.
2.  Open your n8n instance.
3.  Select **Import from File** and import the workflow JSON.
4.  Configure the required Airtable, Gemini, Perplexity, and
    image-generation credentials.
5.  Verify the Airtable base, tables, fields, record IDs, and status
    values.
6.  Review the prompts and model settings for the content planner and
    research agent.
7.  Verify how research results and source information are passed to the
    writing stage.
8.  Confirm that the section loop retrieves and updates the correct
    article record.
9.  Check that the image-generation node receives content from the
    intended article.
10. Test the workflow with a non-production article record.
11. Inspect the generated article, image output, execution logs, and
    Airtable updates.
12. Verify that completion and cleanup steps behave as intended.
13. Activate the workflow after testing.

If the pipeline consists of multiple connected or sub-workflows, import
and configure all required workflows before running an end-to-end test.

## Configuration and Reliability Notes

- Verify that every stage uses the same intended article ID.
- Ensure the section being generated belongs to the article
  represented by the accumulated content.
- Check that the latest article content is appended or updated
  correctly and does not duplicate previous sections.
- Confirm that research sources and evidence are preserved if factual
  verification is required.
- Review internal links and ensure they are relevant and valid.
- Check the final article for unsupported claims, repetition,
  inconsistent headings, and broken formatting.
- Confirm that the image-generation input uses the correct article
  title and content.
- Verify that the article status reflects the actual workflow state.
- Test error handling for failed API calls, empty research results,
  and incomplete model responses.
- Check that cleanup does not remove data needed for debugging or
  review.
- Consider adding source verification, duplicate-content checks,
  editorial approval, and explicit publishing gates before automatic
  publication.
- Review model usage and provider billing data before estimating the
  cost per article.

## Limitations

- AI-generated research and content can contain errors and should be
  reviewed.
- Access to a research tool does not guarantee that every factual
  claim is supported by a reliable source.
- Token usage, execution time, and output length can vary by topic,
  model response, tool calls, and workflow configuration.
- The execution metrics in this README describe one observed test and
  are not performance guarantees.
- The exact Airtable schema and field names depend on the configured
  base.
- Successful workflow completion does not, by itself, establish that
  an article is accurate, original, SEO-effective, or ready to
  publish.

## Use Cases

- Automated SEO article generation
- Research-assisted blog writing
- Structured content planning
- Section-by-section long-form writing
- Brand-aware content generation
- Airtable-managed editorial workflows
- Image generation for blog articles
- Building an end-to-end SEO content pipeline
- Experimenting with AI content quality, execution time, and cost

## License

Add the license that applies to this workflow and its accompanying
assets before redistribution.
