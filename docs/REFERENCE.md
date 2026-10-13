# Veritas-ai source reference


Source reviewed: [`b7ca6b193d05`](https://github.com/noel-ult/Veritas-ai/commit/b7ca6b193d051ac2628ff16b68446fdc81ff9295).

This reference records the checked-in source, scripts, configuration names, and route declarations. It is a navigation aid; service availability and successful test execution require separate verification.

## Package commands

Run each command in the directory containing its package manifest. A declared script is not necessarily a passing check; guides call out placeholders and known mismatches.

### frontend/package.json

| Script | Shell command |
| --- | --- |
| `dev` | `next dev --port 3000` |
| `build` | `next build` |
| `start` | `next start` |
| `lint` | `next lint` |

Manifest: [frontend/package.json](../frontend/package.json).

## Configuration names

Names below are declared by source or example files. Example-only entries may be stale; consult the linked reader and project guide before relying on them. Secret values are intentionally omitted.

| Name | Declared/read in |
| --- | --- |
| `FRONTEND_ORIGIN` | [backend/.env.example](../backend/.env.example), [backend/config.py](../backend/config.py) |
| `GEMINI_API_KEY` | [backend/.env.example](../backend/.env.example), [backend/config.py](../backend/config.py) |
| `GROQ_API_KEY` | [backend/.env.example](../backend/.env.example), [backend/config.py](../backend/config.py) |
| `GROQ_MODEL` | [backend/.env.example](../backend/.env.example), [backend/config.py](../backend/config.py) |
| `LLM_PROVIDER` | [backend/.env.example](../backend/.env.example), [backend/config.py](../backend/config.py) |
| `NEXT_PUBLIC_API_URL` | [frontend/services/api.ts](../frontend/services/api.ts) |

## HTTP route declarations

Paths are **as declared in each source file**. Router/blueprint mount prefixes from the entry point must be prepended; the project guide describes the active entry point and common prefixes. Alternate entry points (such as SQLite) are listed separately by file. Authentication, request bodies, and response schemas live in the linked handlers/models.

| Source | Method | Declared path | Handler |
| --- | --- | --- | --- |
| [backend/routes/health.py](../backend/routes/health.py) | GET | `/` | `read_root` |
| [backend/routes/health.py](../backend/routes/health.py) | GET | `/health` | `health_check` |
| [backend/routes/interview.py](../backend/routes/interview.py) | POST | `/start` | `start_interview` |
| [backend/routes/interview.py](../backend/routes/interview.py) | POST | `/answer` | `process_answer` |
| [backend/routes/interview.py](../backend/routes/interview.py) | GET | `/{session_id}` | `get_interview_state` |
| [backend/routes/interview.py](../backend/routes/interview.py) | POST | `/end` | `end_interview` |
| [backend/routes/interview.py](../backend/routes/interview.py) | POST | `` | `spec_interview_turn` |
| [backend/routes/interview.py](../backend/routes/interview.py) | POST | `/` | `spec_interview_turn` |

## File-based pages and handlers

- [frontend/app/interview/page.tsx](../frontend/app/interview/page.tsx)
- [frontend/app/page.tsx](../frontend/app/page.tsx)
- [frontend/app/results/page.tsx](../frontend/app/results/page.tsx)
- [frontend/app/select/page.tsx](../frontend/app/select/page.tsx)

## Existing documentation

Historical plans/reports describe their own revision; use current source when they disagree.

- [AI_USAGE.md](../AI_USAGE.md)
- [README.md](../README.md)
- [backend/README.md](../backend/README.md)
- [backend/requirements.txt](../backend/requirements.txt)
- [technical-spec.md](../technical-spec.md)

## Source and configuration map

Generated lockfiles, binary assets, compiled output, vendored dependencies, and cached bytecode are omitted. Test files remain listed so coverage can be located.

- [Dockerfile](../Dockerfile)
- [backend/.env.example](../backend/.env.example)
- [backend/Dockerfile](../backend/Dockerfile)
- [backend/__init__.py](../backend/__init__.py)
- [backend/agents/__init__.py](../backend/agents/__init__.py)
- [backend/agents/evidence_engine.py](../backend/agents/evidence_engine.py)
- [backend/agents/interview_director.py](../backend/agents/interview_director.py)
- [backend/agents/question_bank.py](../backend/agents/question_bank.py)
- [backend/config.py](../backend/config.py)
- [backend/database/__init__.py](../backend/database/__init__.py)
- [backend/main.py](../backend/main.py)
- [backend/models/__init__.py](../backend/models/__init__.py)
- [backend/models/candidate.py](../backend/models/candidate.py)
- [backend/models/curriculum.py](../backend/models/curriculum.py)
- [backend/models/evidence.py](../backend/models/evidence.py)
- [backend/models/interview_requests.py](../backend/models/interview_requests.py)
- [backend/models/interview_response.py](../backend/models/interview_response.py)
- [backend/models/interview_state.py](../backend/models/interview_state.py)
- [backend/prompts/__init__.py](../backend/prompts/__init__.py)
- [backend/requirements.txt](../backend/requirements.txt)
- [backend/routes/__init__.py](../backend/routes/__init__.py)
- [backend/routes/health.py](../backend/routes/health.py)
- [backend/routes/interview.py](../backend/routes/interview.py)
- [backend/services/__init__.py](../backend/services/__init__.py)
- [backend/services/candidate_service.py](../backend/services/candidate_service.py)
- [backend/services/curriculum_service.py](../backend/services/curriculum_service.py)
- [backend/services/interview_service.py](../backend/services/interview_service.py)
- [backend/services/llm_provider.py](../backend/services/llm_provider.py)
- [backend/services/session_service.py](../backend/services/session_service.py)
- [backend/tests/test_answer_aware_followups.py](../backend/tests/test_answer_aware_followups.py)
- [backend/tests/test_api.py](../backend/tests/test_api.py)
- [backend/tests/test_evidence_engine.py](../backend/tests/test_evidence_engine.py)
- [backend/tests/test_gemini_evidence.py](../backend/tests/test_gemini_evidence.py)
- [backend/tests/test_groq_provider.py](../backend/tests/test_groq_provider.py)
- [backend/tests/test_interview_service.py](../backend/tests/test_interview_service.py)
- [backend/tests/test_llm_adapters.py](../backend/tests/test_llm_adapters.py)
- [backend/tests/test_question_bank.py](../backend/tests/test_question_bank.py)
- [backend/tests/test_relevance_handling.py](../backend/tests/test_relevance_handling.py)
- [backend/tests/test_spec_endpoint.py](../backend/tests/test_spec_endpoint.py)
- [backend/tests/test_two_agent_feedback.py](../backend/tests/test_two_agent_feedback.py)
- [backend/utils/__init__.py](../backend/utils/__init__.py)
- [backend/utils/relevance.py](../backend/utils/relevance.py)
- [candidates.json](../candidates.json)
- [curriculum.json](../curriculum.json)
- [frontend/Dockerfile](../frontend/Dockerfile)
- [frontend/app/globals.css](../frontend/app/globals.css)
- [frontend/app/interview/page.tsx](../frontend/app/interview/page.tsx)
- [frontend/app/layout.tsx](../frontend/app/layout.tsx)
- [frontend/app/page.tsx](../frontend/app/page.tsx)
- [frontend/app/results/page.tsx](../frontend/app/results/page.tsx)
- [frontend/app/select/page.tsx](../frontend/app/select/page.tsx)
- [frontend/components/AnswerInput.tsx](../frontend/components/AnswerInput.tsx)
- [frontend/components/ChatWindow.tsx](../frontend/components/ChatWindow.tsx)
- [frontend/components/EvidenceGraph.tsx](../frontend/components/EvidenceGraph.tsx)
- [frontend/components/GrowthMap.tsx](../frontend/components/GrowthMap.tsx)
- [frontend/components/HiringConfidence.tsx](../frontend/components/HiringConfidence.tsx)
- [frontend/components/InterviewDNA.tsx](../frontend/components/InterviewDNA.tsx)
- [frontend/components/MessageBubble.tsx](../frontend/components/MessageBubble.tsx)
- [frontend/components/Navbar.tsx](../frontend/components/Navbar.tsx)
- [frontend/components/ResultsCard.tsx](../frontend/components/ResultsCard.tsx)
- [frontend/components/VerifiedSkills.tsx](../frontend/components/VerifiedSkills.tsx)
- [frontend/components/ui/Box.tsx](../frontend/components/ui/Box.tsx)
- [frontend/components/ui/Counter.tsx](../frontend/components/ui/Counter.tsx)
- [frontend/components/ui/Cursor.tsx](../frontend/components/ui/Cursor.tsx)
- [frontend/components/ui/Magnetic.tsx](../frontend/components/ui/Magnetic.tsx)
- [frontend/components/ui/Marquee.tsx](../frontend/components/ui/Marquee.tsx)
- [frontend/components/ui/Reveal.tsx](../frontend/components/ui/Reveal.tsx)
- [frontend/components/ui/ScoreDial.tsx](../frontend/components/ui/ScoreDial.tsx)
- [frontend/hooks/useInterview.ts](../frontend/hooks/useInterview.ts)
- [frontend/hooks/useTypewriter.ts](../frontend/hooks/useTypewriter.ts)
- [frontend/lib/utils.ts](../frontend/lib/utils.ts)
- [frontend/next-env.d.ts](../frontend/next-env.d.ts)
- [frontend/next.config.mjs](../frontend/next.config.mjs)
- [frontend/package.json](../frontend/package.json)
- [frontend/postcss.config.mjs](../frontend/postcss.config.mjs)
- [frontend/services/api.ts](../frontend/services/api.ts)
- [frontend/tailwind.config.ts](../frontend/tailwind.config.ts)
- [frontend/tsconfig.json](../frontend/tsconfig.json)
- [frontend/types/interview.ts](../frontend/types/interview.ts)
