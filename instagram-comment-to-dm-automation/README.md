# Instagram Comment to DM Automation

Automated Instagram comment-to-DM workflow built with n8n.

This workflow automatically:

- receives new Instagram comments

- checks the comment keyword against configured triggers

- identifies the Instagram post or reel using its Post/Reel ID

- looks up the matching DM configuration from Google Sheets

- retrieves the relevant message and link

- builds a personalized DM

- sends the DM directly to the commenter

- stops the workflow when no matching post or keyword is found

**## Features**

- Instagram comment monitoring

- Keyword-based comment triggers

- Post/Reel ID matching

- Google Sheets-based DM configuration

- Dynamic DM message generation

- Automatic link delivery

- Direct Instagram DM sending

- No workflow changes required for new triggers

- Centralized message and link management

- Conditional workflow execution

- End-to-end comment-to-DM automation

**## Workflow Architecture**

New Comment → Find DM → Build DM → Send DM

**## Google Sheets Structure**

The DM configuration is managed through Google Sheets using the following columns:

```text
Post/Reel ID | Post Details | Short Message | Link | Comment Keyword
```

Each row represents a different Instagram post or reel and its corresponding comment trigger.

For example:

```text
Post/Reel ID | Post Details | Short Message | Link | Comment Keyword
123456789    | Payment Guide | Here is the payment link | https://example.com/payment | PAYMENT
```

When someone comments **PAYMENT**, n8n uses the Post/Reel ID and comment keyword to find the matching configuration in the sheet.

**## How It Works**

1. A user comments on an Instagram post or reel.

2. n8n receives the new comment.

3. The workflow extracts the Post/Reel ID and comment keyword.

4. n8n searches the Google Sheet for a matching post and keyword.

5. If a matching row is found, the workflow retrieves the configured message and link.

6. n8n builds the DM using the retrieved information.

7. The DM is sent directly to the commenter.

8. If no matching post or keyword is found, the workflow stops without sending a message.

**## Tech Stack**

- n8n

- Instagram API

- Google Sheets

- Webhook

**## Requirements**

This workflow may require Instagram API credentials, a Meta developer application, Google Sheets credentials, and other external services depending on your setup.

**## Import Workflow**

1. Download `workflow.json`

2. Open n8n

3. Click `Import from File`

4. Select the workflow file

**## License**

MIT License
