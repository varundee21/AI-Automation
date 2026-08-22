# Day 2 — AI Email Summarizer

Built an n8n workflow that automatically summarizes incoming Gmail emails using Google Gemini and sends the generated summary back via Gmail.

**Workflow:**  
Gmail Trigger → Gemini LLM → Gmail Send

Prompt:
Summarize the following email in 2-3 concise sentences. Focus on the main point, important details, dates, times, and required actions.

Email:
{{$json.snippet}}
