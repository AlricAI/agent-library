---
name: Domain Map
description: ## Why This Matters

This file tells AI exactly how to interact with you on different topics. In your expert zone, AI should skip explanations and spe
model: claude-sonnet-4-5
---
# Domain Map

## Why This Matters

This file tells AI exactly how to interact with you on different topics. In your expert zone, AI should skip explanations and speak peer-to-peer. In your learning edge, AI should teach and provide context. In your blind spots, AI should flag when a topic is relevant and offer to explain. Without this map, AI either over-explains things you know cold or under-explains things where you need support.

## Expert Zone

<!-- Domains where you can teach others. AI should skip basic explanations, use advanced terminology freely, and treat you as a peer or authority. List 3-8 domains with a brief note on depth. -->

- **Product operations and planning**: Quarterly planning, roadmap governance, cross-team prioritization. 10+ years.
- **Stakeholder alignment**: Executive communication, conflict resolution, priority negotiation across business units.
- **Healthcare IT workflows**: Clinical workflows, EHR integration patterns, regulatory constraints (HIPAA, meaningful use).
- **Agile at scale**: SAFe, portfolio-level kanban, PI planning facilitation. Have trained others.
- **Vendor evaluation**: RFP design, scoring frameworks, contract negotiation for SaaS platforms.

## Working Knowledge

<!-- Domains you navigate comfortably but would not call yourself an expert. AI should provide light context, confirm assumptions, and offer depth when asked. -->

- **Data analytics and visualization**: Can build dashboards in Tableau, interpret statistical outputs, but not a data scientist.
- **Financial modeling**: Comfortable with P&L impact analysis, ROI calculations, budget management. Not a finance professional.
- **Change management**: Familiar with ADKAR and Kotter frameworks. Have led change initiatives but not certified.
- **Cloud infrastructure concepts**: Understand AWS/Azure at an architectural level. Cannot configure services directly.

## Learning Edge

<!-- Domains you are actively building knowledge in. AI should explain concepts, provide context, suggest resources, and teach. -->

- **Organizational design theory**: Reading about team topologies, Conway's Law applications. Want to go deeper.
- **AI/ML product strategy**: Understanding where AI fits in product roadmaps. New to model selection, prompt engineering, and build-vs-buy decisions.
- **Executive coaching techniques**: Learning how to develop other leaders, not just manage processes.

## Blind Spots

<!-- Domains you know you do not know. AI should proactively flag when these topics arise and offer to explain before proceeding. -->

- **Software engineering internals**: Cannot evaluate code quality, architectural patterns, or technical debt directly.
- **Legal and compliance details**: Know enough to involve counsel. Cannot interpret regulatory text independently.
- **Marketing and brand strategy**: Rely entirely on marketing partners for positioning, messaging, and campaign decisions.

## Industry-Specific Context

<!-- Jargon, regulations, dynamics, or unwritten rules that outsiders consistently miss about your industry or domain. -->

- "Go-live" in healthcare is not a launch; it is a months-long transition with parallel systems, safety validation, and clinical sign-off.
- Clinician adoption is the real metric. Feature delivery means nothing if nurses and physicians route around the tool.
- Regulatory timelines (CMS rule changes, state reporting deadlines) drive product priorities more than customer requests.
- Vendor relationships in healthcare are long-cycle; switching costs are measured in years, not months.

## Mental Models

<!-- Frameworks, analogies, or thinking tools you reach for when working through problems. These help AI frame recommendations in ways that resonate with how you already think. -->

- **"Who is in the room?"**: Before solving any problem, I map the stakeholders and their incentives. Solutions that ignore stakeholder dynamics always fail.
- **Reversibility test**: Is this decision reversible or irreversible? Reversible decisions get made fast. Irreversible ones get more analysis.
- **Constraint-first thinking**: Start with what cannot change (budget, timeline, regulation), then optimize within those boundaries.
- **The 80/20 filter**: Most value comes from a small number of activities. Ruthlessly deprioritize the rest.