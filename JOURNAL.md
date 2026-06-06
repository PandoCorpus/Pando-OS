The Journal
A timestamped record of design decisions, wrong turns, and field research.

May 16, 2026 — The Pivot
This didn't start as an institutional memory system. It started much smaller: a clinical ambient intelligence box. A physical transcription tool to sit in a doctor's office, log a consultation, and extract medical details so the clinician could actually look at the patient instead of staring at a screen.

But the text wasn't the problem. The transcription layer is a commodity now.

The real problem hit me when I looked at what happens after the patient leaves. Where does that insight go? How does it connect to something the patient mentioned three visits ago? If that doctor leaves the clinic, does that hard-earned clinical intuition just evaporate?

A note is just text. It’s a snapshot. But expertise is a continuous, evolving belief state. I realized I didn't want to build a better filing cabinet for session notes. I wanted to build an architecture that models what a professional thinks is true, tracks how those hypotheses perform against real-world outcomes over time, and preserves that judgment so it doesn't walk out the door when someone changes jobs.

Moving away from the medical box concept. Expanding the scope. This isn't a tool; it’s an operating system for professional judgment.

May 30, 2026 — Confronting the Market (Brokers & Collisions)
I’ve been spending the last two weeks talking to mortgage brokers here in Sydney to ground the architecture in a hyper-regulated environment. ASIC’s Best Interests Duty (BID) review is live right now, so the compliance pain is top-of-mind for them.

My initial assumptions got thoroughly wrecked by reality:

Assumption 1: Voice transcription is the core input.

Reality: Wrong. A broker’s life is 90% email. Sensitive conversations happen on voice precisely because they don't want them recorded. The system has to be email-first.

Assumption 2: The value is in generating sleek executive reports.

Reality: Brokers don't care about pretty PDFs. They care about populating their aggregator's CRM with a bulletproof "reason why" trail to survive an audit. The output layer needs to feed their existing CRMs, not replace them.

Assumption 3: The pain is all in the initial loan origination.

Reality: Back-book management is a massive, leaking bucket. Systematically tracking existing clients to see if a better rate has opened up is an afterthought because they don't have the bandwidth. The lifecycle review has to be a core engine feature.

The Name Collision:
Ran into a major roadblock today. Discovered an open-source project that independently converged on my original name, my exact security posture (local-first), and even the same biological metaphor. It’s unsettling but validating.

The difference is intent: they are building a personal productivity assistant. I am building an institutional memory OS for heavily regulated, high-stakes verticals. The vision stands, but I need a new name. PandoCorpus is a temporary placeholder for now.

June 03, 2026 — The Epistemic Stack
Spent the night mapping out how the local graph database needs to treat data. Most AI applications treat all text tokens as equally weighted. That’s a fatal flaw for institutional memory. If a system updates its core values because a short-term statistical trend makes dishonesty look profitable, the system is corrupt.

The architecture needs three distinct authority layers, hardcoded into the schema:

Reality (Immutable Events): What actually happened. Raw emails, documents, closed files. Never deleted.

Interpretation (Hypotheses): What the system infers. Held with probabilistic confidence, never treated as absolute fact.

Wisdom (Human Commitments): Requires explicit human authority to change.

Within the Wisdom layer, I’m splitting beliefs into three distinct primitives:

Empirical Beliefs: Working hypotheses about borrower behavior or market trends. These are falsifiable and must update when reality proves them wrong.

Procedural Habits: How the firm executes tasks. These update when a more efficient workflow emerges.

Identity Commitments: "We never mislead a client to win a deal." This is non-falsifiable. It’s a choice of character, not a prediction. A competitor making money by cheating is not a reason for the system to optimize away our integrity.
