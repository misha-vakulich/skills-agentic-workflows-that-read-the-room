---
name: update-github-info
model: auto
description: Keep Mona's GitHub Info page current with useful, source-attributed updates.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
    allowed-files:
      - site/content/github-info.md
---

Read `notes/mona-notes.md` first and follow its editorial guidance.

Use `web-fetch` to read all of these sources:

- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/

Identify timely GitHub updates that are useful to developers learning GitHub. Keep
the page concise and practical, and attribute each update to its GitHub Blog,
GitHub Changelog, or Awesome Copilot workflows source. Do not invent details or
add filler when there is no useful update.

Update only `site/content/github-info.md`. If the page needs no meaningful
changes, leave it unchanged and do not open a pull request.

When there are changes, use the configured `create-pull-request` safe output to
open one pull request for Mona to review. Summarize the updates and cite their
sources in the pull request description. Never write directly to `main`, push
changes outside the safe output, or merge the pull request.
