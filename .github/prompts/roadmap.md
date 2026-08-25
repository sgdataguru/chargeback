You are helping me draft the roadmap for a new security-wearable venture I am joining as Technical Director on retainer. The roadmap goes to my two co-founders Dexter and Siva — both are commercial operators from the security-agency world, not technical. It is an internal working document, not an investor pitch. Deliver it as a single .md file.

Apply my bertie-voice skill throughout: so-what first, causality over chronology, British business English, short declarative sentences, no American ChatGPT register, no bullet-point spam where prose does the job.

## Venture context

Dexter and Siva run a security services business (CIS) in Singapore. We are forming a new Pte Ltd — separate from CIS — to build a wrist-worn AI wearable for security officers, sold on subscription. CIS is the first design partner and early customer. The device replaces app-only solutions because an app has no defensible barrier; a wearable tied to a platform, corpus and control-room console does.

Locked design decisions from the 21 July MoM:
- Wrist-worn, watch form factor
- GPS built in, simple camera, cellular SIM only (no WiFi — sites do not have coverage)
- Cost target SGD 20–30 per unit, hard ceiling SGD 100
- Subscription model, device recyclable across officers when they leave the agency
- SIMs bundled through the venture (Dexter negotiating SimTel volume pricing on 400+ SIMs, target SGD 5–6 per month)
- Software scope minimalist: 5–6 emergency prompts per scenario, incident report auto-generation in regulator format, deeper SOP queries handled by AI on demand
- Role-based access (supervisor sees site-level info, not officer-device transcripts)
- PDPA-compliant, Singapore-hosted cloud
- Security-domain-only guardrails at model layer

Go-to-market is top-down: sell assurance to end clients (property owners, condo/commercial/industrial site managers) and let them mandate the device in security tenders. Target the top 25% of agencies who can absorb the cost. Wedge is the PWM salary rise from ~SGD 3,600 today to ~SGD 6,000 by 2028.

IP path: file patent in India for patent-pending status. Budget SGD 5,000. Full grant unlikely and accepted. Patent pending is enough for commercial signalling.

Device sourcing: India or Shenzhen. Minimum 3–4 year supplier continuity. Joint decision — Dexter sources and shortlists, I recommend.

Timeline target: 3–4 month rollout. Device prototyping is the critical path, not software.

## Roadmap structure

Produce the roadmap across four parallel tracks, each on its own timeline:

1. **Software and platform** — model layer, guardrails, three journeys (officer wrist, control room console, administrator back-end), incident-report generator, cloud hosting, PDPA sign-off
2. **Device** — form factor confirmation, supplier shortlist, prototype build, field trial units, unit economics validation at scale
3. **Commercial and IP** — new company incorporation, NDA to retainer to project-level engagement, patent filing in India, SIM contract with SimTel, pricing model, first design-partner deployment at CIS
4. **Go-to-market** — end-client positioning materials, top-25% agency shortlist, public education channel scoping, first client conversations

For each track show the month-by-month milestones across a 4-month horizon (call them M1, M2, M3, M4 — do not put calendar dates on it, we have not agreed a start). Against each milestone show the owner (Mahesh, Dexter, Siva, or joint) and the dependency it unblocks.

Call out the critical path explicitly — the device track is the bottleneck. Show which software and commercial milestones can run in parallel without waiting on the device, and which cannot.

## Sections I want in the .md

1. **One-paragraph opener** — what this roadmap is, who it is for, the 3–4 month horizon, the critical path in one line
2. **Four track timelines** — as described above, one section per track
3. **Cross-track dependencies** — the two or three points where tracks must sync (e.g. patent filing before we show device photos to end clients, incorporation before retainer formalises, prototype before first CIS deployment)
4. **What can go wrong** — the three or four things most likely to slip the timeline (supplier continuity, SIM pricing, patent agent responsiveness, PDPA sign-off), with the mitigation for each
5. **Decisions we need to make now** — what Dexter, Siva and I need to close in the next two weeks to keep M1 on track
6. **Open questions for the next meeting** — the handful of items I want Dexter and Siva to answer

## Tone and format rules

- Markdown, but sparing — headers for structure, tables where they earn their place (the four track timelines are the right place for tables), prose everywhere else
- No emoji, no filler, no "in conclusion"
- British English throughout
- Address Dexter and Siva as "we" — this is a joint working document, not a report I am handing to them
- Do not restate the MoM back to them. They were in the room. Start from decisions and go forward.

Produce the full .md now.