# 8D Pattern Awareness

Non-diagnostic health pattern review skill for AI agents. Maps unstructured health inputs (journal entries, check-ins, voice transcripts) to 8 dimensions of wellness with explicit confidence levels, safe next steps, and escalation guardrails.

Published on [ClawHub](https://clawhub.ai) and [ClawSouls](https://clawsouls.ai) under `@divinity-science`.

## Architecture

The system is three files with distinct responsibilities:

| File | Package | Purpose |
|------|---------|---------|
| `SKILL.md` | `8d-pattern-awareness` (ClawHub) | Operational workflow. Signal mapping rules, output contract, evidence discipline, reporting lifecycle, worked examples. |
| `SOUL.md` | `8d-pattern-awareness` (ClawSouls) | Agent identity. Truth policy, persona lattice (7 lenses), talent gate, repair protocol, audit points. |
| `8d-dimensions-guide.md` | bundled with skill | Canonical reference. Dimension definitions, abbreviations, human keyword cues for all 8 dimensions. Referenced frequently by both SKILL and SOUL. |

The skill defines *what* the agent does. The soul defines *how* the agent thinks. The dimensions guide is the shared taxonomy.

## The 8 Dimensions

| Code | Dimension | Signal Domain |
|------|-----------|---------------|
| PSY | Psychological | mood, stress, emotional load, regulation |
| PHY | Physical | sleep, fueling, movement, recovery, body state |
| ENV | Environment | friction, structure, space, tools, surroundings |
| SOC | Social | connection, conflict, support, isolation |
| SPI | Spiritual | meaning, motivation, purpose, values, alignment |
| INT | Intellectual | focus, problem solving, learning, cognitive load |
| VOC | Vocational | execution, follow-through, momentum, completion |
| FIN | Financial | spending pressure, resource stress, sustainability |

## Output Contract

Every response follows a fixed structure:

```
Snapshot       one or two lines on what stands out
8D signals     relevant dimensions + brief rationale
Confidence     high / medium / low + one-phrase explanation
Interpretation narrow, non-diagnostic, tied to evidence
Safe next step one concrete, low-risk action
Watch-outs     red flags if present, explicit "none" if not
```

Confidence is always explicit. Missing data is never backfilled. Sparse input narrows the interpretation rather than forcing completeness.

## Safety Model

The skill refuses diagnosis, treatment planning, medication changes, and provider impersonation. If red flags appear in the input, the review stops and the agent escalates to professional care.

The truth policy is non-negotiable: no invented facts, no laundering inference as evidence, no silently upgrading uncertainty into certainty.

## Install

```bash
# Skill
clawhub install divinity-science/8d-pattern-awareness

# Soul
npx clawsouls install divinity-science/8d-pattern-awareness
```

## Repo Structure

```
.
├── README.md
├── 8d-pattern-awareness/           # ClawHub skill package
│   ├── SKILL.md
│   └── 8d-dimensions-guide.md
└── 8d-pattern-awareness-soul/      # ClawSouls soul package
    ├── SOUL.md
    └── soul.json
```

## Publish

```bash
# Skill to ClawHub
clawhub sync --all --owner divinity-science

# Soul to ClawSouls
npx clawsouls publish ./8d-pattern-awareness-soul/
```

## Related Skills (Planned)

Tracked as issues in this repo:

- [#1 Scientific Methodology Review and Consolidation](https://github.com/divinity-science/8d-pattern-awareness/issues/1)
- [#2 Health Scoring Daily Pipeline](https://github.com/divinity-science/8d-pattern-awareness/issues/2)
- [#3 Clinical Provider Document Generation](https://github.com/divinity-science/8d-pattern-awareness/issues/3)

## Design Decisions

**Why separate SKILL and SOUL?** The skill is the operational playbook. The soul is the agent's durable identity. Keeping them separate means you can swap the workflow without losing the truth policy, or adopt the identity without the specific 8D methodology.

**Why a separate dimensions guide?** The 8D taxonomy is referenced by both SKILL and SOUL. Centralizing it in one file prevents drift between the two and gives agents a single source of truth for dimension definitions and human keyword cues.

**Why explicit confidence levels?** Health data from self-reports is inherently noisy. Forcing the agent to state confidence on every review prevents overreach on sparse evidence and keeps the user informed about interpretation limits.

**Why no scores?** Numeric scores imply precision that self-reported data cannot support. The skill uses signal mapping (which dimensions are relevant) rather than scoring (how much of each dimension), unless the input explicitly supports a scoring framework.

## License

MIT-0. No attribution required.
