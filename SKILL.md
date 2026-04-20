---
name: post-call-analysis
description: Runs a thorough post-call wrap-up analysis after a conference/sales/discovery call so the user can learn and improve for the next one. Takes a call transcript (markdown) plus an optional presentation PDF and produces (a) decision-intent read with probability range and quoted reasons, (b) top objections and risks with mitigations, (c) evaluation of the user's own performance, (d) a short polite thank-you email draft, and (e) tips for the next call. Use this skill whenever the user mentions debriefing, wrapping up, analyzing, reviewing, or learning from a call, meeting, or pitch — especially when they reference a transcript file, want to draft a follow-up email, or ask "how did that call go?" Trigger even if the user doesn't say "post-call" explicitly — phrases like "review this meeting", "what should my follow-up look like", "read the transcript and tell me what they're really thinking", or attaching a transcript + deck together are all signals.
---

# Post-call analysis

Help the user do an honest, useful wrap-up of a call they ran, so they can learn from it and move the relationship forward. This is an internal exercise — the user is trying to see themselves and the counterparty clearly, not generate marketing copy.

## Step 1 — Make sure you have the four things you need

You need four pieces of information before analyzing. **First check what the user already provided** in their initial message — if everything is there, don't ask anything; just acknowledge what you got and move on. Only ask about the pieces that are genuinely missing.

The four pieces:

1. **Counterparty name** — the person (or lead contact) on the other side of the call. Needed so the output reads naturally and the email has the right salutation.
2. **Topic** — one line: what the call was about (e.g. "discovery call about agent orchestration for their support team").
3. **The user's own name in the transcript** — transcripts often use speaker labels like "Andre:" or "A.M.:". You need this to tell whose lines to evaluate in part (c).
4. **File locations** — the path(s):
   - Transcript (markdown) — **required**.
   - Presentation the user walked through (PDF) — **optional**. If provided, it anchors what the user *intended* to convey versus what actually landed.

**How to handle this in practice:**

- If the user's opening message gives you all four (e.g. "Analyze my call with Jane Doe about pricing at /tmp/call.md, deck at /tmp/deck.pdf, I'm 'Andre' in the transcript") — do **not** ask clarifying questions. Just confirm in one line what you understood ("Got it — analyzing your call with Jane Doe about pricing, you're 'Andre' in the transcript, reading both files now") and proceed.
- If some pieces are missing, ask only for those, in a single message. Don't re-ask for things already given.
- If you're genuinely uncertain about one of the fields (e.g. the user wrote "my call with the ACME folks" — is that the company or the specific contact?), flag it and ask for that one field only.

**Always do this sanity check before analyzing** (regardless of whether you had to ask): read the first ~30 lines of the transcript and confirm the counterparty name and the user's speaker label both actually appear. If they don't — wrong file, different speakers, different topic — surface the mismatch before spending tokens on a full analysis of the wrong call. This check is a silent safety net; only bring it up if something is actually off.

## Step 2 — Read the inputs fully

- Read the transcript end-to-end. Don't skim — the subtext (hedges, topic changes, who talks more near the end, what questions get dodged) is usually where the real signal is.
- If a PDF is provided, read it too. Use it as the "intended narrative" benchmark — what slides got skipped, glossed over, or challenged tells you what resonated and what didn't.

## Step 3 — Produce the analysis

Output the five sections below in order, using these exact headings. Be thorough in the analysis but concise in the writing — no filler, no restating the prompt. Quotes must be verbatim from the transcript.

### a) Decision and intent (read between the lines)

What does `<name>` likely want? What are their concerns? How likely are they to decide in the user's favor?

- Give a **probability range** as a percentage, e.g. "35–55%". A range, not a point estimate — signals the uncertainty honestly. Narrow ranges (±10%) mean strong signal; wider ranges (±25%) mean the transcript is genuinely ambiguous.
- Give **3 reasons** for that range, each anchored in a **short verbatim quote** from the transcript with the speaker label. Mix positive and negative signal if the call was mixed — don't pick three reasons that all point the same way unless the call really was that one-sided.
- Read between the lines: hedges ("we'd need to check with…"), deflections, who pushes back vs. who defers, changes in tone, what they ask about vs. what they don't.

### b) Objections and risks

The **top 3** risks or deal blockers, each with:
- **What it is** — one sentence.
- **Evidence** — a quote or specific moment from the call.
- **How to address it** — concrete next action (a follow-up artifact, a stakeholder to bring in, a reframe to try). Not platitudes.

If there are genuinely only one or two real risks, say so — don't manufacture a third.

### c) Performance evaluation (the user's lines)

Honest assessment of how the user (`<my name>` in the transcript) handled the call. Cover:
- **Effectiveness** — did they advance the deal/relationship? Where specifically?
- **Answer quality** — were responses crisp, evasive, too long, off-target? Cite examples.
- **Engagement and presence** — who was driving? Did the user listen or talk past the counterparty? Any moments of real connection or missed cues?
- **What they did well** — specific moments worth repeating.
- **What to tighten** — specific, actionable, no generic advice like "be more confident".

Be candid. The user is doing this to improve, not to feel good. Flattery wastes their time.

### d) Thank-you email draft

A **short, polite** email the user can send to `<name>` now. Keep it:
- Under ~120 words.
- Warm but not effusive.
- Includes a one-or-two-sentence summary of what was discussed and any clear next step that came out of the call.
- No hard sell. No pasted bullet lists. No "circling back". Sounds like a human wrote it.
- Subject line included.
- Match the tone of how the user spoke in the transcript — if they were formal, the email is formal; if they were casual, it is too.

Format it as a ready-to-copy block (Subject + body).

### e) Tips for the next call with `<name>`

3–5 concrete lessons for the next conversation with this specific counterparty. Anchor each one in something from *this* call, not generic sales advice. Examples of useful tips:
- "They went quiet when you mentioned pricing — prepare a pricing frame that leads with value, not numbers."
- "They asked twice about integration with X — have a one-page technical answer ready."
- "Your best moments were when you told the story about Y — use more concrete customer examples."

### Additional observations (optional)

If there's something important that doesn't fit the five sections — a stakeholder you didn't know was influential, a competitor mentioned in passing, a timing constraint — add it here. Skip this section if you have nothing meaningful to add; don't pad.

## Tone and style

- Concise, direct, specific. The user explicitly wants "thorough in analysis, concise in answer".
- Prefer quotes over paraphrase when citing the transcript — quotes are falsifiable; paraphrase isn't.
- Don't hedge the assessment out of politeness. If the call went poorly, say so and explain why. If it went well, say that too — don't manufacture problems.
- Don't invent facts. If the transcript doesn't support a claim, don't make it. "The transcript doesn't show enough signal on X" is a valid answer.
