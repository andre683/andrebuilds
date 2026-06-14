# andrebuilds.com

Personal site for Andre Arias, Analytics Engineer. Serves two purposes:
personal brand and portfolio for senior analytics engineering job search.

## Hosting and deployment

- Hosted on GitHub Pages, plain HTML/CSS, no frameworks, no build step.
- Pushing to the default branch deploys the site. Always show me the diff
  before committing.
- Keep it dependency-free. Do not add npm, bundlers, or JS frameworks.
  Vanilla JS only if a feature truly needs it.
- If the Notes section grows past ~6 entries, raise the option of migrating
  to Eleventy. Do not migrate without asking.

## Design system (must match LinkedIn banner and GitHub READMEs)

Colors (CSS variables in :root, already defined in index.html):
- --bg: #0d1117 (page background, GitHub-dark)
- --bg-soft: #161b22 (cards)
- --border: #21262d
- --text: #e6edf3
- --muted: #9aa4b2
- --green: #7ee787 (section labels, $ prompt, SQL comments)
- --cyan: #58d6ff (links, accents)
- --magenta: #ff2d92 and --gold: #ffb300 (only in the tri-color rule)

Typography:
- Monospace stack for headings, labels, nav, accents.
- System sans stack for body text. Never set body text in monospace.

Signature motifs (reuse, do not invent new ones):
- Section labels are SQL comments: "-- selected work", "-- notes"
- Terminal prompt: green "$" before andrebuilds.com in nav and footer
- Blinking cursor block after the name in the hero (respects
  prefers-reduced-motion)
- Thin tri-color gradient rule (cyan, magenta, gold) as the hero divider,
  echoing the LinkedIn banner line bundles. Use sparingly, max once per page.

## Site structure

- index.html: single-page home (hero, work, notes, about, contact)
- /work/<slug>.html: case study pages. Skeleton: problem, architecture
  (one diagram), decisions and tradeoffs, outcome. Same nav and footer
  as home.
- /notes/<slug>.html: short posts repurposed from LinkedIn, 300-800 words.
- New notes get added to the Notes list on index.html, newest first,
  date format YYYY-MM.

## Content roadmap (build in this order)

Work (3 entries max, skeleton: problem, architecture, decisions, outcome):
1. Unified GA4 pipeline for 8 brands (flagship; mentions config-driven
   brand pattern, layered structure, incremental pre-ops, bot detection,
   schema-drift safeguards; no code links)
2. Event-driven ingestion on GCP (Scheduler, Cloud Run, GCS, Pub/Sub,
   BigQuery DTS; replaced brittle cron/SFTP)
3. Open-source dbt package for GA4 + BigQuery (in-progress badge until
   launched; links prominently to its public repo)

Notes (one idea per page, seeded from Andre's LinkedIn posts and gists):
1. Backfilling incremental models with a BACKFILL_DATE compilation variable
2. Reusable partition override pre-operations helper (expand the gist)
3. Catching schema drift before it breaks the pipeline (anonymized)
4. Config-driven multi-brand modeling
5. Centralizing channel logic in one helper
6. Bot detection fields for GA4 server-side tagging with Stape

Cross-linking pattern: the pipeline case study links to notes 1-5; each
note links back to its case study and to a public gist or repo where one
exists. Notes ship first (2-3 are nearly written), case studies second.

## Writing style

- Never use the em dash character. Use commas, colons, or "to" instead.
- First person, plain language, no buzzwords. Lead with the problem and
  the outcome, tools second.
- Keep pages skimmable: short paragraphs, one idea each.

## Content facts (do not invent beyond these)

- Andre Arias, Analytics Engineer at Direct Wines, Inc.
- Owns the GA4 to BigQuery to Dataform pipeline for 8 ecommerce brands.
- Stack: BigQuery, Dataform, GA4, GTM, SQL, Python, Looker Studio, Power BI.
- Building an open-source dbt package for GA4 + BigQuery (in progress).
- LinkedIn: linkedin.com/in/augustoarias

## GitHub linking policy (decided 2026-06)

- andre-arias-dwi is the WORK GitHub profile. The analytics_unified repo is
  being made private. Never link to andre-arias-dwi or analytics_unified
  from the site.
- Public links go only to the personal profile (andre683) and public
  artifacts: gists, the clean-room patterns repo, and the dbt GA4 package.
- Work and notes are PAGES on this site, not links to GitHub. GitHub is
  cited as evidence inside pages where a public artifact exists, never as
  the destination for a homepage card.
- If a homepage card's page does not exist yet, leave the card unlinked
  rather than pointing it at a repo.

## Things to always check before finishing a task

1. Mobile rendering at ~390px width (nav collapses prompt to "$ ~").
2. All internal links resolve, no placeholder "#" left behind on shipped
   pages.
3. Color values come from the CSS variables, never hardcoded hex in new code.
