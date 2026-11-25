# interview-prep

A 16-week interview prep tracker: DSA (NeetCode 150), system design, low-level design and AI system design, with readings, videos, a weekly view and progress saved in each visitor's browser.

`index.html` is the whole app: one self-contained page with no build step.

## How the Vercel site works

The Vercel project is not linked to this repo. It serves a small loader page that fetches `index.html` from this repo, pinned to a commit, through the jsDelivr CDN, falling back to raw.githubusercontent.com.

To publish a change:

1. Commit and push `index.html` to `main`.
2. Redeploy the loader on Vercel with the new commit SHA.

If the Vercel GitHub app is ever installed on this account, link the repo to the Vercel project instead and pushes will deploy on their own.
