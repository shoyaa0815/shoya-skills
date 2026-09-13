# shoya-skills

Skills for AI harness.

## List

Skills in `skills/`

* `dev/` — daily coding (unstable)
  * `shoya-ask` — persistent, exhaustive requirements clarification before implementation
  * `shoya-build` — traceable implementation of approved changes with verification evidence
  * `shoya-debug` — evidence-first debugging that proves root causes before repair
  * `shoya-review` — independent, flow-to-flow code review by a fresh reviewer

## Install

Install these skills from the repository with the shared skills CLI:

```bash
npx skills@latest add shoyaa0815/shoya-skills
```

Choose the skills and target agents when prompted. The installer copies each
selected `SKILL.md` directory into the location supported by that agent.

To install non-interactively, pass the target agent and skill names:

```bash
npx skills@latest add shoyaa0815/shoya-skills --agent codex --skill shoya-ask --skill shoya-build --skill shoya-debug --skill shoya-review --yes
```

Update installed skills later with:

```bash
npx skills update
```
