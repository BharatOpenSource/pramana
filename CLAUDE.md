# Pramana — Claude Instructions

*Pramana (प्रमाण) — Sanskrit for proof, evidence, authority.*

> Read this before doing any work in this directory.
> Org context: see `../CLAUDE.md`.

## What this project is

An identity management system designed for Indian civic and institutional context. Provides verified identity for people, organizations, and systems that participate in pravaaha processes.

**The problem:** pravaaha processes involve actors — applicants, officials, contractors, businesses. For processes to be accountable, the actors must be verifiable. A process step signed by "Tax Officer" means nothing. A step signed by a verified identity tied to a real person in a real role means everything.

**The idea:** A standalone identity system with its own CLI that integrates with pravaaha and other tools under BharatOpenSource. Identity is verified once at onboarding. Every subsequent action (publishing a process, signing a step, proposing a change) is confirmed via key. The system is robust, secure, scalable, and Indian-context-aware.

## Relationship to other projects

- **pravaaha** uses Pramana to verify process owners and actors
- **Sutra** (the language) may define identity schemas
- **Pramana CLI** complements `pravaaha` CLI — a separate binary, works alongside it
- Future: could integrate with Aadhaar or other Indian identity infrastructure (separate, sensitive discussion)

## Potential scope

- Key generation and management at onboarding (non-technical user friendly)
- Org identity (an NGO, a government department, a business)
- Role identity (Tax Officer at Income Tax Department, Delhi)
- Integration with Active Directory and equivalent systems
- Identity verification for real persons (sensitive — requires separate privacy/security session)
- Process initiation triggers automatic access grant for restricted processes

## Current status

**Seed idea. Not yet spec.**

Emerged from pravaaha technical QA (2026-06-26). Requirements will become concrete once pravaaha v0.1 is built and real identity pain points surface. Do not design this in a vacuum.

## Session start checklist

Before doing anything else each session:
1. Read `docs/ConvoQA.md` — past decisions and open questions
2. Read `docs/lessons.md` — mistakes and rules to avoid repeating
3. Read `docs/LatestTask.md` — what was being worked on last session

## Working conventions

- **200-line limit** on all markdown files in `docs/`
- **Feature branches:** `feature/<short-description>` — never commit to main directly

## Git

Repo: TBD (GitHub repo not yet created)
