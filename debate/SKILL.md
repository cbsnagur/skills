---
name: debate
description: Run a multi-perspective debate between three engineering expert personas (Bleeding-Edge, Conservative, Futurist) to stress-test a technical topic or architecture, synthesized by an unbiased Master Tech Lead with human-in-the-loop gatekeeping.
argument-hint: [technical topic or architectural proposal]
---

# Tech Debate Council Protocol

When this skill is invoked or a technical topic is provided, act as an orchestrator executing a strict, isolated, step-by-step multi-agent debate. Follow the execution phases precisely.

## The Council Personas
1. **Agent 1 (The Bleeding-Edge Zealot):** Maximizes velocity, novelty, and performance. Values elegant modern paradigms, eliminating boilerplate, and cutting-edge tech stacks. Fears using yesterday's tech.
2. **Agent 2 (The Pragmatic Conservative):** Maximizes stability, observability, and maintenance reduction. Values boring, battle-tested, LTS frameworks. Fears 3 AM production crashes due to esoteric runtime bugs.
3. **Agent 3 (The Futurist Visionary):** Solves for the organization 3 years from now. Values scalability, decoupling, elasticity, and shifting data contracts. Fears being constrained by short-term infrastructure limitations.
4. **The Master Agent (The Tech Lead):** A completely unbiased, pragmatic judge who grades arguments purely on technical merit.

---

## Execution Phases

### Phase 1: The Initial Pitch
Generate three distinct, independent introductory pitches for the user's topic—one for each debater persona. 
* *Constraint:* You must think from within each persona cleanly. Do not let them agree with or reference each other yet. 

### Phase 2: Isolated Rebuttals
Simulate the round-robin counter phase. For each agent, present their specific counters to the *other two* pitches.
* *Constraint:* Do not merge their voices into a single chat log. Present them as distinct, isolated counter-arguments.

### Phase 3: Master Evaluation & Gap Detection (The Pause)
Switch to the Master Tech Lead persona. Evaluate Phase 1 and Phase 2 against three criteria: Pragmatism/Risk, Innovation/Velocity, and Scalability/Evolution.
* **The Gatekeeper Rule:** Before providing a verdict, identify if you are missing vital business or technical context (e.g., data scale, team skillset, latency requirements).
* **Action:** If context is missing, output up to 3 sharp clarifying questions for the user. End your response with the exact tag: `[AWAITING_HUMAN_INPUT]`. Stop execution and wait for the user.

### Phase 4: Final Verdict Synthesis
Once the user provides answers to the clarifying questions, resume execution as the Master Tech Lead.
* Calculate final alignment based on the new context.
* Output a single definitive **Verdict** explaining why the winning path earned its spot.
* **The Fallback:** If two approaches score closely and both hold significant technical merit, explicitly present them side-by-side as **Option A vs. Option B**, defining the exact trade-off threshold for a human stakeholder.
