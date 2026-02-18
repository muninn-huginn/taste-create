# taste-create

A Claude Code skill that discovers and builds your visual taste through conversation.

## What it does

Walks you through 5 phases of style discovery — one question at a time — until you have a complete visual style package:

1. **Soul** — What should this feel like? Find the emotional foundation.
2. **Eyes** — What do you find beautiful? Build a shared visual vocabulary from real references.
3. **Dimensions** — Where do you fall on each axis of taste? Position the style on 7 spectrums.
4. **Tokens** — What are the concrete values? Derive colors, type, spacing, shape, and motion.
5. **Validation** — Does this feel right? Test tokens against real components and iterate.

The result is a fully installable Claude Code skill — a taste companion that reviews your visual code, guides your design decisions, and generates UI in your style.

## Install

```bash
npx skills add muninn-huginn/taste-create
```

## Usage

Tell Claude to create a style:

- "Create a style"
- "Define visual style"
- "Help me figure out the aesthetic"
- "What should this look like?"
- "Build a design language"

The skill will guide you through the discovery process conversationally. You can share URLs, screenshots, and moodboards as visual references during Phase 2.

After all five phases, the skill packages the result as a standalone taste skill you can install and use across projects.

## What you get

A complete taste skill directory:

```
taste-{name}/
├── SKILL.md                     # Behavioral instructions for the taste companion
├── references/
│   ├── soul.md                  # Philosophy and emotional foundation
│   ├── principles.md            # Do's and don'ts
│   ├── tokens.md                # Design tokens (colors, type, spacing, shape, motion)
│   ├── components.md            # Component patterns with code
│   ├── motion.md                # Motion rules and strategy
│   └── imagery.md               # Image treatment guidelines
└── assets/
    ├── css/{name}.css            # Ready-to-use stylesheet (web)
    └── showcase/index.html       # Interactive showcase page
```

The taste companion works in three modes:
- **Review** — evaluates existing visual code against your taste
- **Guide** — suggests aligned choices during design decisions
- **Generate** — produces new UI code in your style

## Skill structure

```
taste-create/
├── SKILL.md                           # Main skill instructions
├── references/
│   ├── discovery-process.md           # Detailed 5-phase workflow
│   ├── style-dimensions.md            # 7 axes of taste with positions
│   ├── question-bank.md               # Curated questions per phase
│   ├── output-format.md               # Output specification
│   └── showcase-guide.md              # Showcase page builder guide
└── assets/
    └── style-template/                # Templates for generated files
        ├── SKILL.md.template
        └── references/*.template
```

## License

MIT
