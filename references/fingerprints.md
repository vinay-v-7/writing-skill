# Claude fingerprints — self-audit

**Evidence:** T1 · STORYSCOPE Table 17. **Version pin:** corpus model **Sonnet 4.6**. Re-check when the skill's target Claude generation changes — not on a calendar.

**Last reviewed (fingerprints):** 2026-09-29 · pin Sonnet 4.6

**Context:** Claude reaches 77.1% per-class F1 on narrative features alone; 26 fingerprint features (vs Kimi 3). Paper line: “Claude keeps it cool” — restraint, lowest event escalation, most uniform voice, reverent/continuist 62% vs 39–56% others; favors epilogues; avoids dreams; quiet over “avalanche” endings.

Use during Phase B (live constraints) and as a Claude-specific Pass S adjunct for fiction/long narrative. Do not apply fiction fingerprints mechanically to short LinkedIn posts.

---

## Top fingerprints (Table 17 top 5 of 26)

| Fingerprint | Dim | SHAP | Uniq. | Counter-move |
|---|---|---|---|---|
| Strength of event escalation | EVT | 0.402 | 22.4 | Plot stakes beat-by-beat; if beat 8 ≈ beat 3, flat in a Claude-identifying way. Loudest per-model signal overall |
| Event-type diversity | EVT | 0.491 | 10.7 | Highest SHAP of any fingerprint on any model. Mix registers: bureaucratic, physical, social, interpersonal |
| Ending temporal scope → epilogue/flash-forward | TMP | 0.096 | 8.9 | Delete time-skip coda; usually no loss |
| Dreams / visions as temporal distortion → no | TMP | 0.116 | 7.7 | Total avoidance of the irrational; consistency of refusal is the signature |
| Setting mood → uncanny / haunted | SET | 0.059 | 4.6 | Choose mood from the material, not house tone |

Remaining paper themes: event density, conflict modality, relationship trajectory, heteroglossia, closure.

---

## 7-item self-audit checklist

1. **Does intensity actually escalate?** Plot stakes beat by beat. Beat 8 ≈ beat 3 → flat Claude signature.
2. **Is every complication the same kind?** Mix registers: bureaucratic setback, physical accident, social humiliation, betrayal.
3. **Is there an epilogue?** Reach for time-skip codas. Delete; usually fine.
4. **Is the ending quiet by default or by choice?** Quiet OK as choice, not reflex.
5. **Am I honoring the genre or doing something to it?** 62% reverent/continuist. Pick the convention to break before drafting.
6. **Does the narrative voice ever shift?** Most uniform voice of any source. Register should move with scene/character/stakes.
7. **Have I refused the irrational?** Systematic avoid dreams/visions — not required, but total avoidance is signature.

**Character introduction tip:** prefer **in-dialogue** (human fingerprint uniq 21.4); avoid in-action (Kimi’s top fingerprint).

---

## Other models (contrast)

| Source | # fp | Summary |
|---|---|---|
| **Human** | 32 | In-dialogue intro (uniq 21.4), single-focal narration, no direct narrator address, back-loaded revelation, crossover-genre literary ambition — targets, not contrasts |
| **GPT-5.4** | 11 | Gossip/rumour plot, distant retrospective, more subversion, ambiguous reconciliations, ensemble social nets — most socially-oriented AI |
| **Gemini 3 Flash** | 11 | Expanding social nets, direct speech, siege/ordeal, named personal names, frequent flashbacks; tidiest endings; 88% bleak/oppressive settings |
| **DeepSeek V3.2** | 7 | High narrator presence, emotion via behavioural cues, atmosphere over plot, interleaved backstory, embedded storytelling; front-loads context |
| **Kimi K2.5** | 3 | Character intro in action event, in medias res, no explicit trait labelling — fewest fps; lowest attribution F1 55.0% |
