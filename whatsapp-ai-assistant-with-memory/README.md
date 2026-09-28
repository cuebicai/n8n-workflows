# WhatsApp AI Memory Assistant

AI-powered WhatsApp assistant built with n8n, designed to respond to
incoming messages while maintaining conversation context and saving
useful information to memory.

This workflow:

- receives incoming WhatsApp messages
- splits and processes the incoming message
- routes message content through message-type handling rules
- prepares chat memory and the user's message for the assistant
- sends the prepared context to an AI assistant powered by GPT-4.1
- gives the assistant access to a memory tool for saving relevant
  information
- sends the assistant's response back to the user on WhatsApp

## Features

- WhatsApp message handling
- Text and audio message-type routing
- Message splitting and preparation
- Conversation memory context
- AI-powered responses using GPT-4.1
- Assistant-accessible memory-saving tool
- Context-aware message processing
- Automated WhatsApp replies
- n8n-based workflow orchestration

## Workflow Architecture

User Message → Split Message → Message Types → Chat Memory → Prepare
Chat Memory → User's Message → AI Assistant → Send message

The AI Assistant is connected to the GPT-4.1 chat model and has access
to the Save Message tool.

## Memory

The workflow includes a Chat Memory stage to prepare conversation
context for the assistant. It also connects a Save Message tool to the
AI Assistant, allowing the assistant to store information it considers
useful for future interactions.

The memory-saving behavior depends on the instructions configured in the
AI Assistant and the implementation of the Save Message tool. Review
those node settings to define what should be saved and how it should be
retrieved.

## How It Works

1.  A user sends a message to the WhatsApp number connected to the
    workflow.
2.  The User Message trigger receives the incoming message.
3.  Split Message separates the message content for processing.
4.  Message Types applies rules to route or handle the message according
    to its type, including audio and text paths.
5.  Chat Memory and Prepare Chat Memory prepare the conversation
    context.
6.  User's Message prepares the current message for the AI Assistant.
7.  The AI Assistant processes the message using GPT-4.1 and the
    available memory context.
8.  When appropriate, the assistant can use the Save Message tool to
    store relevant information.
9.  Send message delivers the assistant's response to the user on
    WhatsApp.

## Tech Stack

- n8n
- WhatsApp integration
- OpenAI GPT-4.1
- n8n Chat Memory
- AI tool connection for saving memory

## Requirements

Depending on your n8n setup, you may need:

- An active n8n instance
- WhatsApp credentials and a configured WhatsApp messaging integration
- OpenAI credentials with access to GPT-4.1
- The required memory and tool nodes configured
- Any credentials or external services required by your specific Save
  Message implementation

## Import Workflow

1.  Download `workflow.json`.
2.  Open n8n.
3.  Select **Import from File**.
4.  Choose the workflow JSON file.
5.  Configure the credentials and node settings for your environment.
6.  Test the workflow with a WhatsApp message before activating it.

## Configuration Notes

- Confirm the WhatsApp trigger and sending nodes are connected to the
  correct account or phone number.
- Review the Message Types rules and confirm the audio and text paths
  match your intended behavior.
- Configure the Chat Memory and Prepare Chat Memory nodes to match
  your desired conversation-context strategy.
- Review the AI Assistant instructions to define response behavior and
  memory-saving criteria.
- Verify that the Save Message tool stores only the information you
  intend to retain.
- Test the complete workflow before publishing or activating it.

## License

MIT License
