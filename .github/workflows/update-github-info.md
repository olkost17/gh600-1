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
  github:
    toolsets: [repos]
safe-outputs:
  create-pull-request:
    draft: true
    title-prefix: "[mona] "
    max: 1
---

# Update GitHub Info

Maintain the content that powers Mona's GitHub Info website.

## Instructions

1. Use the GitHub repository API tools to read `README.md`, `notes/mona-notes.md`, and `site/content/github-info.md` from this repository.
2. Review the existing structure and content format in these files.
3. Ensure the `site/content/github-info.md` file is well-maintained with current information.
4. If you identify any issues or areas that need updating, use the edit tool to update the file while preserving the existing Markdown structure.
5. Review the resulting content for accuracy and consistency.
6. If changes are made, open a draft pull request for review. Do not write directly to `main` and do not merge the pull request.

