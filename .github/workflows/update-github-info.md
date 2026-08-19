---
name: update-github-info
description: Keep Mona's GitHub Info content current from official GitHub sources.
on:
  schedule: daily
  workflow_dispatch:
engine: copilot
permissions:
  contents: read
  pull-requests: read
tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos]
network:
  allowed:
    - github.blog
    - github.com
    - raw.githubusercontent.com
safe-outputs:
  create-pull-request:
    draft: true
    title-prefix: "[mona] "
    max: 1
---

# Update GitHub Info

Maintain the content that powers Mona's GitHub Info website.

## Instructions

1. Use the GitHub repository API tools to read `README.md`, `notes/mona-notes.md`, `site/content/github-info.md`, and any repository guidance or reference files needed for this task. Do not use terminal, CLI, or sandboxed commands for repository reads.
2. Use web-fetch to read the external public gh-aw guidance at `https://raw.githubusercontent.com/github/gh-aw/main/.github/aw/github-agentic-workflows.md`.
3. Use web-fetch to read `https://github.blog/latest/` and `https://github.blog/changelog/`.
4. Identify recent, developer-useful GitHub Blog and GitHub Changelog updates. Keep summaries short and practical, attribute each update to its official source, and avoid duplicating entries already present.
5. Use the edit tool to update `site/content/github-info.md` with the curated updates. Preserve the existing Markdown structure and editorial angle.
6. Review the resulting content for accurate links, clear dates, concise summaries, and consistency with Mona's notes.
7. Open a draft pull request for Mona to review with the proposed changes. Do not write directly to `main` and do not merge the pull request.
