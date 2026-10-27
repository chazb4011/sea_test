# SEA Evidence Inputs and Workflow

READ BEFORE USING THIS FILE

- `START_HERE_SEA_GLOBAL_RULES.md`
- `02_PROCESS/SEA_GUIDANCE/GENERAL_SEA_GUIDANCE.md`
- `03_TEMPLATES/SEA_OUTPUT_TEMPLATE.md`
- The applicable family guidance and question records

## PURPOSE

This file defines the assessment workflow and evidence-retrieval process.

Policy decisions are controlled by `START_HERE_SEA_GLOBAL_RULES.md`.

Question-specific gates, allowed answers, and answer definitions are controlled by the applicable question record.

## REQUIRED INPUTS

Use the following when available:

- Vendor name
- Product or service name
- UTAN
- Current assessment year
- Current-year vendor evidence location
- Prior-year vendor evidence location
- Output location

If UTAN is unavailable, use the vendor and product or service identity.

Do not use evidence when the vendor, product, service, or scope cannot be established well enough to prevent cross-vendor or cross-product use.

## AUTHORIZED EVIDENCE LOCATION

Use only the vendor evidence location authorized for the assessment.

Treat source evidence as read-only.

Do not:

- Modify, rename, move, delete, or overwrite source files
- Save generated output into the evidence location
- Search adjacent vendor folders merely because they are accessible

Apply the `PROHIBITED EVIDENCE` rules in `START_HERE_SEA_GLOBAL_RULES.md`.

A prohibited file may be skipped without opening it when its filename, folder, or metadata clearly identifies the prohibited type.

## EVIDENCE INVENTORY

Build one compact inventory before evaluating questions.

The inventory is a navigation aid. It is not evidence.

For each candidate source, record:

```text
Exact Source:
Evidence Folder:
Direct Source Location:
Evidence Year or Period:
Source Type:
Readable: Yes | Partial | No
Likely Relevance: Gate Facts | LM | CM | VM | Cross-Cutting | Unknown
Scope or Limitation:
```

Use filenames, metadata, indexed content, headings, and targeted inspection to route evidence.

Do not fully read every source merely to complete the inventory.

Do not treat a filename or keyword match as proof of content.

For partially readable sources:

- Use only reliable content
- Record the limitation
- Do not reconstruct unreadable content
- Continue using other evidence

Before evaluating questions, review the entire current sn_grc_profile evidence, including the issue information at the bottom of the profile.

Apply any current issues found there to relevant SEA questions, using the precedence rules in START_HERE_SEA_GLOBAL_RULES.md.

If an issue may be relevant but the profile does not contain enough detail to resolve its impact, use Needs Human Review. Do not let weaker positive evidence resolve the question.

## SOC 2 RUNTIME BEHAVIOR

Before building the evidence inventory, convert each authorized PDF in the evidence folder to Markdown.

PDF conversion:
- Use the locally installed MarkItDown utility.
- Try markitdown first, or python3 -m markitdown, whichever works.
- Write the converted files to a local temp folder outside the evidence and output folders.
- Use the converted Markdown, not the PDF, for evidence review.
- Use the source PDF only when the Markdown conversion is unusable or needed to resolve a source citation.
- Delete the temporary Markdown files after the final output is written.

SOC 2 handling:
- When a Markdown conversion of an authorized SOC 2 is available, use the Markdown as the working evidence.
- Do not require a prepared digest.
- If no usable Markdown conversion exists, the original SOC 2 PDF may be read directly.
- Treat the Markdown and original SOC 2 as the same evidence source.
- Cite the original SOC 2 by document name and the best reliable locator available, such as original page, section, heading, Trust Services Criteria, or control identifier.
- Never guess or reconstruct an original page number.

## CURRENT-YEAR EVIDENCE

Start with current assessment-year evidence.

Do not automatically process the entire prior-year folder.

Use prior-year evidence only for a specific question when:

- No current-year vendor folder exists
- Current-year evidence does not address the required fact
- Current-year evidence is insufficient for a defensible answer
- A current bridge letter requires an older SOC 2 digest or report for context

## PRIOR-YEAR FALLBACK

When prior-year evidence is needed:

1. Identify the exact missing fact.
2. Search only for prior-year evidence likely to establish that fact.
3. Confirm that the source applies to the same vendor, product, service, and scope.
4. Check for newer contradictory evidence.
5. Stop when the fact is defensibly established or no likely source remains.
6. Record the evidence year and fallback reason in the final Basis.

Prior-year evidence does not automatically receive Low confidence.

Do not present prior-year evidence as current-year evidence.

## BRIDGE LETTERS

When a bridge letter extends an older SOC 2 period:

- Confirm that both documents apply to the same vendor service and scope
- Preserve the SOC 2 audit period
- Preserve the bridge-letter date and covered period
- Preserve material changes, incidents, exceptions, or limitations stated in the letter
- Cite both sources when both are needed

Do not treat a bridge letter as independent auditor testing unless it explicitly contains such testing.

## REUSABLE GATE FACTS

Before detailed question evaluation, identify only the reusable facts needed to apply gates.

Examples include:

- Vendor-built or NM-built
- Vendor-operated or NM-operated
- Vendor-hosted, SaaS, or NM-hosted
- Software, Hardware, Purchase Dataset, or Other scope
- Whether applicable source code exists
- Whether containers or container images are used
- Whether production and lower environments exist
- Whether DAST applicability facts are available
- Whether audit logging exists
- LM2 category when established

For each fact, preserve:

```text
Fact:
Evidence Folder:
Exact Source:
Best Available Location:
Confidence:
Limitation:
```

Do not create a gate fact from assumption, reputation, marketing, a previous SEA, or a threat-model conclusion.

## REQUIRED ASSESSMENT ORDER

1. Read `START_HERE_SEA_GLOBAL_RULES.md`.
2. Read this file completely.
3. Read `02_PROCESS/SEA_GUIDANCE/GENERAL_SEA_GUIDANCE.md`.
4. Read `03_TEMPLATES/SEA_OUTPUT_TEMPLATE.md`.
5. Record the assessment identity, scope, evidence locations, and output location.
6. Confirm that the evidence location belongs to the intended vendor and scope.
7. Build the evidence inventory once.
8. Establish reusable gate facts.
9. Before each question family, read that family guidance file once.
10. Read each applicable question record when evaluating that question.
11. Evaluate LM in dependency order.
12. Evaluate CM in question order.
13. Evaluate VM in question order.
14. Run the final consistency check in the global rules.
15. Produce one consolidated output using `SEA_OUTPUT_TEMPLATE.md`.
16. Save the output without overwriting an existing run folder.

## QUESTION ORDER

### LM

1. LM1
2. LM2
3. LM3
4. LM4
5. LM5
6. LM6

Evaluate each LM gate in order.

LM2 and LM6 are mutually exclusive for substantive evaluation, but both receive a question block. Record N/A for the question whose hosting prerequisite fails.

### CM

1. CM1
2. CM2
3. CM3
4. CM4

### VM

1. VM1
2. VM2
3. VM3
4. VM4
5. VM5
6. VM6

The question record controls the exact gate and allowed answers.

## PER-QUESTION PROCESS

For each question:

1. Read the entire question record.
2. Evaluate the gate before searching for question-specific evidence.
3. If the gate clearly fails:
   - Answer N/A.
   - Identify the failed gate and supporting evidence.
   - Do not perform additional question-specific searches.
   - Continue.
4. If the gate is satisfied:
   - Use the LLM-friendly question and answer definitions.
   - Identify every material fact or clause.
   - Select likely evidence from the inventory.
   - Review only the evidence needed to determine the answer.
5. Apply the evidence, outcome, confidence, and citation policies in the global rules.
6. Preserve the best available evidence reference during the first successful review.
7. Confirm that the result remains consistent with the original SEA question.
8. Use the original SEA question in the final output.
9. Continue to the next question.

When different sources establish different required facts, apply the `COMBINED EVIDENCE` and `FACT-TO-EVIDENCE CHECK` sections in the global rules.

## SEARCH AND CREDIT DISCIPLINE

- Read global rules, process guidance, and family guidance once
- Build the inventory once
- Evaluate gates before detailed searches
- Use targeted searches and targeted reading
- Reuse gate facts, evidence references, and prior source reviews
- Stop when the complete answer is defensibly supported and no unresolved higher-precedence contradiction exists
- Do not read unrelated evidence merely to increase document count
- Do not treat repeated weak claims as stronger proof
- Do not stall to improve an already usable citation

Efficiency must not remove material exceptions, qualifiers, customer responsibilities, scope limitations, or contradictory evidence.

## OUTPUT LOCATION

Save generated output only under:

```text
100_OUTPUT/Name_UTAN/
```

If `Name_UTAN` does not exist:

1. Create `Name_UTAN`.
2. Create `SEA` beneath it.
3. Save the run under `SEA`.

If `Name_UTAN` exists but `SEA` does not:

1. Create `SEA`.
2. Save the run under `SEA`.

If `SEA` already exists, including an empty `SEA` folder:

1. Do not overwrite, delete, rename, or reuse it.
2. Create `SEA_MMYY` using the current month and two-digit year.
3. Save the run under `SEA_MMYY`.

If `SEA_MMYY` already exists, create the next sequential folder:

```text
SEA_MMYY_02
SEA_MMYY_03
SEA_MMYY_04
```

For the September 2026 Workday UTAN 48015 test, an existing empty `SEA` folder means the new run folder is:

```text
100_OUTPUT/Workday_48015/SEA_0926/
```

Save every artifact from the run inside the selected SEA run folder.

## FAILURE HANDLING

Do not halt the entire assessment because one source or question fails.

For an unreadable or inaccessible source:

- Record the exact source and limitation
- Continue using other evidence
- Apply the global outcome rules to affected questions

For a missing question record:

- Do not invent the question logic
- Record the missing record
- Mark the affected question Needs Human Review
- Continue evaluating available records

For uncertain vendor or service scope:

- Do not use unverified evidence
- Record the scope problem
- Continue only where defensible

## FINAL RULE

This workflow produces a first-pass assessment package subject to the human-ownership rules in `START_HERE_SEA_GLOBAL_RULES.md`.
