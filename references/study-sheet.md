# Study sheet guide

Use this when composing a sheet. Default to a non-technical builder who knows what they wanted the project to do but may not write code. Adapt to stated experience, requested depth, and project scope; do not force a research narrative onto an app or invent sections that lack evidence. Keep substantive teaching in the main explanation and use appendices for supporting inventories.

## Opening

Begin with the real-world purpose and a short orientation in the learner's language. Follow with one familiar story, a small system map drawn from inspected code, and the beginning of a concrete journey. Explain where the analogy stops fitting. For experienced readers, shorten familiar foundations and move to the connections they want to understand.

Include the repository, inspected revision or local snapshot, selected scope, and coverage limits in a compact context note. Put concise source pointers beside the relevant claims. Keep detailed evidence tables later in the sheet or in requested notes so the opening remains a lesson. Mark inferred purpose and material uncertainty in plain language.

Explain essential technical terms when they first appear, including words such as function or test if the learner has not indicated familiarity. Introduce terms through the current example; do not begin with a vocabulary dump. Collect useful definitions in a glossary later. A short opening must lead into the requested full explanation, not substitute for it.

## Main explanation

1. **Why it exists and what it does.** The problem, intended user, and central behavior or research question. Use a consistent everyday analogy if it helps; name its limitations.
2. **A map and a reading route.** Normally show a beginner the main parts in a small Mermaid or plain-text diagram derived from inspected code. Use ordinary labels with real filenames underneath or beside them. Verify the arrows and cite their sources; identify grouped steps, unknown connections, and partial coverage. No external diagram service is needed. List the first files/functions to read in order, each with a question it answers, introducing identifiers after their role makes sense. Explain relevant dependencies and environment assumptions when they matter to the journey.
3. **One complete journey.** Start with a real input, example, or test fixture when possible. Trace the values and decisions across files, including validation, storage/external calls, and output. Explain a meaningful failure or boundary case. If an example is invented, label it; if behavior was only read, call it a static walkthrough.
4. **Choices and consequences.** Record the important design decisions, evidence of their reasons, and meaningful rejected alternatives when documented. Mark missing reasons as not documented. Include one small hypothetical change and its likely effects, clearly labelled as a prediction from inspection.
5. **What is supported and what remains uncertain.** Separate implementation, documented promises, reported runs, and interpretation. Explain material contradictions and provenance gaps. Keep limitations beside the claims they qualify.
6. **Practice.** Invite optional guesses tied to actual rules or data: trace an input, predict a change, explain a failure, or locate a behavior. Frame them as opportunities to explore, not a test the reader must pass. Keep answers after the questions so they can be attempted independently, and offer hints or an alternative example. Interactive teaching instead waits for the learner's response unless they prefer explanations without questions.
7. **A compact reference.** Glossary, a plain-labelled code map, key rules, open questions, and an optional one-page cheat sheet. Add 30-second and two-minute explanations when useful to the learner.

Add "You might be wondering..." explanations at points where an important connection would otherwise be skipped. Prefer substantive answers to decorative callout boxes.

Choose depth from the learner's needs. Provide a complete worked journey and preserve the cause-and-effect links across files, even when that takes several paragraphs. Avoid mechanically repeating every topic at three lengths or compressing away the very step a beginner needs. Use unfamiliar terms, learner questions, and actual responses as signals to slow down or explain differently; do not assume reading a section established understanding.

## Conditional material

### Research, experiments, and quantitative results

Include the question, setup, data origin and transformations, scoring/statistical rules, controls or comparisons, and reported results. Explain thresholds, tie-breaks, exclusions, and invalid cases when they affect the conclusion. Cite input data and configuration as well as the result table. Describe uncertainty, missing provenance, and practical magnitude; statistical significance alone does not establish importance or causation.

A p-value describes how unusual the observed statistic, or a more extreme one, would be under the specified null model and assumptions. For example, p = 0.0003 corresponds to about 3 in 10,000 under that model. It is not the probability the finding was "luck" or the hypothesis is false. See the [American Statistical Association statement](https://www.amstat.org/asa/files/pdfs/P-ValueStatement.pdf) when a statistical explanation is needed.

Use a chart when comparing quantities is central. Label units, groups, denominators, and uncertainty where available. Draw every plotted value from identified evidence; do not fabricate a comparison or perform an unstated new experiment.

Include reviewer questions about weaknesses supported by the inspected record. Distinguish an observed limitation from a question that remains unanswered.

### History and decisions

Use relevant commits, plans, corrections, and saved results to show what was tried, learned, and changed. A chronological commit list alone does not establish the author's motivation. Retain failed approaches when they explain the present design. Report recorded tool/process mistakes and their actual consequences without automatically excusing or exaggerating them.

### Applications and libraries

Explain entry points, the public interface, important business rules, data flow, state, integrations, configuration, and failure behavior. Where relevant, distinguish build/deployment intent from evidence of a working deployment. Do not turn the sheet into a comprehensive security or code-quality audit unless that was requested.

### Related work

Connect other projects only when they are already in the user's scope or documented in the inspected sources. Do not roam through the author's repositories to fill a mandatory section.

## Final reading pass

Check that a newcomer can follow every important transition and navigate to the named code. Ask whether the opening tells a comprehensible story, whether essential terms were introduced before relying on them, and whether the map helps explain the worked journey. Verify numbers, data provenance, line pointers, and the revision associated with each claim. Say what was not inspected. Avoid declaring the learner understands something until their own answer demonstrates it.
