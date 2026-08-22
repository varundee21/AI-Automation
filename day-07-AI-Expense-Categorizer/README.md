Built an n8n workflow that reads multiple expenses from Google Sheets, uses Gemini to automatically categorize each expense, and writes the category back to the correct row.

Workflow:
Google Sheets → Gemini → Google Sheets

Prompt:
You are an expense categorization assistant.
Categorize the expense into exactly ONE of these categories:
Food
Transportation
Shopping
Entertainment
Travel
Utilities
Healthcare
Other

Expense:
{{ $json.Description }}
Amount:
{{ $json.Amount }}

Return ONLY the category name.
Do not provide an explanation.
