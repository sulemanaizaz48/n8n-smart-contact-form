# n8n Smart Contact Form

AI-powered contact form that thinks before it stores. Not just an inbox dump.

## What It Does

- Frontend form captures name, email, message
- Webhook sends data to n8n
- OpenAI reads the message and assigns:
  - Category: sales, support, spam, job
  - Priority: high, medium, low
- Supabase PostgreSQL stores everything in a structured table
- If priority is high, Gmail fires an instant alert to admin
- Zero manual work from submission to notification

## Tech Stack

- n8n (self-hosted)
- OpenAI API (GPT for categorization and prioritization)
- Supabase (PostgreSQL database, free tier)
- Gmail (SMTP for high-priority alerts)
- Webhook trigger
