# nt-brand-guidelines

Agent skill that applies NT (National Telecom) brand colors, typography, logo rules, and slide
layouts when generating PowerPoint decks.

## Install

Claude Code / Claude Desktop:

```bash
git clone https://github.com/kaebmoo/nt-brand-guidelines ~/.claude/skills/nt-brand-guidelines
```

Codex: clone anywhere and point `NT_SKILL_DIR` at the folder. `agents/openai.yaml` is the Codex
agent definition.

Read [SKILL.md](SKILL.md) for the full spec and [references/layouts.md](references/layouts.md)
for per-layout placeholder positions.

## What's in here

| Path | Contents |
|------|----------|
| `SKILL.md` | Brand spec — colors, fonts, logo rules, prohibited elements |
| `references/layouts.md` | Layout-by-layout placeholder map for the template |
| `assets/fonts/` | NT Bold / NT Regular typefaces |
| `assets/logos/` | Four official logo lockups |
| `assets/graphic-elements/` | "Vital Sign" icon family |
| `assets/NT_Presentation_Template.pptx` | Official 12-layout template |

## Assets & trademarks

The NT name, logo lockups, "Vital Sign" marks, typefaces, and presentation template are the
property of National Telecom Public Company Limited. They are included here so the skill can
produce correctly branded output, and are **not** licensed for use outside NT-branded material.
The instructional text in `SKILL.md` and `references/` is MIT-licensed.
