# Sentinel build cost estimate

The short answer: we need roughly **SGD 215,000** before the first paying deployment, plus the Technical Director retainer. Once running, a device costs us **SGD 130 a month in a 100-device fleet, falling to SGD 22 at 1,000** — the gap is almost entirely the engineering team amortising across more wrists. At a SGD 75 subscription and 500 devices by M12, we turn monthly cash-positive around M6 and recover the build cost around M19.

All figures SGD. Where sourcing costs were quoted in INR or USD, converted at SGD 1 = INR 62 = USD 0.74. Figures marked (guess) are judgement, not quotes.

## 1. One-off build costs

Everything spent before the first paying deployment. The software line is scoped to the platform requirements — device fleet lifecycle, event-driven alerting and control-room workflow, guardrailed retrieval and report drafting, tenant isolation — not to three screens. The security review line exists because the DPIA, penetration test and supplier reviews are gated deliverables (R-009); leaving them out is how three-month plans become nine-month ones (R-019).

| Line item | Low | Likely | High |
|---|---:|---:|---:|
| Software build (fleet lifecycle, alert workflow, RAG assistant, report drafting, RBAC, three journeys) | 80,000 | 120,000 | 180,000 |
| Security and privacy reviews (DPIA and counsel, threat model, penetration test, supply-chain and OTA review) | 15,000 | 25,000 | 40,000 |
| Device prototyping (design fees, prototype batches, bench and field testing — critical path, R-001/R-002) | 10,000 | 20,000 | 40,000 |
| Patent filing in India (agent and government fees; prior filing cost 3,000) | 3,000 | 5,000 | 7,000 |
| Incorporation and legal (Pte Ltd, NDA, retainer, standard contracts) | 3,000 | 6,000 | 10,000 |
| Technical Director retainer (3–4 months) | TBD | TBD | TBD |
| Cloud and infrastructure setup (Azure Singapore environment, Terraform, CI/CD) | 5,000 | 10,000 | 15,000 |
| Contingency 15% (the price of timeline risk R-019, not padding) | 17,500 | 28,000 | 44,000 |
| **Total excluding retainer** | **133,500** | **214,000** | **336,000** |

Add the retainer at 3–4 × the agreed monthly figure. The likely case with a SGD 10,000 monthly retainer lands at ~SGD 254,000 all-in.

## 2. Recurring per-device monthly cost

What one wrist on one officer costs us per month. Assumptions stated inline; the maintenance allocation is what moves with fleet size.

| Cost line | Basis | 100 devices | 500 devices | 1,000 devices |
|---|---|---:|---:|---:|
| Hardware amortisation | SGD 45 unit (guess) over 24 months; defensible because devices recycle across officers (R-007) | 2 | 2 | 2 |
| SIM and connectivity | SGD 5.50 volume target (R-003); SGD 8 fallback | 5.50 | 5.50 | 5.50 |
| Cloud hosting | Event storage under provisional retention (A-010), compute, monitoring | 1.50 | 1.50 | 1.50 |
| Model inference | ~200 queries per device per month (guess): a handful of prompts per shift plus occasional SOP queries, scope constrained by design (C-010) | 1 | 1 | 1 |
| Platform maintenance | SGD 12,000 per month engineering and support (guess), divided across fleet | 120 | 24 | 12 |
| **Total per device per month** | | **130** | **34** | **22** |

The lesson in this table: below 500 devices we are an engineering team with a hardware hobby. The subscription price only becomes a product price once the fleet amortises the team.

## 3. Subscription pricing and break-even

This is what the venture charges the agency per device per month, not what the end client pays. Pricing conversations anchor on measured pilot economics, not this model (R-022).

**Price for target gross margin, by fleet size:**

| Fleet | Per-device cost | Price at 50% margin | Price at 70% margin |
|---|---:|---:|---:|
| 100 | 130 | 260 | 435 |
| 500 | 34 | 68 | 115 |
| 1,000 | 22 | 44 | 73 |

**Break-even model.** Assumptions: CIS deploys 100 devices at M4, fleet grows linearly to 500 by M12, subscription SGD 75 per device per month (guess), one-off spend at the likely SGD 214,000 excluding retainer. Monthly contribution is fleet × SGD 65 minus the SGD 12,000 platform team.

| Position | M4 | M6 | M9 | M12 |
|---|---:|---:|---:|---:|
| Fleet | 100 | 200 | 350 | 500 |
| Monthly contribution | −5,500 | +1,000 | +10,750 | +20,500 |
| **Cumulative cash (incl. one-off)** | **−219,500** | **−220,750** | **−198,250** | **−146,500** |

Monthly cash turns positive around M6 at roughly 200 devices. The one-off build cost is recovered around M19–M20 if the fleet holds at 500; sooner if it keeps growing. One caveat: device purchases are cash up front — 500 units at SGD 45 is ~SGD 22,500 of working capital the amortisation line smooths over. We need that cash before the subscription income pays it back.

## 4. Sensitivity — the numbers that move the answer most

Four inputs swing the result. Each maps to a risk we already track.

| Swing | Effect on per-device cost (500 fleet) | Effect on break-even |
|---|---|---|
| Unit hardware SGD 30 → 100 (C-005, R-003) | 33 → 38 | Payback slips ~1 month. Hardware matters less than feared — amortisation dilutes it |
| SIM at SGD 8 not SGD 5 (R-003) | 34 → 36.50 | ~1 month later at SGD 75 pricing; worse if pricing is squeezed |
| Fleet reaches 500 at M18 not M12 | Contribution accumulates ~6 months slower | Payback pushes from ~M19 to ~M25. The biggest single swing |
| Inference SGD 0.50 → 3 per device (scope creep past C-010) | 33.50 → 36 | Negligible at current scope; material only if AI usage escapes the guardrails |

The uncomfortable finding: the model is most sensitive to ramp speed and to the SGD 12,000 platform team — both within our control — and least sensitive to hardware cost, which is where procurement attention naturally goes.

## 5. What we have assumed and do not yet know

The numbers above stand or fall on a handful of assumptions Dexter and Siva should challenge directly.

Device life is assumed at 24 months. If field trial shows units dying at 12, the amortisation doubles and the SGD 45 unit matters twice as much. The recycling model (R-007) is what makes 24 months plausible; the field trial is what proves it.

Query volume is assumed at ~200 per device per month. If officers actually use the assistant heavily — which would be a good problem — inference and possibly cloud lines rise, though the constrained scope (C-010) caps the damage. We will not know the real number until the CIS pilot measures it.

The platform team at SGD 12,000 a month is the largest recurring line and the least validated. It assumes one engineer plus support cover. Whether that is right depends on how much of the build is contracted versus hired, and on what support load 500 devices actually generate.

Retention positions are provisional (A-010). If counsel requires longer audio retention, storage costs rise; if shorter, they fall. Either way the line is small — but the compliance cost of getting it wrong is not.

CIS pricing is unresolved. This model assumes CIS pays SGD 75 like any agency. If CIS gets design-partner pricing, break-even moves right and external agencies carry more of the recovery. We should decide this before the pilot, not after.

Finally, the retainer is a placeholder and the one-off totals exclude it. The three of us need to put a number in that line before this estimate means anything to a bank account.
