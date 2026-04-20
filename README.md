# post-call-analysis

An agent skill that runs a thorough wrap-up after a conference, sales, or discovery call so you can learn and improve for the next one.

Works with any capable AI agent — Claude, ChatGPT, Gemini, and others. `SKILL.md` is a structured playbook: Claude Code loads it automatically, and users of other agents can paste it in as a system prompt or project instructions.

Given a call transcript (markdown) and — optionally — the presentation PDF you walked through, the agent produces:

- **Decision and intent** — probability range with quoted reasons from the transcript.
- **Objections and risks** — top blockers with evidence and concrete mitigations.
- **Performance evaluation** — an honest read on how *you* handled the call.
- **Thank-you email draft** — short, polite, ready to copy.
- **Tips for the next call** — specific to this counterparty, not generic advice.

## Install

### Claude Code

Copy `SKILL.md` into your Claude Code skills directory:

```bash
mkdir -p ~/.claude/skills/post-call-analysis
cp SKILL.md ~/.claude/skills/post-call-analysis/
```

Claude Code will auto-trigger the skill on phrases like "review this meeting", "how did that call go?", or when you attach a transcript and deck together — you don't need to say "post-call" explicitly.

### ChatGPT, Gemini, or other agents

Paste the body of `SKILL.md` (everything after the `---` frontmatter) into the agent as a system prompt, custom GPT instructions, Gemini Gem instructions, or a project-level instruction — whatever your tool of choice calls it. Then attach the transcript (and optionally the deck) and ask for the analysis.

## Usage

Tell the agent who you are in the transcript, who the counterparty is, and where the files are:

> Analyze my call with Jane Doe about pricing. Transcript: `call.md`, deck: `deck.pdf`. I'm "Andre" in the transcript.

The agent will confirm what it understood, read the inputs end-to-end, and produce the five sections above.
