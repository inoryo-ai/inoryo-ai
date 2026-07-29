# Ryo Ino

Solo developer at Centaurus, based in Chiba, Japan. I ship **production multi-tenant SaaS** and **deterministic, auditable knowledge-response engines**, and publish working code for both.

## What I work on

- **Production SaaS with paying customers** — a LINE-based restaurant loyalty platform (live, monthly subscription) and a subscription-affiliate platform (live, on a monthly maintenance contract).
- **Contract AI development** — structural screening from architectural drawings, and inquiry-response systems for client-owned knowledge. Requirements gathering through delivery and operation, all solo.
- **A deterministic knowledge-response engine (NOUS)** — Brain + Book architecture that returns traceable, source-attributed answers over versioned JSON knowledge bases, with zero runtime LLM dependency.

## Selected work

| Repository | Summary |
|---|---|
| [repitol-clean](https://github.com/inoryo-ai/repitol-clean) | LINE-based restaurant loyalty platform — stamp cards, coupons, auto-delivery. Next.js 16 + Supabase + LINE Messaging API. Sanitized public mirror of an in-production multi-tenant SaaS. |
| [nous-core](https://github.com/inoryo-ai/nous-core) | Deterministic, LLM-free knowledge-response engine. Traceable answers over versioned JSON knowledge bases. Zero runtime dependencies. Currently used in one production system. |
| [shift-tool-public](https://github.com/inoryo-ai/shift-tool-public) | Restaurant shift management — Excel↔JSON conversion + OR-Tools CP-SAT auto-generation with Streamlit UI. In use at 3 restaurants. |
| [centaurus-oss](https://github.com/inoryo-ai/centaurus-oss) | Cross-project Python utilities — pluggable external-service adapters, TTL response cache, FastAPI security helpers. |
| [logos](https://github.com/inoryo-ai/logos) | Multi-tenant business workflow platform — trace-first observability, fail-soft validation, annotation cache. Next.js 15 + Supabase RLS + Langfuse. **Design and implementation in progress.** |

## Not public

My largest contract projects are not on GitHub, as they are covered by NDA:

- **Seismic-diagnosis AI for an architecture firm** — structural detection from floor plans, scoring aligned with the Building Standards Act and MLIT notices, supervised by a licensed architect. Delivered as both a web version and a fully offline local version.
- **Inquiry-response system for an education company** — `nous-core` handles knowledge matching; a small LLM is used only to phrase the final answer. Answers below a confidence threshold are escalated to a human instead of guessed.

I am happy to walk through the design decisions and technology trade-offs in conversation.

## Exploratory

These are records of exploration, not confirmatory results.

- [cognitive-research-papers](https://github.com/inoryo-ai/cognitive-research-papers) — Notes on modeling cognitive function with LLMs, and on emotional parameters in memory-free agents. **Small samples (N=3–1,131), self-reported labels — exploratory, not confirmatory.**
- [cognitive-dictionary](https://github.com/inoryo-ai/cognitive-dictionary) — Bottom-up "dictionary" of cognitive operations derived from a 0/1 substrate, probed against ARC-AGI tasks.

## Stack

**Frontend** Next.js (App Router) / React / TypeScript / Tailwind
**Backend** Python (FastAPI) / Node.js / Supabase Postgres / pgvector
**AI / ML** Anthropic / OpenAI / NOUS (in-house) / YOLO / OR-Tools CP-SAT
**Infra** Vercel / Docker / GitHub Actions / Langfuse

## Contact

- Email — see GitHub profile
- Based in Chiba, Japan — open to fully remote engagements
