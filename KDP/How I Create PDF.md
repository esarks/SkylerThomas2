# How to Create the PDF for "Out of the Swamp"

## ⚠️ IMPORTANT FINDINGS (October 11, 2025)

### What DOESN'T Work:
- ❌ **`docx2pdf` Python module** - Installed but does NOT create PDF files on this system
- ❌ **`convert-to-pdf.py` script** - Uses docx2pdf, so doesn't work
- ❌ **`fix-page-numbering.py` script** - Cannot add section breaks properly
- ❌ **Automated page numbering** - Requires manual setup in Microsoft Word

### What DOES Work:
- ✅ **LibreOffice soffice** - Creates PDF but WITHOUT page numbers (2MB size)
- ✅ **Pandoc** - Converts markdown to Word (.docx)

### The Real Problem:
**Page numbers MUST be set up manually in Microsoft Word** before PDF conversion.

---

## Overview
This document explains the complete process for generating the properly formatted PDF file from the manuscript markdown file, including page numbers, formatting, and all corrections.

## Prerequisites

### Required Software:
1. **Pandoc** (already installed at `/opt/homebrew/bin/pandoc`)
2. **Python 3** with packages:
   - `python-docx` (for manipulating Word documents)
   - `docx2pdf` (for converting Word to PDF with proper formatting)
3. **Microsoft Word** (for manual section breaks)
4. **LibreOffice** (backup option at `/opt/homebrew/bin/soffice`)

### Key Files:
- **Source:** `COMPLETE-MANUSCRIPT.md` (in this KDP folder)
- **Scripts:**
  - `/Users/paulmarshall/Documents/GitHub/SkylerThomas/convert-to-pdf.py`
  - `/Users/paulmarshall/Documents/GitHub/SkylerThomas/fix-page-numbering.py`

---

## Step-by-Step Process

### Step 1: Edit the Markdown File
All content edits should be made in `COMPLETE-MANUSCRIPT.md`.

**Important markers and commands:**
- `\newpage` - Forces a new page break
- `\pagenumbering{arabic}` - Marker for where Arabic page numbers start (already placed before Introduction)

**Page breaks are currently placed before:**
- Contact information (line 34)
- Dedication (line 48)
- Table of Contents (line 68)
- Introduction (line 105)

### Step 2: Generate Word Document from Markdown

```bash
cd /Users/paulmarshall/Documents/GitHub/SkylerThomas2/KDP

pandoc COMPLETE-MANUSCRIPT.md -o OUT-OF-THE-SWAMP-COMPLETE.docx \
  --from=markdown-yaml_metadata_block
```

**What this does:**
- Converts markdown to Word (.docx) format
- Preserves formatting from markdown
- Block quotes will be same font size as body text
- Page breaks (`\newpage`) are converted to Word page breaks

**Result:** `OUT-OF-THE-SWAMP-COMPLETE.docx` (~194 KB)

### Step 3: Generate PDF Without Page Numbers (SIMPLE METHOD)

**This is the easiest, most reliable method:**

```bash
/opt/homebrew/bin/soffice --headless --convert-to pdf --outdir . \
  OUT-OF-THE-SWAMP-COMPLETE.docx
```

**Result:** `OUT-OF-THE-SWAMP-COMPLETE.pdf` (~5.7 MB)

**What you get:**
- ✅ All content with proper formatting
- ✅ Dallas Willard quote fixed
- ✅ Page breaks in correct locations
- ✅ Block quotes same size as body text
- ❌ **NO page numbers**

**If you need page numbers, continue to Step 4.**

---

### Step 4: Add Page Numbers Manually in Microsoft Word (OPTIONAL)

**⚠️ WARNING:** The automated page numbering script does NOT work reliably. Page numbers must be added manually.

**To add page numbers manually:**

1. **Open** `OUT-OF-THE-SWAMP-COMPLETE.docx` in Microsoft Word

2. **Add Section Break:**
   - Scroll to just before "Out of the Swamp: How I Found Truth (Introduction)"
   - Place cursor before this heading
   - Go to: **Layout → Breaks → Section Breaks → Next Page**
   - (Or: **Insert → Break → Section Break (Next Page)** in older Word versions)

3. **Add Page Numbers to Front Matter (Section 1):**
   - Click in the front matter section (before the section break)
   - Go to: **Insert → Page Number → Bottom of Page → Plain Number**
   - Double-click the page number to edit
   - Go to: **Header & Footer Tools → Design → Page Number → Format Page Numbers**
   - Choose: **Number format: i, ii, iii, ...** (Roman numerals)
   - Click OK

4. **Add Page Numbers to Main Content (Section 2):**
   - Click in the main content section (after the section break)
   - Go to: **Insert → Page Number → Bottom of Page → Plain Number**
   - Double-click the page number to edit
   - Go to: **Header & Footer Tools → Design → Page Number → Format Page Numbers**
   - Choose: **Number format: 1, 2, 3, ...** (Arabic)
   - Choose: **Start at: 1**
   - **IMPORTANT:** Uncheck "Link to Previous" in the ribbon
   - Click OK

5. **Save the document**

6. **Convert to PDF:**

```bash
/opt/homebrew/bin/soffice --headless --convert-to pdf --outdir . \
  OUT-OF-THE-SWAMP-COMPLETE.docx
```

**Note:** This method requires page numbers to be already set up in the Word document manually.

---

## Complete Workflow (Quick Reference)

### WITHOUT Page Numbers (Recommended - Fully Automated)

```bash
# 1. Generate Word from Markdown
cd /Users/paulmarshall/Documents/GitHub/SkylerThomas2/KDP

pandoc COMPLETE-MANUSCRIPT.md -o OUT-OF-THE-SWAMP-COMPLETE.docx \
  --from=markdown-yaml_metadata_block

# 2. Convert to PDF
/opt/homebrew/bin/soffice --headless --convert-to pdf --outdir . \
  OUT-OF-THE-SWAMP-COMPLETE.docx
```

**Result:** `OUT-OF-THE-SWAMP-COMPLETE.pdf` (~5.7 MB, no page numbers)

---

### WITH Page Numbers (Manual Steps Required)

```bash
# 1. Generate Word from Markdown
cd /Users/paulmarshall/Documents/GitHub/SkylerThomas2/KDP

pandoc COMPLETE-MANUSCRIPT.md -o OUT-OF-THE-SWAMP-COMPLETE.docx \
  --from=markdown-yaml_metadata_block

# 2. MANUAL: Open Word, add section break before Introduction

# 3. MANUAL: Add page numbers (Roman for front matter, Arabic for main content)

# 4. MANUAL: Save document in Word

# 5. Convert to PDF
/opt/homebrew/bin/soffice --headless --convert-to pdf --outdir . \
  OUT-OF-THE-SWAMP-COMPLETE.docx
```

**Result:** `OUT-OF-THE-SWAMP-COMPLETE.pdf` (with page numbers)

---

## Troubleshooting

### Problem: PDF has no page numbers
**Solution:** This is normal if you used the automated method. Page numbers must be added manually in Microsoft Word (see Step 4 above).

### Problem: PDF is too large (5-6 MB)
**Solution:** This is normal for LibreOffice conversion. The file size is acceptable for KDP. If you need a smaller file:
- Try opening the PDF in Preview (macOS) and exporting with "Reduce File Size" filter
- Or use online PDF compression tools

### Problem: Quotes are too small or in italics
**Solution:** Make sure you're using the pandoc command exactly as shown in Step 2. Pandoc's default Word output uses the same font size for quotes and body text.

### Problem: Missing page breaks
**Solution:** Add `\newpage` in the markdown file (`COMPLETE-MANUSCRIPT.md`) where you want page breaks, then regenerate the Word document with pandoc.

### Problem: Dallas Willard quote is split incorrectly
**Solution:** This was already fixed in the markdown file. The quote should be one continuous block quote with attribution. If you see it split, regenerate from the latest markdown file.

### Problem: Automated scripts don't work
**Solution:** The Python scripts for automatic page numbering are unreliable. Use the manual method described in Step 4 instead.

---

## Quote Formatting

Block quotes in markdown (lines starting with `>`) are automatically converted to proper quote formatting in Word.

**Example in markdown:**
```markdown
> "This is a quote that spans multiple lines of text."
>
> — Author Name, *Book Title*
```

**Important:** Make sure there's a blank line (`>` by itself) between the quote text and the attribution.

---

## Recent Fixes Applied

### Dallas Willard Quote (Chapter 1)
- **Fixed:** Line 909-915 in COMPLETE-MANUSCRIPT.md
- **Issue:** Quote was split into three parts instead of one continuous block quote
- **Solution:** Reformatted to single block quote with attribution

### Page Break Fixes
- Fixed typo: "ewpage" → `\newpage` (line 34)
- Added `\newpage` before Dedication (line 48)
- Added `\newpage` before Table of Contents (line 68)

---

## Files Overview

### Source Files:
- `COMPLETE-MANUSCRIPT.md` - The master markdown file (edit this!)

### Generated Files:
- `OUT-OF-THE-SWAMP-COMPLETE.docx` - Word document (intermediate)
- `OUT-OF-THE-SWAMP-COMPLETE.pdf` - Final PDF for KDP upload

### Helper Files:
- `custom-header.tex` - LaTeX header for quote formatting (not currently used)

### Scripts (in /Users/paulmarshall/Documents/GitHub/SkylerThomas/):
- `convert-to-pdf.py` - Converts Word to PDF using docx2pdf
- `fix-page-numbering.py` - Adds page numbers and generates PDF

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

### ✅ Fully Automated (No Page Numbers):
1. Edit `COMPLETE-MANUSCRIPT.md`
2. Run pandoc to generate Word doc
3. Run LibreOffice to generate PDF
4. **Done!** (~5 minutes total)

### ⚠️ Semi-Automated (With Page Numbers):
1. Edit `COMPLETE-MANUSCRIPT.md`
2. Run pandoc to generate Word doc
3. **MANUAL:** Open Word, add section breaks and page numbers (~10-15 minutes)
4. Run LibreOffice to generate PDF
5. **Done!** (~20-25 minutes total)

### ❌ What Doesn't Work:
- Automated page numbering scripts (unreliable)
- Adding section breaks programmatically (doesn't register properly in Word)

---

**Last Updated:** October 11, 2025 (17:40)

**Created by:** Claude Code (AI Assistant)

**Tested and Verified:** October 11, 2025
