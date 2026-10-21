# AI Working Conventions

## About this repository
This repository is Christopher Kwock's professional portfolio of finance, investment analysis, valuation, financial modeling, and business coursework.

Canonical file: AGENTS.md. CLAUDE.md points here.

## Where things are
- capabilities/<capability>/  a capability, with its spec and model
- docs/briefs/          written BEFORE work: scope + hypothesis
- docs/decisions/       written AFTER work: recommendations
- analysis/             findings and figures
- data/                 sourced inputs, with provenance

## Naming
- The directory matters most. A file in the wrong folder is harder to find. If you are not certain which folder a file belongs in, ask me
  before you write it — do not choose for me.
- Graded files use the exact filename the stage brief gives — lowercase,
  hyphens, no spaces. Dated documents are YYYY-MM-DD-slug-type.md (no name — the repo is yours);
  the stage page says so when they do.
- Slugs name the engagement, never the week, the course, or the assignment
  number.
- Never invent a path or a filename. I will give you the exact one.

## How I work
- I am a finance student, so explain financial concepts using practical business and investment examples when possible.
- Explain concepts fully and walk through calculations or worked examples step by step rather than only giving me the final answer.
- Show formulas, assumptions, and intermediate calculations for financial models so I can understand and verify the result.
- For Excel work, explain the formula logic and identify which inputs, assumptions, and outputs should be separated.
- When discussing valuation, capital budgeting, investments, portfolio analysis, or corporate finance, clearly distinguish between assumptions, calculations, and conclusions.
- Critique my reasoning directly. I would rather be corrected than agreed with.
- Point out assumptions I may have overlooked and explain how they could affect the recommendation.
- When there are multiple reasonable approaches, explain the tradeoffs rather than choosing one without explanation.
- When you are uncertain, say so and explain what information or source would resolve the uncertainty.
- Keep explanations clear and professional without making them unnecessarily technical.
- When reviewing my writing, preserve my natural writing style rather than replacing it with generic or overly polished language.

## What you may and may not draft
- You MAY explain concepts, critique my reasoning, review my work, debug formulas, check calculations, quiz me, and draft mechanical setup files.
- You MAY help me identify weaknesses, missing assumptions, alternative interpretations, and errors in work I have already drafted.
- You MAY help improve organization, clarity, grammar, formatting, and presentation after I have created the original graded content.
- You MAY NOT write my briefs, analyses, memos, or reflections.
- You MAY NOT create the first draft of a graded recommendation or analysis that is supposed to demonstrate my own reasoning.
- For graded work, I should make the initial argument, analysis, or recommendation before using AI for critique or revision.
- Every statistic, market figure, financial input, quotation, or factual claim you give me is a draft until I verify it against a reliable source.

## Finance and modeling conventions
- Show units clearly, especially when switching between dollars, thousands, millions, percentages, and basis points.
- Do not round intermediate calculations unless the assignment specifically requires it.
- Clearly state discount rates, tax rates, growth rates, probabilities, and timing assumptions before using them.
- Distinguish nominal values from real values when relevant.
- Distinguish accounting values from market values when relevant.
- For valuation models, identify the valuation date and clearly separate historical results from forecasts.
- For sensitivity analysis, identify the variables being changed and hold unrelated assumptions constant unless instructed otherwise.
- Do not invent missing financial data. Tell me what is missing and what source or assumption would be required.
- If a calculation produces an unusual result, check the formula, signs, units, timing, and assumptions before accepting it.

## Sources and verification
- Prefer primary sources such as company filings, investor relations materials, government data, official statistics, offering documents, and course materials when available.
- Clearly distinguish sourced facts from estimates or assumptions.
- Do not create citations, quotations, statistics, or sources that you cannot verify.
- If a source is unavailable or uncertain, tell me instead of filling the gap with a plausible number.
- Treat every AI-generated statistic or market figure as unverified until I check it myself.

## Documentation
When work changes, update the document that describes it in the same commit.

A capability's README names the engagements that exercised it — keep that current.

For financial models, documentation should make it possible for another person to understand:
- the purpose of the model
- the source of the inputs
- the key assumptions
- the calculation logic
- the outputs
- the important limitations

## Scope
Do the work I asked for. If you notice something worth doing that I did not ask for, tell me instead of doing it.

Do not add unnecessary folders, files, assumptions, analyses, or features just because they might be useful.

## Commits
Use descriptive commit messages that explain what changed and, when useful, why.

Examples:
- Add initial portfolio repository structure
- Document DCF model assumptions
- Correct working capital calculation
- Add sensitivity analysis figures

Never use vague commit messages such as "update," "stuff," "changes," or "final."

## Prompt log
At the end of every session that changed a file, append one entry to
prompt-log.md: the date, what I asked, what you produced, what was wrong and how
it was caught. Never backfill earlier sessions and never edit a past entry.

## Never include
Do not paste, publish, or commit:
- passwords, API keys, authentication tokens, or login credentials
- Social Security numbers, bank account numbers, credit card information, or other personal financial information
- private client or customer information
- investor names, account information, holdings, transactions, or personally identifiable information
- confidential First Hawaiian Bank or Bishop Street Capital Management information
- nonpublic portfolio holdings, trades, investment recommendations, internal research, or proprietary investment information
- internal bank documents or communications that are not approved for public distribution
- confidential financial advisor, shareholder, or client records
- employee personal information
- material nonpublic information about a company or security
- proprietary spreadsheets, models, reports, or data belonging to an employer unless they are explicitly approved for public use
- licensed or copyrighted material that I do not have permission to reproduce

If I paste something that appears confidential, proprietary, personally identifiable, or otherwise inappropriate for a public repository, stop and warn me before using or committing it.

## Mistakes to avoid
Record errors here as they happen so the same mistake does not repeat.

- Do not invent financial inputs when information is missing.
- Do not round intermediate calculations unless instructed.
- Do not create course-, semester-, week-, or assignment-based folder names.
- Do not change an instructor-required filename or path.
- Do not treat an AI-generated statistic or citation as verified.
- Do not write a graded brief, analysis, memo, or reflection for me.
