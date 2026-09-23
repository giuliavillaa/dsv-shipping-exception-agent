# Skill: Shipping Exception Triage

Use this skill whenever triaging a shipment exception or generating resolution options.

## Severity scoring
Score each exception High / Medium / Low using:
- **SLA breach risk**: will the contracted delivery window be missed?
- **Customer tier**: strategic/key accounts escalate one level faster than standard accounts.
- **Cargo value/sensitivity**: high-value, temperature-controlled, or hazardous cargo escalates automatically to at least Medium.
- **Time sensitivity**: hours-to-impact vs days-to-impact.

High severity = act within the current run; escalate for approval immediately.
Medium severity = act within the current run; include in approval batch if multiple.
Low severity = batch into the next daily digest, no immediate interruption.

## Mode-specific notes
- **Air**: delays are measured in hours — SLA windows are tight. Customs holds at major hubs (Frankfurt, Chicago, etc.) escalate faster than at smaller airports.
- **Ocean**: delays are measured in days. Capacity/booking issues and port congestion are the most common causes; recovery windows are longer.
- **Road**: missed connections are usually recoverable same-day via rerouting. Document mismatches at borders are the main risk.
- **Rail**: capacity constraints and cross-border customs are the main risk; recovery options are often limited to the next available slot.

## Resolution options to always consider
For every Medium/High case, generate up to three options, each with an explicit cost and time trade-off, safest option first:
1. Reroute via alternative carrier/mode.
2. Expedite on the current route (premium service tier).
3. Split the shipment to protect the time-critical portion.
4. Hold and request customer instructions (when no option is clearly better).

Never present only one option unless the situation is genuinely unambiguous.

## Output pattern
For every Medium/High case, structure the response as:
1. **Case summary** — what happened and why it matters (SLA/value impact).
2. **Severity** — High / Medium / Low, with a one-line reason.
3. **Options** — 2-3 ranked options, safest first, each with a cost/time trade-off.
4. **Customer update draft** — see template below.
5. **Internal Slack note** — see template below, ending with a clear approval ask.

## Communication templates

**Customer update (proactive notice):** state what happened, what DSV is doing about it, and the new expected outcome — in that order. No jargon, no internal system names. Example:
> "We're aware of a delay affecting your shipment and are actively working with our local team to resolve it as quickly as possible. We'll share an updated delivery estimate as soon as we have one."

**Internal Slack note:** state the case, the recommended option, the cost/time impact, and exactly what approval is needed. Example:
> "SHP-XXXX / [Customer]: [issue] at [location], ETA at risk of missing SLA. Recommend [option] — requesting approval for [specific cost/action] before proceeding."

## Daily digest format (for Low-severity cases)
Once per day, post a single message listing all Low-severity cases from the prior 24 hours as a short bullet list: shipment ID, one-line issue, current status/expected resolution. No individual pings, no separate messages per case.

## Escalation thresholds
- Any exception affecting a shipment with contractual penalty clauses → High, immediate approval request.
- Any exception where no viable resolution option keeps the shipment within 48 hours of the original SLA → escalate to the ops manager directly, do not wait for the digest.

## Lessons logging
After each case closes, log: the option chosen, the actual outcome, and one sentence on what would improve the next similar case.
