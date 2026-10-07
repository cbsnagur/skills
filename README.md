# Skills

Agent skills for [Claude Code](https://code.claude.com/docs/en/skills). Each skill is a folder with a `SKILL.md`
that Claude loads when the skill is invoked or when a task matches its description.

## Skills

| Skill | What it does |
|---|---|
| [`debate`](debate/SKILL.md) | Stress-tests a technical decision by debating it from three expert viewpoints, then has a neutral tech lead give a verdict. |

### `debate`: Tech Debate Council

Use it to pressure-test an architecture or technology choice before you commit to it. You get three
deliberately biased viewpoints, then a neutral judge:

| Persona | Optimizes for | Fears |
|---|---|---|
| Bleeding-Edge Zealot | Velocity, novelty, performance | Using yesterday's tech |
| Pragmatic Conservative | Stability, observability, low maintenance | 3 AM production incidents |
| Futurist Visionary | Scalability and decoupling, three years out | Short-term infrastructure lock-in |
| Master Tech Lead | Technical merit only | — |

The debate runs in four phases:

1. **Pitch.** Each persona argues its case independently.
2. **Rebuttals.** Each persona counters the other two, kept as separate arguments.
3. **Evaluation and gap check.** The tech lead scores the arguments on risk, velocity and scalability.
   If context is missing, such as data scale, team skills or latency needs, it asks up to three questions
   and pauses with `[AWAITING_HUMAN_INPUT]`.
4. **Verdict.** After you answer, it gives one verdict with its reasoning. If two approaches score
   close, it lays them out as **Option A vs. Option B** and names the trade-off that decides between them.

**Example**

```
/debate Should we move our batch ETL from Airflow to a streaming pipeline on Kafka + Flink?
```

## Install

Copy a skill folder into your personal skills directory to use it in every project:

```bash
git clone https://github.com/cbsnagur/skills.git
mkdir -p ~/.claude/skills
cp -r skills/debate ~/.claude/skills/
```

Or copy it into a project's `.claude/skills/` directory to share it with everyone who works on that repo.
Start a new Claude Code session and run `/debate <topic>`.

## Adding a skill

Create `<skill-name>/SKILL.md` with YAML front matter (`name`, `description`, and optionally
`argument-hint`) followed by the instructions. Then add a row to the table above.
