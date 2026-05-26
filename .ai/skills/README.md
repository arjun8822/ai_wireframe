# Skills

Short, scenario-specific playbooks for common tasks in this repo. Each skill
is **self-contained** — an agent loading only that file should have enough to
do the task without going hunting.

## When to load a skill

When you start a task that matches one of these scenarios, load the matching
skill _before_ writing code:

| Scenario           | Skill                                |
| ------------------ | ------------------------------------ |
| Adding a feature   | [`add-feature.md`](add-feature.md)   |
| Fixing a bug       | [`fix-bug.md`](fix-bug.md)           |
| Refactoring        | [`refactor.md`](refactor.md)         |
| Writing tests      | [`write-tests.md`](write-tests.md)   |

## Adding a new skill

Skills earn their place by being **repeated**. If you find yourself giving
the same instructions to the agent twice, capture them as a skill.

To add one:

1. Copy `add-feature.md` as a starting structure.
2. Title the file after the task (imperative, kebab-case): `add-migration.md`,
   `update-api-client.md`, `add-feature-flag.md`.
3. Keep it under ~100 lines. If it's longer, the task is probably two skills.
4. Add a row to the table above.
5. If the skill is needed often, also link it from the "When to load more
   context" table in [`/AGENTS.md`](../../AGENTS.md).
