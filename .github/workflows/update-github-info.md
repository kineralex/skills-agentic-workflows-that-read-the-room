---
name: update-github-info
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
on:
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
env:
  COPILOT_OFFLINE: "true"
  COPILOT_PROVIDER_TYPE: "openai"
  COPILOT_PROVIDER_BASE_URL: "https://opencode.ai/zen/go/v1"
  COPILOT_MODEL: "kimi-k2.6"
secrets:
  COPILOT_PROVIDER_API_KEY: OPENCODE_GO_KEY
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.com
    - github.blog
    - awesome-copilot.github.com
    - opencode.ai
---

# Update Mona's GitHub Info website

Use the repository's Copilot model setting (for example `GH_AW_DEFAULT_MODEL_COPILOT` in Actions variables) instead of hardcoding a model. Leave the default model to the project/repo configuration.

Read `notes/mona-notes.md` before making changes.

Web fetch https://awesome-copilot.github.com/workflows/ as an additional source.

Use these sources:
- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- Awesome Copilot workflows: https://awesome-copilot.github.com/workflows/

Update `site/content/github-info.md` with concise, practical updates for readers and include source context when content comes from the GitHub Blog, GitHub Changelog, or Awesome Copilot workflows.

Open a pull request for Mona to review. Use a pull request title that mentions Mona or GitHub Info. Do not write directly to `main`; rely on `safe-outputs` with `create-pull-request`.
