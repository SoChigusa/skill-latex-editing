---
name: latex-editing
description: Draft, revise, review, and compile academic LaTeX manuscripts and technical notes while preserving author intent. Use for prose, equations, notation, figures, tables, author comments, and BibTeX work, including mechanical LaTeX edits, INSPIRE-first bibliography sourcing, and latexdiff verification.
---

# LaTeX Editing

Treat the manuscript as a polished scientific argument, not as a transcript of the author–assistant conversation.
For prose drafting, revision, review, or citation placement, read [references/house-style.md](references/house-style.md).
Before modifying LaTeX or bibliography files, or compiling a document, read the relevant sections of [references/latex-workflow.md](references/latex-workflow.md): source conventions, bibliography sourcing, latexdiff, and build verification.
For local revisions, preserve the temporary latexdiff baseline before editing.

## Establish the editing contract

1. Determine whether the user requested an explanation, a review, or a manuscript edit.
2. Do not edit files for a console-only derivation, question, or diagnosis.
3. Inspect repository instructions, manuscript macros, journal class, build commands, and the current Git diff before editing.
4. Preserve unrelated user changes and local style unless the user explicitly asks for a global conversion.
5. Apply the user's explicit scope narrowly; do not turn a local correction into an unsolicited rewrite.

For a comment-only review, apply `latex-collaborative-revision` when relevant and let its designated-macro and comment-preservation workflow govern the review. The comment rules below are defaults for direct revision; explicit user scope and project-specific conventions take precedence.

## Handle author comments safely

Discover the comment macros before responding.
Use this default convention when the manuscript defines these commands:

- Treat `\rem{...}` as an actionable revision request.
- Resolve only the `\rem{...}` comments in scope, incorporate the necessary content into clean prose, and remove those resolved comments.
- Treat `\comm{...}` as the author's private note.
- Never delete, answer, paraphrase, or use a `\comm{...}` note as authorization to rewrite the manuscript unless the user explicitly says to do so.

Do not treat every `\rem{...}` as immediate authorization to edit.
If a comment contains `Question`, `discussion`, `discuss`, `console`, or otherwise asks for an opinion, explanation, choice, or joint decision, treat it as a deliberative comment:

1. Leave the comment and manuscript text unchanged.
2. Answer the question in the console, explain the relevant options, and give a recommendation when useful.
3. Wait for the author's explicit decision before editing the manuscript or removing the comment.

A general request to “address the comments” does not override this deliberative-comment rule.
If one comment mixes an explicit revision instruction with a request for discussion, pause the manuscript edit for that comment and resolve the ambiguity with the author first.

If the project specifies different semantics, follow the project-specific convention instead.

## Revise in context

1. Read the complete paragraph and subsection around the target.
2. Search the whole manuscript for every affected symbol, definition, label, citation, figure, table, and repeated explanation.
3. Identify the logical role of the passage before rewriting it.
4. Write the shortest complete argument that preserves scientific accuracy.
5. Remove obsolete or duplicate definitions created by the revision.
6. Re-read the surrounding transition and the manuscript-wide terminology after the edit.

Do not encode the dialogue in the paper.
When the author asks whether “A is really C rather than B,” write the final positive account of C unless the A/B contrast is scientifically necessary.

## Verify and hand off

Apply the compilation, log inspection, visual verification, latexdiff, and artifact-retention rules in [references/latex-workflow.md](references/latex-workflow.md).
Confirm that protected author comments and unrelated files did not change.
Report the completed outcome, the files changed, the verification performed, and any unresolved issue.
