---
name: md-to-pdf
description: Converts a markdown or MDX file to a clean PDF
disable-model-invocation: true
allowed-tools: Read, Write, Bash
argument-hint: [file-path]
---

Convert the given markdown or MDX file to a PDF.

## Steps

1. Read the file at `$ARGUMENTS`.
2. Parse the YAML frontmatter (content between the opening `---` and closing `---`). Extract the `title` field if present. Remove the entire frontmatter block from the content.
3. If a title was extracted, prepend `# <title>\n\n` to the content so it appears as the PDF heading.
4. Determine the output PDF name from the original filename: strip the extension and append `.pdf`. Example: `openclaw-aws-ec2-setup-guide.mdx` becomes `openclaw-aws-ec2-setup-guide.pdf`. The PDF goes in the same directory as the source file.
5. Write the processed content to a temporary file in the same directory as the source file. Name it `_temp-pdf-export.md`.
6. Run: `npx --yes md-to-pdf _temp-pdf-export.md` (from the source file's directory).
7. Rename the resulting `_temp-pdf-export.pdf` to the final PDF name determined in step 4.
8. Delete `_temp-pdf-export.md`.
9. Report the full path to the generated PDF.

## Rules

- If the file has no frontmatter, skip steps 2-3 and convert the content as-is.
- Do not modify the source file.
- If a PDF with the target name already exists, overwrite it without asking.
