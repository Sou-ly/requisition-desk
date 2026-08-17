# Requisition Desk

A single-page job application tracker, hosted on GitHub Pages. The page itself
holds no data: on open it asks for a fine-grained personal access token and
pulls the role set (`data/roles.json`) and your pipeline (`tracker.json`) from
a private repo through the GitHub API. Every status change is committed back to
`tracker.json`, so the pipeline follows you across machines with full history.

## Setup on a new machine

1. Open the page.
2. Paste a fine-grained token with **Contents: read and write** on the data
   repo only (GitHub: Settings, Developer settings, Fine-grained tokens).
3. That's it. The token stays in that browser's local storage.

The sync chip in the top bar shows synced, unsynced or syncing. Click it to
reconnect or point at a different repo.

## Regenerating

`index.html` is generated from the Claude artifact viewer by a build script
that strips the embedded dataset and swaps the localStorage-only persistence
for the GitHub-backed layer. The dataset lives in the private data repo.
