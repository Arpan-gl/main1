# Contract Analyzer API

A Flask-based API that analyzes legal contracts using Google Gemini AI and Legal-BERT for comprehensive contract analysis.

## Features

- PDF contract text extraction
- AI-powered contract analysis using Google Gemini
- Legal-BERT for enhanced legal term recognition
- Risk assessment and improvement suggestions
- RESTful API endpoint for contract analysis

## Local Development

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

2. Download spaCy model:
   ```bash
   python -m spacy download en_core_web_sm
   ```

3. Set up environment variables:
   ```bash
   cp .env.example .env
   # Edit .env and add your GEMINI_API_KEY
   ```

4. Run the application:
   ```bash
   python main.py
   ```

## API Usage

### Endpoint: POST /analyze

Upload a PDF contract for analysis.

**Request:**
- Method: POST
- Content-Type: multipart/form-data
- Body: PDF file

**Response:**
```json
{
  "analysis": [
    {
      "clause_type": "Arbitration",
      "original_text": "...",
      "simplified_summary": "...",
      "risk_level": "High",
      "suggested_rewording": "...",
      "improvement_advice": "...",
      "risk_factor_score": 3,
      "bert_insights": {
        "risk_level": "High",
        "important_terms": ["arbitration", "dispute"],
        "term_alternatives": {...}
      }
    }
  ],
  "extracted_text": "Full contract text..."
}
```

## Deployment on Render

1. Push your code to GitHub
2. Connect your GitHub repository to Render
3. Set the following environment variables in Render:
   - `GEMINI_API_KEY`: Your Google Gemini API key
4. Deploy using the provided render.yaml configuration

## Environment Variables

- `GEMINI_API_KEY`: Required. Your Google Gemini API key
- `FLASK_ENV`: Optional. Set to 'production' for production deployment
- `PORT`: Optional. Port number (default: 5000)
