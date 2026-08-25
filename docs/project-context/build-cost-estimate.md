# Sentinel build cost estimate

The short answer: we need roughly **SGD 85,000** before the first paying deployment, plus the Technical Director retainer, if the build is done by an India-based team. Once running, a device costs us **SGD 51 a month in a 100-device fleet, falling to SGD 15 at 1,000** — the gap is almost entirely the ops team amortising across more wrists. At a SGD 75 subscription and 500 devices by M12, we turn monthly cash-positive at M4 and recover the one-off spend by M9.

All figures SGD unless marked INR. Conversion at SGD 1 = INR 75, per the workbook. Figures marked (guess) are judgement, not quotes. The full model, with editable inputs, lives in the companion workbook Sentinel_India_Build_Cost_Estimate.xlsx; this document is the narrative around its likely case.

## 1. One-off build costs

Everything spent before the first paying deployment. The software line is built bottom-up from man-days by role at India day rates — 409 person-days across eleven roles, with a 10% rework buffer — rather than a top-down guess at three apps. Of those 409 days, 123 (S$18,160) are delivered by the Technical Director, Mahesh, personally — discovery and architecture, the AI/RAG assistant and guardrails, project management and ongoing code review (see §6). Those lines are not paid out, so the software line below is the reduced "New Cost" payable to the India team: **S$33,657 (₹2,524,300)**. The security review line exists because the DPIA, penetration test and supplier reviews are gated deliverables (R-009); leaving them out is how three-month plans become nine-month ones (R-019).

| Line item | Low | Likely | High |
|---|---:|---:|---:|
| Software build — India team, 286 man-days after Technical Director (Mahesh) keeps 123 days in-house; fleet lifecycle, alert workflow, report drafting, RBAC, three journeys (the S$33,657 "New Cost", see §6) | 30,000 | 33,657 | 42,000 |
| Device prototyping — India, two rounds (design fees, ~20 prototype units, bench and field testing; critical path R-001/R-002) | 8,500 | 16,000 | 24,000 |
| Security and privacy reviews (DPIA and counsel, threat model, penetration test, supply-chain and OTA review) | 8,500 | 14,500 | 22,000 |
| Patent filing in India (agent, government, drafting; prior filing cost INR 195k ≈ SGD 3,000) | 2,500 | 4,500 | 6,000 |
| Incorporation and legal (Pte Ltd, NDA, retainer, standard contracts) | 3,000 | 5,000 | 8,000 |
| Cloud and infrastructure setup (Azure Singapore tenant, Terraform baseline, CI/CD — setup only) | 4,500 | 8,500 | 12,000 |
| Technical Director retainer (3–4 months) | TBD | TBD | TBD |
| Contingency 10% (the price of timeline risk R-019, not padding) | 5,700 | 8,200 | 11,400 |
| **Total excluding retainer** | **62,700** | **90,357** | **125,400** |

The workbook's central case lands near SGD 90,000 once the Technical Director's 123 kept days (S$18,160) are removed from the payable software line; the table above keeps a band around that mid-point. The S$18,160 of Mahesh's own labour is a contribution in kind, not cash out — it substitutes for contracted spend rather than adding to the budget. Add the retainer at 3–4 × the agreed monthly figure — at SGD 10,000 a month the likely case comes to roughly SGD 120,000 all-in.

**Software man-day roll-up** (base build, before the 10% rework buffer):

| Role | Days | INR/day | SGD |
|---|---:|---:|---:|
| Tech Lead / Architect | 32 | 15,000 | 6,400 |
| Embedded / Firmware Engineer | 55 | 12,000 | 8,800 |
| AI / RAG Engineer | 35 | 12,000 | 5,600 |
| Senior Full-stack Engineer | 45 | 10,000 | 6,000 |
| Mid Full-stack Engineer | 50 | 6,000 | 4,000 |
| DevOps / Cloud Engineer | 25 | 10,000 | 3,300 |
| Mobile Engineer | 15 | 8,000 | 1,600 |
| UI / UX Designer | 27 | 7,000 | 2,500 |
| QA Engineer | 40 | 5,000 | 2,700 |
| Security Consultant | 8 | 18,000 | 1,900 |
| Project Manager | 40 | 8,000 | 4,300 |
| **Total (372 base days)** | **372** | | **47,100** → **51,800 incl. buffer (INR 3.89m)** |

Firmware is the single largest role line, as it should be — the device is the critical path. The workbook breaks this down by work package (wrist firmware, control-room console, admin back-end, RAG assistant, cloud) if we need to negotiate scope line by line.

## 2. Recurring per-device monthly cost

What one wrist on one officer costs us per month. Assumptions stated inline; the ops team allocation is what moves with fleet size.

| Cost line | Basis | 100 devices | 500 devices | 1,000 devices |
|---|---|---:|---:|---:|
| Hardware amortisation | SGD 45 unit (guess) over 24 months; defensible because devices recycle across officers (R-007) | 2 | 2 | 2 |
| SIM and connectivity | SGD 5.50 volume target (R-003); SGD 8 fallback | 5.50 | 5.50 | 5.50 |
| Cloud hosting | Azure Singapore, PDPA-compliant; event storage under provisional retention (A-010), compute, monitoring | 2 | 2 | 2 |
| Model inference | ~200 queries per device per month (guess), scope constrained by design (C-010) | 1 | 1 | 1 |
| Platform ops team — India | SGD 4,000 per month (two mid engineers plus partial DevOps; guess), divided across fleet | 40 | 8 | 4 |
| **Total per device per month** | | **51** | **19** | **15** |

The lesson in this table: below 500 devices we are an ops team with a hardware hobby. The subscription price only becomes a product price once the fleet amortises the team.

## 3. Subscription pricing and break-even

This is what the venture charges the agency per device per month, not what the end client pays. Pricing conversations anchor on measured pilot economics, not this model (R-022).

**Price for target gross margin, by fleet size:**

| Fleet | Per-device cost | Price at 50% margin | Price at 70% margin |
|---|---:|---:|---:|
| 100 | 51 | 101 | 169 |
| 500 | 19 | 37 | 62 |
| 1,000 | 15 | 29 | 49 |

**Break-even model.** Assumptions: CIS deploys 100 devices at M4, fleet grows linearly to 500 by M12 and holds, subscription SGD 75 per device per month (guess), one-off spend at SGD 85,000 excluding retainer, contribution SGD 56 per device at the 500-fleet cost. The workbook models M1–M24; the shape of it:

| Position | M4 | M6 | M9 | M12 |
|---|---:|---:|---:|---:|
| Fleet | 100 | 200 | 350 | 500 |
| Monthly contribution | +7,400 | +14,900 | +26,100 | +37,400 |
| **Cumulative cash (incl. one-off)** | **−77,800** | **−51,700** | **+15,500** | **+116,400** |

Monthly cash turns positive at M4 — the first month CIS pays. The one-off build cost is recovered by M9. One caveat: device purchases are cash up front — 500 units at SGD 45 is ~SGD 22,500 of working capital the amortisation line smooths over. We need that cash before the subscription income pays it back, and the break-even month moves right if the fleet ramp is slower than assumed.

## 4. Sensitivity — the numbers that move the answer most

Five inputs swing the result. Each maps to a risk we already track.

| Swing | Effect on per-device cost (500 fleet) | Effect on break-even |
|---|---|---|
| Unit hardware SGD 30 → 100 (C-005, R-003) | ~SGD 5 move | Payback slips ~1 month at worst. Least sensitive line — amortisation dilutes it |
| SIM at SGD 8 not SGD 5.50 (R-003) | ~SGD 2.50 move | ~1 month later at SGD 75 pricing; worse if pricing is squeezed |
| Fleet at M12: 300 vs 500 vs 750 | Contribution accumulates slower or faster | The biggest swing: payback moves from ~M25 to ~M15 around the M19-ish base |
| Inference SGD 1 → 6 per device (scope creep past C-010) | ~SGD 5 move | Negligible at current scope; material only if AI usage escapes the guardrails |
| Platform team SGD 3k → 8k per month | Direct, recurring | Second biggest swing: every SGD 1k on the team pushes break-even out ~2 months |

The uncomfortable finding stands: the model is most sensitive to ramp speed and the platform team — both within our control — and least sensitive to hardware cost, which is where procurement attention naturally goes. Spend management attention where the numbers say.

## 5. What we have assumed and do not yet know

The numbers above stand or fall on a handful of assumptions Dexter and Siva should challenge directly.

India day rates are the foundation of the software line. They assume freelance or small-studio rates — Tech Lead at INR 15,000 a day, mid engineers at INR 6,000 — and they assume we can actually hire and hold that team for the build window. If we end up with an agency or Singapore-based contractors, the software line roughly triples and the whole estimate needs re-opening. This is the assumption to test first, with real candidate rates.

The platform ops team at SGD 4,000 a month is the largest recurring line and the least validated. It assumes two mid engineers in India plus partial DevOps cover. Whether that is right depends on how much of the build is contracted versus hired, and on what support load 500 devices actually generate.

Device life is assumed at 24 months. If field trial shows units dying at 12, the amortisation doubles and the SGD 45 unit matters twice as much. The recycling model (R-007) is what makes 24 months plausible; the field trial is what proves it.

Query volume is assumed at ~200 per device per month. If officers actually use the assistant heavily — which would be a good problem — inference rises, though the constrained scope (C-010) caps the damage. We will not know the real number until the CIS pilot measures it.

Retention positions are provisional (A-010). If counsel requires longer audio retention, storage costs rise; if shorter, they fall. Either way the line is small — but the compliance cost of getting it wrong is not.

CIS pricing is unresolved. This model assumes CIS pays SGD 75 like any agency. If CIS gets design-partner pricing, break-even moves right and external agencies carry more of the recovery. We should decide this before the pilot, not after.

Finally, the retainer is a placeholder and the one-off totals exclude it. The three of us need to put a number in that line before this estimate means anything to a bank account.

## 6. What the Technical Director (Mahesh) keeps — a plain-English walk-through

This section explains, line by line and in everyday terms, which parts of the software build the Technical Director, Mahesh, will personally deliver instead of paying an outside team for. It is the story behind the "New Cost" cell on the `3. Software Man-Days` sheet of `Sentinel_India_Build_Cost_Estimate.xlsx` — the figure of **₹2,524,300 (S$33,657)** that remains payable to the India team once Mahesh's own work is removed.

If you have never opened the workbook, read this section first. Every number below comes straight from the sheet; nothing here is a new assumption.

### 6.1 The starting point — the full software build

The sheet prices the entire software build as a list of work packages. Each package is split into the roles that touch it, and each role line is just:

> **days worked × day rate = cost for that line**

Day rates come from the `2. Assumptions` sheet (India freelance/small-studio rates, 2026). The exchange rate used everywhere is **S$1 = ₹75**.

Add every line from row 5 to row 22 and you get the base build:

| | Days | Cost (₹) | Cost (S$) |
|---|---:|---:|---:|
| Base build (all 18 lines) | 372 | 3,533,000 | 47,107 |
| + 10% rework buffer | 37 | 353,300 | 4,711 |
| **Total software build** | **409** | **3,886,300** | **51,817** |

That S$51,817 is the "full price if we paid a team for everything". It is cell `G26` on the sheet.

### 6.2 The six lines the Technical Director keeps

Three work packages — six role lines in total — are delivered by Mahesh (Technical Director) personally, so they are **not** paid out to the India team. They are:

**A. Discovery & architecture** — the upfront thinking that decides what we are building and how the pieces fit together.

| Line | Role | Days | Day rate (₹) | Cost (₹) | Cost (S$) | What it actually means |
|---|---|---:|---:|---:|---:|---|
| Row 5 | Tech Lead / Architect | 12 | 15,000 | 180,000 | 2,400 | System design, data model, deciding how each part talks to the others |
| Row 6 | UI / UX Designer | 6 | 7,000 | 42,000 | 560 | Drawing the user journeys for the officer, the control room, and the admin |
| **Group A subtotal** | | **18** | | **222,000** | **2,960** | |

**B. AI / RAG assistant + guardrails** — the emergency-guidance assistant that answers an officer's questions using only approved SOPs, plus the safety rails that stop it going off-topic.

| Line | Role | Days | Day rate (₹) | Cost (₹) | Cost (S$) | What it actually means |
|---|---|---:|---:|---:|---:|---|
| Row 16 | AI / RAG Engineer | 35 | 12,000 | 420,000 | 5,600 | Building the prompts, the SOP retrieval, and the domain guardrails |
| Row 17 | Senior Full-stack Engineer | 10 | 10,000 | 100,000 | 1,333 | The API layer that routes prompts and logs every answer |
| **Group B subtotal** | | **45** | | **520,000** | **6,933** | |

**C. Project management + ongoing tech lead** — running the build and reviewing everyone else's code as the build progresses.

| Line | Role | Days | Day rate (₹) | Cost (₹) | Cost (S$) | What it actually means |
|---|---|---:|---:|---:|---:|---|
| Row 21 | Project Manager | 40 | 8,000 | 320,000 | 4,267 | Stand-ups, sprint reviews, tracking, keeping the build on schedule |
| Row 22 | Tech Lead / Architect | 20 | 15,000 | 300,000 | 4,000 | Code review across all packages, architecture calls, unblocking the team |
| **Group C subtotal** | | **60** | | **620,000** | **8,267** | |

### 6.3 Adding up the kept work

| Group | Days | Cost (₹) | Cost (S$) |
|---|---:|---:|---:|
| A. Discovery & architecture | 18 | 222,000 | 2,960 |
| B. AI / RAG assistant + guardrails | 45 | 520,000 | 6,933 |
| C. PM + ongoing tech lead | 60 | 620,000 | 8,267 |
| **Total kept by Technical Director (Mahesh)** | **123** | **1,362,000** | **18,160** |

This is cell `H26` on the sheet. In words: of the 409 man-days in the full build, Mahesh (Technical Director) personally owns **123 days (30%)**, worth **₹1,362,000 (S$18,160)**.

### 6.4 The "New Cost" — what is left to pay the India team

Subtract Mahesh's kept work from the full build total:

| | Days | Cost (₹) | Cost (S$) |
|---|---:|---:|---:|
| Total software build (incl. 10% buffer) | 409 | 3,886,300 | 51,817 |
| Less: Technical Director (Mahesh) kept work (the six lines above) | 123 | 1,362,000 | 18,160 |
| **New Cost — payable to India team** | **286** | **2,524,300** | **33,657** |

This is the "New Cost" cell (`F27` = ₹2,524,300, `G27` = S$33,657) on the sheet. It is the amount of cash that actually leaves the venture to pay the outside team.

### 6.5 How the math works, in one line

> Full build (S$51,817) − Mahesh's own work (S$18,160) = **New Cost to pay out (S$33,657)**.

Mahesh's labour as Technical Director substitutes for ₹1,362,000 of contracted spend. That is the concrete value of keeping those six lines in-house rather than outsourcing them.

### 6.6 What the Technical Director (Mahesh) is personally signing up to deliver

In plain terms, by keeping these six lines Mahesh is committing to:

1. **Set the architecture** — decide the system design, data model, and integration points before anyone else starts building (12 days).
2. **Map the user journeys** — sketch how the officer, the control room, and the admin each move through the product (6 days).
3. **Build the AI assistant and its guardrails** — the prompts, the SOP retrieval, the safety rails, and the API layer that serves and logs every answer (45 days).
4. **Run the project** — stand-ups, sprint reviews, delivery tracking, keeping the India team unblocked (40 days).
5. **Review the code** — cross-package code review and architecture calls throughout the build (20 days).

That is 123 working days of Mahesh's time as Technical Director. At 21 working days a month (the sheet's assumption), it is roughly **six months of part-time Technical Director effort** spread across the build window — not six months full-time, because the PM and code-review days are interleaved with the rest of the team's work.

### 6.7 The one caveat to read before quoting the number

The "New Cost" of S$33,657 is the **software line only**. It does not include device prototyping, security reviews, patent filing, legal, cloud setup, contingency, or the Technical Director retainer. Those sit on the `4. One-off Build` sheet and are unaffected by which software lines the Technical Director keeps. The full one-off picture — including the retainer placeholder — is in §1 above.
