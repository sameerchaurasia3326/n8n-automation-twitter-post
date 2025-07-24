Automated Twitter (X) Content Poster with Telegram Approval
This repository contains an n8n workflow that automates a content pipeline: it fetches news from an RSS feed, processes it with AI, sends it for manual approval via Telegram, and then posts the approved content to a social media platform like Twitter (X).

Features
Scheduled Execution: Automatically runs every day at a set time (e.g., 9 AM).

Content Sourcing: Fetches the latest articles from any specified RSS feed.

AI-Powered Processing: Uses a Google Gemini model to process, summarize, or rephrase the content.

Human-in-the-Loop Approval: Implements a crucial manual review step. Posts are sent to a Telegram chat with an "Approve" button, giving you full control over what gets published.

Automated Posting: Once approved, the content is automatically published to your connected social media account.

How It Works
The workflow follows a clear, sequential process:

Trigger: A CRON node starts the workflow on a daily schedule.

Fetch Content: An HTTP Request node gets the latest posts from a cybersecurity news RSS feed.

Format Data: An XML to JSON node converts the feed data into a usable format.

Process with AI: The content is sent to a Google Gemini model via a Basic LLM Chain to be summarized or rewritten.

Send for Review: The AI-processed text is sent to a specific Telegram chat. The message includes an "Approve" button, and the workflow pauses to wait for a response.

Check Approval: An IF node checks the callback data from Telegram.

Upload Post: If the "Approve" button was clicked, the workflow proceeds down the "true" path, and the final Upload Post node publishes the content. If not, the workflow stops.

Setup Instructions
To use this workflow in your own n8n instance:

Import the Workflow: Import the .json file for this workflow into your n8n canvas.

Configure Credentials: You must create and configure credentials for the following services within your n8n instance:

Google Gemini: For the AI processing step.

Telegram: For your bot that will send the approval messages.

Upload Post: For the final node that posts to Twitter (X) or another platform.

Customize Nodes:

Get Cybersecurity News (RSS): Change the URL to your desired RSS feed.

Send Post for Review (Telegram): Update the Chat ID to your personal or group chat ID where you want to receive approval messages.

Basic LLM Chain: Modify the prompt to instruct the AI on how you want your content to be processed.
