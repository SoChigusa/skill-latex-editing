# LaTeX source, bibliography, and build workflow

## Apply the source convention

- Preserve the project's existing structure, macros, bibliography system, quotation and cross-reference conventions, and unrelated user changes.
- Put a physical newline after every complete prose sentence in edited text.
- Keep each sentence on one source line unless an existing structural construct requires otherwise.
- Do not mistake abbreviations, decimal points, citation keys, or command arguments for sentence endings.
- Keep display mathematics, environments, lists, tables, and command-only lines formatted according to their LaTeX structure.
- When changing a prose paragraph, reflow the changed paragraph so all of its sentences follow the sentence-per-line convention.
- Preserve intentional blank lines at paragraph and section boundaries.
- Use `align` for display mathematics unless the project explicitly requires another environment.
- Put separate displayed relations on separate visual lines and align related derivations at `&=` or the relevant comparison operator.
- Avoid unrelated equations side by side; short conditions may share a line when readability improves.
- Use labels and semantic cross-references rather than hard-coded equation or figure numbers.

## Source bibliography entries

Apply the author's standing preference when creating or updating bibliography entries for any LaTeX manuscript or note:

1. Search INSPIRE HEP first. If the work has a record, use its official BibTeX export.
2. If no INSPIRE record exists, consult Google Scholar and use its BibTeX export when available.
3. If neither source has a record, construct the entry from verified bibliographic information, following the INSPIRE BibTeX conventions, and explicitly report which entries were made manually.

Match the work by DOI or arXiv identifier, then title and authors as needed; do not substitute a different work or edition. Preserve existing citation keys unless the author requests renaming. Preserve the authoritative metadata and LaTeX protection of names and titles; record meaningful corrections such as newly available publication details.

Distinguish an absent record from an inaccessible service. If access prevents obtaining an export, try available permitted access methods, then clearly report any manually reconstructed fallback and its verified sources; never label it an official export. This sourcing rule applies to bibliography work, not a requirement to recheck every reference during an unrelated LaTeX edit.

## Show fine-grained revisions with latexdiff

- For a local or fine-grained revision to an existing LaTeX document, preserve the root source immediately before the requested edit in a temporary baseline and generate a latexdiff against the completed source.
- Compile the latexdiff and provide both its `.tex` source and PDF so the user can inspect the changes directly.
- Use stable output names derived from the document root, such as `<root>_latexdiff.tex` and `<root>_latexdiff.pdf`.
- Overwrite the same latexdiff files for each subsequent revision request; do not create a new diff file or add an instruction-specific suffix for every request unless the user explicitly asks to retain a history.
- Remove the temporary baseline after the diff has been generated and verified; do not accumulate per-request source snapshots in the project.
- Prefer word-level markup for prose. If fine-grained math markup produces invalid LaTeX, use whole-equation markup or another minimally coarser setting that compiles without changing the manuscript source.
- Apply the compilation, verification, and build-artifact cleanup rules below to the latexdiff document as well.

## Compile and verify

1. Run `git diff --check` and inspect the focused diff.
2. Identify the document's root `.tex` file and its established build command from project instructions, a `Makefile`, or Latexmk configuration. Preserve the normal output location and SyncTeX behavior so an open editor PDF viewer remains synchronized.
3. Compile after editing with SyncTeX enabled. Use the project command and its usual interaction and error flags. If no command is documented and the project uses Latexmk, run `latexmk -quiet -pdf -synctex=1 -interaction=nonstopmode -halt-on-error <root>.tex` from the source directory. With a direct TeX engine, pass `-synctex=1`.
4. Check the log for errors, undefined references or citations, overfull boxes, and newly introduced warnings before cleaning build outputs.
5. Treat the edit as verified only if the build succeeds and both `<root>.pdf` and `<root>.synctex.gz` exist. If the document uses BibTeX or Biber, also verify that `<root>.bbl` exists.
6. Render and inspect affected PDF pages whenever layout, figures, tables, equations, or floats changed.
7. After a successful build and verification, retain only the generated `<root>.bbl`, `<root>.pdf`, and `<root>.synctex.gz` files. A document without a bibliography need not produce a `.bbl`.
8. Delete all other files generated by that build, such as `.aux`, `.bcf`, `.blg`, `.fdb_latexmk`, `.fls`, `.log`, `.out`, `.run.xml`, and `.toc` files. Resolve and delete explicit build-output paths; do not use a broad glob or recursive deletion.
9. Never delete source files, bibliography databases, figures, class or style files, project configuration, pre-existing user files, or any file whose provenance as a build output is uncertain.
10. If compilation fails, report the failure and the relevant diagnostic. Do not claim success or conceal the failed build by deleting its log.
