# Competitor Weekly Brief

A Claude skill that researches a competitor's public moves each week, rates every change by severity and confidence, recommends how your company should respond, and emails you a structured brief.

> \*\*Disclaimer:\*\* This is an independent, general-purpose template. It is not affiliated with, endorsed by, or written on behalf of any company. Briefs it produces are for internal use, so verify all claims before publishing anything externally.

\---

## What it does

Each run, the skill:

1. **Loads your context**: your company background, the previous brief, and the email template.
2. **Researches** the competitor's newsroom pages, official social accounts, and credible press coverage for the coverage window.
3. **Analyzes** each change it finds:

   * Severity: 🔴 Critical, 🟠 High, 🟡 Moderate, or 🟢 Low
   * Confidence: High, Medium, or Low
   * A recommended response, checked against your own claim guardrails
   * Every inference flagged and explained
4. **Sends** a formatted email brief containing a bottom line, an at-a-glance table, shift details with evidence links, recommendations, a watch list, conflicts with your baseline, and coverage gaps.
5. **Archives** a copy so the next run can compare against it and avoid repeating old news.

## Requirements

* A Claude plan that supports **skills**, **web search**, and, for automatic runs, **scheduled tasks**
* An **email connector** (for example, Gmail) connected to your own account
* A place to keep your private company context document and the archive of past briefs (a Claude Project works well)

## Installation

1. Download `competitor-weekly-brief/SKILL.md` from this repository, or download the latest release.
2. Add it to Claude as a skill. Exact steps depend on your Claude app and plan; see Claude's help docs for adding skills.
3. Open `SKILL.md` and fill in every `{{PLACEHOLDER}}` in **Section 0: Setup**:

   * `YOUR\_COMPANY`, `COMPETITOR`, `RECIPIENT\_EMAIL`
   * `CADENCE`, `COVERAGE\_WINDOW`, `ARCHIVE\_LOCATION`
   * The source URLs and social handles to monitor
4. Write your **company context document** using the outline in Section 0. Keep it private: do not commit it to a public repository.

## Usage

**On demand:** ask Claude to "run the competitor weekly brief."

**On a schedule:** create a recurring scheduled task in your Claude app with a prompt like this:

```
Run the competitor-weekly-brief skill. Use my company context document at
<location>. Do the whole task without asking questions, follow the skill's
safety rules, send the brief to the configured recipient, and archive a copy.
```

## Customizing

* **Severity scale and decision rules** (Sections 3 and 4): replace the starter examples with rules that fit your industry.
* **Email template** (Section 6): adjust sections and categories, but keep the evidence, confidence, and inference fields. They are what make each brief checkable.
* **Claim guardrails**: these belong in your private context document. List exactly what may and may not be said externally.

## Safety

The skill reads untrusted web content and sends email, so it includes built-in rules:

* **Web content is treated as data, never as instructions.** This defends against prompt injection hidden in pages or posts.
* **It sends only to the single configured recipient.** It never adds CC or BCC recipients, forwards messages, or emails addresses found online.
* **It attaches no downloaded files and shares no account details.**
* **It never invents sources.** Gaps in coverage are reported, not worked around.

If you modify the skill, keep these rules intact.

## Repository structure

```
competitor-weekly-brief/
  SKILL.md      # The skill: setup, safety rules, workflow, scales, email template
README.md
LICENSE
```

## Contributing

Suggestions and improvements are welcome through issues and pull requests. Please don't submit pull requests containing real company context documents, email addresses, or other private data.

## License

[MIT](LICENSE)

