# Writing Skill (Unslop)

A Cursor Agent skill for rewriting and drafting prose so it reads like a person chose the sentences, not like a model stacked templates.

It routes short text through a surface pass (typography, rhetoric habits) and longer craft work through a structural plan before wording. It is not a detector-evasion tool.

## Why it exists

Surface cleanup (swap a few AI-favored words) barely moves structure-based detection scores in STORYSCOPE research (UMD / Google DeepMind). Vocabulary tells also age out as models change. What lasts is how the text is built: over-determined themes, metronomic rhythm, tidy paragraph outlines that summarize themselves.

This skill separates those layers on purpose: cut mechanical tells first; only restructure when the piece is long and the goal is craft or originality.

## What you get

| Path | Role |
|------|------|
| `SKILL.md` | Routing gate and workflow |
| `references/surface.md` | Level 1 mechanics + Pass S procedure |
| `references/blacklist.md` | Rhetoric and vocabulary habit lists |
| `references/structural.md` | STORYSCOPE-aligned structural clusters |
| `references/fingerprints.md` | Model self-audit notes for drafting |
| `references/prose-benchmarks.md` | Positive plain-prose checks |
| `references/nonfiction.md` | Nonfiction mapping (use high-confidence rows unless asked) |
| `references/style-profile-template.md` | Empty template for voice calibration |
| `examples/mindfulness.md` | Before/after teaching example |

Do not commit a filled `references/style-profile.md`. That file is local calibration and is gitignored.

## How routing works

| Condition | Route |
|-----------|-------|
| Release notes, API docs, error messages where tidy prose is correct | Stand down |
| Under ~1,000 words | Pass S only |
| Over ~1,000 words, craft / originality | Phase A → B → C, then Pass S |
| Over ~1,000 words, reach / trust | Pass S first; offer Phase C; do not restructure unasked |

Volume modes: free (default for "humanize this"), careful (keep structure, 80–110% length), minimal (only clear AI constructions).

## Install

1. Copy this folder into your Cursor skills directory, for example:
   - macOS / Linux: `~/.cursor/skills/writing-skill/`
   - Windows: `%USERPROFILE%\.cursor\skills\writing-skill\`
2. Attach or invoke the skill when you ask to rewrite, humanize, or draft prose.
3. Optional: calibrate with 3–5 samples of your own non-AI writing (2,000+ words total) and save the result as `references/style-profile.md` locally.

## Quick start

Example Agent prompts:

- "Rewrite this blog post. Use the writing skill. Careful mode."
- "Humanize this paragraph. Pass S only."
- "Draft a product update in a plain voice. No summary ending."
- "Calibrate to my style from these samples."

What Pass S typically removes: formulaic em-dash stacks, stock openers from the blacklist, promotional verbs with no referent, self-summarizing closings, chatbot markdown debris.

What it refuses to invent: fake anecdotes, numbers, or "lived detail" added only to sound human. Epistemics stay on even when a style profile is present.

## License

MIT. Portions adapted from [asavvin-pixel/unslop](https://github.com/asavvin-pixel/unslop). Structural workflow, STORYSCOPE rubric files, and routing gate are part of this Cursor skill package. See `LICENSE`.
