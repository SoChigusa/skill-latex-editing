---
name: latex-editing
description: Edit and compile LaTeX source files using durable source-layout and build-artifact conventions, including overwrite-in-place latexdiff output for fine-grained revisions. Use whenever Codex creates or modifies .tex manuscripts, notes, reviews, reports, or other LaTeX documents. Apply alongside domain-specific skills such as paper coauthoring; this skill governs LaTeX source formatting and compilation outputs, not the document's substantive content.
---

# LaTeX Editing

## Apply the source convention

- Preserve the project's existing structure, macros, bibliography system, and unrelated user changes.
- Put a physical newline after every complete prose sentence in edited text.
- Keep each sentence on one source line unless an existing structural construct requires otherwise.
- Do not mistake abbreviations, decimal points, citation keys, or command arguments for sentence endings.
- Keep display mathematics, environments, lists, tables, and command-only lines formatted according to their LaTeX structure.
- When changing a prose paragraph, reflow the changed paragraph so all of its sentences follow the sentence-per-line convention.

## Coordinate prose editing

- Apply the `english-composition` skill when editing English prose. Let it govern wording and author-specific prose preferences while this skill governs LaTeX source and build conventions.

## Interpret inline author comments

- Treat a blanket request to address manuscript comments as an instruction to honor each comment according to its own wording, not as permission to turn every comment into a source edit.
- Comments that explicitly ask to "tell me on console," "answer in chat," or otherwise request a response outside the manuscript are questions, not editing instructions. Preserve both the surrounding manuscript text and the inline comment verbatim, and answer only in the user-facing conversation unless the user separately asks to incorporate the answer into the document.
- Do not remove a question-only inline comment merely because it has been answered in the conversation unless the user explicitly asks to remove resolved comments.
- For comments that do request a manuscript change, identify the conceptual purpose from the comment and nearby argument before editing. A request to explain motivation or meaning should not be replaced by numerical settings, implementation details, or other technically related information that does not answer that purpose.
- Follow any project-specific convention that distinguishes actionable author-comment macros from private note macros, and leave non-actionable comment macros untouched.

## Show fine-grained revisions with latexdiff

- For a local or fine-grained revision to an existing LaTeX document, preserve the root source immediately before the requested edit in a temporary baseline and generate a latexdiff against the completed source.
- Compile the latexdiff and provide both its `.tex` source and PDF so the user can inspect the changes directly.
- Use stable output names derived from the document root, such as `<root>_latexdiff.tex` and `<root>_latexdiff.pdf`.
- Overwrite the same latexdiff files for each subsequent revision request; do not create a new diff file or add an instruction-specific suffix for every request unless the user explicitly asks to retain a history.
- Remove the temporary baseline after the diff has been generated and verified; do not accumulate per-request source snapshots in the project.
- Prefer word-level markup for prose. If fine-grained math markup produces invalid LaTeX, use whole-equation markup or another minimally coarser setting that compiles without changing the manuscript source.
- Apply the compilation, verification, and build-artifact cleanup rules below to the latexdiff document as well.

## Keep layout work proportional

- Continue to correct local typesetting problems, such as overfull boxes, clipping, or collisions, when they occur in or immediately around the material changed by the current request.
- Treat ordinary manuscript edits as iterative steps rather than final typesetting passes. Do not chase downstream pagination changes or adjust unrelated parts of the manuscript merely to optimize the document's overall appearance.
- Do not introduce manuscript-wide line-spacing, text-height, float-placement, page-balancing, or similar global layout adjustments unless the user explicitly requests full-document formatting or visual polish.
- When the user does explicitly request a whole-manuscript layout pass, inspect the complete rendered output and perform the same careful level of visual adjustment across the document, including downstream pagination and float placement.

## Compile and verify

1. Identify the document's root `.tex` file and its established build command from project instructions, a `Makefile`, or Latexmk configuration.
2. Compile after editing and enable SyncTeX generation. With Latexmk, prefer `latexmk -pdf -synctex=1 <root>.tex` plus the project's usual interaction and error flags. With a direct TeX engine, pass `-synctex=1`.
3. Treat the edit as verified only if the build succeeds and both `<root>.pdf` and `<root>.synctex.gz` exist. If the document uses BibTeX or Biber, also verify that `<root>.bbl` exists.
4. After a successful build, retain only the generated `<root>.bbl`, `<root>.pdf`, and `<root>.synctex.gz` files. A document without a bibliography need not produce a `.bbl`.
5. Delete all other files generated by that build, such as `.aux`, `.bcf`, `.blg`, `.fdb_latexmk`, `.fls`, `.log`, `.out`, `.run.xml`, and `.toc` files. Resolve and delete explicit build-output paths; do not use a broad glob or recursive deletion.
6. Never delete source files, bibliography databases, figures, class or style files, project configuration, pre-existing user files, or any file whose provenance as a build output is uncertain.
7. If compilation fails, report the failure and the relevant diagnostic. Do not claim success or conceal the failed build by deleting its log.

## Combine with job-specific skills

Apply this skill concurrently with any relevant content or workflow skill.
Let the job-specific skill govern scientific content, argumentation, citations, voice, and collaboration workflow.
Let this skill govern sentence-per-line source layout, compilation verification, and retention of only the `.bbl`, PDF, and SyncTeX build artifacts.
Follow an explicit user instruction when it overrides either layer.
