# Build Journal

*A dated log of how this project came to be, what changed, and why.*
*Author: Charles Hendra Kurniawan Kwee — © 2026 All rights reserved.*

---

## Why a journal?

Building in public is a credibility mechanism. Anyone can claim an idea. A timestamped log of decisions, corrections, and field research is harder to fake — and more valuable for the same reason.

I'm not logging this to show a clean story. I'm logging it because the real story — including the wrong turns — is the actual proof of work.

---

## Entry 001 — June 2026

**Where this started**

The first version of this idea was much smaller. I was thinking about a transcription tool for doctors — something that could listen to a consultation, extract the relevant clinical details, and surface them clearly so the practitioner could focus on the patient rather than the notes.

But the more I sat with that problem, the more I realized the transcription was the least interesting part. The interesting part was what happens to that information *after* the consultation. Does it connect to what the patient said three visits ago? Does it change the practitioner's understanding of a pattern they've been observing for months? Does it survive when the doctor changes roles?

That question — what happens to professional knowledge over time — is what this project is actually about.

**The first big shift: from transcription tool to memory system**

The early design was organized around sessions. Each session produced a note. The notes accumulated. That was the "memory."

But a note isn't a belief. A session isn't a decision. And a collection of session notes — however well-organized — doesn't tell you whether the practitioner's working hypothesis about this patient is still holding, or whether three recent outcomes should be causing a rethink.

I needed to model not just what happened, but what the practitioner currently *thinks* is true — and track whether reality is confirming or challenging that view.

**The second shift: from memory system to operating system**

Once I started modeling beliefs and their relationship to outcomes, I realized the problem was bigger than one profession. Every regulated professional has the same fundamental challenge: they accumulate judgment over time, their judgment needs to be traceable for compliance purposes, and the organization around them struggles to preserve that judgment when people move on.

The specific profession changes. The architecture doesn't.

That's when it became an OS — a generic core that any profession can specialize with the right configuration.

**What field research changed**

I spent time talking with actual mortgage brokers in Australia. Several things I assumed turned out to be wrong:

- I assumed voice transcription was the key input. It isn't — the broker's work is ~90% email. Voice is reserved for sensitive conversations that nobody wants recorded.
- I assumed the value was in generating reports. It's mostly in helping the broker populate their aggregator's CRM — specifically the "reasons why" reasoning trail that the Best Interests Duty (ASIC RG 273) requires.
- I assumed the broker's biggest pain was the initial loan origination. It's equally — possibly more — in the ongoing back-book management: systematically reviewing existing clients to see if a better deal has become available.

Each of these corrections changed the design. The input layer became email-first. The output layer became CRM-oriented. The lifecycle review cadence became a core feature rather than an afterthought.

**What I found when I went looking for competitors**

I found an open-source project that had independently converged on the same name, the same metaphor, and much of the same infrastructure philosophy. Same local-first architecture, same security posture, same mycelium metaphor, even a written "constitution."

That was both unsettling and validating. The infrastructure instincts were right enough that someone else arrived at them independently. But the product is completely different — they're building a personal productivity assistant; I'm building a professional memory OS for regulated verticals. The name needed to change. The vision didn't.

**Where the architecture landed**

The core design has three authority layers:
- **Reality**: what actually happened (immutable events, never deleted)
- **Interpretation**: what the system thinks it means (held with confidence, not treated as fact)
- **Wisdom**: what the entity believes and how it acts (requires human authority to change)

Within Wisdom, there are three types with different rules about what can change them:
- Empirical beliefs: learned from outcomes, should update when reality contradicts them
- Procedural habits: how we do things, updates when better methods emerge
- Identity commitments: what we've chosen to stand for, changes only by conscious decision — not by evidence alone

That last distinction took a while to get right. Most AI systems treat all beliefs as equivalent. But an organization's integrity shouldn't update because a competitor profits from dishonesty, and a working hypothesis about borrower behavior shouldn't be treated as a core value just because someone held it for a long time. The architecture had to handle both without conflating them.

**What I haven't figured out yet**

- The right name (the original collides with an existing project; working on it)
- The exact right cut of the Phase 0 build — thin enough to validate quickly, complete enough to produce the audit export the broker actually needs
- Whether to fork existing open-source infrastructure for the security layer or build fresh

More to come.

---

*Next entry: when I have the Phase 0 build spec locked and a design-partner broker confirmed.*

---

*Charles Hendra Kurniawan Kwee, June 2026*
