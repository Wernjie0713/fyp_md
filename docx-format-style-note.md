# DOCX Format Style Note

This note records the formatting pattern observed in the existing proposal Word document:

- [FYPi Proposal - YONG WERN JIE A22EC0121.docx](C:/laragon/www/marrybrown/fypi_md_split/FYPi%20Proposal%20-%20YONG%20WERN%20JIE%20A22EC0121.docx)

The purpose of this note is to preserve the actual Word styling approach so the final report can follow the same visual structure when the markdown content is transferred into `.docx`.

## 1. Overall Page Setup

- Page size: A4 portrait
- Top margin: about `2.5 cm`
- Bottom margin: about `2.5 cm`
- Left margin: about `3.25 cm`
- Right margin: about `3.25 cm`
- Header distance: about `1.25 cm`
- Footer distance: about `1.25 cm`

## 2. Base Font And Body Formatting

- Base document font: `Times New Roman`
- Base font size: `12 pt`
- Normal line spacing: `1.5 lines`

The proposal document uses custom body paragraph styles rather than relying only on plain `Normal`.

Main body styles found:

- `Para 2 lines`
- `Para 4 lines`
- `Para 2a`
- `Para 4a`

## 3. Main Body Paragraph Style

### 3.1 Normal body paragraph

Use style:

- `Para 2 lines`

Observed formatting:

- alignment: justified
- first-line indent: `36 pt` (about `1.27 cm`)
- after spacing: about `10 pt`
- intended use: standard body paragraph

### 3.2 Last paragraph before next section

Use style:

- `Para 4 lines`

Observed formatting:

- alignment: justified
- first-line indent: `36 pt`
- after spacing: about `20 pt`
- intended use: final paragraph before the next heading or section break

This confirms that the "last paragraph need 4 lines spacing" rule is handled by paragraph style, not by manually pressing Enter multiple times.

### 3.3 Transitional variants

Additional styles found:

- `Para 2a`
- `Para 4a`

These appear to be transition variants with top spacing and are useful when a paragraph needs visual separation without using the exact standard paragraph pattern.

## 4. Chapter And Heading Style

### 4.1 Chapter title

Use style:

- `Heading 1`

Observed behaviour:

- uppercase chapter title presentation
- strong chapter separation
- large gap after heading, about `48 pt`
- heading is kept with the next paragraph

Examples:

- `INTRODUCTION`
- `LITERATURE REVIEW`
- `METHODOLOGY`
- `ANALYSIS AND DESIGN`

### 4.2 Section heading

Use style:

- `Heading 2`

Observed behaviour:

- bold
- about `10 pt` spacing after
- kept with next paragraph

Examples:

- `Introduction`
- `Problem Background`
- `System Analysis`

### 4.3 Subsection heading

Use style:

- `Heading 3`

Observed behaviour:

- bold
- about `10 pt` spacing after
- kept with next paragraph

Examples:

- `Sales and Payment Reporting in Vendor-Managed POS Environments`
- `Case Study Context (Continuity Reporting for Sales and Payments)`

### 4.4 Deeper technical subsection

Use style:

- `Heading 4`

Observed behaviour:

- bold
- about `10 pt` spacing after
- kept with next paragraph

Examples:

- `Data Sources and Replication Boundary`
- `Refresh Cadence and Idempotent Load Pattern`

## 5. Preface / Front Matter Headings

Use style:

- `TITLE AT PREFACE`

Observed use:

- `ABSTRACT`
- `ABSTRAK`
- `LIST OF TABLES`
- similar front-matter title pages

This style gives the formal preface heading appearance and large separation below the heading.

## 6. Abstract Formatting

Main abstract style found:

- `Abstract 1.5 line`

Observed formatting:

- alignment: justified
- first-line indent: `36 pt`
- based on the normal `1.5 line` reading pattern

Additional style found:

- `Abstract Single Line`

This appears to be a variant for cases where single-line spacing is intentionally required in abstract-related content.

## 7. Figure Caption Style

Figure captions are placed below the figure or figure placeholder.

### 7.1 Single-line figure caption

Use style:

- `Caption for Figure`

Observed formatting:

- alignment: centered
- line spacing: single
- top spacing before caption: about `5 pt`

### 7.2 Multi-line figure caption

Use style:

- `Caption for Figure 2 line`

Observed formatting:

- alignment: justified
- line spacing: single
- top spacing before caption: about `5 pt`

Interpretation:

- short figure captions are centered
- longer figure captions may be switched to the 2-line justified caption style

## 8. Table Caption Style

Table captions are placed above the table, following the supervisor's correction for the final thesis.

### 8.1 Single-line table caption

Use style:

- `Caption for Table`

Formatting guidance:

- alignment: centered
- line spacing: single
- keep a consistent gap between the caption and the table

### 8.2 Multi-line table caption

Use style:

- `Caption for Table 2 lines`

Formatting guidance:

- alignment: justified
- line spacing: single
- keep a consistent gap between the caption and the table

Interpretation:

- short table captions are centered
- longer table captions are justified using the 2-line variant

## 9. Table Styling

Most tables in the proposal document use:

- `Table Grid`
- `Table Grid1`

Observed pattern:

- full bordered academic table layout
- simple row/column structure
- header row as labelled cells
- no decorative visual styling

This is appropriate to keep for the final report because it matches standard university report presentation.

## 10. Table Of Contents / List Pages

TOC styles found:

- `toc 1`
- `toc 2`
- `toc 3`
- `toc 4`
- `toc 5`
- `toc 6`

List-entry style found:

- `table of figures`

Observed formatting for list-style entries:

- justified
- single-spaced
- hanging indent

This is the style family used for:

- table of contents
- list of tables
- list of figures

## 11. References Formatting

References heading style observed:

- `References`

Reference-entry style observed:

- `List of References`

Observed reference-entry behaviour:

- hanging indent of about `36 pt`
- suitable for standard bibliography formatting

This means the final report references should keep:

- `Times New Roman`
- `12 pt`
- hanging indent bibliography structure

## 12. Appendix Formatting

Appendix heading style observed:

- `Appendix`

Observed formatting:

- centered
- bold
- single-spaced
- about `12 pt` spacing after

Appendix content then follows the same body paragraph, table, and caption system as the main chapters.

## 13. Recommended Style Mapping For Final Report

When building the final report `.docx`, the safest style mapping is:

- chapter title: `Heading 1`
- section title: `Heading 2`
- subsection title: `Heading 3`
- deeper technical subsection: `Heading 4`
- normal body paragraph: `Para 2 lines`
- last paragraph before next heading: `Para 4 lines`
- short figure caption: `Caption for Figure`
- long figure caption: `Caption for Figure 2 line`
- short table caption: `Caption for Table`
- long table caption: `Caption for Table 2 lines`
- tables: `Table Grid` or `Table Grid1`
- references list entry: `List of References`
- appendix title: `Appendix`

## 14. Important Note

The proposal `.docx` still contains old proposal-stage content in areas such as:

- table of contents
- list of figures
- list of tables
- appendix entries

That old content should not be copied as content reference.

However, the Word style system itself is still the correct formatting reference for:

- heading hierarchy
- paragraph spacing
- last-paragraph spacing pattern
- caption placement
- table presentation
- reference formatting

## 15. Practical Final-Report Rule

For the final report `.docx`, preserve this visual pattern:

1. use `Heading 1` for each chapter title
2. use `Heading 2` / `Heading 3` / `Heading 4` according to hierarchy
3. use `Para 2 lines` for normal paragraphs
4. use `Para 4 lines` for the last paragraph before the next heading
5. put figure captions below figures
6. put table captions above tables
7. keep all content in `Times New Roman 12 pt`
8. keep tables simple and bordered
9. keep references in hanging-indent format
