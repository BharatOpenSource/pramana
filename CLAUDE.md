# Pramana — Claude Instructions

*Pramana (प्रमाण) — Sanskrit for proof, evidence, authority.*

> Read this before doing any work in this directory.
> Org context: see `../CLAUDE.md`.

## What this project is

An internal identity and access management (IAM) system for pravaaha — a replacement for Active Directory within the pravaaha ecosystem.

**What it does:**
- Manages users, roles, and organisations within a pravaaha deployment
- Manages signing keys for pravaaha operations (publish, approve, propose-change)
- Enforces multi-sig signer lists and role-based access
- Provides a pluggable interface for external identity providers (LDAP, SAML, OAuth, Aadhaar, etc.)

**What it does NOT do:**
- Pramana does not verify external identities — that is the adopting org's responsibility
- Pramana does not integrate with Aadhaar directly — orgs wire that themselves if needed
- Pramana does not hold biometric or sensitive government ID data
- Pramana is not responsible for verifying that "this person is a Tax Officer" — the org's own authority chain does that; Pramana manages the result

**The principle:** Minimize what Pramana holds. Keys belong to users, not to Pramana. Transparency enforced wherever possible.

## Relationship to pravaaha

pravaaha v0.1 uses lightweight GPG/SSH key signing. Pramana replaces this in v0.2 with a proper IAM layer:
- Users are Pramana identities
- Signing keys are Pramana-managed (generated, rotated, revoked through Pramana)
- Multi-sig signer lists for a process branch are Pramana role assignments
- External IdP integration (LDAP, SAML, OAuth) lets orgs plug in their existing identity systems
- Aadhaar or any other government ID integration is the org's layer, not Pramana's

## Integration surface

Pramana exposes hooks for external identity providers. An org can wire:
- Their existing Active Directory / LDAP
- SAML / OAuth (Google Workspace, Microsoft Entra, etc.)
- Government systems (Aadhaar e-KYC, DigiLocker) — at their own discretion
- Any custom identity system

Pramana accepts the verified identity result and manages it internally. It does not own the verification.

## Design principles

1. **Minimum data held** — keys belong to users; Pramana stores the minimum required to operate
2. **Pluggable IdP** — no assumption about how users are verified externally
3. **Transparency** — all access changes, key rotations, and role assignments are auditable
4. **Org sovereignty** — government and enterprise deployments make their own data decisions; Pramana enables, does not mandate
5. **CLI-first** — `pramana` CLI complements `pravaaha` CLI

## Current status

**Seed idea. Design not yet started.**

Requirements will crystallise once pravaaha v0.1 is used and real IAM pain points surface. Do not design this in a vacuum.

## Session start checklist

Before doing anything else each session:
1. Read `docs/ConvoQA.md` — past decisions and open questions
2. Read `docs/lessons.md` — mistakes and rules to avoid repeating
3. Read `docs/LatestTask.md` — what was being worked on last session

## Working conventions

- **200-line limit** on all markdown files in `docs/`
- **Feature branches:** `feature/<short-description>` — never commit to main directly

## Git

Repo: https://github.com/BharatOpenSource/pramana
Branch convention: `feature/<short-description>`
