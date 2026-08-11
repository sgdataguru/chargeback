You are helping me draft a rough build cost estimate for Sentinel, the wrist-worn security wearable platform I am joining as Technical Director on retainer. The estimate goes to my two co-founders Dexter and Siva. They are commercial operators from the security-agency world, not technical, but they read numbers well. This is an internal working document, not a fundraising deck. Deliver it as a single .md file.

Apply my bertie-voice skill throughout: so-what first, causality over chronology, British business English, short declarative sentences, no American ChatGPT register. Numbers first, commentary second.

## Source material to align with

Before writing, read and align with the existing Sentinel documentation in [docs](../../docs). Do not restate it; use it to keep scope, terminology and risk framing consistent, and to make sure every cost line traces back to something we have actually decided to build:

- [docs/project-context/overview.md](../../docs/project-context/overview.md) — venture definition, MVP boundaries, buyers, commercial model, hardware constraints
- [docs/project-context/data-platform-strategy.md](../../docs/project-context/data-platform-strategy.md) — the business requirements (REQ-001 to REQ-006) the build must cover, and the architectural bets. Software build scope in Section 1 should map to these requirements, not to a generic app build.
- [docs/project-context/value-delivery-roadmap.md](../../docs/project-context/value-delivery-roadmap.md) — the four-phase delivery plan. The 3–4 month build period in the estimate is Phases 0–3; the recurring cost model starts when the Phase 3 pilot gate passes.
- [docs/project-context/risk-constraint-register.md](../../docs/project-context/risk-constraint-register.md) — risks, assumptions and constraints. Where a cost line hedges a risk or depends on an unvalidated assumption, cite the register ID (e.g. R-003, A-010, C-005).
- [docs/architecture/overview.md](../../docs/architecture/overview.md) — what the platform actually consists of (API, event store, control-room services, AI Search + Azure OpenAI RAG, device-management adapter, Key Vault). Cloud and inference cost lines should reflect this component list.
- [docs/admin/security-and-privacy.md](../../docs/admin/security-and-privacy.md) — the required pre-production reviews (DPIA, threat model, penetration test, supply-chain review, OTA security review). These are real one-off costs that belong in Section 1, and their absence from a naive estimate is exactly the kind of thing that sinks a 3–4 month plan (R-019).

Key facts from the docs that must shape the estimate:

- The build is not three apps. It is a managed device fleet (REQ-005: provisioning, SIM association, OTA, deactivation, verified-wipe recycling), a secure event-driven platform (REQ-001, REQ-004), and a guardrailed RAG assistant with human-approved report drafting (REQ-003). Cost the software accordingly.
- Security and privacy reviews are gated deliverables, not optional extras (REQ-004). Budget the DPIA, penetration test and supplier security review as named one-off lines.
- Retention positions are provisional: audio 30 days, transcripts and reports two years, pending legal confirmation (A-010). Storage cost lines depend on this surviving counsel's review.
- The five emergency scenarios are fixed (A-004); the AI scope is constrained by design (C-010), which keeps inference cost modest — but the estimate must show the query-volume assumption, not hide it.
- Device recycling is core to the subscription model (REQ-005, R-007). Hardware amortisation must therefore assume devices outlive individual officers, and fleet records and wipe verification are build costs, not afterthoughts.
- The 3–4 month timeline is itself a rated risk (R-019). The contingency line is not padding; it is the price of holding the gate discipline when something slips.

## Venture context

Dexter and Siva run a security services business (CIS) in Singapore. We are forming a new Pte Ltd — separate from CIS — to build and operate Sentinel. CIS is the first design partner and early customer.

Locked design and commercial decisions from the 21 July MoM, consistent with the constraint register:

- Wrist-worn, watch form factor (C-001)
- GPS built in, basic camera, cellular SIM only — no WiFi (C-002, C-003, C-004)
- Unit cost target SGD 20–30, hard ceiling SGD 100 (C-005)
- Subscription model; devices recyclable across officers with verified wipe and re-provisioning (R-007)
- SIMs bundled through the venture. Dexter currently runs ~100 SIMs at SGD 8 per month (400GB) via SimTel; volume target on 400+ SIMs is SGD 5–6 (R-003)
- Voice payload is small (KB, not GB), so data plans stay light
- Software scope minimalist: 3–6 approved prompts for each of the five scenarios (A-004), incident report drafts with human approval (C-012), deeper SOP queries by guardrailed retrieval (C-010)
- Three journeys: officer wrist, control room console, administrator back-end
- PDPA-compliant, Singapore-hosted Azure (C-008); DPIA before any collection (R-009)
- Manufacturing in India or Shenzhen, minimum 3–4 year supplier continuity (C-006)
- Patent filing in India. Budget SGD 5,000. My prior filing cost SGD 3,000
- Rollout target: 3–4 months (C-007)
- Design partner: CIS. First deployment volume assumption to model at: 100 devices, scaling to 500 within 12 months

## What I need the estimate to do

The estimate has to answer three questions Dexter and Siva will ask:

1. How much cash do we need to put in before we earn a dollar — the one-off spend
2. What does each device cost us per month once we are running — the recurring per-device cost
3. At what subscription price and volume do we break even, and how quickly

Everything else is commentary around those three numbers.

## Structure

Build the estimate in five sections.

**Section 1: One-off build costs.** Everything we spend before the first paying deployment. Split into:
- Software build — frame the scope by the platform requirements, not by screen count: device fleet lifecycle (REQ-005), secure event-driven alert and control-room workflow (REQ-001, REQ-002), guardrailed RAG assistant and report drafting (REQ-003), tenant/site isolation and RBAC (REQ-004, REQ-006), plus the three journeys that sit on top
- Security and privacy reviews — DPIA and legal counsel (R-009), threat model, penetration test, device supply-chain and OTA security review. These are gated pre-production deliverables, not optional extras
- Device prototyping (design fees, first batch of prototype units, bench and field testing — this is the critical path, R-001, R-002)
- Patent filing in India (agent fees, government fees, translation if any)
- Company incorporation and legal (Pte Ltd setup, NDA, retainer agreement, standard commercial contracts)
- My retainer for the build period (assume 3–4 months at a Technical Director retainer level — leave the monthly figure as a placeholder for me to fill in, but show the total line)
- Cloud and infrastructure setup (initial PDPA-compliant Azure Singapore environment, Terraform foundation, CI/CD — the setup cost, not per-device run cost)
- Contingency (15% — this prices the timeline risk R-019; say so)

Present as a table with a low estimate, a likely estimate, and a high estimate per line item, and a total row for each column.

**Section 2: Recurring per-device monthly cost.** What it costs us to keep one wrist on one officer for one month. Include:
- Hardware amortisation (unit cost divided over a realistic device life — assume 24 months, note the assumption, and note that recycling across officers (R-007) is what makes this figure defensible)
- SIM and connectivity (use the SGD 5–6 volume target, note the SGD 8 fallback, R-003)
- Cloud hosting per device (event storage under the provisional retention positions A-010, compute, monitoring, PDPA overhead)
- Model inference per device (a handful of emergency prompts per shift plus occasional SOP queries, C-010 — state the assumed query volume explicitly)
- Platform maintenance allocation (a share of ongoing engineering and support divided across the device fleet — this shrinks per device as volume grows, so show it at 100, 500 and 1,000 device fleets)

Present as a table. Show per-device monthly cost at three fleet sizes: 100, 500, 1,000. The per-device cost should fall as fleet grows because platform maintenance amortises.

**Section 3: Subscription pricing and break-even.** Given the per-device monthly cost at each fleet size, work out:
- What subscription price gives us a 50% gross margin at each fleet size
- What subscription price gives us a 70% gross margin at each fleet size
- Break-even month, assuming CIS deploys 100 devices at M4 and we scale to 500 by M12 (consistent with the venture roadmap timeline)
- Cumulative cash position at M4, M6, M9 and M12

State the pricing assumption clearly: this is what the venture charges the agency per device per month, not what the end client pays. Note also the register risk that commercial claims must not outrun pilot evidence (R-022) — pricing conversations anchor on measured pilot economics, not on this model.

**Section 4: Sensitivity — the numbers that move the answer most.** Not a long list. The three or four inputs where a small change swings the model materially, each mapped to its register risk:
- Unit hardware cost (SGD 30 vs SGD 60 vs SGD 100 — the C-005 ceiling; R-003)
- SIM price (SGD 5 vs SGD 8 — the R-003 negotiation)
- Fleet ramp speed (500 by M12 vs 500 by M18)
- Model inference cost (assume a plausible band; the constrained AI scope C-010 is the mitigant)

Show what happens to break-even month under each swing.

**Section 5: What I have assumed and what I do not know yet.** A short prose section — not a table. Call out the assumptions that most need Dexter and Siva to challenge or confirm, and tie each to the register where one exists: device life, average query volume per officer per shift, how many officers per site, whether the provisional retention positions survive legal review (A-010), whether CIS pays the venture the same rate as external agencies or gets design-partner pricing.

## Tone and format rules

- Markdown, sparing. Tables in Sections 1, 2, 3 and 4. Prose elsewhere.
- All figures in SGD. Convert INR or USD sourcing costs at a stated rate, and state the rate.
- Round to sensible figures — SGD 4,500 not SGD 4,487
- No emoji, no filler, no "in conclusion", no "I hope this helps"
- British English throughout
- Address Dexter and Siva as "we"
- Do not restate the MoM or the docs. Start from numbers and go forward.
- Where a figure is genuinely a guess, mark it (guess) inline. Do not pretend precision we do not have.
- Where a cost line hedges a risk or depends on an unvalidated assumption, cite the register ID in brackets — e.g. (R-003), (A-010) — so the estimate and the risk register stay traceable to each other

Produce the full .md now.
