# Pramana (प्रमाण)

*Sanskrit: प्रमाण — proof, authority, evidence.*

> Part of [Bharat Open Source](https://github.com/BharatOpenSource)

Identity and access management for [pravaaha](https://github.com/BharatOpenSource/pravaaha) — an Active Directory replacement built for the pravaaha ecosystem.

## What it is

Pramana manages users, roles, and signing keys within a pravaaha deployment. It is the internal IAM layer — not an external identity verifier.

**What it does:**
- Manages users and roles within a pravaaha deployment
- Manages signing keys for `pravaaha publish`, `pravaaha approve`, and other signed operations
- Enforces multi-sig signer lists (who must sign before a process version is sealed)
- Provides a pluggable interface for external identity providers

**What it does not do:**
- Pramana does not verify external identities — that is the adopting org's responsibility
- Pramana does not integrate with Aadhaar, DigiLocker, or any government ID system directly
- Pramana does not hold biometric or sensitive government ID data

If a government body wants to link Aadhaar e-KYC to their pravaaha deployment, that is their integration to build. Pramana provides the hook; the org wires their own identity source into it.

## Design principles

1. **Minimum data held** — keys belong to users, not to Pramana
2. **Pluggable IdP** — LDAP, SAML, OAuth, or any custom identity system can be wired in
3. **Transparency** — all access changes, key rotations, and role assignments are auditable
4. **Org sovereignty** — government and enterprise deployments make their own data decisions

## Relationship to pravaaha

pravaaha v0.1 uses lightweight GPG/SSH key signing. Pramana replaces this in v0.2 as a full IAM layer — users are Pramana identities, signing keys are Pramana-managed, multi-sig signer lists are Pramana role assignments.

## Current status

**Seed. Design not yet started.**

Requirements will crystallise once pravaaha v0.1 is used in practice and real identity pain points surface.

## Part of

[Bharat Open Source](https://github.com/BharatOpenSource) — infrastructure built by India, for India.
