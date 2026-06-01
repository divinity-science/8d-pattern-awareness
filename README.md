# 8D Pattern Awareness

> Turn health notes into clear 8D signals, confidence levels, and safe next steps — without diagnosis.

## What this is

A ClawdHub **skill** and **soul** for AI agents that review health notes through 8 dimensions of wellness. The agent maps messy input (journal entries, check-ins, transcripts) into structured, confidence-aware pattern reviews.

### The 8 Dimensions

| Abbr | Dimension | Covers |
|------|-----------|--------|
| **PSY** | Psychological | mood, stress, emotional load, regulation |
| **PHY** | Physical | sleep, fueling, movement, recovery, body state |
| **ENV** | Environment | friction, structure, space, tools, surroundings |
| **SOC** | Social | connection, conflict, support, isolation |
| **SPI** | Spiritual | meaning, motivation, purpose, values, alignment |
| **INT** | Intellectual | focus, problem solving, learning, cognitive load |
| **VOC** | Vocational | execution, follow-through, momentum, completion |
| **FIN** | Financial | spending pressure, resource stress, sustainability |

## What this is NOT

- Not a diagnosis engine
- Not a treatment planner
- Not a replacement for clinicians
- Not a medication recommendation system

## Package Structure

```
8d-pattern-awareness/          ← ClawdHub Skill
├── SKILL.md                   ← Operational workflow + output contract
└── 8d-dimensions-guide.md     ← Canonical dimension definitions + cues

8d-pattern-awareness-soul/     ← ClawSouls Soul (separate package)
├── SOUL.md                    ← Agent identity, truth policy, repair rails
└── soul.json                  ← Soul manifest
```

## Install

### Skill (via ClawdHub)
```bash
clawhub install divinity-science/8d-pattern-awareness
```

### Soul (via ClawSouls)
```bash
npx clawsouls install divinity-science/8d-pattern-awareness
```

## How it works

1. Agent reads the health note
2. Maps signals to the 8D lens using the dimensions guide
3. Assigns a confidence level (high / medium / low)
4. Writes one narrow, non-diagnostic interpretation
5. Gives one safe, actionable next step
6. Flags watch-outs only when warranted

### Example Output

```
Snapshot: Sleep debt and cognitive load are the main signals.
8D signals: PHY, INT, VOC
Confidence: medium — the note is sparse
What may be going on: Recovery is lagging behind demand
Safe next step: Simplify the day and protect sleep
Watch-outs: No red flags mentioned
```

## Safety

- Never crosses into diagnosis or medical certainty
- Stops the review and escalates when red flags appear
- Keeps confidence explicit when evidence is thin
- Never invents missing facts or backfills data

## Related Projects

> These are planned — issues are tracked in this repo.

- Scientific Methodology Review & Consolidation
- Health Scoring Daily Pipeline
- Clinical Provider Document Generation

## License

Published on ClawdHub under [MIT-0](https://opensource.org/license/mit-0). Attribution not required.

## Published by

[Divinity Science](https://github.com/divinity-science) — `@divinity-science` on ClawdHub
