# boss-greeting-writer Release Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Make the skill repository installable from GitHub via `git clone` and a release archive.

**Architecture:** Add a concise `README.md` for install and usage, then package the repository into a `tar.gz` archive whose top-level directory is `boss-greeting-writer/`, and publish that archive as a GitHub release asset.

**Tech Stack:** Markdown, git, tar, GitHub CLI

---

### Task 1: Add user-facing install documentation

**Files:**
- Create: `README.md`
- Create: `docs/superpowers/specs/2026-04-16-boss-greeting-writer-release-design.md`

- [ ] **Step 1: Write the documentation files**

Add a `README.md` that includes:
- repository purpose
- install via `git clone`
- install via downloaded release archive
- usage example

Add a short spec capturing the chosen release shape and non-goals.

- [ ] **Step 2: Verify the docs mention both install paths**

Run:

```bash
rg -n "git clone|tar.gz|Releases page" README.md docs/superpowers/specs/2026-04-16-boss-greeting-writer-release-design.md
```

Expected: matches for clone and release-based installation wording

- [ ] **Step 3: Commit the documentation**

```bash
git add README.md docs/superpowers/specs/2026-04-16-boss-greeting-writer-release-design.md
git commit -m "docs: add install and release guide"
```

### Task 2: Package and publish the release

**Files:**
- Create: `docs/superpowers/plans/2026-04-16-boss-greeting-writer-release.md`
- Create: release asset `boss-greeting-writer.tar.gz`

- [ ] **Step 1: Create the archive from the repository root**

Run:

```bash
cd /Users/xyc/Documents
tar -czf /tmp/boss-greeting-writer.tar.gz boss-greeting-writer \
  --exclude='boss-greeting-writer/.git'
```

Expected: `/tmp/boss-greeting-writer.tar.gz` exists

- [ ] **Step 2: Verify the archive layout**

Run:

```bash
tar -tzf /tmp/boss-greeting-writer.tar.gz | sed -n '1,20p'
```

Expected: paths begin with `boss-greeting-writer/`

- [ ] **Step 3: Publish the release**

Run:

```bash
gh release create v0.1.0 /tmp/boss-greeting-writer.tar.gz \
  --repo sh3rlockC/boss-greeting-writer \
  --title "v0.1.0" \
  --notes "Initial packaged release for install via git clone or release archive."
```

Expected: a GitHub release exists with the attached archive asset

- [ ] **Step 4: Verify the release asset**

Run:

```bash
gh release view v0.1.0 --repo sh3rlockC/boss-greeting-writer
```

Expected: output includes `boss-greeting-writer.tar.gz`
