---
name: update-github-info
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
tools:
  edit:
  github:
    toolsets: [repos]
  web-fetch:
network:
  allowed: 
    - "*.github.blog"
    - "github.blog"
    - "*.github.com"
    - "github.com"
    - "*.github.io"
safe-outputs:
  create-pull-request:
    max: 1
    title-prefix: "[github-info] "
    if-no-changes: ignore
---

# Update GitHub Information

Keep `site/content/github-info.md` current for Mona to review.

1. Read `notes/mona-notes.md` before making changes.
2. Use GitHub repository API tools to read repository guidance and reference files. Do not use terminal, CLI, or sandboxed commands for repository guidance or reference files.
3. Use web-fetch to read these public GitHub sources:
   - https://github.blog/latest/
   - https://github.blog/changelog/
  - https://awesome-copilot.github.com/workflows/
4. Update only `site/content/github-info.md` with concise, accurate information relevant to the site's existing content and Mona's notes.
5. Do not write directly to `main` or change any other file.
6. When there is a useful update, use the `create-pull-request` safe output to open one pull request for Mona to review. Include the sources consulted and a concise summary of the change in the pull request body.
7. Do not open a pull request when no content update is needed.