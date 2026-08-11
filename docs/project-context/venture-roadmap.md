# Sentinel venture roadmap

## What this is

This is the working roadmap for the new venture, for the three of us. It covers four months from an agreed start — M1 to M4 — across four parallel tracks: software and platform, device, commercial and IP, and go-to-market. The device track is the critical path: nothing in the field moves until prototype hardware proves itself, so everything else is sequenced to be ready before it, not after it.

## Track 1: Software and platform

The platform work runs ahead of the device wherever it can. Cloud, security, guardrails and the control-room journeys are built and tested against emulators and vendor SDKs. Only measured cellular, GPS and battery behaviour waits for real hardware. Milestones below are the phase gates from the technical delivery plan, not arbitrary dates.

| Month | Milestone | Owner | Unblocks |
|---|---|---|---|
| M1 | Azure Singapore tenancy, environments and CI/Terraform path stood up. DPIA and threat model opened with legal counsel (R-009). Five emergency scenarios scripted and SOP corpus owners named with CIS (A-005). | Mahesh | Phase 1 build starts without waiting on hardware. |
| M2 | Phase 1 assurance slice passing in staging: device identity, authenticated alert ingestion, control-room acknowledgement and escalation workflow, full audit trail, role boundaries enforced (R-008). | Mahesh | Device-to-cloud field test the moment prototypes land. |
| M3 | Phase 2: SOP retrieval with citations, off-topic refusal, incident-report drafts in regulator format with named human approval (R-011, R-012, R-014). DPIA signed off (R-009). | Mahesh | Control-room demo with real content; pilot data collection lawful. |
| M4 | Phase 3 pilot readiness: fleet monitoring, signed OTA with rollback, deactivation and verified-wipe recycling (R-007, R-024), operational drills with the CIS control room. Gate review passed. | Mahesh | First CIS deployment. |

## Track 2: Device

This is the bottleneck (R-001, R-002). Every other track's later milestones hang off measured results from real units.

| Month | Milestone | Owner | Unblocks |
|---|---|---|---|
| M1 | Scored shortlist of two or three suppliers in India or Shenzhen against the agreed criteria: LTE/4G, GPS, secure identity, OTA, battery, unit cost. Continuity terms probed with each (R-001, R-002). | Joint — Dexter sources, Mahesh scores | Prototype order placed without rework. |
| M2 | Prototype units in hand and bench-tested: cellular attach, GPS accuracy, battery under representative load, OTA, reset behaviour (R-004, R-005, R-006). Fallback supplier kept warm. | Mahesh | Phase 1 gate moves from staging to field. |
| M3 | Field trial units on CIS sites. Measured cellular, GPS and battery data replaces vendor claims. Failure and replacement rates feed the cost model (R-003). | Joint | Pricing model built on evidence, not estimates. |
| M4 | Unit economics validated at 400-plus scale. Supplier continuity commitment signed for three to four years (R-002). Production order decision taken. | Joint | CIS fleet deployment and the subscription price point. |

## Track 3: Commercial and IP

The legal shell and the IP signal must exist before we show anything outside the room.

| Month | Milestone | Owner | Unblocks |
|---|---|---|---|
| M1 | New Pte Ltd incorporation filed. NDA with CIS executed. Retainer formalised into project-level engagement. Patent agent in India engaged within the SGD 5,000 budget. | Dexter | Detailed operational exchange with CIS; everything downstream. |
| M2 | Patent filed in India; patent-pending status secured. SimTel negotiation opened on 400-plus SIMs against the SGD 5–6 target (R-003). | Dexter | Device photos and form factor can be shown externally. |
| M3 | SimTel contract signed. Draft subscription pricing model written, with device recycling across officers built in. | Dexter | Pricing finalisation once field economics land. |
| M4 | First design-partner agreement with CIS signed, conditional on the Phase 3 pilot-readiness gate. Pricing finalised against measured unit economics. | Joint | Revenue; the reference customer for go-to-market. |

## Track 4: Go-to-market

We sell assurance to property owners and let them mandate the device in tenders. Claims stay inside what the pilot can evidence (R-022).

| Month | Milestone | Owner | Unblocks |
|---|---|---|---|
| M1 | End-client positioning one-pager drafted: the assurance storey and the PWM wage wedge. Top-25% agency shortlist assembled. | Siva | Consistent message before anyone speaks to a client. |
| M2 | Positioning materials finalised — no device imagery until the patent is filed. Public education channel scoped and costed. | Siva | First client conversations. |
| M3 | First end-client conversations opened, using the Phase 1 alert-flow demo as evidence. | Dexter and Siva | Pipeline seeded ahead of the CIS pilot readout. |
| M4 | First end-client letters of intent. Agency conversations prepared for the moment pilot results exist. | Dexter and Siva | Post-pilot sales motion. |

## Cross-track dependencies

Three points where the tracks must sync. Miss one and the timeline slips everywhere.

1. **Incorporation and NDA before anything else (M1).** The retainer cannot formalise, and CIS cannot exchange detailed operational material, until the new company exists and the NDA is signed. This is the Phase 0 gate for the whole venture.
2. **Patent filed before the device is shown (Commercial M2 before GTM M2–M3).** Patent-pending is the only protection we will have. No end client, agency or channel sees the form factor until filing is confirmed.
3. **Field data before pricing and deployment (Device M3 before Commercial M4 and Software M4).** The subscription price and the CIS deployment both depend on measured unit economics and a passed pilot-readiness gate. We do not price on estimates or deploy on vendor claims.

## What can go wrong

Four things are most likely to slip the timeline. All four have mitigations we have already agreed in principle; the discipline is starting them in M1, not when the problem surfaces.

**Supplier continuity fails (R-002).** A shortlisted supplier cannot commit to three to four years, or fails diligence. Mitigation: we hold two suppliers through the shortlist and keep the fallback warm until the production order. We do not commit to a single source before contractual continuity terms are signed.

**SIM pricing lands above SGD 6 (R-003).** The subscription model is sensitive to a dollar or two per SIM at our volumes. Mitigation: Dexter opens the SimTel negotiation in M2 with the 400-plus volume on the table, and we keep the total-cost model live so a bad SIM number reprices the subscription before we sign anything, not after.

**PDPA sign-off slips (R-009).** Legal review of voice and location collection takes longer than the build. Mitigation: the DPIA opens in M1 alongside the first line of code, collection is minimised by design, and no pilot data is collected before sign-off. Legal runs in parallel, never in sequence.

**The patent agent is slow.** Filing is a third party's calendar, not ours. Mitigation: the agent is engaged in M1 with fixed milestones and a named backup. We only need filing for patent-pending status — the grant timeline is irrelevant to the plan.

The umbrella risk is the timeline itself (R-019). The answer is the gate discipline already in the technical plan: a failed gate pauses that track; it is not absorbed silently into the next month.

## Decisions we need to make now

These close in the next two weeks or M1 slips. They are the Phase 0 exit criteria, restated as commitments.

- **Incorporation.** Company name, shareholding, directorships. Dexter and Siva to table the proposal; we sign off in one sitting.
- **NDA and retainer.** Terms agreed and executed with CIS, and the retainer converted to project-level engagement. Dexter owns the paper.
- **Device shortlist.** Dexter brings candidate suppliers; we score them jointly against the agreed criteria and pick the two or three to engage.
- **Pilot scope.** Siva confirms the CIS sites, the officers, the control-room participants and the five scenarios we will drill.
- **Cloud and legal.** Mahesh confirms Azure subscription access and Singapore-region service availability, and engages counsel for the DPIA.
- **Patent agent.** Dexter selects the India agent against the SGD 5,000 budget.

## Open questions for the next meeting

A handful of items we need Dexter and Siva to answer. Each converts an assumption into a fact, or closes a gap the roadmap cannot.

1. Which CIS sites, officers and control-room staff are committed to the pilot, and from when (A-001)?
2. Is SGD 5–6 per SIM realistic at 400-plus units, and what contract length does SimTel want in exchange (A-003)?
3. Who at CIS owns the SOP corpus, and who has authority to approve it for use on the platform (A-005)?
4. What subscription price will end clients actually tolerate — have we had any soundings, even informal?
5. Do we file the patent on the device, the assurance workflow, or both within the one budget?
6. Are we agreed the provisional retention positions — audio thirty days, transcripts and reports two years — go into the DPIA as drafted, or do we amend first (A-010)?
