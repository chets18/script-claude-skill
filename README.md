# 🎬 Script Pattern Analyzer — Claude Skill

A Claude skill that reverse-engineers what makes great YouTube scripts work. Feed it a transcript; get back a structured pattern sheet you can reuse in your own writing — without copying a single line.

## What It Does

This skill turns a spoken YouTube transcript into a reusable **pattern file** covering:

| Section | What You Get |
|---|---|
| **Hook Formula** | Opening move, promise, payoff location, and the mechanism that makes it work |
| **Spoken Voice** | Sentence-length stats, filler counts, marker frequencies, contraction ratios |
| **Word-Choice Habits** | Specific word picks vs. obvious alternatives, with reasons each one lands |
| **Personality Moves** | Where the speaker admits being wrong, surprised, or uncertain — with quotes |
| **Humor & Fact Delivery** | Every joke technique and how each hard number is made tangible |
| **Structure Map** | Segment breakdown with % runtime, re-hook locations, ending type |
| **Rules for the Script AI** | 8–10 evidence-backed, copy-pasteable instructions for writing a new script |
| **Do Not Copy** | Things that only work for *this* creator and shouldn't be imitated |

## How It Works

```
transcript (spoken)  ──▶  prompt_used  ──▶  pattern file (structured)
```

1. **Input** — Drop a raw YouTube transcript (with timestamps) into `script/<channel>/`.
2. **Analyze** — Run the prompt from [`Readme/prompt_used`](Readme/prompt_used) against the transcript in Claude.
3. **Output** — The resulting pattern file lands in `pattern/<channel>/` with the same filename.

Every claim in the pattern file must be backed by a **quoted excerpt** (≤ 12 words) and a timestamp. Adjective-only observations like "engaging" or "compelling" are banned unless the exact mechanism is explained.

## Project Structure

```
script-claude-skill/
├── README.md
├── Readme/
│   ├── prompt_used          # The master analysis prompt
│   └── SKILL.md             # Claude skill definition
├── script/                  # Raw transcripts (input)
│   ├── varitasium/
│   │   ├── fiber_optics.txt
│   │   └── engnima.txt
│   ├── cleo/
│   │   ├── nuralink.txt
│   │   └── sun-wedier.txt
│   ├── Kurzgesagt/
│   │   └── AI-Out.txt
│   └── out/
│       └── disgusting_influncer.txt
├── pattern/                 # Extracted patterns (output)
│   ├── varitasium/
│   │   ├── fiber_optics.txt
│   │   └── engnima.txt
│   ├── cleo/
│   │   ├── nuralink.txt
│   │   └── sun-wedier.txt
│   ├── Kurzgesagt/
│   │   └── AI-Out.txt
│   └── out/
│       └── disgusting_influncer.txt
```

## Channels Analyzed So Far

- **Veritasium** — Fiber Optics, Enigma Machine
- **Cleo Abram** — Neuralink, Sun Weather
- **Kurzgesagt** — AI Out
- **Other** — Disgusting Influencer (investigative)

## Quick Start

1. Get a YouTube transcript (auto-captions or manual) and save it to `script/<channel>/<topic>.txt`.
2. Open Claude and paste the prompt from `Readme/prompt_used`.
3. Attach or paste the transcript.
4. Save Claude's output to `pattern/<channel>/<topic>.txt`.
5. Use the **"Rules for the Script AI"** section from the pattern file when writing your next script.

## Why This Exists

Most "how to write like X" advice is vague — *"be conversational," "hook the viewer."* This skill forces Claude to be specific: counts per minute, quoted evidence, named techniques. The result is a pattern library you can query across creators to find what actually works — and what's creator-specific fluff you shouldn't imitate.

## License

MIT

