Built an n8n workflow that accepts a resume PDF and job description, uses Gemini to compare them, generates a match score and identifies skill gaps, then sends the analysis by email.

Workflow:
n8n Form → Extract PDF → Gemini → Code → Gmail

Prompt:
You are an AI job-matching assistant.
Compare the candidate's resume against the job description.
Evaluate the candidate based ONLY on information explicitly present in the resume and job description.
Return the result as JSON with exactly these fields:
{
  "match_score": 0,
  "matching_skills": [],
  "partial_matches": [],
  "missing_skills": [],
  "recommendations": []
}

Scoring:
90-100 = Excellent match
75-89 = Strong match
60-74 = Moderate match
40-59 = Weak match
0-39 = Poor match

Do not invent skills or experience.
Do not give credit for a skill unless the resume provides evidence.

RESUME:
{{ $json.text }}

JOB DESCRIPTION:
{{ $('On form submission').item.json['Job Description'] }}
