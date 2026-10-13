# Veritas AI development guide

An interview application with a Next.js frontend and a FastAPI backend. An Interview Director selects questions/follow-ups; an Evidence Engine evaluates answers and produces structured competency feedback.

## Local setup

Use Python 3.11 and Node.js 20 to match the root Dockerfile. From the root:

```sh
python3 -m venv .venv
.venv/bin/pip install -r backend/requirements.txt
cp backend/.env.example backend/.env
cd backend
../.venv/bin/uvicorn main:app --reload --port 8000
```

In another terminal:

```sh
cd frontend
npm ci
npm run dev
```

The frontend runs on port 3000. Its Next.js configuration proxies API requests to the backend; `frontend/services/api.ts` also supports a build-time `NEXT_PUBLIC_API_URL` override. `FRONTEND_ORIGIN` configures backend CORS.

## Providers and state

`LLM_PROVIDER` defaults to `groq`; `GROQ_API_KEY` and `GROQ_MODEL` configure that provider. Gemini is optional through `GEMINI_API_KEY` and provider selection. Missing/unusable provider responses fall back to deterministic logic. Provider failure is therefore not proof that an interview cannot run, nor that a returned result came from an external model.

`candidates.json` and `curriculum.json` provide seed content. Session state is held by `backend/services/session_service.py`; inspect its in-memory storage before configuring multiple workers or relying on persistence across restarts. API data models live in `backend/models/`; frontend response types are in `frontend/types/interview.ts`.

## Interview API

- `POST /api/interview/start`: JSON `candidateId` starts a session.
- `POST /api/interview/answer`: JSON `sessionId` and `answer` advances evaluation.
- `GET /api/interview/{session_id}`: retrieves current session state.
- `POST /api/interview/end`: JSON `sessionId` ends the session early.

Use a candidate ID from the checked-in seed file. Missing candidates/sessions return 404, completed-session conflicts 409, empty answers 422, and missing-current-question errors 400. FastAPI exposes its generated API schema locally.

## Tests and deployment

Backend tests are in `backend/tests/`. Install the test runner and HTTP client into the virtual environment with `python -m pip install pytest httpx` if absent, then run `python -m pytest` from `backend/`; inspect provider-specific tests before enabling live keys. Tests and source describe fallback and provider behavior separately. Frontend `npm run build` is the production build; the declared `next lint` script may need updating for the installed Next.js CLI and is not evidence of lint coverage.

The root Dockerfile builds both applications and `start.sh` launches them; separate Dockerfiles also exist. Verify frontend proxy destination, seed-file availability, and session persistence expectations in your chosen topology. Historical AI transcripts and specification files are supporting artifacts, not runtime configuration.

## More documentation

- [Source, command, and configuration reference](REFERENCE.md)
- [Contributing](../CONTRIBUTING.md)
