# Inbox Agent — Kosovo 2026 Demo

A bilingual staff interface for the five Inbox Agent challenge cases, backed by the deterministic FastAPI service. It displays actual decisions, customer replies, tool-call evidence, escalation records, and sanitized audits. The order data is fictional and the prototype is offline; it is not a live shop system.

## Run on Windows

Open PowerShell in the `backend` folder and run:

```powershell
py -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m uvicorn app.main:app --reload --port 8000
```

Keep that terminal open and visit:

- `http://127.0.0.1:8000/` — staff interface
- `http://127.0.0.1:8000/docs` — interactive API documentation
- `http://127.0.0.1:8000/health` — server health

## Verify the backend

From a second PowerShell terminal opened in this project folder, run:

```powershell
.\backend\.venv\Scripts\python.exe .\verify_checkpoint6.py
.\backend\.venv\Scripts\python.exe .\verify_checkpoint7.py
```

The first script exercises the five challenge messages and API routes. The
second checks the reply wording for cases with and without a real escalation.

## Run on macOS or Linux

From `backend/`:

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
uvicorn app.main:app --reload --port 8000
```

## Interface

- Select one of the five official messages or enter another message.
- View the actual response, decision, extracted details, tool calls, and any escalation.
- Open the escalation list or look up a sanitized audit record by request ID.
- Switch interface labels between English and Albanian. Sample buttons retain the official challenge wording.

The frontend uses plain HTML, CSS, and JavaScript, with no build step or frontend package dependencies. FastAPI serves it from the same origin as the API.
