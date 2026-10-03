---
name: unslop
description: >
  Improves English prose on two orthogonal axes: discourse-level narrative habits
  measured in STORYSCOPE (structural), and typography/vocabulary tells (Unslop
  Levels 1–2 / Pass S). Routes by length. Use when the user names Unslop or asks
  to humanize, unslop, de-AI, remove AI style, or make writing sound less generated.
disable-model-invocation: true
---

# Unslop

Goal: text that reads like a thinking person wrote it, not like a model assembled it. Without a style profile the default is still the model's house voice — say so once when it matters.

**Key fact.** STORYSCOPE (UMD / Google DeepMind, 61,608 texts): surface editing of AI text barely moves structure-based detection (LAMP −1.6pt). Vocabulary tells also decay by model era. What persists is how the text is built. So this skill maps:

| Unslop level | Skill route |
|---|---|
| 1 Typography & mechanics | Pass S → [surface.md](references/surface.md) |
| 2 Vocabulary & rhetoric | Pass S → [blacklist.md](references/blacklist.md) |
| 3 Structure & epistemics | Phase A→B→C → [structural.md](references/structural.md); epistemics always on |

Not a detector-evasion tool. Independent of `code-review` and `ui-ux-pro-max`.

## Routing gate (do this first)

| Condition | Route |
|---|---|
| Tidy prose is correct (release notes, API docs, error messages) | **Stand down.** Say so and stop. |
| Under ~1,000 words | **Pass S only.** Skip structural phases — features have no referent. |
| Over ~1,000 words, craft / originality | **Phase A → B → C**, then Pass S last. |
| Over ~1,000 words, reach / trust | **Pass S first**, then offer Phase C. Do not restructure unasked. |

For nonfiction long-form craft routes, also read [nonfiction.md](references/nonfiction.md) (unvalidated extrapolation — use high-confidence rows only unless asked).

## How to work

1. **Author profile.** If `references/style-profile.md` exists, read it. Profile overrides conventions (em dashes, quotes, rhythm) but **never** Epistemics. No profile + text published under the user's name: mention once that output carries house voice and offer calibration. Once per conversation.
2. **Rewriting vs writing.** Rewriting: keep meaning, facts, genre; remove AI patterns. Writing: apply rules from the first draft.
3. **Genre survives.** A post stays a post; an email stays an email.
4. **Volume mode** (pick if unspecified; say which if it matters):
   - *Free* (default for "humanize this"): delete filler; length may shrink.
   - *Careful* (fixed formats): structure survives; length 80–110%.
   - *Minimal* (explicit): only unambiguous AI constructions.
5. **Read references for the route.** Pass S → surface + blacklist (+ prose-benchmarks for final check). Structural → structural (+ fingerprints for Claude self-audit in Phase B).

## Phase A — Structural planning

Before prose (craft route only). Choose a short list of live constraints from the cluster rubric below — typically 3–4 axes — plus any standing items from [fingerprints.md](references/fingerprints.md). This is the only phase where structural humanizing works.

**Cluster quick rubric** (largest gaps; move toward human mean and stop; prefer subtraction on AI-elevated axes):

| Cluster | Direction | One-line fix |
|---|---|---|
| Thematic over-determination | AI↑ | Cut the sentence that names the lesson; cut narrator thematic asides |
| Sensory & embodied performativity | AI↑ | Thin body-metaphor emotion; weather can be weather |
| Structural streamlining | AI↑ | One loose joint; not every ending is "understands and accepts" |
| Intertextual richness | Human↑ | Name real books, brands, places, dates from source/user |
| Reader engagement | Human↑ | Occasional direct address / fourth-wall aside (rare; high overshoot risk) |
| Temporal complexity | Human↑ | One real jump or re-pricing reveal — not kaleidoscope |
| Narrative diversity | Human↑ | Ambivalent protagonist; more talk; explicit emotion labels allowed |

Full means and overshoot: [structural.md](references/structural.md).

## Phase B — Constrained drafting

Draft holding the Phase A shortlist + Claude self-audit ([fingerprints.md](references/fingerprints.md)) + style profile if present. Do not invent specifics for liveliness (see Epistemics).

## Phase C — Structural audit

Score against the rubric. Emit a **shortlist of the 3 worst cluster offenders** (full 30-row score only if asked). Anything on the AI side of the human mean returns to **Phase A as restructuring**. Never resolve Phase C findings as wording. After structure settles → Pass S.

## Pass S — Surface (Levels 1–2)

Orthogonal to A/B/C. Never receives Phase C findings.

1. **Level 1 typography** — see [surface.md](references/surface.md): em dashes, quote consistency, sentence-case headings, bold/list debris, "Conclusion" restatements, markdown/chatbot artifacts. Grep-checkable.
2. **Level 2 rhetoric** — read [blacklist.md](references/blacklist.md). 19 categories; judge the *habit*, not zero-hit scrubbing. Category 19 (clean slop) matters after a cleanup pass.
3. **Safe vs rate.** Subtraction-safe constructions: delete. Overshoot-risky: reduce density, don't ban existence.
4. **Positive check** — [prose-benchmarks.md](references/prose-benchmarks.md): length variance, slack, uneven confidence.
5. **60-second scan** in surface.md when short on time.

## Epistemics (no profile can override)

Every substantive claim is one of: (1) from the data, (2) computed on a named assumption, (3) judgment with basis, (4) a gap named once.

- Never invent specifics, examples, numbers, or thresholds for liveliness.
- Hedge once per limitation, not once per sentence.
- Editing is not fact-checking: soften to what the text can carry, or flag missing receipts.
- **Protect human constructions** AI avoids: plain is/has; plain verbs; true superlatives; honest hedges.
- **Replacement tics:** any substitute phrase repeated across three texts becomes a marker. Cure is usually absence.

## Calibration

On "calibrate to my style" / "learn my voice":

1. Ask for 3–5 texts the user wrote without AI, 2,000+ words total.
2. Fill [style-profile-template.md](references/style-profile-template.md) from observations only.
3. Save as `references/style-profile.md` (skill folder; if unwritable, hand the user the file).
4. Show the profile; allow hand edits.

On "learn from this text too": append; fresher sample wins; date the note.

Limits: no invented facts, no Epistemics off, no imitate-another-author.

## Final check

Mechanics grep (if shell available; profile may allow em dashes):

```bash
grep -nE '—|not just|not only|important to note|worth noting|Additionally,|Moreover|delve|tapestry|testament|serves as|stands as|boasts|In summary|Overall,|game-chang|That.s not [a-z].* That.s|The real question|Here.s the thing|Here.s what that' text.md
```

Reread:

1. Every concrete detail traces to source or user — nothing invented.
2. Thresholds have named baselines or are gone.
3. Hedges: one per limitation.
4. No paragraph ends by restating itself.
5. Paragraph shapes vary; genre and profile survived.
6. **Outline test:** first sentence of every paragraph in order — if they form a tidy summary, structure is machine-shaped (exempt: specs, runbooks).
7. **Aphorism budget:** ≤1 punchy one-liner closing a paragraph.
8. **Slack:** ≥1 sentence at half pressure; confidence uneven ([prose-benchmarks.md](references/prose-benchmarks.md)).
9. No replacement tics from past edits.

## How to report

If needed: one or two plain sentences — what was removed, any judgment call. No numbered category audits. If nothing contentious and user didn't ask: no report.

## References

- [structural.md](references/structural.md) — 30 STORYSCOPE features
- [surface.md](references/surface.md) — Level 1 + Pass S procedure
- [blacklist.md](references/blacklist.md) — 19 rhetoric categories
- [prose-benchmarks.md](references/prose-benchmarks.md) — positive plain-prose checks
- [fingerprints.md](references/fingerprints.md) — Claude self-audit
- [nonfiction.md](references/nonfiction.md) — NF mapping (unvalidated)
- [style-profile-template.md](references/style-profile-template.md) — calibration
- [examples/mindfulness.md](examples/mindfulness.md) — before/after teaching example

Surface last reviewed: 2026-09-29. Structural: durable (STORYSCOPE arXiv:2604.03136v6). Adapted in part from [asavvin-pixel/unslop](https://github.com/asavvin-pixel/unslop) (MIT).
