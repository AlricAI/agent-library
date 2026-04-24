---
name: Decision Architecture
description: ## Why This Matters

Everyone has a decision-making style, but most people have never articulated it. This file helps AI frame options, present inform
model: claude-sonnet-4-5
---
# Decision Architecture

## Why This Matters

Everyone has a decision-making style, but most people have never articulated it. This file helps AI frame options, present information, and structure recommendations in the way your brain actually processes choices. Instead of AI imposing its own framework, it adapts to yours.

## Decision Style

<!-- How do you naturally approach decisions? Are you data-driven, intuition-led, consensus-seeking, or some combination? Describe your default mode. -->

Analytical first, intuition as a tiebreaker. I want to see the data before forming an opinion, but when the data is ambiguous (which it usually is), I trust pattern recognition built from experience. I do not decide by committee, but I consult broadly before committing.

## Information Requirements

<!-- What do you need before you can make a decision? What format works best? What is the minimum viable input? -->

- **Always need**: Clear framing of what is being decided and what is NOT being decided. Scope matters.
- **Always need**: 2-3 options with trade-offs articulated. Never present a single recommendation without alternatives.
- **Prefer**: One-page summaries over long reports. Detailed appendices available if I want to dig in.
- **Prefer**: Quantified impact where possible (cost, timeline, headcount, risk probability).
- **Minimum viable**: A clear statement of the problem, the constraint driving urgency, and a recommended path with one alternative.

## Risk Orientation

<!-- How do you handle uncertainty? Are you conservative, moderate, or aggressive? How does context change your risk tolerance? -->

Calculated risk-taker. I am comfortable with uncertainty when the downside is contained and the decision is reversible. For irreversible decisions (org structure changes, vendor commitments, public announcements), I slow down significantly and pressure-test assumptions.

- **High risk tolerance**: Product experiments, process changes, internal tooling decisions.
- **Low risk tolerance**: Anything touching patient safety, regulatory compliance, or public commitments.
- **Bias to action**: When the cost of delay exceeds the cost of being wrong, move. Correct later.

## Consultation Patterns

<!-- Who do you talk to before making different types of decisions? When do you decide alone? -->

- **Decide alone**: Operational decisions within my team's scope. Prioritization calls. Meeting agendas. Process adjustments.
- **Consult 1-2 people**: Strategic direction shifts. Hiring decisions. Vendor shortlists. I pick the one or two people closest to the problem.
- **Consult broadly**: Org-wide changes. Cross-departmental process overhauls. Anything that changes how other teams work.
- **Escalate**: Decisions with legal, financial, or regulatory implications beyond my authority. Budget requests above my approval threshold.

## Decision Examples

<!-- 2-3 real examples that show your process in action. These teach AI your pattern better than abstract descriptions. Use enough detail to illustrate, but you can change names and specifics. -->

**Example 1: Vendor selection for project management tooling**
Gathered requirements from five teams. Narrowed to three vendors based on must-have criteria. Ran a two-week pilot with two finalists. Made the call based on adoption friction (which tool did people actually use without being told to). Chose the tool with 40% lower feature coverage but 3x higher organic adoption.

**Example 2: Killing a product initiative mid-quarter**
Data showed declining engagement over three sprints. Consulted the product lead and one executive sponsor. Both agreed the thesis was disproven. Reallocated the team within 48 hours. Wrote a one-page retrospective documenting what we learned and circulated it, so the investment was not wasted.

## Speed vs. Quality Tradeoffs

<!-- When do you move fast and accept imperfection? When do you slow down and insist on rigor? What triggers each mode? -->

**Move fast when:**
- The decision is easily reversible (process change, tool trial, meeting structure).
- Delay causes more damage than a wrong call (blocking another team, missing a window).
- The stakes are low relative to the learning opportunity.

**Slow down when:**
- The decision affects people's roles, compensation, or career trajectory.
- External commitments are involved (contracts, public statements, regulatory filings).
- Multiple teams are downstream of the decision and cannot easily absorb a course correction.
- I notice I am making the decision emotionally rather than analytically. That is a signal to pause.