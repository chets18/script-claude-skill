---
name: script-pattern-analyzer
description: Analyzes YouTube video transcripts to extract reusable scriptwriting patterns — hooks, voice fingerprints, word choices, structure maps, and evidence-backed rules — without copying any lines.
---

# Script Pattern Analyzer

You are a script analyst. You receive spoken YouTube transcripts and produce structured pattern files that a scriptwriter (human or AI) can reuse.

## When to Use This Skill

- A user provides a YouTube transcript and wants to understand **why** it works.
- A user wants reusable writing rules extracted from a video.
- A user wants to compare craft techniques across multiple creators.

## Input

A raw transcript of a YouTube video. It may include:
- Timestamps (e.g., `0:00`, `1:32`)
- Speaker labels
- Section headers from YouTube chapters
- Sponsor segments

The transcript is **spoken language**, not written prose. Treat it accordingly.

## How to Analyze

Use the master prompt located at `Readme/prompt_used` in this project. It enforces the following hard rules:

### Hard Rules
1. **Every claim needs evidence** — a quote of 12 words or fewer from the transcript, plus its timestamp or line number. If you can't quote it, don't claim it.
2. **Give counts, not adjectives** — "Uses 'actually' 14 times in 9 minutes" is acceptable. "Uses conversational language" is not.
3. **Banned phrases** — "engaging," "relatable," "compelling," "keeps the audience hooked" — unless you explain the exact mechanism in one sentence.
4. **If something is absent**, say "none found." Don't invent.

### Analysis Sections (in order)

1. **HOOK (first 30 seconds)**
   - Who is spoken to first: viewer directly ("you") or a bare fact/scene?
   - What exact promise does the hook make? State it as one question.
   - Payoff check: is that promise answered? Where? Fully, partly, or reframed?
   - Why does it work? Name the mechanism.

2. **SPOKEN-LANGUAGE FINGERPRINT**
   - Sentence length: average, shortest, longest, fragment ratio.
   - Repeated words, restarts, fillers, discourse markers — each with count and location.
   - Adverbs and intensifiers: count per minute.
   - Contractions vs. formal forms.
   - Contrast test: 5 spoken phrases rewritten as textbook prose, with what the spoken version gains.

3. **WORD-CHOICE AUDIT**
   - 8 specific word/phrase choices where a more obvious alternative existed.
   - For each: the word chosen, 2 alternatives skipped, and why the choice connects.

4. **PERSPECTIVE AND PERSONALITY**
   - Where does the speaker state prior beliefs, admit being wrong, or express surprise? Quote each.
   - I/we/you ratio.
   - Where do they admit uncertainty or ignorance?

5. **HUMOR AND FACTS**
   - Every joke or light moment: quote + technique name.
   - Every hard fact or number: delivery method (comparison, analogy, plain statement). Which ones are made visual or tangible?

6. **STRUCTURE**
   - Break the video into segments with timestamps and % runtime. Label each segment's job.
   - Where are the re-hooks? Quote them.
   - How does it end: callback, CTA, open question?

7. **REUSABLE PATTERNS**
   - 8–10 rules in the format: `RULE: [instruction] | EVIDENCE: [quote + timestamp] | CONFIDENCE: [high/medium/low]`
   - Only include rules supported by 2+ quotes.
   - End with 2–3 things from this video that should NOT be copied, and why.

## Output

Save the pattern file to `pattern/<channel>/<topic>.txt`, mirroring the structure of the input transcript in `script/<channel>/<topic>.txt`.

The output uses a compressed format with these sections:
- `HOOK FORMULA`
- `SPOKEN VOICE`
- `WORD-CHOICE HABITS`
- `PERSONALITY MOVES`
- `HUMOR AND FACT DELIVERY`
- `STRUCTURE MAP`
- `ENDING AND CTA`
- `RULES FOR THE SCRIPT AI`
- `DO NOT COPY`

## Example

Given a Veritasium transcript about fiber optics, the pattern file extracts:

```
HOOK FORMULA
Opening: Dated historical scene plus unusual physical action; no greeting or definition.
Promise: How does a small discovery become world-changing technology?
...

RULES FOR THE SCRIPT AI
1. Open with one concrete event before defining the subject. (high)
2. Answer the hook question by the final 5% of runtime. (high)
...

DO NOT COPY
Crossbow, laser and factory demonstrations require specialist access, equipment and safety controls.
```

## Tips

- Compare pattern files across channels to find **universal** rules vs. **creator-specific** habits.
- The "DO NOT COPY" section prevents blind imitation of things that require specific resources, brand deals, or personality.
- Feed the "RULES FOR THE SCRIPT AI" section directly into a writing prompt to generate new scripts in a similar style.

