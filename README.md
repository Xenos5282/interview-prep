# interview-prep

A 16-week interview prep tracker: DSA (NeetCode 150), system design, low-level design and AI system design, with readings, videos, a weekly view and progress saved in each visitor's browser.

`index.html` is the whole app: one self-contained page with no build step.

The app has four sections: **This week** (today's work, a 16-week strip and progress), **Tracks** (the full syllabus per track, with search, filters and how to work each track), **Leaderboard**, and **You** (sync code, stats, start date and reset). The sync button sits in the top bar on every page.

Live: https://interview-prep-green-five-60.vercel.app

## How the Vercel site works

The Vercel project is not linked to this repo. It serves a small loader page that fetches `index.html` from this repo, pinned to a commit, through the jsDelivr CDN, falling back to raw.githubusercontent.com.

To publish a change:

1. Commit and push `index.html` to `main`.
2. Redeploy the loader on Vercel with the new commit SHA.

If the Vercel GitHub app is ever installed on this account, link the repo to the Vercel project instead and pushes will deploy on their own.

## Sync and leaderboard

On the website, progress can sync across devices with a 12-character code (no sign-up), and people can join a leaderboard with a nickname. Both use the Supabase project `interview-prep` (Mumbai). Browsers can't read the table; they call four database functions: `prep_load`, `prep_save`, `prep_set_profile` and `prep_leaderboard`. Only a SHA-256 hash of each code is stored.

## Streaks and friends

- **Daily streak:** a day counts when you tick anything. Every 7 days in a row earns a streak freeze (hold up to 2), and a missed day uses one. The flame in the top bar opens the streak page.
- **Friend streaks:** each profile has a public 8-character friend code, separate from the secret sync code. An invite link (`/?friend=CODE`) lets a friend accept in one tap. A friend streak counts the days since becoming friends when both people ticked something.
- **Daily points cap:** at most 10 points count per day, so the leaderboard rewards consistency, not bulk-ticking.
- Database functions: `prep_friends`, `prep_friend_lookup`, `prep_add_friend`, `prep_remove_friend`. The streak rules live in `prep_streak` (server) and `streakInfo()` (page), and they match.
