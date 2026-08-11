You are helping me draft a rough build cost estimate for a new security-wearable venture I am joining as Technical Director on retainer. The estimate goes to my two co-founders Dexter and Siva. They are commercial operators from the security-agency world, not technical, but they read numbers well. This is an internal working document, not a fundraising deck. Deliver it as a single .md file.

Apply my bertie-voice skill throughout: so-what first, causality over chronology, British business English, short declarative sentences, no American ChatGPT register. Numbers first, commentary second.

## Venture context

Dexter and Siva run a security services business (CIS) in Singapore. We are forming a new Pte Ltd — separate from CIS — to build a wrist-worn AI wearable for security officers, sold on subscription. CIS is the first design partner and early customer.

Locked design and commercial decisions from the 21 July MoM:
- Wrist-worn, watch form factor
- GPS built in, simple camera, cellular SIM only (no WiFi)
- Unit cost target SGD 20–30, hard ceiling SGD 100
- Subscription model, device recyclable across officers when they leave the agency
- SIMs bundled through the venture. Dexter currently runs ~100 SIMs at SGD 8 per month (400GB) via SimTel; volume target on 400+ SIMs is SGD 5–6
- Voice payload is small (KB, not GB), so data plans stay light
- Software scope minimalist: 5–6 emergency prompts per scenario, incident report auto-generation, deeper SOP queries on demand
- Three journeys to build: officer wrist, control room console, administrator back-end
- PDPA-compliant, Singapore-hosted cloud
- Manufacturing in India or Shenzhen. Minimum 3–4 year supplier continuity
- Patent filing in India. Budget SGD 5,000. My prior filing cost SGD 3,000
- Rollout target: 3–4 months
- Design partner: CIS. First deployment volume assumption to model at: 100 devices, scaling to 500 within 12 months

## What I need the estimate to do

The estimate has to answer three questions Dexter and Siva will ask:

1. How much cash do we need to put in before we earn a rupee — the one-off spend
2. What does each device cost us per month once we are running — the recurring per-device cost
3. At what subscription price and volume do we break even, and how quickly

Everything else is commentary around those three numbers.

## Structure

Build the estimate in five sections.

**Section 1: One-off build costs.** Everything we spend before the first paying deployment. Split into:
- Software build (three journeys, model integration, guardrails, incident-report generator, admin back-end)
- Device prototyping (design fees, first batch of prototype units, testing)
- Patent filing in India (agent fees, government fees, translation if any)
- Company incorporation and legal (Pte Ltd setup, NDA, retainer agreement, standard commercial contracts)
- My retainer for the build period (assume 3–4 months at a Technical Director retainer level — leave the monthly figure as a placeholder for me to fill in, but show the total line)
- Cloud and infrastructure setup (initial PDPA-compliant environment, not per-device run cost)
- Contingency (15%)

Present as a table with a low estimate, a likely estimate, and a high estimate per line item, and a total row for each column.

**Section 2: Recurring per-device monthly cost.** What it costs us to keep one wrist on one officer for one month. Include:
- Hardware amortisation (unit cost divided over a realistic device life — assume 24 months, note the assumption)
- SIM and connectivity (use the SGD 5–6 volume target, note the SGD 8 fallback)
- Cloud hosting per device (storage, compute, PDPA overhead)
- Model inference per device (assume moderate query volume — a handful of emergency prompts per shift plus occasional SOP queries)
- Platform maintenance allocation (a share of ongoing engineering and support divided across the device fleet — this shrinks per device as volume grows, so show it at 100, 500 and 1,000 device fleets)

Present as a table. Show per-device monthly cost at three fleet sizes: 100, 500, 1,000. The per-device cost should fall as fleet grows because platform maintenance amortises.

**Section 3: Subscription pricing and break-even.** Given the per-device monthly cost at each fleet size, work out:
- What subscription price gives us a 50% gross margin at each fleet size
- What subscription price gives us a 70% gross margin at each fleet size
- Break-even month, assuming CIS deploys 100 devices at M4 and we scale to 500 by M12
- Cumulative cash position at M4, M6, M9 and M12

State the pricing assumption clearly: this is what the venture charges the agency per device per month, not what the end client pays.

**Section 4: Sensitivity — the three numbers that move the answer most.** Not a long list. The three or four inputs where a small change swings the model materially:
- Unit hardware cost (SGD 30 vs SGD 60 vs SGD 100)
- SIM price (SGD 5 vs SGD 8)
- Fleet ramp speed (500 by M12 vs 500 by M18)
- Model inference cost (assume a plausible band)

Show what happens to break-even month under each swing.

**Section 5: What I have assumed and what I do not know yet.** A short prose section — not a table. Call out the assumptions that most need Dexter and Siva to challenge or confirm. Examples: device life, average query volume per officer per shift, how many officers per site, whether CIS pays the venture the same rate as external agencies or gets design-partner pricing.

## Tone and format rules

- Markdown, sparing. Tables in Sections 1, 2, 3 and 4. Prose elsewhere.
- All figures in SGD. Convert INR or USD sourcing costs at a stated rate, and state the rate.
- Round to sensible figures — SGD 4,500 not SGD 4,487
- No emoji, no filler, no "in conclusion", no "I hope this helps"
- British English throughout
- Address Dexter and Siva as "we"
- Do not restate the MoM. Start from numbers and go forward.
- Where a figure is genuinely a guess, mark it (guess) inline. Do not pretend precision we do not have.

Produce the full .md now.