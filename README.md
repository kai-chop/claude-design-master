# claude-design-master

**Public release audited and completed by Claude fable-5** — competitive analysis against top-starred design skills, packaging, and verification were driven by the model itself.

[日本語版 README はこちら / Japanese README](./README.ja.md)

A web design skill for [Claude Code](https://claude.com/claude-code) targeting the acceptance bar of **Japan's curated web-design galleries**.

Most design skills tell the model to "make it beautiful". This one replaces taste-words with **numbers, decision procedures, and a falsification round** that must pass before the design is called done.

## Why this instead of generic design skills

| Feature | claude-design-master |
|---|---|
| **Quantitative completion check** | 10-item check (Q1–Q10) where contrast ratios are actually *computed*, not eyeballed |
| **Falsification round** | Before "done": reverse-genre inspection, deletion test, blur test, one-hero-per-viewport test — findings reported to the user first |
| **Token-first workflow** | No CSS before design tokens: OKLCH color ramps, the 90-7-3 rule, modular type scale, a 4px-based spacing scale. Raw HEX / raw px are forbidden in implementation |
| **Genre recipes** | 6 ready variable recipes (cool / corporate / LP etc.) chosen *first* — and never mixed |
| **Japanese typography** | Line-height, letter-spacing and jump-rate guidance for CJK text — largely absent from English-language design skills |
| **Explicit priority order** | On conflict: accessibility > visual hierarchy > genre fidelity > decoration. The model has a tiebreaker, not vibes |

The knowledge base is written in **Japanese**. Claude reads it natively and applies it in whatever language your conversation uses.

## What's inside

```
SKILL.md                      Phase 0–5 workflow, review mode, priority order
knowledge/
├── 01-color.md               OKLCH ramps, 90-7-3 rule, contrast criteria
├── 02-typography.md          Modular scale, jump rate, Japanese typesetting
├── 03-layout-space.md        Spacing scale, grid, ratios
├── 04-hierarchy-gaze.md      Gaze guidance, gestalt, cognitive laws
├── 05-motion.md              Duration/easing numbers, implementation priority
├── 06-genres.md              Genre variable recipes (cool / corporate / LP ...)
└── 07-evaluation.md          Quantitative checks, falsification round, scoring
```

Knowledge files are loaded per phase (progressive disclosure — low token overhead).

## Install

**Personal (all projects):**

```bash
git clone https://github.com/kai-chop/claude-design-master ~/.claude/skills/design-master
```

**Per project:**

```bash
git clone https://github.com/kai-chop/claude-design-master .claude/skills/design-master
```

Then ask Claude Code to design or review a UI / page / LP — the skill activates on design tasks (trigger phrases include "design this", "make it look good", "review this design" and their Japanese equivalents).

## Workflow at a glance

- **Phase 0** Genre decision — 3 adjectives, target, single most-important action; pick exactly one recipe
- **Phase 1** Design tokens — color / type / spacing / radius / border / shadow as CSS variables, before any layout
- **Phase 2** Structure — importance scores 1–5 (only one "1" per viewport), spacing hierarchy, gaze design
- **Phase 3** Implementation — semantic HTML, token references only, `clamp()`-based responsive
- **Phase 4** Motion — hover 150ms → scroll-reveal → hero, easeOutExpo default, `prefers-reduced-motion` required
- **Phase 5** Falsification & completion — quantitative Q1–Q10, blur test, falsification round (non-skippable)

## License

[Apache License 2.0](./LICENSE)

---

## Related

- [claude-config-lifeboat](https://github.com/kai-chop/claude-config-lifeboat) — secret-safe disaster-recovery backup for your Claude Code `~/.claude` (whitelist backup, fail-safe staleness nudge, recovery routing).
