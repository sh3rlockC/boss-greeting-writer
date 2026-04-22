# boss-greeting-writer

`boss-greeting-writer` is a Codex skill for writing tailored first-message outreach on Boss 直聘 from a job description plus candidate materials.

It is designed for cases where the user has:
- one specific JD
- candidate experience notes, long-form text, or screenshots
- a preference for concise, reply-oriented outreach instead of generic self-introduction

## What It Does

The skill helps Codex:
- infer what the role is actually hiring for
- pick the strongest candidate evidence for that role
- avoid overclaiming titles or project scope
- produce three first-message variants:
  - `自然版`
  - `稳妥版`
  - `超短首条版`
- switch into a direct-output mode for rapid Boss application sessions

See [`SKILL.md`](./SKILL.md) for the full behavior contract.

## Repository Layout

```text
boss-greeting-writer/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    └── validation-cases.md
```

## Install

### Option 1: `git clone`

Clone directly into your local Codex skills directory:

```bash
git clone https://github.com/sh3rlockC/boss-greeting-writer.git \
  ~/.codex/skills/boss-greeting-writer
```

If the directory already exists, update it with:

```bash
cd ~/.codex/skills/boss-greeting-writer
git pull
```

### Option 2: Download a Release Archive

1. Open the [Releases page](https://github.com/sh3rlockC/boss-greeting-writer/releases)
2. Download `boss-greeting-writer.tar.gz`
3. Extract it into `~/.codex/skills/`

Example:

```bash
mkdir -p ~/.codex/skills
tar -xzf boss-greeting-writer.tar.gz -C ~/.codex/skills
```

After extraction, you should have:

```text
~/.codex/skills/boss-greeting-writer/SKILL.md
```

## Use

Reference the skill by name in your prompt:

```text
Use $boss-greeting-writer to judge this JD, pick my strongest evidence, and write three Boss first-message variants.
```

Typical inputs:
- JD text
- JD screenshots
- structured experience bullets
- candidate narrative text
- candidate screenshots
- style constraints such as `自然`, `稳妥`, `更短`, `不要强调 AI`
- direct-output constraints such as `直接给最终版`, `连打模式`, `不要分析`

### Direct-output / 连打模式

When the user is in a rapid-application flow and says things like:
- `直接给最终版`
- `连打模式`
- `不要分析`
- `不要再说给我一版`

the skill should skip the full analysis structure and return just **one final Boss-ready first message** that can be copied and sent immediately.

This mode is intended for high-frequency application sessions where speed and sendability matter more than explanation.

Suggested prompt styles:

```text
用 boss-greeting-writer，连打模式。下面是 JD 和我的经历，直接给最终版，别分析。
```

```text
直接用 boss-greeting-writer 出一条可发版首条消息，不要铺垫，不要三版。
```

```text
这是新岗位，继续连打。保持自然、短一点、像真人发的。
```

What changes in this mode:
- output only one sendable message by default
- no long reasoning block unless the user asks
- keep the first line compact
- prefer conservative claims if OCR or image understanding is uncertain
- treat `兴趣` / `长期关注` as supporting signal, not the core match argument

Recommended use cases:
- batch Boss applications
- mobile copy-send workflows
- cases where the user is iterating across many similar JDs quickly

## Notes

- Screenshot inputs rely on the OCR skill named in [`SKILL.md`](./SKILL.md).
- This repository is intentionally small so the release archive can be dropped into `~/.codex/skills/` without extra setup.

## Release

This repository publishes a release archive named `boss-greeting-writer.tar.gz` so users can install without cloning git history.

## Changelog & Releases

- User-visible changes are tracked in [`CHANGELOG.md`](./CHANGELOG.md).
- For a new release, update the `Unreleased` section first, then cut the versioned release.
- GitHub Release notes should match the same user-visible changes, not just raw commit history.

