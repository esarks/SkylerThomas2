# Out of the Swamp: Publications Workflow

**Complete workflow documentation for generating publication-ready files**

---

## Overview

This workflow generates three publication files from markdown source files:
1. **COMPLETE-MANUSCRIPT.md** - Combined manuscript from all chapter files
2. **OUT-OF-THE-SWAMP-KDP-READY.pdf** - KDP paperback-ready PDF (6" × 9")
3. **OUT-OF-THE-SWAMP.epub** - EPUB for ebook distribution

---

## Directory Structure

```
/Users/paulmarshall/Documents/GitHub/skylerthomas2wiki/
├── create_complete_manuscript.py
├── create_pdf_kdp_ready.py
├── create_epub.py
├── 00_title-page.md
├── 00_copyright-page.md
├── 00_dedication.md
├── 00_table-of-contents.md
├── 00_introduction-secular.md
├── 01_movement-1-swamp-intro-secular.md
├── 02_chapter-01-my-swamp-secular.md
├── 03_chapter-02-but-then-i-prayed-secular.md
├── 04_chapter-03-stop-decide-secular.md
├── 05_chapter-04-dying-changes-secular.md
├── 06_movement-2-waters-edge-intro-secular.md
├── 07_chapter-05-living-waters-edge-secular.md
├── 08_chapter-06-shadow-grace-secular.md
├── 09_chapter-07-amazing-grace-secular.md
├── 10_chapter-08-dig-deeper-secular.md
├── 11_movement-3-unforced-rhythms-intro-secular.md
├── 12_chapter-09-unforced-rhythms-secular.md
├── 13_chapter-10-deep-roots-secular.md
├── 14_chapter-11-redemptions-story-secular.md
├── 15_chapter-12-nothing-wasted-secular.md
├── 16_chapter-13-devils-run-secular.md
├── 17_chapter-14-living-moment-secular.md
├── 99_epilogue.md
└── 99_about-author.md

/Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/
├── COMPLETE-MANUSCRIPT.md (generated)
├── OUT-OF-THE-SWAMP-KDP-READY.pdf (generated)
├── OUT-OF-THE-SWAMP.epub (generated)
├── image_cache/ (cached images from remote URLs)
├── qr-ch01-i-will-rise.png
├── qr-ch02-but-then-i-prayed.png
├── qr-ch03-stop.png
├── qr-ch04-dying-changes.png
├── qr-ch05-living-waters-edge.png
├── qr-ch06-shadow-grace.png
├── qr-ch07-amazing-grace.png
├── qr-ch08-dig-deeper.png
├── qr-ch09-mindful-bliss.png
├── qr-ch10-trust-you-lord.png
├── qr-ch11-redemption-story.png
├── qr-ch12-nothing-wasted.png
├── qr-ch13-devils-run.png
└── qr-ch14-this-moment.png
```

---

## Running the Complete Workflow

### Command

From the `/Users/paulmarshall/Documents/GitHub/skylerthomas2wiki/` directory:

```bash
python3 create_complete_manuscript.py && \
python3 create_pdf_kdp_ready.py && \
python3 create_epub.py
```

### Expected Output

```
✓ COMPLETE-MANUSCRIPT.md: ~336 KB
✓ OUT-OF-THE-SWAMP-KDP-READY.pdf: ~10 MB (includes 3 photos + 14 QR codes)
✓ OUT-OF-THE-SWAMP.epub: ~8 MB
```

---

## Critical Formatting Rules

### 1. Song Lyrics Formatting

**RULE: Song lyrics MUST end with a blank line before the `---` divider**

**Correct Pattern:**
```markdown
I'm gonna dig, dig a little deeper,
'Til I find my soul.

---
## Key Takeaways
```

**Incorrect Pattern (causes bolding):**
```markdown
'Til I find my soul.
---
## Key Takeaways
```

**Why:** Without the blank line, markdown parsers treat the last lyric as part of a paragraph that continues with the `---`, causing formatting issues (bolding, heading conflicts).

**All 14 chapters MUST follow this pattern:**
- Chapter 1: My Swamp
- Chapter 2: But Then I Prayed
- Chapter 3: STOP!! And Make a Decision
- Chapter 4: Dying Changes Everything
- Chapter 5: Living Waters Edge
- Chapter 6: In the Shadow of Your Grace
- Chapter 7: Amazing Grace I Did Receive
- Chapter 8: Dig a Little Deeper
- Chapter 9: Unforced Rhythms of Grace
- Chapter 10: Deep Roots, Strong Growth
- Chapter 11: Redemption's Story
- Chapter 12: Nothing is Wasted
- Chapter 13: Devil's On The Run
- Chapter 14: Living in the Moment

### 2. Photo Embedding

**Three photos must be embedded:**

1. **Chapter 1 - Swamp/Alligator (Sawgrass Lake Park)**
   ```markdown
   <img src="https://www.skylerthomas.com/wp-content/uploads/2015/01/IMG_0589_tonemapped.jpg" alt="Alligator in Sawgrass Lake Park" />
   *Sawgrass Lake Park, St. Petersburg, FL*
   ```
   - Location: After "The Wayfarer Moment" section, before "Song Integration"
   - Size in PDF: 4.5" × 3.0"

2. **Chapter 5 - Lake Hefner Boat Ramp**
   ```markdown
   <img src="https://www.skylerthomas.com/wp-content/uploads/2015/05/HefnerBridge-v20140412d-Blue-Sky_tonemapped.jpg" alt="Lake Hefner boat ramp" />
   *Oklahoma City, Lake Hefner*
   ```
   - Location: In "The Wayfarer Moment" section
   - Size in PDF: 4.5" × 3.4"

3. **Chapter 6 - Shadow of Grace**
   ```markdown
   <img src="https://www.skylerthomas.com/wp-content/uploads/2018/09/CRW_3969-1-199x300.jpg" alt="In the Shadow of Your Grace" />
   ```
   - Location: After opening scripture, before audio link
   - Size in PDF: 4.3" × 6.5" (portrait orientation)

**Image Handling:**
- Remote images are automatically downloaded and cached in `image_cache/` directory
- Cache uses MD5 hash of URL as filename
- Images scaled to fit within 4.5" width × 6.5" height while preserving aspect ratio
- Images centered on page
- 0.1" spacer added after each image

### 3. QR Codes

**14 QR codes (one per chapter) are embedded:**
- Format: `![Scan to listen: Song Title](qr-chXX-filename.png)`
- Size: 1.3" × 1.3" (square)
- Location: After song audio link, before main chapter content
- Files must exist in `/Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/` directory

### 4. Chapter Opening Scriptures

**Each chapter MUST have an opening scripture after the chapter title:**

- **Chapter 1:** Augustine, *Confessions*
- **Chapter 2:** Psalm 142:1
- **Chapter 3:** Deuteronomy 30:19
- **Chapter 4:** Galatians 2:20
- **Chapter 5:** John 4:14
- **Chapter 6:** Psalm 91:1
- **Chapter 7:** Ephesians 2:8
- **Chapter 8:** Jeremiah 29:13 (NOT Jeremiah 17:8 - that's in Chapter 10)
- **Chapter 9:** Matthew 11:28-30 (full passage including verse 30)
- **Chapter 10:** Jeremiah 17:7-8 (full passage with "tree planted by water")
- **Chapter 11:** 2 Corinthians 5:17 (NOT Genesis 50:20)
- **Chapter 12:** Romans 8:28
- **Chapter 13:** Colossians 2:15
- **Chapter 14:** Exodus 3:14

**NOTE:** Chapters 8 and 10 previously had duplicate scriptures. This has been fixed.

---

## PDF Requirements (KDP Paperback)

### Format Specifications
- **Page size:** 6" × 9"
- **Margins:** 0.75" all sides
- **Font:** Times New Roman (fully embedded)
- **Pagination:**
  - Front matter (i, ii, iii, iv, v): Title, Copyright, Dedication, TOC, Introduction
  - Main content (1, 2, 3...): Chapters and epilogue
- **Headers:** Running headers on all pages except title page

### Font Embedding
- **CRITICAL:** All fonts MUST be fully embedded for KDP acceptance
- Times New Roman must be available on system: `/Library/Fonts/Times New Roman.ttf`
- Script verifies font embedding in final PDF
- If fonts not embedded, PDF will be rejected by KDP

### Image Quality
- Photos: High resolution (300 DPI minimum when possible)
- QR codes: Sharp, scannable at print size
- All images compressed appropriately for file size

---

## EPUB Requirements

### Features
- Reflowable text (adapts to screen size)
- Auto-generated table of contents (navigation)
- All metadata embedded (title, author, ISBN)
- Compatible with: Kindle, Apple Books, Google Play, Kobo, Nook

### EPUB-Specific Cleaning
The `create_epub.py` script automatically removes:
- Metadata blocks (`---` at start of files)
- Manual table of contents (EPUB auto-generates)
- QR code images (audio links are clickable in digital format)
- "Listen at:" lines with shortened URLs
- LaTeX commands

### What Remains in EPUB
- All chapter content
- All three photos (embedded)
- Clickable song title links
- All scripture quotes
- All formatting and structure

---

## Image Processing Details

### Image Detection
The PDF script detects images in two formats:

1. **Markdown format:**
   ```markdown
   ![Alt text](path/to/image.png)
   ```

2. **HTML format:**
   ```markdown
   <img src="url" alt="Alt text" />
   ```

### Image Downloading
- Remote images (http/https URLs) are downloaded on first run
- Downloaded images cached in `image_cache/` directory
- Cache filename: MD5 hash of URL + original extension
- Browser headers used to avoid 406 errors from web servers

### Image Scaling
```python
# For QR codes
width = 1.3 inches
height = 1.3 inches

# For content photos
max_width = 4.5 inches
max_height = 6.5 inches

# Calculate with aspect ratio preservation:
aspect_ratio = original_height / original_width
target_width = 4.5 inches
target_height = target_width * aspect_ratio

# If height exceeds max, scale by height instead
if target_height > 6.5 inches:
    target_height = 6.5 inches
    target_width = target_height / aspect_ratio
```

---

## Common Issues and Fixes

### Issue 1: Last lyric appears bolded in PDF/EPUB

**Cause:** Missing blank line before `---` after song lyrics

**Fix:** Add blank line:
```markdown
Last line of lyrics

---
## Key Takeaways
```

**Check all 14 chapters:**
```bash
python3 << 'EOF'
import os
files = [f for f in os.listdir('.') if 'chapter' in f and f.endswith('.md')]
for filename in sorted(files):
    with open(filename, 'r') as f:
        lines = f.readlines()
    for i in range(len(lines)):
        if lines[i].strip() == '## Key Takeaways':
            if i >= 2:
                dash_line = lines[i-1].strip()
                blank_line = lines[i-2].strip()
                if dash_line == '---' and blank_line == '':
                    print(f"✓ {filename}: Correct")
                else:
                    print(f"✗ {filename}: NEEDS FIX")
            break
EOF
```

### Issue 2: Photos not appearing in PDF

**Debugging steps:**

1. **Check images are in manuscript:**
   ```bash
   grep "<img" /Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/COMPLETE-MANUSCRIPT.md
   ```
   Should show 3 HTML img tags (plus QR code markdown images)

2. **Check cached images exist:**
   ```bash
   ls -lh /Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/image_cache/
   ```
   Should show 3 .jpg files:
   - Swamp image (~5-6 MB)
   - Lake Hefner (~5-6 MB)
   - Shadow of Grace (~11 KB)

3. **Check PDF file size:**
   ```bash
   ls -lh /Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/OUT-OF-THE-SWAMP-KDP-READY.pdf
   ```
   Should be ~10 MB (if smaller, images may not be embedded)

4. **Test image embedding:**
   Create test PDF with single image to verify ReportLab is working:
   ```python
   from reportlab.lib.pagesizes import letter
   from reportlab.platypus import SimpleDocTemplate, Image, Paragraph
   from reportlab.lib.styles import getSampleStyleSheet
   from reportlab.lib.units import inch

   doc = SimpleDocTemplate('test.pdf', pagesize=letter)
   story = []
   story.append(Paragraph("Test Image", getSampleStyleSheet()['Heading1']))
   img = Image('image_cache/05f24ec7f5eb1fafe9e4ca1ff3337416.jpg', width=4.5*inch)
   story.append(img)
   doc.build(story)
   ```

### Issue 3: Duplicate chapter opening scriptures

**Fixed:** Chapters 8 and 10 previously both used Jeremiah 17:8
- Chapter 8 now uses: Jeremiah 29:13
- Chapter 10 now uses: Jeremiah 17:7-8 (fuller passage)

**Verify no duplicates:**
```bash
grep -h "^> " *chapter*.md | sort | uniq -d
```
Should return empty (no duplicates)

### Issue 4: Font embedding fails

**Cause:** Times New Roman not found on system

**Check font exists:**
```bash
ls -l /Library/Fonts/Times\ New\ Roman.ttf
```

**If missing, install from:**
- macOS: Install Microsoft Office or download font
- Windows: Should be pre-installed
- Linux: Install `ttf-mscorefonts-installer` package

### Issue 5: EPUB shows raw markdown (##Key Takeaways as text)

**Cause:** Missing blank lines around decorative dividers prevent pandoc from parsing headings

**Fix:** The `create_epub.py` script now preserves blank lines when skipping decorative `---` dividers

**Code (lines 38-48 of create_epub.py):**
```python
if is_metadata_block:
    # This opens a metadata block
    in_metadata = True
    i += 1
    continue
else:
    # Just a decorative divider, skip it but preserve spacing
    # Add a blank line to ensure proper markdown parsing
    cleaned_lines.append('\n')
    i += 1
    continue
```

---

## Quality Checks Before Publication

### 1. Manual PDF Review
- [ ] Open PDF in Adobe Acrobat or Preview
- [ ] Check all 3 photos appear correctly:
  - [ ] Chapter 1: Swamp/alligator photo
  - [ ] Chapter 5: Lake Hefner boat ramp
  - [ ] Chapter 6: Shadow of Grace
- [ ] Verify all 14 QR codes are present and scannable
- [ ] Check page numbers: Roman (i-v) then Arabic (1, 2, 3...)
- [ ] Verify all fonts render correctly (no missing characters)
- [ ] Check no lyrics are incorrectly bolded
- [ ] Verify headers appear on all pages except title page

### 2. EPUB Validation
- [ ] Open EPUB in Calibre or Apple Books
- [ ] Navigate using table of contents
- [ ] Click audio links to verify they work
- [ ] Check all 3 photos display
- [ ] Verify chapter opening scriptures display correctly
- [ ] Check no raw markdown (##) appears as text
- [ ] Test reflowable text at different font sizes

### 3. KDP Paperback Validator
- [ ] Upload PDF to KDP
- [ ] Run KDP's built-in validator
- [ ] Check for font embedding warnings
- [ ] Verify no low-resolution image warnings
- [ ] Check page count is correct

### 4. Test Print (Recommended)
- [ ] Order proof copy from KDP
- [ ] Check physical print quality
- [ ] Verify QR codes scan with phone camera
- [ ] Check margins are correct (0.75" all sides)
- [ ] Verify text is readable at 6"×9" size

---

## File Version Control

### Git Workflow
```bash
# Check what changed
git status

# View specific changes
git diff 02_chapter-01-my-swamp-secular.md

# Stage all chapter changes
git add *chapter*.md

# Commit with descriptive message
git commit -m "Fix: Add blank lines before --- in all lyrics sections

- Fixed 11 chapters with missing blank lines after lyrics
- Prevents last lyric from being bolded in PDF/EPUB
- All chapters now follow: [lyric] → [blank] → [---] → [## Key Takeaways]"

# Push to remote
git push origin main
```

### Generated Files (Do NOT Commit)
Add to `.gitignore`:
```
/KDP/COMPLETE-MANUSCRIPT.md
/KDP/OUT-OF-THE-SWAMP-KDP-READY.pdf
/KDP/OUT-OF-THE-SWAMP.epub
/KDP/image_cache/
/KDP/TEST-*.pdf
```

These files are generated from source and should be recreated each time.

---

## Workflow Scripts

### 1. create_complete_manuscript.py

**Purpose:** Combines all markdown files into single manuscript

**Process:**
1. Reads files in numerical order (00_, 01_, 02_, etc.)
2. Concatenates content with blank lines between files
3. Preserves all metadata blocks, images, formatting
4. Outputs to: `/Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/COMPLETE-MANUSCRIPT.md`

**Expected output:**
```
Adding: 00_title-page.md
Adding: 00_copyright-page.md
...
Adding: 99_about-author.md

✓ Created: COMPLETE-MANUSCRIPT.md (336.2 KB)
```

### 2. create_pdf_kdp_ready.py

**Purpose:** Generates KDP-ready PDF with embedded fonts and images

**Process:**
1. Reads COMPLETE-MANUSCRIPT.md
2. Parses markdown to ReportLab flowables
3. Downloads remote images to cache
4. Embeds Times New Roman fonts
5. Adds sequential pagination (Roman/Arabic)
6. Adds running headers
7. Centers images on page
8. Outputs to: `/Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/OUT-OF-THE-SWAMP-KDP-READY.pdf`

**Key features:**
- 6" × 9" page size
- 0.75" margins all sides
- Times New Roman fully embedded
- Images scaled with aspect ratio preserved
- QR codes at 1.3" × 1.3"
- Content photos max 4.5" × 6.5"

**Expected output:**
```
✓ Using Times New Roman fonts (fully embedded)
Converting to PDF: COMPLETE-MANUSCRIPT.md
  Building PDF with embedded fonts...
  ✓ PDF created: OUT-OF-THE-SWAMP-KDP-READY.pdf
  ✓ Fonts are fully embedded
  ✓ Ready for KDP upload
```

### 3. create_epub.py

**Purpose:** Generates EPUB for ebook distribution

**Process:**
1. Reads COMPLETE-MANUSCRIPT.md
2. Removes metadata blocks
3. Removes manual TOC (EPUB auto-generates)
4. Removes QR codes (links are clickable)
5. Removes "Listen at:" lines
6. Preserves blank lines for proper markdown parsing
7. Converts to EPUB using pandoc
8. Outputs to: `/Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/OUT-OF-THE-SWAMP.epub`

**Expected output:**
```
✓ Cleaning manuscript for EPUB...
✓ Converting to EPUB format...
✓ EPUB created successfully!
   File: OUT-OF-THE-SWAMP.epub
   Size: 8064.4 KB
```

---

## Dependencies

### Required Python Packages
```bash
pip install reportlab
pip install Pillow
pip install pypandoc
```

### Required System Tools
```bash
# Pandoc (for EPUB generation)
brew install pandoc  # macOS
apt-get install pandoc  # Linux

# Fonts
# Times New Roman must be installed
# macOS: /Library/Fonts/Times New Roman.ttf
```

### Python Version
- Python 3.9 or higher recommended
- Tested on Python 3.9

---

## Publication Checklist

### Before Running Workflow
- [ ] All chapter markdown files updated
- [ ] Chapter opening scriptures verified (no duplicates)
- [ ] All lyrics sections end with blank line before `---`
- [ ] All 3 photos have correct HTML img tags
- [ ] All 14 QR code PNG files exist in KDP directory
- [ ] Git status clean or changes committed

### After Running Workflow
- [ ] COMPLETE-MANUSCRIPT.md generated (336 KB)
- [ ] OUT-OF-THE-SWAMP-KDP-READY.pdf generated (~10 MB)
- [ ] OUT-OF-THE-SWAMP.epub generated (~8 MB)
- [ ] PDF contains all 3 photos
- [ ] PDF contains all 14 QR codes
- [ ] No errors in terminal output
- [ ] Font embedding verified

### Quality Review
- [ ] Manual PDF review completed
- [ ] EPUB validation completed
- [ ] Test print ordered (optional but recommended)
- [ ] KDP validator passed
- [ ] Final approval from author

### Publication
- [ ] Upload PDF to KDP for paperback
- [ ] Upload EPUB to KDP for Kindle
- [ ] Upload EPUB to other platforms (Apple Books, Kobo, etc.)
- [ ] Set pricing and metadata
- [ ] Preview using KDP's online previewer
- [ ] Publish!

---

## Troubleshooting Commands

### Check manuscript has all photos
```bash
grep -c "<img" /Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/COMPLETE-MANUSCRIPT.md
# Should return: 3 (plus 14 for QR codes if counted)
```

### Verify lyrics formatting in all chapters
```bash
cd /Users/paulmarshall/Documents/GitHub/skylerthomas2wiki/
python3 << 'EOF'
import os
files = [f for f in os.listdir('.') if 'chapter' in f and f.endswith('.md')]
issues = []
for filename in sorted(files):
    with open(filename) as f:
        lines = f.readlines()
    for i, line in enumerate(lines):
        if line.strip() == '## Key Takeaways' and i >= 2:
            if lines[i-1].strip() == '---' and lines[i-2].strip() != '':
                issues.append(filename)
                break
print(f"Chapters with issues: {len(issues)}")
for f in issues:
    print(f"  - {f}")
EOF
```

### Check PDF file size (should be ~10 MB with images)
```bash
ls -lh /Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/OUT-OF-THE-SWAMP-KDP-READY.pdf
```

### Count pages in PDF
```bash
# Using pdfinfo (if installed)
pdfinfo /Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/OUT-OF-THE-SWAMP-KDP-READY.pdf | grep Pages

# Or open in Preview and check page count
```

### Verify EPUB structure
```bash
# Extract EPUB (it's just a ZIP file)
cd /tmp
unzip -q /Users/paulmarshall/Documents/GitHub/skylerthomas2/KDP/OUT-OF-THE-SWAMP.epub -d epub_contents
ls -la epub_contents/
```

---

## Contact and Support

**Author:** Skyler Thomas
**Email:** skyler@skylerthomas.com
**Website:** https://www.skylerthomas.com

**Book Title:** Out of the Swamp: How I Found Truth
**ISBN:** 979-8-218-57544-4
**Publication Date:** 2025

---

## Revision History

| Date | Version | Changes |
|------|---------|---------|
| 2025-10-13 | 1.0 | Initial workflow documentation |

---

**Last Updated:** October 13, 2025
