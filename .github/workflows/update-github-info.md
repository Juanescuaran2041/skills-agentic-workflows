---
name: update-github-info
emoji: 📰
description: Draft updates for Mona's GitHub Info site from GitHub's official sources and open a review pull request.
on:
  workflow_dispatch: {}
  schedule:
    - cron: '09 12 * * *'
permissions:
  contents: read
  issues: read
  pull-requests: read
tools:
  edit: {}
  web-fetch: {}
safe-outputs:
  create-pull-request:
    title-prefix: "[Mona site] "
    draft: false
    fallback-as-issue: false
network:
  allowed:
    - defaults
    - github.blog
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making any updates.

Use the following sources:
- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/

Update `site/content/github-info.md` with concise, reader-facing content under a `## Latest GitHub Updates` section. Use the blog and changelog content to keep the summary accurate and practical.

Open a pull request for Mona to review. Do not write directly to `main`; rely on `safe-outputs` with `create-pull-request` so the agent can propose changes safely.

If there are no meaningful updates, call `noop` with a short reason and do not modify the file.
