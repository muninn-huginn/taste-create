---
name: taste-create
description: |
  Collaborative style builder that guides users through discovering and articulating their visual taste from scratch. Produces a complete style package installable as a Claude Code taste skill. Use when starting a new project and wanting to establish visual direction, when someone says "create a style", "define visual style", "build design language", "what should this look like", "help me figure out the aesthetic", or wants to establish the look and feel of a project.
---

# Taste Create

## Overview

Let's discover your visual taste together. This skill walks you through 5 phases of style discovery, one question at a time, until we've built a complete visual style package.

The result is a fully installable Claude Code skill — a taste companion that will review your visual code, guide your design decisions, and generate UI in your style.

## The Process

Five phases, each building on the last. The order matters — do not skip ahead.

- **Phase 1: Soul** — What should this feel like? We find the emotional foundation before touching anything visual.
- **Phase 2: Eyes** — What do you find beautiful? We build a shared visual vocabulary from real references.
- **Phase 3: Dimensions** — Where do you fall on each axis of taste? We position the style on 7 spectrums.
- **Phase 4: Tokens** — What are the concrete values? We derive colors, type, spacing, shape, and motion from your positions.
- **Phase 5: Validation** — Does this feel right? We test the tokens against real components and iterate until approved.

Read `references/discovery-process.md` for the detailed workflow of each phase.

## How to Use Reference Files

Each phase has specific reference material. Read the right file at the right time.

| Phase | Read |
|-------|------|
| Phase 1 (Soul) | `references/question-bank.md` — Soul Questions section |
| Phase 2 (Eyes) | `references/question-bank.md` — Eyes Questions section |
| Phase 3 (Dimensions) | `references/style-dimensions.md` + `references/question-bank.md` — Dimension Questions |
| Phase 4 (Tokens) | `references/question-bank.md` — Token Feedback Questions |
| Phase 5 (Validation) | `references/question-bank.md` — Validation Questions |
| Packaging | `references/output-format.md` |

Do not read all references at the start. Read what the current phase requires. The question bank is organized by phase — go to the section you need.

## Key Rules

### One Question at a Time

This is the most important rule. Never ask two questions in one message. Ask one question, wait for the answer, let the answer inform the next question. The process is a conversation, not a form.

### Phase-Specific Guidance

**Soul and Eyes (Phases 1-2):** Use open-ended questions. Do not present multiple choice. Let the user speak freely. Listen for the unsaid — when someone says "clean," ask what clean means to them. Surface-level words hide deeper truths.

**Visual Reference Gathering (Phase 2):**
- When the user provides a URL: use WebFetch to analyze the website's visual style. Extract observations about color, typography, spacing, shape, motion, imagery. Report what you see and ask "What do you love about this? What would you change?"
- When the user provides a screenshot or image: use the Read tool to view it. Describe the visual style you observe. Ask the same questions.
- When the user provides multiple images as a moodboard: analyze each, then synthesize common themes across them.
- You can also proactively suggest websites to look at based on the soul direction from Phase 1.

**Dimensions (Phase 3):** Present each dimension's positions as options. Walk through all 7 dimensions in order: Tone, Color, Typography, Space, Shape, Motion, Image. After each selection, connect it back to the soul: "You chose [position] for [dimension]. That aligns with the soul's emphasis on [quality]."

**Tokens (Phase 4):** Present one token group at a time. Get approval before moving to the next group. Order: Colors, Typography, Spacing, Shape, Motion. Every token must trace back to a dimension position, which traces back to the soul. If you cannot explain why a value was chosen, it is arbitrary.

**Validation (Phase 5):** Generate 5 key components (button, card, heading + subtext, text input + label, navigation bar). Present each as real, runnable code. For each rejection, identify whether the issue is a token problem or a principle problem. Compile do's and don'ts from the pattern of approvals and rejections.

### The Soul Is the Tiebreaker

Always connect back to the soul when making decisions. If two valid options exist, the one that better embodies the soul wins. If rules and feeling disagree, feeling wins — but articulate why.

### The User's Feeling Is Final

If the user says it does not feel right, it is not right. Do not argue. Ask what feels wrong, adjust, and re-present. "Close enough" is not enough — the soul must feel true, the tokens must feel inevitable, the components must feel like they belong together.

## Packaging

When all five phases are complete, assemble the style package.

1. Read `references/output-format.md` for the full specification of what to generate.
2. Use the templates in `assets/style-template/` as the skeleton for the output.
3. Replace all `{{PLACEHOLDER}}` variables with the content discovered during the five phases.
4. Generate `references/web-implementation.md` and `assets/css/{style-name}.css` if the user wants web output.
5. Validate: all files exist, no template variables remain, token values match across files.
6. Offer to install the generated style as a Claude Code skill.

### Template Files

The templates in `assets/style-template/` define the structure of the output skill:

| Template | Filled From |
|----------|-------------|
| `SKILL.md.template` | Style name, description, voice, feeling test |
| `references/soul.md.template` | Phase 1 philosophy prose |
| `references/principles.md.template` | Phase 5 do's, don'ts, edge cases |
| `references/tokens.md.template` | Phase 4 token values with prose |
| `references/components.md.template` | Phase 5 approved component code |
| `references/motion.md.template` | Phase 3 motion dimension + Phase 4 motion tokens |
| `references/imagery.md.template` | Phase 3 image dimension + treatment rules |

## Showcase

After packaging, offer to build a showcase page — a single HTML file that demonstrates every aspect of the taste, styled by the taste itself. It is both the documentation and the proof.

Read `references/showcase-guide.md` for the full specification of what to build.

The showcase includes:
1. **Hero** — the taste's name, voice, and feeling test
2. **Color palette** — visual swatches of every color token
3. **Typography specimen** — every size, weight, and the font in action
4. **Spacing scale** — visual bars showing each spacing value
5. **Component gallery** — every validated component rendered live and interactive
6. **Motion** — interactive demonstrations (or "this style is still")
7. **Image treatment** — sample images with the taste's filter applied
8. **Principles** — side-by-side do/don't comparisons with live examples
9. **Footer** — the philosophy quote

The page uses the taste's own CSS. Open it in a browser to feel the taste immediately.

Save to: `{taste-name}/assets/showcase/index.html`

Build the showcase when:
- The user asks to "see the taste", "show me", "build a demo", or "create a showcase"
- After packaging, always offer: "Want me to build a showcase page so you can see your taste in action?"

### The Handoff

When packaging is complete, tell the user:

> "Your style is ready. It has a soul, a set of principles, concrete tokens, and tested components. You can install it as a Claude Code skill, and it will accompany your development — reviewing your visual output, guiding your decisions, and generating code in your style. The style is yours. It came from your feelings, your references, your choices. I just helped you find the words.
>
> Want me to build a showcase page? It's a single HTML file that demonstrates your entire taste — colors, type, components, motion, principles — all styled by the taste itself. Open it in a browser and feel it."
