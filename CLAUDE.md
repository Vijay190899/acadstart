# CLAUDE.md — working notes for AI-assisted development

Read README.md first: it is the product and architecture source of truth.

## Rules
- Build module by module (M0 → M6 in README §3). Keep each PR/commit to one milestone slice.
- Synthetic data only. Never commit real student, parent or staff data.
- Every table carries `institution_id`; enforce tenant isolation with PostgreSQL RLS.
- Fees: invoices may only use fee heads from the active, locked FEE_STRUCTURE. No parent-side app/convenience fees.
- Children's data: no ads, no profiling, no cross-school profiles; sharing only through guardian CONSENT_GRANT.
- Never use Aadhaar as an identifier. National/state IDs (UDISE+, EMIS, APAAR) are optional linked fields.
- UI strings go through i18n (ta, en) from day one.
- No facial recognition of children. Voice notes deleted after transcription; scanned register images deleted after confirmation + retention window.
- Mermaid diagrams in README must render: avoid reserved ids (e.g. Class, end) and validate before pushing.

## Status
- [ ] M0 Clickable demo
- [ ] M1 Foundation + Snap-to-Digitise
- [ ] M2 Daily core + Digital diary & permission slips
- [ ] M3 Fees & payments
- [ ] M4 Transport + Safe Handover + Custody Chain
- [ ] M5 Voice-first Tamil assistant + two-way translated messaging
- [ ] M6 Identity & records

## Decisions log
Record architecture decisions in docs/adr/NNNN-title.md.
