# Pramana — Decisions & Open Questions

> 200-line limit — split into `ConvoQA-2.md` if exceeded.

## Decisions (locked)

### Name
**Pramana (प्रमाण)** — Sanskrit for proof, evidence, authority.
Locked 2026-06-26.

### Origin
Emerged from pravaaha technical QA. pravaaha processes require verified actors — the identity system cannot live inside pravaaha. It needs to be a standalone project that pravaaha and other tools integrate with.

### Core principle
Identity is verified once at onboarding. Every subsequent action is key-confirmed. pravaaha is an enabler of transparency, not an identity authority — Pramana is the authority layer.

### Relationship to pravaaha
- pravaaha process owners are Pramana identities
- Restricted process access is granted automatically at transaction initiation via Pramana
- Every `pravaaha publish` requires a Pramana key confirmation

### CLI model
Pramana has its own CLI (`pramana`) that works alongside `pravaaha`. Separate binary, separate concerns.

### Migration path
v0.1 pravaaha uses lightweight key signing (GPG/SSH). Pramana replaces this in v0.2 as the full identity layer.

## Open Questions

- [ ] What does onboarding look like for a non-technical user (e.g., a gram panchayat official)?
- [ ] Org identity vs person identity — how are they linked? (an official acts on behalf of an org)
- [ ] Active Directory integration — which version, which protocol (LDAP, SAML, OAuth)?
- [ ] Aadhaar integration — politically and technically sensitive, separate dedicated session required
- [ ] Key management for lost/compromised keys — recovery model?
- [ ] How does Pramana handle identity in private/confidential processes?
- [ ] Does Pramana eventually become a public identity registry, or always org-scoped?
- [ ] Privacy and data security — full dedicated session required before any design decisions
