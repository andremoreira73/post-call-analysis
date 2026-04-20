# post-call-analysis

A Claude Code skill that runs a thorough wrap-up after a conference, sales, or discovery call so you can learn and improve for the next one.

Given a call transcript (markdown) and — optionally — the presentation PDF you walked through, it produces:

- **Decision and intent** — probability range with quoted reasons from the transcript.
- **Objections and risks** — top blockers with evidence and concrete mitigations.
- **Performance evaluation** — an honest read on how *you* handled the call.
- **Thank-you email draft** — short, polite, ready to copy.
- **Tips for the next call** — specific to this counterparty, not generic advice.

## Install

Copy the `SKILL.md` into your Claude Code skills directory:

```bash
mkdir -p ~/.claude/skills/post-call-analysis
cp SKILL.md ~/.claude/skills/post-call-analysis/
```

The skill triggers on phrases like "review this meeting", "how did that call go?", or when you attach a transcript and deck together — you don't need to say "post-call" explicitly.

## Usage

Point Claude at your transcript (and optionally your deck) and tell it who you are in the transcript:

> Analyze my call with Jane Doe about pricing at `/tmp/call.md`, deck at `/tmp/deck.pdf`. I'm "Andre" in the transcript.

The skill will confirm what it understood, read the inputs end-to-end, and produce the five sections above.
