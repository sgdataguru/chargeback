You are helping me draft the venture-level roadmap for Sentinel, the wrist-worn security wearable platform I am joining as Technical Director on retainer. The roadmap goes to my two co-founders Dexter and Siva — commercial operators from the security-agency world, not technical readers. It is an internal working document, not an investor pitch. Deliver it as a single .md file.

Apply my bertie-voice skill throughout: so-what first, causality over chronology, British business English, short declarative sentences, no American ChatGPT register, no bullet-point spam where prose does the job.

## Source material to align with

Before writing, read and align with the existing Sentinel documentation in [docs](../../docs). Do not restate it; use it to keep terminology, scope and risk framing consistent:

- [docs/project-context/overview.md](../../docs/project-context/overview.md) — venture definition, MVP boundaries, buyers, commercial model
- [docs/project-context/value-delivery-roadmap.md](../../docs/project-context/value-delivery-roadmap.md) — the four-phase technical delivery plan (Phase 0 mobilise, Phase 1 assurance slice, Phase 2 AI-assisted reporting, Phase 3 pilot readiness). The venture roadmap must nest around this: my phase gates are the dependency spine for the commercial and go-to-market tracks.
- [docs/project-context/risk-constraint-register.md](../../docs/project-context/risk-constraint-register.md) — the risk IDs (R-001 to R-025), assumptions (A-001 to A-012) and constraints (C-001 to C-013). Cite these where a roadmap milestone retires a risk or validates an assumption.
- [docs/architecture/overview.md](../../docs/architecture/overview.md) — the three user journeys (officer wrist, control room console, administrator back-end), the trust boundaries, and the human-controlled AI model.

Key facts from the docs that must shape the roadmap:

- The platform is Azure-hosted in Singapore (C-008), event-driven, with the cloud — not the device — authoritative for identity, policy, tenancy and report submission.
- AI is constrained to approved security-domain assistance, SOP retrieval with citations, and report drafting (C-010). It cannot autonomously submit reports or command devices (C-012). Supervisors never see officer-to-device transcripts (C-011).
- The MVP proves value through the assurance vertical slice: provisioned device → authenticated critical alert → auditable control-room workflow. Five initial scenarios: fire, medical emergency, intrusion, duress, suspicious person or package (A-004).
- The highest-rated delivery risks are device capability and supplier continuity (R-001, R-002), cellular and GPS performance (R-004, R-005), unit economics (R-003), PDPA/legal approval (R-009), and the compressed timeline itself (R-019). The "what can go wrong" section must map to these.
- The technical roadmap's Phase 0 (weeks 1–2) is the de-risking gate: NDA, device shortlist, Azure/legal path, pilot scope. M1 of the venture roadmap must close the same items.

## Venture context

Dexter and Siva run a security services business (CIS) in Singapore. We are forming a new Pte Ltd — separate from CIS — to build and operate Sentinel. CIS is the first design partner and early customer. The device replaces app-only solutions because an app has no defensible barrier; a wearable tied to a platform, corpus and control-room console does.

Locked design decisions from the 21 July MoM, consistent with the constraint register:

- Wrist-worn, watch form factor (C-001)
- GPS built in, basic camera, cellular SIM only — no WiFi (C-002, C-003, C-004)
- Unit cost target SGD 20–30, hard ceiling SGD 100 (C-005)
- Subscription model; devices recyclable across officers with verified wipe and re-provisioning (per R-007)
- SIMs bundled through the venture; Dexter negotiating SimTel volume pricing on 400+ SIMs, target SGD 5–6 per month (per R-003)
- Software scope minimalist: 5–6 approved emergency prompts per scenario, incident report drafts in regulator format, deeper SOP queries by guardrailed retrieval (C-010)
- Role-based access: supervisor sees site-level information, never officer-device transcripts (C-011)
- PDPA-compliant, Singapore-hosted cloud; DPIA before any collection (C-008, R-009)
- Security-domain-only guardrails enforced at the application layer, not trusted to the model (per architecture decision 3)

Go-to-market is top-down: sell assurance to end clients (property owners, condo/commercial/industrial site managers) and let them mandate the device in security tenders. Target the top 25% of agencies who can absorb the cost. Wedge is the PWM salary rise from ~SGD 3,600 today to ~SGD 6,000 by 2028.

IP path: file patent in India for patent-pending status. Budget SGD 5,000. Full grant unlikely and accepted. Patent pending is enough for commercial signalling.

Device sourcing: India or Shenzhen, minimum 3–4 year supplier continuity (C-006). Joint decision — Dexter sources and shortlists, I recommend against the scored criteria in the technical roadmap (LTE/4G, GPS, secure identity, OTA, battery, cost).

Timeline target: 3–4 month rollout (C-007). Device prototyping is the critical path, not software.

## Roadmap structure

Produce the roadmap across four parallel tracks, each on its own timeline. The tracks map to the technical phases — note where a venture milestone corresponds to a technical phase gate (e.g. "first CIS deployment" cannot precede Phase 3 pilot-readiness gate):

1. **Software and platform** — model layer guardrails, the three journeys (officer wrist, control room console, administrator back-end), incident-report drafting with human approval, Azure Singapore hosting, PDPA DPIA and sign-off. Frame milestones as the phase gates from the value-delivery roadmap: Phase 1 assurance slice, Phase 2 AI-assisted reporting, Phase 3 pilot readiness.
2. **Device** — form factor confirmation, scored supplier shortlist, prototype build, field trial units, unit economics validation at scale. Every milestone should state which risk it retires (R-001, R-002, R-003, R-006).
3. **Commercial and IP** — new company incorporation, NDA then retainer then project-level engagement, patent filing in India, SimTel contract, pricing model, first design-partner deployment at CIS.
4. **Go-to-market** — end-client positioning materials, top-25% agency shortlist, public education channel scoping, first client conversations. Commercial claims must not exceed pilot evidence (R-022).

For each track show month-by-month milestones across a 4-month horizon (M1, M2, M3, M4 — no calendar dates; we have not agreed a start). Against each milestone show the owner (Mahesh, Dexter, Siva, or joint) and the dependency it unblocks.

Call out the critical path explicitly — the device track is the bottleneck (R-001, R-002). Show which software and commercial milestones can run in parallel without waiting on the device, and which cannot. Use the technical roadmap's phasing logic: cloud, security and AI guardrail work proceeds against vendor SDKs and emulators; anything requiring measured cellular, GPS or battery behaviour waits for prototype hardware.

## Sections I want in the .md

1. **One-paragraph opener** — what this roadmap is, who it is for, the 3–4 month horizon, the critical path in one line
2. **Four track timelines** — as described above, one section per track
3. **Cross-track dependencies** — the two or three points where tracks must sync (e.g. patent filing before we show device photos to end clients, incorporation before retainer formalises, prototype before first CIS deployment, Phase 1 gate before any end-client demo of the alert flow)
4. **What can go wrong** — the three or four things most likely to slip the timeline, drawn from the risk register (supplier continuity R-002, SIM pricing R-003, PDPA sign-off R-009, patent agent responsiveness), with the mitigation for each as already recorded in the register
5. **Decisions we need to make now** — what Dexter, Siva and I must close in the next two weeks to keep M1 on track; this maps to the Phase 0 exit criteria (NDA executed, pilot scope approved, device shortlist scored, Azure and legal path confirmed)
6. **Open questions for the next meeting** — the handful of items I want Dexter and Siva to answer, including which assumptions (A-001 design-partner availability, A-003 cellular terms, A-005 SOP corpus ownership) they can convert into confirmed facts

## Tone and format rules

- Markdown, but sparing — headers for structure, tables where they earn their place (the four track timelines are the right place for tables), prose everywhere else
- No emoji, no filler, no "in conclusion"
- British English throughout
- Address Dexter and Siva as "we" — this is a joint working document, not a report I am handing to them
- Do not restate the MoM or the docs back to them. They were in the room. Start from decisions and go forward.
- Where a milestone retires a risk or validates an assumption, cite the register ID in brackets — e.g. (R-002), (A-003) — so the roadmap and the risk register stay traceable to each other

Produce the full .md now.
