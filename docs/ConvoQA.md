# Pramana — Decisions & Open Questions

> 200-line limit — split into `ConvoQA-2.md` if exceeded.

## Decisions (locked)

### Name
**Pramana (प्रमाण)** — Sanskrit for proof, evidence, authority.
Locked 2026-06-26.

### What Pramana is
An internal IAM (Identity and Access Management) system for pravaaha. An Active Directory replacement within the pravaaha ecosystem. It manages users, roles, and keys *inside* a pravaaha deployment.

**What it does NOT do:**
- Does not verify external identities — that is the adopting org's responsibility
- Does not integrate with Aadhaar, DigiLocker, or any government ID system directly — orgs wire that themselves
- Does not hold biometric or sensitive government ID data
- Does not determine whether "this person is a Tax Officer" — the org's own authority chain does that; Pramana manages the result

Locked 2026-06-26.

### External identity is the org's problem
Whether a government body wants to link their Aadhaar e-KYC, Active Directory, or custom HR system — that is their wiring. Pramana provides a pluggable IdP interface and accepts the result. It does not own the verification.

Locked 2026-06-26.

### Minimum data held
Keys belong to users, not to Pramana. Pramana stores the minimum required to operate. Transparency enforced wherever possible. If government deploys Pramana, their data decisions are theirs.

Locked 2026-06-26.

### CLI model
Pramana has its own CLI (`pramana`) that works alongside `pravaaha`. Separate binary, separate concerns.

### Migration path
v0.1 pravaaha uses lightweight GPG/SSH key signing. Pramana replaces this in v0.2 as the full IAM layer.

### Origin
Emerged from pravaaha technical QA. pravaaha processes require role-based actors and signing keys — that cannot live inside pravaaha. Pramana is the IAM layer that pravaaha integrates with.

## Open Questions

- [ ] What does the internal user/role/org data model look like?
- [ ] Key management for non-technical users — how does a gram panchayat official manage a signing key?
- [ ] Lost/compromised key recovery model
- [ ] How does Pramana handle identity in private/confidential processes?
- [ ] What does the pluggable IdP interface look like technically (LDAP, SAML, OAuth hooks)?
- [ ] Does Pramana eventually become org-scoped only, or can there be federation between orgs?
