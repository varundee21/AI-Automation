Built an n8n workflow where Gemini analyzes a support ticket, returns structured JSON, and n8n uses the AI-generated priority to route the ticket to different actions.

Workflow:
Support Ticket
      ↓
    Gemini
      ↓
  JSON Output
      ↓
   Code Node
      ↓
      IF
   ↙       ↘
High      Normal
 ↓          ↓
Urgent     Normal
Email      Email

Prompt:
You are an AI support ticket router.
Analyze the following support ticket.

Return ONLY valid JSON with exactly these three fields:
{
  "category": "",
  "priority": "",
  "action": ""
}

Rules:
category must be one of:
Billing
Technical
Account
General

priority must be one of:
High
Medium
Low

action should be a short description of what the support team should do.

Support ticket:
{{ $json.ticket }}
