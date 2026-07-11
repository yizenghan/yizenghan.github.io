# Editorial Homepage Refresh Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Refine the personal homepage into a distinctive editorial academic profile that foregrounds efficient visual generation and remains concise on mobile.

**Architecture:** Keep the site as a dependency-free single-page document. Rework the existing HTML hierarchy and embedded CSS in `index.html`, preserve all publication data and assets, and use progressive disclosure for older news and awards.

**Tech Stack:** Semantic HTML, embedded CSS, minimal vanilla JavaScript, GitHub Pages.

---

### Task 1: Establish the editorial visual system

**Files:**
- Modify: `index.html`

**Steps:**
1. Add page description, social metadata, theme color, and a lightweight favicon.
2. Replace the dashboard-like palette and spacing with warm paper, ink, and restrained aubergine tokens.
3. Increase the desktop content width while preserving comfortable reading measures.
4. Verify that the page has no horizontal overflow at 1440px and 390px.

### Task 2: Rebuild the opening profile and biography

**Files:**
- Modify: `index.html`

**Steps:**
1. Rewrite the hero positioning statement around efficient visual generation, dynamic models, and inference.
2. Move professional links into the text column and remove the statistics strip.
3. Condense the biography into two focused paragraphs.
4. Convert education and research experience into a responsive editorial timeline.

### Task 3: Reduce content density

**Files:**
- Modify: `index.html`

**Steps:**
1. Show the newest news entries directly and move older entries into a native disclosure section.
2. Present the first three recent works as featured cards and the remaining works as compact rows.
3. Keep representative papers accessible through the existing tab with consistent compact styling.
4. Normalize visible venue typography and publication descriptions where inconsistent.

### Task 4: Refine supporting sections and responsive behavior

**Files:**
- Modify: `index.html`

**Steps:**
1. Prioritize major awards and place older scholarships in a disclosure section.
2. Simplify contact and footer content, using Gmail as the sole contact address.
3. Make the mobile hero text-first, simplify paper rows, and keep navigation usable at narrow widths.
4. Add focus states, reduced-motion handling, link labels, and image loading hints.

### Task 5: Verify the result

**Files:**
- Test: `index.html`

**Steps:**
1. Validate HTML structure and check referenced local assets.
2. Render at 1440×1000 and 390×844.
3. Review hero, biography, news, featured works, compact papers, awards, contact, and footer.
4. Confirm the working tree contains only intended changes and do not push.
