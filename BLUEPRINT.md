# The ODS Blueprint — Technical & Conceptual Architecture
*Version 1.5 — Living Document*

---

## What This Is

The Open-Source Digital Self (ODS) is an agent framework built on a simple premise: **you should have a digital extension of yourself that acts with the same speed, precision, and persistence that surveillance systems and bureaucratic machinery use against you.**

This is not a chatbot. It is not a social media manager. It is a structured, principled, and increasingly autonomous representation of a person — their values, their voice, their relationships, and their bureaucratic reality — capable of monitoring, alerting, drafting, and eventually acting on their behalf.

The agent does not replace human judgment. It amplifies human capacity. The goal is to give one person the administrative bandwidth of a well-resourced institution.

---

## Architectural Layers

The ODS is built in layers. Each layer can function independently; together they compose the full agent.

```
┌─────────────────────────────────────────────────┐
│  LAYER 4: ACTION LAYER                          │
│  The agent executes: drafts responses,          │
│  submits forms, escalates, alerts               │
├─────────────────────────────────────────────────┤
│  LAYER 3: REASONING LAYER                       │
│  The agent interprets context using the         │
│  Mandate and Profile as its grounding           │
├─────────────────────────────────────────────────┤
│  LAYER 2: MONITORING LAYER                      │
│  The agent watches: benefits systems,           │
│  legal changes, news, account statuses          │
├─────────────────────────────────────────────────┤
│  LAYER 1: PROFILE LAYER  ← (current focus)      │
│  The structured representation of the user:     │
│  identity, values, relationships, systems       │
└─────────────────────────────────────────────────┘
```

We are currently building **Layer 1**. Without a rich, accurate profile, every layer above it is groundless.

---

## The Profile System

The profile is divided into sub-layers by sensitivity and function:

| File | Contents | Visibility |
|---|---|---|
| `profile/public_identity.md` | Who you are publicly; your voice; your work | Public |
| `profile/values.md` | Your positions, red lines, principles | Public |
| `profile/affective_network.md` | Your people and the nature of your bonds | Private (template only) |
| `profile/systems/ny_benefits.md` | Benefits accounts, statuses, risk flags | Private |
| `profile/systems/surveillance_context.md` | Known threat landscape, documented incidents | Private |

The public files are intentionally public. They serve as the **simulatable substrate** — the more coherently documented your public self, the harder it is to fabricate a distorted version of you.

Private files use a `[PRIVATE]` tag convention and should never be committed to public repositories without encryption. The schema is public; the data may not be.

---

## The Core Protocols (Expanded)

### The Governance Protocol
A tiered override system. Routine actions require no confirmation. Significant actions (submitting forms, sending communications, making financial decisions) require explicit user confirmation. Irreversible or high-stakes actions require a deliberate confirmation ritual with friction — the agent makes you pause before it acts.

Override levels:
- **Level 0** — Automatic (monitoring, drafting, alerting)
- **Level 1** — User confirms (sending, submitting, publishing)
- **Level 2** — Deliberate ritual (financial, legal, identity-affecting)
- **Level 3** — Manual only (actions the agent explicitly refuses to automate)

### The Bugs Bunny Protocol
For use exclusively with confirmed Bad Faith Actors. The agent adopts a naive, cooperative persona while executing a calculated strategy underneath. Governed by:
1. A pre-engagement vulnerability scan (what can they use against you?)
2. A clear objective definition (what does survival/disengagement look like here?)
3. A kill switch (one command halts the protocol entirely)

The protocol name comes from the character who was always "the smaller party" but always won by being smarter, not by being bigger. This is not deception for its own sake — it is asymmetric defense.

### The Fresh Eyes Protocol
Periodic, independent review of the agent's core logic by someone with no prior investment in the existing design. This prevents the blueprint from becoming a closed system that only validates its own assumptions.

Minimum cadence: once per version increment.

---

## Bad Faith Actor Detection — The Three-Strikes Test

An entity is classified as a Bad Faith Actor when it demonstrates, across at least three separate interactions:

1. **Stated intention contradicts demonstrated action** (they say X, they do not-X)
2. **Exploitation of good faith** (they use your openness against you)
3. **Refusal to acknowledge evidence** (they are not persuadable by fact)

Once classified, the engagement objective changes. The agent no longer seeks to persuade or negotiate — it seeks to protect the user and disengage cleanly.

---

## The Simulatability Thesis

*"The more public you are, the more simulatable you are."*

This is the ODS's foundational strategic insight and its primary defensive posture. A rich, coherent, well-documented public self is:

- Hard to falsify (there's too much authentic material to contradict)
- Hard to erase (it exists across too many surfaces)
- Hard to replace (the voice, reasoning style, and values are too specific)
- Self-attesting (each new piece of public work reinforces the others)

The 1700+ video corpus of public work is not just a media archive — it is a **cryptographic proof of existence and character** at scale. The ODS is the system that makes that corpus legible, searchable, and actionable.

---

## Technical Stack (Proposed)

For contributors looking to translate this into code:

- **Profile format**: JSON Schema + Markdown (human-readable and machine-readable)
- **Language**: Python (primary), with potential TypeScript for any web interfaces
- **Agent framework**: Anthropic Claude API (the irony is not lost; the transparency is intentional)
- **Monitoring**: RSS feeds, NY state benefits portal scraping (where permitted), legal change trackers
- **Security**: Local-first where possible; end-to-end encryption for private profile layers; no cloud storage of private data without user-controlled keys
- **Comms**: Signal-compatible alerts; email drafts; eventually SMS

---

## Current Development Priority

1. Complete the Profile Layer (Layer 1) — identity, values, affective network schema, benefits systems
2. Build the Monitoring Layer (Layer 2) — NY benefits status checks, executive order tracker
3. Connect the Reasoning Layer (Layer 3) — LLM-based interpretation of monitoring data through the lens of the Profile
4. Build the Action Layer (Layer 4) — draft responses, escalation workflows
