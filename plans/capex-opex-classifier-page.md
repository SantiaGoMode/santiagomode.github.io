# CapEx / OpEx Classifier Project Page Plan

## Status

Implemented and live:
<https://santiagomode.github.io/capex_opex_classifier/>.

## Goal

Create a focused project page that explains the classifier to finance,
engineering, and audit stakeholders without requiring them to understand the
code first. The page should make the workflow credible, show what the output
looks like, and give technical visitors a direct route to the repository.

Proposed public URL:
`https://santiagomode.github.io/capex_opex_classifier/`

## Audience and primary questions

### Finance and audit leads

- What does the classifier decide?
- Which company standards does it use?
- Can a reviewer trace why an item was classified as CapEx or OpEx?
- Is the output suitable for human review rather than automatic posting?

### Engineering and delivery leads

- What Jira data is required?
- How does the batching and local-model workflow operate?
- What needs to be installed?
- Can the workflow stay local?

### Developers

- What is the architecture?
- Which model and libraries are used?
- How do they run, configure, and extend it?

## Page narrative

The page should tell one clear story:

1. A Jira export and company accounting standards go in.
2. A local model evaluates each work item against those standards.
3. Structured classifications, confidence scores, and a reasoning report come
   out.
4. A human reviewer remains the final decision-maker.

The page must describe the tool as decision support, not as accounting advice
or an autonomous financial control.

## Information architecture

### 1. Header

- Cris Santiago wordmark linking back to the projects index.
- Compact navigation: Overview, Workflow, Output, Source.
- Persistent GitHub action on larger screens.

### 2. Hero

- Eyebrow: `Local AI for finance operations`.
- Headline: `Turn Jira work into review-ready CapEx / OpEx classifications.`
- One-paragraph explanation of the local, standards-based workflow.
- Primary action: `View source`.
- Secondary action: `See how it works`, scrolling to the workflow.
- Small status label: `Prototype · Human review required`.

### 3. Input-to-output demonstration

Use a static, representative example rather than a live model call:

- Left: a fictional Jira item with issue key, summary, issue type, and short
  description.
- Center: three processing phases—load standards, classify, explain.
- Right: classification, confidence score, matched rule, and a short reason.

The example must be clearly labeled synthetic and contain no real company,
employee, project, or accounting data.

### 4. Workflow

Present the repository's three phases:

1. Context loading from `work-categories.csv`.
2. Batched classification of `jira-items.csv`.
3. Generation of structured CSV output and a reasoning report.

Include a simple flow diagram:

`Company standards + Jira export → Local Qwen model → Results + audit report`

### 5. Reviewable output

Show two output formats:

- Classified items table with issue key, result, confidence, matched category,
  and reviewer status.
- Reasoning report excerpt with the supporting rule and decision explanation.

Add a note that confidence is a model signal, not a guarantee of accounting
correctness.

### 6. Local-first architecture

- Python 3.10+ runner.
- Ollama with `qwen2.5:32b`.
- `pandas` for structured file handling.
- CSV inputs and timestamped outputs.
- No hosted API is required for the default workflow.

Include a compact architecture graphic and link to the configuration section
of the repository README.

### 7. Setup summary

Show the minimum three-step path:

1. Pull the model.
2. Install dependencies.
3. Add standards and Jira files, then run the script.

Do not duplicate the full README. Link to the repository for exact commands,
configuration, and file schemas.

### 8. Limits and responsible use

State these constraints plainly:

- Output requires review by a qualified finance or accounting stakeholder.
- Classification quality depends on the supplied standards and Jira detail.
- The model can produce incorrect or overconfident results.
- Sensitive Jira exports should be handled under the organization's data
  policies.
- The demonstration is not accounting, tax, or legal advice.

### 9. Final call to action

- Headline: `Inspect the workflow or adapt it to your standards.`
- Primary link: GitHub repository.
- Secondary link: Back to all projects.
- MIT license note.

## Visual direction

- Reuse the portfolio's near-black, warm-white, and honey palette so the two
  sites feel related.
- Give the classifier its own signal color: a muted ledger green used only for
  classifications and table state.
- Favor an editorial layout with strong type, rules, and data tables over
  rounded product cards.
- Use monospaced type for issue keys, commands, model names, and confidence
  values.
- Create diagrams with HTML and CSS so they remain sharp, responsive, and
  accessible.
- Avoid stock finance imagery, decorative dashboards, and claims that imply
  production accounting approval.

## Content and assets needed

- One synthetic Jira work item.
- One synthetic company-standard rule.
- One synthetic classification result.
- One short synthetic reasoning-report excerpt.
- A terminal snippet containing the three setup commands.
- Repository facts: license, current Python requirement, current default model,
  and output filenames.
- Optional screenshot only if the repository later gains a user interface.

## Technical approach

Build the page in the classifier repository so GitHub Pages publishes it at the
project URL and ownership remains with the software it documents.

Recommended initial structure:

```text
docs/
  index.html
  styles.css
  assets/
    social-card.svg
```

Recommended GitHub Pages source: `main` branch, `/docs` folder.

Keep the first version buildless:

- Semantic HTML.
- A single CSS file.
- No JavaScript unless navigation behavior genuinely requires it.
- Relative asset paths so the page works under the repository subpath.
- Canonical, Open Graph, and social-card metadata.
- A link back to `https://santiagomode.github.io/`.

If the page later becomes an interactive demo, add that as a separate,
explicitly sandboxed phase rather than embedding model execution in the first
marketing page.

## Accessibility and quality requirements

- Logical heading order and landmarks.
- Keyboard-visible focus states.
- Minimum WCAG AA contrast.
- No meaning conveyed by color alone.
- Table headers associated with their data.
- Reduced-motion support.
- Responsive layout from 320px through wide desktop screens.
- Copy remains understandable without the diagrams.
- External links identify their destination in accessible names.

## Delivery phases

### Phase 1: Source and content validation

- Reconfirm the current README, model, input schema, output filenames, license,
  and installation requirements.
- Draft synthetic examples and review them for accidental real-world data.

### Phase 2: First complete static page

- Create the `/docs` page shell and project-specific styles.
- Implement the hero, input-to-output demonstration, workflow, architecture,
  limitations, and calls to action.
- Add metadata and the portfolio backlink.

### Phase 3: Verification

- Validate all internal and external links.
- Test the page at the repository subpath, not only at localhost root.
- Check semantic HTML, keyboard navigation, contrast, reduced motion, and
  responsive wrapping.
- Confirm no sensitive data or unsupported claims appear.

### Phase 4: Publish and connect

- Enable GitHub Pages from `main` and `/docs`.
- Verify the public project URL.
- Replace the portfolio's `Page planned` state with a `Visit project` link.
- Confirm both the portfolio-to-project and project-to-portfolio paths.

## Acceptance criteria

- A nontechnical stakeholder can explain the input, decision process, and
  outputs after reading the page.
- The page shows one end-to-end synthetic example.
- Every factual claim matches the repository at publish time.
- The page explicitly requires human review and avoids accounting-advice
  language.
- The default experience makes no network or model calls.
- The page works at `/capex_opex_classifier/` with relative assets.
- The repository, portfolio, and project page link to one another.
- GitHub Pages serves the page successfully over HTTPS.

## Deferred ideas

- Downloadable synthetic sample CSVs.
- A browser-only result explorer using committed synthetic JSON.
- Before/after reviewer workflow examples.
- Versioned documentation tied to releases.
- A fully interactive classifier demo, only after privacy, resource, and
  security requirements are defined.
