...............................................................................................# TraceWise AI — Evidence-First Incident Investigator

TraceWise is a Streamlit app that analyzes software logs and returns an evidence-backed incident brief using retrieval plus Gemini generation.

## Features
- Paste logs or upload `.log`, `.txt`, `.json`, `.md`, and `.csv` files.
- Load a built-in sample incident.
- Retrieve relevant log fragments before calling Gemini.
- Generate a severity estimate, confidence rating, primary hypothesis, supporting excerpts, next checks, and alternative explanations.
- Inspect exact fragments selected by retrieval.
- Download the report as JSON.
- Keep API keys out of source code using Streamlit Secrets.

## Stack
- Python + Streamlit
- Google GenAI SDK (`google-genai`)
- Lightweight lexical retrieval (no external vector database required)

## Run locally
1. Use Python 3.10+.
2. Install dependencies: `pip install -r requirements.txt`
3. Run: `streamlit run app.py`
4. Enter your Gemini API key in the sidebar for a local session, or set `GEMINI_API_KEY` in the environment.

## Deploy with Streamlit Community Cloud
1. Push this project to GitHub.
2. Go to https://share.streamlit.io/ and create an app from your repository.
3. Choose `app.py` as the main file.
4. In app Settings → Secrets, add:
   ```toml
   GEMINI_API_KEY = "your-new-gemini-api-key"
   GEMINI_MODEL = "gemini-2.5-flash"
   ```
5. Deploy and test with the sample incident.

The selected model must be available to your Gemini API key. You can also choose another supported model in the sidebar.

## Security
- Never commit a real API key to GitHub or paste it into source code.
- Rotate/revoke any key that was shared in a chat if it was active.
- Redact tokens, passwords, personal data, and customer identifiers from logs before uploading.
- Do not upload sensitive production logs to third-party AI APIs without authorization.

## Limitations
- Retrieval is lexical, not embedding-based. It is suitable for a small demo, not a production observability platform.
- Severity and root-cause outputs are AI-generated hypotheses, not confirmed diagnoses.
- The app does not execute remediation actions.
