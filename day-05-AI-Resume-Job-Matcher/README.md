Built an n8n workflow that accepts a resume PDF and job description, uses Gemini to compare them, generates a match score and identifies skill gaps, then sends the analysis by email.

Workflow:
n8n Form → Extract PDF → Gemini → Code → Gmail
