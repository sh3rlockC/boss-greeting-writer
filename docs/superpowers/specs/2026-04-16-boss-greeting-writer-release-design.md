# boss-greeting-writer Release Design

## Goal

Make `boss-greeting-writer` installable out of the box from GitHub using either `git clone` or a downloaded release archive.

## Scope

- Add a `README.md` with installation and usage instructions
- Keep installation paths explicit for Codex users
- Publish a release archive that extracts to `boss-greeting-writer/`

## Decisions

- Primary install path: `git clone`
- Secondary install path: download `boss-greeting-writer.tar.gz` from GitHub Releases
- Archive contents should preserve the top-level folder name `boss-greeting-writer`
- Runtime files remain minimal: `SKILL.md`, `agents/openai.yaml`, `references/validation-cases.md`

## Non-Goals

- Add an installer script
- Add package managers or external distribution channels
- Change the skill behavior itself

## Verification

- Confirm `README.md` covers both install paths
- Confirm archive extracts into `~/.codex/skills/boss-greeting-writer`
- Confirm GitHub release contains the archive asset
