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

For a comment-only review, apply `latex-collaborative-revision` when available and relevant and let its designated-macro and comment-preservation workflow govern the review. The comment rules below are defaults for direct revision; explicit user scope and project-specific conventions take precedence.

## Coordinate prose editing

- Apply the `english-composition` skill when editing English prose. Let it govern wording and author-specific prose preferences while this skill governs LaTeX source and build conventions.

## Handle author comments safely

Treat a blanket request to address manuscript comments as an instruction to honor each comment according to its own wording, not as permission to turn every comment into a source edit.

Discover the comment macros before responding.
Use `\rem{...}` for the author's requests and questions to Codex and `\AI{...}` for Codex's inline replies, unless the user explicitly designates another pair.
All other comment macros, including `\SC{...}`, `\mm{...}`, `\nw{...}`, and `\comm{...}`, are protected collaboration history: preserve each complete invocation verbatim, its occurrence count, its order within the comment thread, and its association with the relevant passage.
When the user requests moving or restructuring a passage, move its attached comments with it as needed; separate permission to move those comments is not required.
Do not delete, rewrite, resolve, rename, or convert this history, or move comments independently of their associated passage, unless the user explicitly requests that change to those comments.
A comment remains protected even when its point has been addressed in the revised prose or it appears obsolete or redundant; a general request to revise the manuscript or address comments does not authorize deleting comments or modifying their contents.

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

Comments that explicitly ask to "tell me on console," "answer in chat," or otherwise request a response outside the manuscript must be answered only in the user-facing conversation, preserving both the surrounding manuscript text and the inline comment verbatim unless the user separately asks to incorporate the answer into the document.
Do not remove a question-only inline comment merely because it has been answered in the conversation unless the user explicitly asks to remove resolved comments.

A general request to “address the comments” does not override this deliberative-comment rule.
If one comment mixes an explicit revision instruction with a request for discussion, pause the manuscript edit for that comment and resolve the ambiguity with the author first.

If the project specifies different semantics, follow the project-specific convention instead.

## Revise in context

1. Read the complete paragraph and subsection around the target.
2. Search the whole manuscript for every affected symbol, definition, label, citation, figure, table, and repeated explanation.
3. Identify the logical role of the passage before rewriting it. For comments that request a manuscript change, identify the conceptual purpose from the comment and nearby argument. A request to explain motivation or meaning should not be replaced by numerical settings, implementation details, or other technically related information that does not answer that purpose.
4. Write the shortest complete argument that preserves scientific accuracy.
5. Remove obsolete or duplicate definitions created by the revision.
6. Re-read the surrounding transition and the manuscript-wide terminology after the edit.

Do not encode the dialogue in the paper.
When the author asks whether “A is really C rather than B,” write the final positive account of C unless the A/B contrast is scientifically necessary.

## Keep layout work proportional

- Continue to correct local typesetting problems, such as overfull boxes, clipping, or collisions, when they occur in or immediately around the material changed by the current request.
- Treat ordinary manuscript edits as iterative steps rather than final typesetting passes. Do not chase downstream pagination changes or adjust unrelated parts of the manuscript merely to optimize the document's overall appearance.
- Do not introduce manuscript-wide line-spacing, text-height, float-placement, page-balancing, or similar global layout adjustments unless the user explicitly requests full-document formatting or visual polish.
- When the user does explicitly request a whole-manuscript layout pass, inspect the complete rendered output and perform the same careful level of visual adjustment across the document, including downstream pagination and float placement.

## Verify and hand off

Apply the compilation, log inspection, visual verification, latexdiff, and artifact-retention rules in [references/latex-workflow.md](references/latex-workflow.md).
Compare protected comment invocations against the pre-edit source, checking complete contents, occurrence counts, order within each thread, and association with the relevant passage; inspect any relocation to confirm that it follows an authorized passage move or restructuring.
Do not rely only on counts or an unordered comparison, and do not require unchanged global comment order or placement when passages move.
Confirm that unrelated files did not change, and do not strip protected comments from latexdiff inputs to simplify a build.
Report the completed outcome, the files changed, the verification performed, and any unresolved issue.
