# ai-radar

Automated daily intelligence briefs produced by Claude routines.

## What this is

This repository holds machine-generated briefs covering AI developments and Turkish/EU public-sector research funding calls. Each brief is produced by a scheduled Claude routine and committed here as a dated markdown file. The routine prompts themselves are versioned alongside their output, so changes in tone, scope, or emphasis can be traced back to a prompt revision.

## Structure

```
ai-radar/
├── README.md
├── .gitignore
├── briefs/                # Daily output, one file per routine per day
│   ├── ai-news/           # Global + Turkey AI news, English
│   ├── tr-calls/          # Turkish public-sector AR-GE calls, Turkish
│   └── tr-eu-calls/       # Turkish + EU research calls, Turkish
└── prompts/               # Source-of-truth prompts for each routine
    ├── ai-news.md
    ├── tr-calls.md
    └── tr-eu-calls.md
```

## Routines

| Routine | Output folder | Language | Cadence | Source prompt |
| --- | --- | --- | --- | --- |
| `ai-news` | `briefs/ai-news/` | English | Daily | `prompts/ai-news.md` |
| `tr-calls` | `briefs/tr-calls/` | Turkish | Daily | `prompts/tr-calls.md` |
| `tr-eu-calls` | `briefs/tr-eu-calls/` | Turkish | Daily | `prompts/tr-eu-calls.md` |

## Naming convention

Each brief is written as `YYYY-MM-DD.md` inside its routine folder. Briefs are append-only — once a brief is committed, it is not edited. Corrections are made as separate commits with a `fix:` prefix in the commit message, leaving the original brief intact as a record of what was published at the time.

## How briefs are generated

Briefs are produced by Claude routines that read the corresponding file in `prompts/` and write the result into `briefs/<routine>/<YYYY-MM-DD>.md`. The prompts are the source of truth for what each brief should contain — its scope, tone, language, and structure. To change what future briefs look like, edit the prompt; do not retroactively edit past briefs.

## Reading the briefs

Open `briefs/<routine>/` and pick the date you want. If a brief reads differently from earlier ones, run `git log prompts/<routine>.md` to see when the prompt last changed.

## License

This repository is private and personal. Its content is not licensed for redistribution. Briefs may include paraphrased summaries and links to original sources; those original sources retain their own copyright and terms.
