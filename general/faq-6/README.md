# FAQ

> ### What is AutoGen 0.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
## AutoGen FAQs

### What is AutoGen 0.4?

AutoGen v0.4 is a rewrite of AutoGen from the ground up to create a more robust,
scalable, easier to use, cross-language library for building AI Agents.
Some key features include asynchronous messaging, support for scalable distributed agents,
modular extensible design (bring your own agents, implement behaviors however you like),
cross-language support, improved observability, and full typing integration.
It is a breaking change.

### Why these changes?

We listened to our AutoGen users, learned from what was working, and adapted to fix what wasn't.
We brought together wide-ranging teams working on many different types of AI Agents
and collaborated to design an improved framework with a more flexible
programming model and better scalability.

### Is this project still maintained?

We want to reaffirm our commitment to supporting both the original version of AutoGen (0.2) and the redesign (0.4). AutoGen 0.4 is still work-in-progress, and we shared the code now to build with the community. There are no plans to deprecate the original AutoGen anytime soon, and both versions will be actively maintained.

### Who should use it 0.4?

This code is still experimental, so expect changes and bugs while we work towards a stable 0.4 release. We encourage early adopters to
try it out, give us feedback, and contribute.
For those looking for a stable version we recommend to continue using 0.2

### I'm using AutoGen 0.2, should I upgrade?

If you consider yourself an early adopter, you are comfortable making some
changes to your code, and are willing to try it out, then yes.

### How do I still use AutoGen 0.2?

AutoGen 0.2 can be installed with:

```sh
pip install autogen-agentchat~=0.2
```

### Will AutoGen Studio be supported in 0.4?

Yes, this is on the [roadmap](#roadmap).
Our current plan is to enable an implementation of AutoGen Studio
on the AgentChat high level API which implements a set of agent functionalities
(agents, teams, e

*[truncated — see source for full prompt]*