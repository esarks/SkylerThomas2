# How to Create the PDF for "Out of the Swamp"

## The Complete Journey: Individual Files → Final PDF

This document explains the ENTIRE workflow, from 20+ individual markdown files all the way to the final publication-ready PDF with headers, page numbers, and perfect formatting.

---

## 📊 VISUAL WORKFLOW OVERVIEW

```
STEP 1: COMBINE FILES
┌─────────────────────────────────────────────────────────────────┐
│  Individual Markdown Files (skylerthomas2wiki/)                 │
│  ─────────────────────────────────────────────────────────────  │
│  📄 00_title-page.md              ← Title page                  │
│  📄 00_copyright-page.md          ← Copyright info              │
│  📄 00_dedication.md              ← Dedication                  │
│  📄 00_table-of-contents.md       ← Table of Contents           │
│  📄 00_introduction-secular.md    ← Introduction                │
│  📄 01_movement-1-swamp-intro.md  ← Movement 1 intro            │
│  📄 02_chapter-01-my-swamp.md     ← Chapter 1                   │
│  📄 03_chapter-02-but-prayed.md   ← Chapter 2                   │
│  📄 04_chapter-03-stop-decide.md  ← Chapter 3                   │
│  📄 05_chapter-04-dying-changes.md← Chapter 4                   │
│  📄 06_movement-2-waters-edge.md  ← Movement 2 intro            │
│  📄 07_chapter-05-living-waters.md← Chapter 5                   │
│  📄 08_chapter-06-shadow-grace.md ← Chapter 6                   │
│  📄 09_chapter-07-amazing-grace.md← Chapter 7                   │
│  📄 10_chapter-08-dig-deeper.md   ← Chapter 8                   │
│  📄 11_movement-3-rhythms.md      ← Movement 3 intro            │
│  📄 12_chapter-09-rhythms.md      ← Chapter 9                   │
│  📄 13_chapter-10-deep-roots.md   ← Chapter 10                  │
│  📄 14_chapter-11-redemption.md   ← Chapter 11                  │
│  📄 15_chapter-12-nothing-wasted.md← Chapter 12                 │
│  📄 16_chapter-13-devils-run.md   ← Chapter 13                  │
│  📄 17_chapter-14-living-moment.md← Chapter 14                  │
│  📄 99_epilogue.md                ← Epilogue                    │
│  📄 99_about-author.md            ← About the Author            │
│  📄 99_acknowledgments.md         ← Acknowledgments             │
│  📄 99_how-to-access-songs.md     ← How to Access Songs         │
│                                                                  │
│              ⬇️  create_complete_manuscript.py                   │
│              Reads files in order, combines them                │
│              Adds separators between sections                   │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
                              ⬇️
┌─────────────────────────────────────────────────────────────────┐
│  Intermediate File (skylerthomas2/KDP/)                         │
│  ─────────────────────────────────────────────────────────────  │
│  📄 COMPLETE-MANUSCRIPT.md                                       │
│     • All 20+ files combined into one                           │
│     • ~500 KB markdown file                                     │
│     • Includes all text, quotes, headings                       │
│     • Has QR code image references                              │
│     • Contains page break commands (\newpage)                   │
│     • Single source of truth for PDF generation                 │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
                              ⬇️
STEP 2: CREATE PDF WITH FORMATTING
┌─────────────────────────────────────────────────────────────────┐
│              ⬇️  create_pdf_with_headers.py                      │
│              Reads COMPLETE-MANUSCRIPT.md                       │
│              Parses markdown → ReportLab PDF objects            │
│              Adds formatting and page decorations               │
│                                                                  │
│  PARSING PROCESS:                                               │
│  ─────────────────────────────────────────────────────────────  │
│  • Reads line by line                                           │
│  • Converts markdown syntax:                                    │
│    # Heading       → PDF H1 (20pt, bold, centered)             │
│    ## Heading      → PDF H2 (16pt, bold)                        │
│    ### Heading     → PDF H3 (13pt, bold)                        │
│    > Quote         → PDF blockquote (11pt, italic, indented)    │
│    | Table |       → PDF table (grid lines, alternating rows)   │
│    Regular text    → PDF paragraph (11pt, justified)            │
│    ![alt](img.png) → Embedded image (2.5" width)                │
│  • Tracks chapter titles from ### headings                      │
│  • Filters out LaTeX commands (\pagenumbering{arabic})          │
│  • Prevents double page breaks                                  │
│                                                                  │
│  PAGE DECORATION (via NumberedCanvas class):                    │
│  ─────────────────────────────────────────────────────────────  │
│  • Pages 1-5 (front matter):                                    │
│    - NO headers                                                 │
│    - Lowercase Roman numerals at bottom: i, ii, iii, iv, v      │
│  • Page 6+ (main content):                                      │
│    - Chapter title header at TOP (centered, italic, 9pt)        │
│    - Arabic numerals at BOTTOM: 1, 2, 3, 4...                   │
│                                                                  │
│  FORMATTING DETAILS:                                            │
│  ─────────────────────────────────────────────────────────────  │
│  • Page size: 6" x 9" (perfect for KDP)                         │
│  • Margins: 0.75" all sides                                     │
│  • Top margin: 1" (extra space for header)                      │
│  • Body font: Times Roman 11pt                                  │
│  • Quote font: Times Italic 11pt (same size as body!)           │
│  • Line spacing: 14pt leading (comfortable reading)             │
│  • Headings: Times Bold (20/16/13pt)                            │
│  • Alignment: Justified (professional look)                     │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
                              ⬇️
┌─────────────────────────────────────────────────────────────────┐
│  Final Output (skylerthomas2/KDP/)                              │
│  ─────────────────────────────────────────────────────────────  │
│  📕 OUT-OF-THE-SWAMP-COMPLETE.pdf                                │
│     • ~930 KB file size                                         │
│     • ~280-300 pages                                            │
│     • Perfect 6" x 9" KDP format                                │
│     • Chapter titles in headers                                 │
│     • Roman numerals (i-v) for front matter                     │
│     • Arabic numerals (1, 2, 3...) for main content             │
│     • All QR codes embedded                                     │
│     • Professional typography                                   │
│     • READY FOR AMAZON KDP UPLOAD ✅                             │
│                                                                  │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🔄 THE TWO-STEP PROCESS EXPLAINED

### STEP 1: Combine Individual Files → Single Manuscript

**What happens:**
1. Script reads 20+ individual markdown files in order
2. For each file:
   - Opens the file
   - Reads all content
   - Appends to growing array
   - Adds separator (`---`) between files
3. Writes entire combined content to `COMPLETE-MANUSCRIPT.md`
4. Reports file size

**Why this step exists:**
- Individual files are easier to edit and maintain
- Can work on one chapter without affecting others
- Git version control works better with smaller files
- Cleaner organization during writing phase

**Script:** `create_complete_manuscript.py`
**Runtime:** ~2 seconds
**Input:** 20+ individual .md files
**Output:** 1 combined COMPLETE-MANUSCRIPT.md (~500 KB)

---

### STEP 2: Parse Markdown → Create Formatted PDF

**What happens:**
1. **Read Phase:**
   - Opens COMPLETE-MANUSCRIPT.md
   - Reads line by line into memory

2. **Parse Phase:**
   - Walks through each line
   - Identifies markdown elements (headings, quotes, images, tables, etc.)
   - Converts to ReportLab PDF objects:
     - `# Title` becomes centered, bold, 20pt heading
     - `## Section` becomes left-aligned, bold, 16pt heading
     - `### Chapter 1: Title` becomes 13pt heading AND registers chapter title for headers
     - `> Quote text` becomes indented, italic blockquote
     - `| Table |` becomes formatted table with grey header, grid lines, alternating row colors
     - `![QR Code](qr-ch01.png)` becomes embedded 2.5" image
     - Regular text becomes justified 11pt paragraph
   - Filters out LaTeX commands (`\pagenumbering{arabic}`)
   - Tracks when page breaks are added to avoid duplicates

3. **Build Phase:**
   - Assembles all PDF objects into "story" array
   - Creates custom canvas for page decorations
   - Processes story and flows content across pages
   - Canvas adds headers and page numbers as each page is created

4. **Decoration Phase:**
   - For each page that gets created:
     - Checks page number
     - If pages 1-5: adds lowercase Roman numeral (i, ii, iii, iv, v)
     - If page 6+: adds chapter title header at top + Arabic page number at bottom
     - Looks up which chapter we're in from the chapter_map
     - Uses appropriate font size for header based on title length

5. **Write Phase:**
   - Saves completed PDF to disk
   - Reports file size

**Why this step is complex:**
- Professional page numbering (Roman → Arabic)
- Dynamic headers that track current chapter
- Smart spacing and typography
- Image embedding
- Proper PDF structure for KDP

**Script:** `create_pdf_with_headers.py`
**Runtime:** ~25 seconds
**Input:** COMPLETE-MANUSCRIPT.md + QR code images
**Output:** OUT-OF-THE-SWAMP-COMPLETE.pdf (~930 KB)

---

## 🎯 THE CORRECT METHOD (October 11, 2025 - UPDATED 18:40)

### THE SOLUTION - FOUND IT!
The working PDF is created using a **Python script with ReportLab** that builds the PDF directly from the markdown file.

**Script Location:** `/Users/paulmarshall/Documents/GitHub/skylerthomas2wiki/create_pdf_with_headers.py`

### How to Create the PDF (FULLY AUTOMATED):

```bash
cd /Users/paulmarshall/Documents/GitHub/skylerthomas2wiki
python3 create_pdf_with_headers.py
```

**Result:** `OUT-OF-THE-SWAMP-COMPLETE.pdf` (~930 KB) in the KDP folder

### What You Get:
- ✅ **Chapter titles as headers** at the top of each page (centered, italicized)
- ✅ **Lowercase Roman numerals** (i, ii, iii, iv, v) for front matter (pages 1-5)
- ✅ **Arabic numerals** starting at 1 for main content (page 6 onward)
- ✅ Perfect 6" x 9" formatting for KDP
- ✅ All content properly formatted
- ✅ QR codes included

### What DOESN'T Work:
- ❌ **`docx2pdf` Python module** - Installed but does NOT create PDF files on this system
- ❌ **`convert-to-pdf.py` script** - Uses docx2pdf, so doesn't work
- ❌ **`fix-page-numbering.py` script** - Cannot add section breaks properly
- ❌ **LibreOffice soffice** - Creates larger PDFs without proper headers
- ❌ **Pandoc → Word → PDF workflow** - Too many manual steps, headers don't work right

---

## Complete Workflow (QUICK REFERENCE)

### If Editing Individual Chapter Files:

**Step 1: Combine individual markdown files into COMPLETE-MANUSCRIPT.md**
```bash
cd /Users/paulmarshall/Documents/GitHub/skylerthomas2wiki
python3 create_complete_manuscript.py
```

**Step 2: Create the PDF from COMPLETE-MANUSCRIPT.md**
```bash
python3 create_pdf_with_headers.py
```

**Done!** Your PDF is ready at: `/Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/OUT-OF-THE-SWAMP-COMPLETE.pdf`

---

### If Editing COMPLETE-MANUSCRIPT.md Directly:

**Step 1: Edit the combined manuscript:**
```bash
nano /Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/COMPLETE-MANUSCRIPT.md
```

**Step 2: Create the PDF:**
```bash
cd /Users/paulmarshall/Documents/GitHub/skylerthomas2wiki
python3 create_pdf_with_headers.py
```

**Done!** Your PDF is ready.

⚠️ **Warning:** Edits to `COMPLETE-MANUSCRIPT.md` will be lost if you regenerate from individual files

---

## How the Script Works

The `create_pdf_with_headers.py` script:
1. Reads `COMPLETE-MANUSCRIPT.md` from the KDP folder
2. Parses the markdown and converts it to PDF using **ReportLab**
3. Adds chapter titles as **headers** at the top of each page
4. Numbers front matter pages with **lowercase Roman numerals** (i, ii, iii, iv, v)
5. Numbers main content pages with **Arabic numerals** starting at 1
6. Formats for 6" x 9" with proper margins
7. Includes all QR codes and images

---

## Prerequisites

### Required Software:
1. **Python 3** with ReportLab package:
   ```bash
   pip3 install reportlab
   ```

### Key Files:
- **Source:** `/Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/COMPLETE-MANUSCRIPT.md`
- **Script:** `/Users/paulmarshall/Documents/GitHub/skylerthomas2wiki/create_pdf_with_headers.py`
- **Output:** `/Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/OUT-OF-THE-SWAMP-COMPLETE.pdf`

---

## Editing the Markdown

All content edits should be made in `COMPLETE-MANUSCRIPT.md`.

**Page breaks are automatically added before:**
- Each H1 heading (# Heading)
- Contact information, Dedication, Table of Contents
- Introduction and all chapters


---

## Recent Fixes (October 11, 2025)

### Fixed Issues:
- ✅ **Markdown tables now supported** - Tables render with proper formatting, grid lines, and alternating row colors
- ✅ **Blank pages removed** - Script no longer adds double page breaks before H1 headings
- ✅ **Quote font sizes** - All citations and scripture quotes now 11pt (same as body text)
- ✅ **LaTeX commands filtered** - `\pagenumbering{arabic}` and similar commands don't appear in PDF
- ✅ **Chapter headers** - Proper chapter titles displayed at top of each page

---

## Troubleshooting

### Problem: Script not found or can't run
**Solution:** Make sure you're in the correct directory:
```bash
cd /Users/paulmarshall/Documents/GitHub/skylerthomas2wiki
python3 create_pdf_with_headers.py
```

### Problem: Missing ReportLab package
**Solution:** Install ReportLab:
```bash
pip3 install reportlab
```

### Problem: Blank pages appearing
**Solution:** This was fixed on October 11, 2025. Make sure you're using the latest version of `create_pdf_with_headers.py`. The script now tracks page breaks to avoid duplicates.

### Problem: Headers not showing chapter titles
**Solution:** The script automatically extracts chapter titles from H3 headings (### Chapter X). Make sure your markdown has proper heading structure.

### Problem: Page numbers not correct
**Solution:** The script uses Roman numerals (i, ii, iii, iv, v) for pages 1-5 and Arabic numerals starting at 1 from page 6 onward. This is hardcoded in lines 84-94 of the script.

### Problem: QR codes or images not showing
**Solution:** Make sure the image paths in the markdown are correct and the image files exist in the KDP folder.

### Problem: Seeing old/cached PDF
**Solution:** Close and reopen the PDF file. Your PDF viewer may be caching the old version.

---

## Files Overview

### Source Files:
- `/Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/COMPLETE-MANUSCRIPT.md` - The master markdown file (edit this!)

### Generated Files:
- `/Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/OUT-OF-THE-SWAMP-COMPLETE.pdf` - Final PDF for KDP upload

### Scripts:
- `/Users/paulmarshall/Documents/GitHub/skylerthomas2wiki/create_pdf_with_headers.py` - **THE CORRECT SCRIPT TO USE**
- `/Users/paulmarshall/Documents/GitHub/skylerthomas2wiki/create_docx_with_headers.py` - Creates DOCX version (optional)

### QR Code Images:
- All QR code PNG files in the KDP folder
- Referenced in the markdown and automatically included in the PDF

---

## KDP Upload

Once the PDF is generated:
1. Go to kdp.amazon.com
2. Upload `OUT-OF-THE-SWAMP-COMPLETE.pdf` as the paperback interior
3. Settings:
   - ISBN: 979-8-218-83354-1
   - Trim size: 6" x 9"
   - Paper: Cream
   - Estimated pages: ~280-300

---

## Summary: What Actually Works

### ✅ THE CORRECT METHOD (100% Automated):
1. Edit `COMPLETE-MANUSCRIPT.md` (if needed)
2. Run: `cd /Users/paulmarshall/Documents/GitHub/skylerthomas2wiki && python3 create_pdf_with_headers.py`
3. **Done!** (~30 seconds total)

**You get:**
- ✅ Chapter titles as headers
- ✅ Roman numerals for front matter (i, ii, iii, iv, v)
- ✅ Arabic numerals for main content (1, 2, 3...)
- ✅ Perfect formatting for KDP
- ✅ All QR codes included
- ✅ ~930 KB file size

### ❌ What Doesn't Work:
- Pandoc → Word → PDF workflow (no headers, manual steps required)
- docx2pdf Python module (doesn't work on this system)
- LibreOffice soffice (creates larger files without proper headers)
- Manual page numbering in Word (too slow, error-prone)

---

**Last Updated:** October 11, 2025 (18:50)

**Created by:** Claude Code (AI Assistant)

**Tested and Verified:** October 11, 2025 (18:50)

**Changelog:**
- 18:50 - **Added markdown table support** - Tables now render with proper formatting, headers, and styling
- 18:45 - Added comprehensive VISUAL WORKFLOW OVERVIEW with ASCII art flowchart
- 18:45 - Added detailed TWO-STEP PROCESS EXPLAINED section with phase-by-phase breakdown
- 18:45 - Documented complete journey from 20+ individual files → intermediate → final PDF
- 18:45 - Explained what each parsing phase does (Read, Parse, Build, Decoration, Write)
- 18:45 - Added "Why this step exists" and "Why this step is complex" explanations
- 18:40 - Created COMPLETE-WORKFLOW.md documenting entire process from individual files to PDF
- 18:40 - Added reference to complete workflow document at top
- 18:40 - Added two-step process (combine → PDF) to quick reference
- 18:35 - Fixed blank pages caused by double page breaks before H1 headings
- 18:30 - Changed quote font size from 10pt to 11pt to match body text
- 18:24 - Added filter for LaTeX commands (`\pagenumbering{arabic}`)
- 18:24 - Initial documentation of correct method using ReportLab script

---

## 📖 Additional Documentation

For even more detail, see: [`COMPLETE-WORKFLOW.md`](./COMPLETE-WORKFLOW.md) which includes:
- Full directory structure
- File naming conventions
- Technical implementation details
- All troubleshooting scenarios
- Amazon KDP upload instructions
