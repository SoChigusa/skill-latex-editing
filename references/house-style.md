# Academic manuscript house style

## Editorial standard

- Write publication-facing prose, not a work log or a reply to reviewer-style prompts.
- Lead each section or subsection with enough motivation that a reader knows the physical or statistical question before encountering detailed formulas.
- Prefer a few coherent subsections over many short fragments.
- Keep claims concise, positive, and proportionate to the evidence.
- Explain why an approximation is appropriate and what is neglected, but do not reproduce every exploratory discussion from the working conversation.
- Preserve useful caveats without allowing them to obscure the main argument.

## Definitions and notation

- Define every symbol where it first appears.
- State the physical meaning of parameters, controls, outcomes, probability laws, priors, policies, and test statistics.
- State domains, normalization, units, and conditioning when they are not obvious.
- Make time labels and indexing conventions explicit.
- State dependencies needed to interpret each symbol and prefer existing notation and macros over synonyms.
- Do not reuse one symbol for different objects.
- Search globally before adding a definition; move or consolidate an existing definition instead of duplicating it.
- Keep notation consistent across prose, equations, figure labels, captions, appendices, and code-generated artifacts.

## Mathematical presentation

- Introduce a displayed equation in prose and explain its consequence afterward.
- Number only equations that are referenced or structurally useful.
- Avoid unexplained changes of approximation order, hypothesis convention, divergence orientation, or averaging measure.

## Scientific narrative

A strong local flow is usually:

1. State the physical or statistical problem.
2. Define the model and assumptions.
3. Define observables, controls, and statistical quantities.
4. Present the calculation or numerical procedure.
5. State the result.
6. Interpret it and delimit its validity.

Use contrasts only when they clarify the science.
Do not write “A is C, not B” merely because the author asked that question during drafting.

## Maintain claim discipline

- Distinguish assumptions, definitions, approximations, diagnostics, numerical observations, and proved results.
- Do not call a heuristic, benchmark, or restricted optimum globally optimal.
- Distinguish simulation results from experimental results.
- Distinguish posterior probability or Bayes factors from calibrated frequentist power.

## Statistical language

- Define the null and alternative hypotheses and say when the alternative is composite.
- Define Type-I error, Type-II error, power, and the rejection rule before using them.
- Calibrate the global false-positive rate for the complete policy and search, including look-elsewhere effects.
- For composite alternatives, label pointwise, nuisance-averaged, prior-averaged, and worst-case performance distinctly.
- A fixed-budget power uses a predetermined sample count and an ensemble of repeated records.
- A single posterior trajectory is diagnostic, not a power curve.
- A sequential stopping rule requires calibration over the stopping procedure, not only at its endpoint.
- Use QFI or CFI only for estimation or local-geometry statements they support.
- Match the information measure to the operational question: total variation or full finite-record distributions for finite-budget discrimination, KL or relative entropy for suitable asymptotic error exponents, and Fisher information for local estimation geometry.

## Figures and tables

- Inspect the actual figure or table artifact before changing its size, caption, or interpretation.
- Update the filename, float width, caption, body discussion, and cross-references together.
- Choose one- or two-column width from legibility, aspect ratio, and author preference.
- Describe what each panel shows and define line styles, markers, colors, reference values, and injected parameters.
- Make captions self-contained about panels and conditions; reserve interpretation for the body.
- Avoid repeating the caption verbatim in the body.
- Keep figure numbering and reading order stable.
- Prevent deferred floats from appearing in a later section or after unrelated material.
- Check tables for units, normalization, significant figures, and explanatory column headings.

## Literature discipline

- Verify the physical mechanism, state preparation, measurement basis, and observable before calling another work an instance of the manuscript's protocol.
- Separate Rabi transitions, Ramsey phase accumulation, oscillator or magnon detection, photon counting, and mechanically mediated sensing when those distinctions matter.
- Prefer primary papers for technical claims and authoritative sources for standards or software behavior.
- Verify that every added citation directly supports the associated claim. Inspect the relevant method instead of classifying a work by its title alone.
- Do not pad the bibliography with adjacent but physically different systems.
- Cite a paper once within a continuous discussion, including adjacent sentences that develop the same point. Repeat its citation only when the context changes, not merely because a new sentence or paragraph begins. Place the citation so that the supported claims are clear; consolidate repeated citations locally without removing later citations in a different context. Preserve citations inside coauthor comments and original passages explicitly kept for reference.
