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

  
## Database Schema

| Column | Type | Description |
|--------|------|-------------|
| name | TEXT | Submitter name |
| email | TEXT | Submitter email |
| message | TEXT | Raw message content |
| category | TEXT | AI-assigned: sales/support/spam/job |
| priority | TEXT | AI-assigned: high/medium/low |
| created_at | TIMESTAMP | ISO timestamp |

## The Timestamp Fix

Supabase requires ISO format. The raw webhook timestamp needed a JavaScript expression in n8n to convert it before the Create Row node.

## Screenshot

https://drive.google.com/file/d/1VD02llw7hllMYoKy0hQdPC7mbE5da_GY/view?usp=sharing

## How to Run

1. Self-host n8n
2. Get OpenAI API key
3. Create Supabase project and table with schema above
4. Import workflow JSON
5. Configure webhook URL in frontend
6. Set Gmail credentials for alerts
7. Submit form and watch the pipeline run
