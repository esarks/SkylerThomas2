# Complete Workflow: Individual Files → Final PDF

## Overview of the Complete Process

This document describes the ENTIRE workflow from individual markdown files all the way to the final PDF ready for Amazon KDP.

**Created:** October 11, 2025 (18:40)
**Last Updated:** October 11, 2025 (18:40)

---

## Directory Structure

```
/Users/paulmarshall/Documents/GitHub/
├── skylerthomas2wiki/              # Source markdown files and scripts
│   ├── 00_title-page.md
│   ├── 00_copyright-page.md
│   ├── 00_dedication.md
│   ├── 00_table-of-contents.md
│   ├── 00_introduction-secular.md
│   ├── 01_movement-1-swamp-intro-secular.md
│   ├── 02_chapter-01-my-swamp-secular.md
│   ├── 03_chapter-02-but-then-i-prayed-secular.md
│   ├── 04_chapter-03-stop-decide-secular.md
│   ├── 05_chapter-04-dying-changes-secular.md
│   ├── 06_movement-2-waters-edge-intro-secular.md
│   ├── 07_chapter-05-living-waters-edge-secular.md
│   ├── 08_chapter-06-shadow-grace-secular.md
│   ├── 09_chapter-07-amazing-grace-secular.md
│   ├── 10_chapter-08-dig-deeper-secular.md
│   ├── 11_movement-3-unforced-rhythms-intro-secular.md
│   ├── 12_chapter-09-unforced-rhythms-secular.md
│   ├── 13_chapter-10-deep-roots-secular.md
│   ├── 14_chapter-11-redemptions-story-secular.md
│   ├── 15_chapter-12-nothing-wasted-secular.md
│   ├── 16_chapter-13-devils-run-secular.md
│   ├── 17_chapter-14-living-moment-secular.md
│   ├── 99_epilogue.md
│   ├── 99_about-author.md
│   ├── 99_acknowledgments.md
│   ├── 99_how-to-access-songs.md
│   ├── create_complete_manuscript.py      # STEP 1 SCRIPT
│   └── create_pdf_with_headers.py         # STEP 2 SCRIPT
│
└── skylerthomas2/KDP/              # Output directory
    ├── COMPLETE-MANUSCRIPT.md      # Combined file (output of Step 1)
    ├── OUT-OF-THE-SWAMP-COMPLETE.pdf  # Final PDF (output of Step 2)
    └── qr-*.png                    # QR code images

```

---

## The Complete 2-Step Process

### STEP 1: Combine Individual Files → COMPLETE-MANUSCRIPT.md

**Script:** `create_complete_manuscript.py`

**Location:** `/Users/paulmarshall/Documents/GitHub/skylerthomas2wiki/create_complete_manuscript.py`

**What it does:**
1. Reads all individual markdown files in the correct order
2. Combines them into a single `COMPLETE-MANUSCRIPT.md` file
3. Adds section separators (`---`) between files
4. Outputs to: `/Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/COMPLETE-MANUSCRIPT.md`

**Command:**
```bash
cd /Users/paulmarshall/Documents/GitHub/skylerthomas2wiki
python3 create_complete_manuscript.py
```

**File Order (as defined in the script):**
1. Front matter:
   - `00_title-page.md`
   - `00_copyright-page.md`
   - `00_dedication.md`
   - `00_table-of-contents.md`
2. Introduction:
   - `00_introduction-secular.md`
3. Movement 1 (In the Swamp):
   - `01_movement-1-swamp-intro-secular.md`
   - `02_chapter-01-my-swamp-secular.md`
   - `03_chapter-02-but-then-i-prayed-secular.md`
   - `04_chapter-03-stop-decide-secular.md`
   - `05_chapter-04-dying-changes-secular.md`
4. Movement 2 (At the Water's Edge):
   - `06_movement-2-waters-edge-intro-secular.md`
   - `07_chapter-05-living-waters-edge-secular.md`
   - `08_chapter-06-shadow-grace-secular.md`
   - `09_chapter-07-amazing-grace-secular.md`
   - `10_chapter-08-dig-deeper-secular.md`
5. Movement 3 (Unforced Rhythms):
   - `11_movement-3-unforced-rhythms-intro-secular.md`
   - `12_chapter-09-unforced-rhythms-secular.md`
   - `13_chapter-10-deep-roots-secular.md`
   - `14_chapter-11-redemptions-story-secular.md`
   - `15_chapter-12-nothing-wasted-secular.md`
   - `16_chapter-13-devils-run-secular.md`
   - `17_chapter-14-living-moment-secular.md`
6. Back matter:
   - `99_epilogue.md`
   - `99_about-author.md`
   - `99_acknowledgments.md`
   - `99_how-to-access-songs.md`

**Output:**
- File: `COMPLETE-MANUSCRIPT.md` (~500 KB)
- Location: `/Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/COMPLETE-MANUSCRIPT.md`

---

### STEP 2: COMPLETE-MANUSCRIPT.md → PDF with Headers & Page Numbers

**Script:** `create_pdf_with_headers.py`

**Location:** `/Users/paulmarshall/Documents/GitHub/skylerthomas2wiki/create_pdf_with_headers.py`

**What it does:**
1. Reads `COMPLETE-MANUSCRIPT.md`
2. Parses markdown and converts to PDF using ReportLab
3. Adds chapter titles as headers at top of each page
4. Numbers front matter with lowercase Roman numerals (i, ii, iii, iv, v)
5. Numbers main content with Arabic numerals starting at 1 (from page 6 onward)
6. Formats for 6" x 9" with 0.75" margins
7. Includes all QR codes and images
8. Filters out LaTeX commands like `\pagenumbering{arabic}`
9. Avoids double page breaks

**Command:**
```bash
cd /Users/paulmarshall/Documents/GitHub/skylerthomas2wiki
python3 create_pdf_with_headers.py
```

**Features:**
- ✅ Chapter titles as headers (centered, italicized, Times Roman 9pt)
- ✅ Page numbers at bottom center
- ✅ Roman numerals for front matter (i-v)
- ✅ Arabic numerals for main content (1, 2, 3...)
- ✅ Body text: Times Roman 11pt
- ✅ Block quotes: Times Italic 11pt (same size as body)
- ✅ Headings: Times Bold (20pt H1, 16pt H2, 13pt H3)
- ✅ QR codes: 2.5" width
- ✅ Perfect 6" x 9" KDP format

**Output:**
- File: `OUT-OF-THE-SWAMP-COMPLETE.pdf` (~930 KB)
- Location: `/Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/OUT-OF-THE-SWAMP-COMPLETE.pdf`

---

## Complete Workflow (Quick Reference)

### Full 2-Step Command Sequence:

```bash
# STEP 1: Combine individual markdown files
cd /Users/paulmarshall/Documents/GitHub/skylerthomas2wiki
python3 create_complete_manuscript.py

# STEP 2: Create PDF with headers and page numbers
python3 create_pdf_with_headers.py
```

**Total time:** ~45 seconds
**Result:** Publication-ready PDF for Amazon KDP

---

## Editing Workflow

### To Edit a Single Chapter:

1. **Edit the individual markdown file:**
   ```bash
   # Example: Edit Chapter 5
   nano /Users/paulmarshall/Documents/GitHub/skylerthomas2wiki/07_chapter-05-living-waters-edge-secular.md
   ```

2. **Regenerate the complete manuscript:**
   ```bash
   cd /Users/paulmarshall/Documents/GitHub/skylerthomas2wiki
   python3 create_complete_manuscript.py
   ```

3. **Regenerate the PDF:**
   ```bash
   python3 create_pdf_with_headers.py
   ```

### To Edit the Complete Manuscript Directly:

If you need to make quick fixes to the combined manuscript:

1. **Edit COMPLETE-MANUSCRIPT.md directly:**
   ```bash
   nano /Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/COMPLETE-MANUSCRIPT.md
   ```

2. **Regenerate only the PDF:**
   ```bash
   cd /Users/paulmarshall/Documents/GitHub/skylerthomas2wiki
   python3 create_pdf_with_headers.py
   ```

**⚠️ Warning:** If you edit `COMPLETE-MANUSCRIPT.md` directly, those changes will be LOST the next time you run `create_complete_manuscript.py`. Make permanent changes in the individual chapter files.

---

## Individual File Naming Convention

Files are numbered to ensure correct order:

- **00_** = Front matter (title, copyright, dedication, TOC, introduction)
- **01-17_** = Main content (movements and chapters)
- **99_** = Back matter (epilogue, about author, acknowledgments)

Within each number:
- **movement-X** = Movement introduction pages
- **chapter-XX** = Full chapter files
- **-secular** suffix = Secular/inclusive version (vs. overtly religious)

---

## Prerequisites

### Required Software:

1. **Python 3** (already installed)

2. **ReportLab package:**
   ```bash
   pip3 install reportlab
   ```

### Required Files:

1. All individual markdown files in `/Users/paulmarshall/Documents/GitHub/skylerthomas2wiki/`
2. QR code images in `/Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/`
3. Both Python scripts in the wiki directory

---

## What Each Script Does (Technical Details)

### create_complete_manuscript.py

**Input:** Individual markdown files (00-99)
**Output:** Single combined `COMPLETE-MANUSCRIPT.md`

**Process:**
1. Defines file order in a Python list
2. Reads each file in sequence
3. Appends content to array
4. Adds `---` separator between files
5. Writes combined content to KDP folder
6. Reports file size and location

**Key features:**
- Skips missing files with warning
- Preserves all markdown formatting
- Maintains file order exactly as specified

### create_pdf_with_headers.py

**Input:** `COMPLETE-MANUSCRIPT.md`
**Output:** `OUT-OF-THE-SWAMP-COMPLETE.pdf`

**Process:**
1. Reads and parses markdown line by line
2. Converts markdown elements to PDF using ReportLab:
   - `# Heading` → H1 (20pt, bold, centered)
   - `## Heading` → H2 (16pt, bold)
   - `### Heading` → H3 (13pt, bold)
   - `> Quote` → Block quote (11pt, italic, indented)
   - `![alt](image.png)` → Embedded image
   - Regular text → Body paragraph (11pt, justified)
3. Tracks chapter titles from H3 headings
4. Uses custom canvas class (NumberedCanvas) to add:
   - Headers with chapter titles
   - Page numbers (Roman i-v, then Arabic 1, 2, 3...)
5. Filters out LaTeX commands (`\pagenumbering`, etc.)
6. Prevents double page breaks

**Key features:**
- Custom page numbering (Roman → Arabic)
- Chapter-aware headers
- Smart page break handling
- QR code embedding
- Proper spacing and margins
- Professional typography

---

## Recent Fixes (October 11, 2025)

### Version History:

**18:35** - Fixed blank pages
- Issue: Double page breaks before H1 headings (Dedication, TOC, etc.)
- Solution: Track `just_added_pagebreak` flag to avoid duplicates
- Result: No more blank pages between sections

**18:30** - Fixed quote font sizes
- Issue: Block quotes were 10pt (smaller than body text)
- Solution: Changed quote_style fontSize from 10 to 11
- Result: All text same size, citations match body

**18:24** - Filtered LaTeX commands
- Issue: `\pagenumbering{arabic}` appearing in PDF
- Solution: Added filter to skip lines starting with `\pagenumbering`
- Result: Clean PDF without LaTeX markup

**Initial Creation (October 10-11, 2025)**
- Created `create_complete_manuscript.py`
- Created `create_pdf_with_headers.py`
- Implemented ReportLab-based PDF generation
- Added chapter headers and page numbering

---

## Troubleshooting

### Problem: "File not found" when running scripts
**Solution:** Make sure you're in the correct directory:
```bash
cd /Users/paulmarshall/Documents/GitHub/skylerthomas2wiki
```

### Problem: Missing ReportLab module
**Solution:**
```bash
pip3 install reportlab
```

### Problem: Individual chapter files not found
**Solution:** All chapter files should be in `/Users/paulmarshall/Documents/GitHub/skylerthomas2wiki/`. Check that all files exist with correct names.

### Problem: QR codes not appearing in PDF
**Solution:** Make sure QR code PNG files exist in `/Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/` and are referenced correctly in the markdown.

### Problem: PDF looks old/cached
**Solution:** Close and reopen your PDF viewer. Mac Preview often caches files.

### Problem: Blank pages in PDF
**Solution:** This was fixed on October 11, 2025. Make sure you're using the latest version of `create_pdf_with_headers.py`.

### Problem: Wrong page numbering
**Solution:** The script hardcodes Roman numerals for pages 1-5 and Arabic from page 6+. This assumes 5 pages of front matter. If your front matter is longer/shorter, adjust lines 84-94 in the script.

---

## File Locations Reference

### Source Files:
```
/Users/paulmarshall/Documents/GitHub/skylerthomas2wiki/
├── 00_title-page.md
├── 00_copyright-page.md
├── 00_dedication.md
├── 00_table-of-contents.md
├── 00_introduction-secular.md
├── 01-17_*.md (chapters)
├── 99_epilogue.md
├── 99_about-author.md
├── 99_acknowledgments.md
└── 99_how-to-access-songs.md
```

### Scripts:
```
/Users/paulmarshall/Documents/GitHub/skylerthomas2wiki/
├── create_complete_manuscript.py
└── create_pdf_with_headers.py
```

### Output Files:
```
/Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/
├── COMPLETE-MANUSCRIPT.md
├── OUT-OF-THE-SWAMP-COMPLETE.pdf
└── qr-*.png
```

---

## Amazon KDP Upload

Once the PDF is generated, you're ready to publish:

1. **Go to:** kdp.amazon.com
2. **Upload:** `OUT-OF-THE-SWAMP-COMPLETE.pdf`
3. **Settings:**
   - ISBN: 979-8-218-83354-1
   - Trim size: 6" x 9"
   - Paper: Cream
   - Estimated pages: ~280-300
4. **Upload your cover** (use KDP Cover Calculator for dimensions)

---

## Summary

### The Complete Process:

1. **Edit** individual markdown files in `skylerthomas2wiki/`
2. **Run** `create_complete_manuscript.py` to combine files
3. **Run** `create_pdf_with_headers.py` to create final PDF
4. **Upload** to Amazon KDP

### What Makes This Work:

- **Individual files** = Easy to edit and maintain
- **Combined manuscript** = Single source for PDF generation
- **ReportLab PDF** = Professional formatting with headers and page numbers
- **Two-step process** = Separation of concerns (combine vs. format)

### Key Success Factors:

✅ Files numbered in correct order (00-99)
✅ Scripts in same directory as source files
✅ Output directory exists (KDP folder)
✅ ReportLab installed
✅ QR codes in correct location

---

**This workflow has been tested and verified on October 11, 2025.**

**Created by:** Claude Code (AI Assistant)
**For:** Skyler Thomas - "Out of the Swamp: How I Found Truth"
