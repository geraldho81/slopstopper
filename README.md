# Slopstopper

A standalone Claude Code skill that detects and removes AI slop from any writing. Point it at an article URL, a file, or pasted text and it rewrites the AI tells into natural human prose while keeping the meaning.

## What it kills

- The "it's not X, it's Y" antithesis tic and its 30+ variants (the #1 AI fingerprint)
- Em dashes, curly quotes, and emoji decoration
- Inflated vocabulary (delve, leverage, robust, tapestry, testament, and 130+ more)
- Throat-clearing openers ("In today's fast-paced world," "Let's dive in")
- Filler and conclusions ("It's worth noting," "In conclusion," "The future looks bright")
- Promotional inflation ("stands as a testament," "nestled in the heart of")
- Chatbot artifacts ("I hope this helps," "As an AI language model," "Certainly!")
- Rule-of-three padding, "from X to Y" false ranges, and superficial "-ing" tails
- Passive voice and subjectless fragments

## How it works

It scans for patterns, rewrites the flagged parts, runs a non-negotiables check (zero em dashes, zero antithesis, no fabricated facts), self-audits, scores the result, and delivers clean text. It detects on density and clustering, not single matches, so real human voice survives.

## SEO-safe

When the input is a published article or web page, the rewrite preserves search signals: target keywords, heading hierarchy, title tag and meta description, URL slug, links and anchor text, image alt text, and structured data. It removes the slop without costing rankings, and flags anything that can't be cleaned without an SEO risk.

## Install

Copy this folder into your skills directory:

```
~/.claude/skills/slopstopper/
```

Then invoke it by name, or ask Claude to "run slopstopper on this article."

## Files

- `SKILL.md`: the skill: workflow, rules, and the priority phrase lists
- `reference/ai-phrase-database.md`: the full categorized database (all 10 categories, with sources)

## Standalone

Self-contained. It depends on no other skill. Everything it needs is in this repo.

## Source

The phrase database was compiled from Wikipedia's "Signs of AI writing," the Kobak et al. excess-vocabulary study (*Science Advances*, 2025), and published AI-detection research. Sources are linked at the bottom of `reference/ai-phrase-database.md`.

## License

MIT
