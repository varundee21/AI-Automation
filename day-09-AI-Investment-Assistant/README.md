An automated n8n workflow that monitors a custom list of US stocks, identifies significant price movements, retrieves relevant news, and uses Google Gemini to explain the likely reasons behind those movements.

The goal is to reduce the time spent manually checking stock prices and searching for news every day.

Workflow:
Stock List
    ↓
Split Tickers
    ↓
Twelve Data API
    ↓
Get Current & Previous Prices
    ↓
Calculate % Movement
    ↓
IF: |Movement| ≥ 2%
    ↓
Google News RSS
    ↓
Extract Latest Articles
    ↓
Combine News
    ↓
Google Gemini
    ↓
AI Analysis
    ↓
Gmail Daily Stock Summary

AI Prompt:
You are a stock market news analyst.

Analyze why this stock moved significantly today.

Stock: {{ $json.ticker }}
Price: {{ $json.price }}
Change: {{ $json.percent_change }}%

Latest news:
{{ JSON.stringify($json.articles) }}

Identify the most likely reason for the stock's movement.

Important:
- Use only information contained in the news articles.
- Do not invent facts.
- If the news does not clearly explain the movement, say that.
- Ignore irrelevant articles.
- Give ONE overall conclusion, not one conclusion per article.

Return ONLY valid JSON:

{
  "ticker": "{{ $json.ticker }}",
  "movement": "UP or DOWN",
  "reason": "Short explanation of why the stock likely moved",
  "impact": "HIGH, MEDIUM, or LOW",
  "confidence": "HIGH, MEDIUM, or LOW"
}
