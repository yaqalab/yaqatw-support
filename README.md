# YaqatW User Guide

**Yet Another Qualitative Analysis Tool for Word**

Welcome to YaqatW! This guide will help you get started with qualitative coding, annotation, and thematic analysis in Microsoft Word.

## Table of Contents

1. [What is YaqatW?](#what-is-yaqatw)
2. [Prerequisites](#prerequisites)
3. [Installation](#installation)
4. [Getting Started](#getting-started)
5. [Document Types](#document-types)
6. [Modes & Features](#modes--features)
   - [Coding Mode](#coding-mode)
   - [Mining Mode](#mining-mode)
   - [Analyzing Mode](#analyzing-mode)
   - [Documenting Mode](#documenting-mode)
   - [Writing Mode](#writing-mode)
   - [Transcribing Mode](#transcribing-mode)
   - [Settings (All Modes)](#settings-all-modes)
7. [Workflow Guide](#workflow-guide)
8. [Cloud Sync](#cloud-sync)
9. [Encryption & Security](#encryption--security)
10. [Export & Analysis](#export--analysis)
11. [AI & Translation](#ai--translation)
12. [Troubleshooting](#troubleshooting)
13. [FAQ](#faq)

---

## What is YaqatW?

YaqatW is a Microsoft Word add-in designed for researchers, students, and analysts who conduct qualitative analysis. Switch between six specialized modes to match each phase of your research workflow:

- **Coding Mode** — Create custom codes, organize them into categories, and document relationships between concepts (with optional AI-assisted coding)
- **Mining Mode** — Search, measure word frequency, map word co-occurrence, and view corpus statistics across your text
- **Analyzing Mode** — Use codes, categories, metadata, and search groups as variables to explore relationships in your data
- **Documenting Mode** — Manage evidential artifacts (images, audio, documents) and analytic notes
- **Writing Mode** — Search your coded data and insert quotes, citations, figures, and tables directly into your writing
- **Transcribing Mode** — Transcribe audio recordings with speaker management, automatic diarization, and time-synced keyboard shortcuts

Core features available across modes:
- **Annotate** documents with metadata and field notes
- **Sync** your work across devices via cloud storage
- **Export** your analysis to Excel, CSV, JSON, HTML, or Word
- **Secure** sensitive data with encryption

### A little background

Yaqat used to be a web application on a private server that I ([F. R. Andriariniaina](https://github.com/frianasoa)) have been using for the past ten years, with very few collaborators. It has also been used by my students for some time. I named it Yet Another Qualitative Analysis Tool because there are already countless qualitative analysis tools out there. Rather than trying to reinvent the field, the goal was to create a tool that solves the specific problems I encountered in my own research.

Recently, I decided to bring Yaqat to Microsoft Word as an Add-in in order to make it accessible to a wider audience. If it happens to make your work a little easier, save you a few hours, or help you discover something new in your data, then it has achieved its purpose.

More documentation is added as the project develops. For more information, visit https://yaqatw.alefa.net/public/about.

---

## Prerequisites

- **Microsoft Office newer than 2019.** Word add-ins are a relatively new mechanism: they do **not** work on versions before 2019, and may not work on some 2019 builds. Install the latest Office available to you (e.g. through a university account). Office 2019 is no longer supported by Microsoft, so upgrading is recommended unless you depend on an older version.
- **Word for Windows, macOS, or the web.** The add-in also runs in Word on the web, though that path is less thoroughly tested. There is **no mobile support** (a Microsoft platform limitation).
- **Cloud storage strongly recommended.** Especially on the web version — where local browser data is more vulnerable — enable a cloud provider (Google Drive, OneDrive, Dropbox, Nextcloud, or S3) so your data survives a browser or device failure. Desktop users are encouraged to enable it too. See [Cloud Sync](#cloud-sync).

---

## Installation

YaqatW is not yet in the Microsoft Store, so installation is a little more involved than a one-click install. (Publishing to the Store has technical and administrative requirements we aren't ready to meet yet; we plan to as the user base grows.) The current method — *sideloading* a manifest — is standard for add-ins with a small user base.

### Step 1: Download the Manifest File

Obtain the `manifest.xml` file from the YaqaLab team (or the source you were directed to). Your browser may warn that the file "may harm your computer" — this is the generic warning browsers show for any `.xml`/manifest download. The file is plain text and safe; **download anyway**, and if you wish, inspect it in Notepad or any text editor before installing.

### Step 2: Trust the Add-in in Word

#### Windows

Reference: [Microsoft's guide to sideload from a network share](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/create-a-network-shared-folder-catalog-for-task-pane-and-content-add-ins) · [Video walkthrough (from 2:34)](https://www.youtube.com/watch?v=XXsAw2UUiQo&t=154s)

**A. Create and share a folder containing `manifest.xml`:**
1. Create a folder in a stable location (e.g. under *Documents*) and move `manifest.xml` into it
2. Share the folder with **Everyone**: right-click the folder → **Properties** → **Sharing** tab → **Share…** → add **Everyone** → **Add** → **Share**
3. Windows shows the shared location, e.g. `\\DESKTOP-NDMDVHB\Users\You\Documents\My add-ins`. Copy it and, if needed, clean it into UNC form (note the backslashes):
   ```
   \\DESKTOP-NDMDVHB\Users\You\Documents\My add-ins
   ```
4. Verify it works: paste that path into the address bar of a File Explorer window and press Enter — your folder should open

**B. Register it as a trusted catalog in Word:**
1. Open Word with a blank document
2. **File → Options → Trust Center → Trust Center Settings… → Trusted Add-in Catalogs**
3. Paste the cleaned `\\…` share path into the box, click **Add catalog**, then **OK** → **OK**
4. Close and reopen Word

**C. Load the add-in:**
1. Open a document, go to the **Insert** (or **Home**) tab and find **Add-ins**
2. **Add-ins → Advanced** (or **My Add-ins**) → **SHARED FOLDER** tab → select **YaqatW** → **Add**
3. The YaqatW icon appears on the ribbon. Click it; the task pane loads on the right. If the document is empty, some placeholder text is written into it.

#### macOS

Sideloading on macOS is actually simpler than on Windows. Reference: [Microsoft's guide to sideload on Mac](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/sideload-an-office-add-in-on-mac).

1. Download `manifest.xml` as in Step 1
2. In Finder, press **Cmd+Shift+G** and go to the following path, creating the `wef` folder if it doesn't exist (replace `<username>` with your Mac account name):
   ```
   /Users/<username>/Library/Containers/com.microsoft.Word/Data/Documents/wef
   ```
3. Copy `manifest.xml` into this `wef` folder
4. Open Word (or quit and reopen it if already running), then open a document
5. **Home** tab → **Add-ins** → select **YaqatW** (sideloaded add-ins appear under **My Add-ins** / **Developer Add-ins**). The pane loads on the right.

> **NB:** On some Mac setups you may need to re-add the add-in from the Add-ins menu each time you launch Word. The manifest stays in the `wef` folder, but Word doesn't always keep it pinned to the ribbon between sessions.

#### Word on the web

Reference: [Microsoft's guide for the web](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/sideload-office-add-ins-for-testing?source=recommendations#manually-sideload-an-add-in-to-office-on-the-web) · [Video (from 4:04)](https://youtu.be/XXsAw2UUiQo?si=gOqDAYBVIKPa1heG&t=244)

1. Sign in at https://office.com with your Microsoft 365 account and open Word
2. **Insert → Add-ins → Upload My Add-in**
3. **Browse**, select your `manifest.xml`, and **Upload**
4. YaqatW is now available in your session (enable cloud storage so your data is preserved — see [Prerequisites](#prerequisites))

### Future: Microsoft AppSource

Once YaqatW is published to the Microsoft Office Store, installation will be one-click:
1. Go to **Insert → Get Add-ins**
2. Search for "YaqatW"
3. Click **Get**

---

## Getting Started

### Initial Setup (First Time Only)

When you first click the YaqatW icon, the task pane opens on the right. A short **disclaimer** appears — read it and click **OK**. If the document was empty, you'll also see some placeholder text written into it. It helps to **widen the pane** at first (drag its left edge); once you're comfortable with the interface you can work in a narrower pane.

You'll then see the Settings tab with the required configuration. Since YaqatW does **not** manage usernames or passwords for you, note anything you set here somewhere secure.

1. **Project Name**
   - Enter a name for your research project (e.g., "interview-study-2024")
   - Can contain lowercase letters, numbers, and hyphens
   - **Note:** Project name is shared across all files in the same project

2. **Data Password** (Required for sensitive data)
   - Create a strong password (8+ characters, mix of letters/numbers)
   - **Important:** Write this down securely. If lost, encrypted data cannot be recovered
   - Confirm the password in the next field

3. **Current File (File ID)**
   - Give this specific document a unique identifier (e.g., "interview-001")
   - Allows you to work on multiple documents within the same project
   - Codes, categories, and relationships are shared across all files in the project; highlights belong to each file

4. **User Name**
   - Enter your name (lowercase, no spaces)
   - Tracks who made each edit when collaborating

![YaqatW initial settings configuration](./assets/initial-settings.png)

5. **Cloud Sync** (Optional but Recommended)
   - Choose a cloud provider: Google Drive™, Dropbox, OneDrive, Nextcloud, or Amazon S3 (and S3-compatible storage)
   - Click "Sync now" and follow the login prompts
   - YaqatW will create a `YaqatW-DATA` folder in your cloud account
   - This folder stores your coding data for backup and multi-device sync

  ![Cloud backend selection dropdown](./assets/select-cloud-backend.png)

**Once these fields are filled, all feature tabs will become available.**

---

## Document Types

Before choosing a mode, YaqatW asks what kind of document this is. Set it in **Settings → Document Type**. The document type determines which modes are available:

- **Analysis document** (default) — your raw data / source text that you code and analyze.
  **All six modes are available.**
- **Writing document** — a manuscript, report, or chapter you are drafting from already-coded data.
  Only **Writing, Analyzing, Mining, and Documenting** modes are available (Coding and Transcribing are hidden so you don't accidentally code your manuscript).

**Note:** You can only switch a document to **Writing** type if it has **no highlights**. This keeps coded source data and written output cleanly separated. The typical setup is one (or several) Analysis documents holding your interviews/sources, plus a separate Writing document for your paper — all under the same project name so they share codes and data.

> 📸 **Screenshot:** [Settings > Document Type selector (Analysis document / Writing document)]

---

## Modes & Features

YaqatW is organized into six modes. Switch between them from **Settings → yaqatw-mode** (or the pinned header bar) — your data persists across modes, so a mode is simply a different lens on the same project. Which modes are available depends on the [document type](#document-types).

| Mode | Tabs | Intended for |
|---|---|---|
| **Coding** | Codes · Categories · Relationships | Coding source text and organizing concepts into categories and relationships |
| **Mining** | Search · Frequency · Co-occurrence · Stats | Exploring the raw text — search, word frequency, collocation networks, corpus statistics |
| **Analyzing** | Analysis | Cross-tabulating codes, categories, metadata, and search groups as variables |
| **Documenting** | Artifacts · Notes | Cataloguing evidence files and writing analytic memos |
| **Writing** | Cite | Drafting a manuscript with quotes, citations, figures, and tables from your project |
| **Transcribing** | Import · Transcribe · Diarize | Turning audio recordings into speaker-labelled, time-stamped text |

*(Every mode also has a **Settings** tab. The table omits it for brevity.)*

The rest of this section documents each mode in depth.

---

### Coding Mode

**Intended for:** turning raw source text into coded data — creating codes, applying them to passages, and organizing those codes into categories and relationships.

In Coding mode you read your source document and mark passages. Each marked passage becomes a **highlight**: a colored span in the Word document that carries one or more codes, plus an optional note and translation. Codes, categories, and relationships are **shared across every file in the project**, so a code you create here is available when coding any other document under the same project name — while the highlights themselves belong to each file.

> This mode is available only for **Analysis documents**; it is hidden for Writing documents (which have no highlights).

#### **Codes** Tab — Mark Up Your Text

**What it does:** Create custom codes (concepts/tags) and apply them to text selections in your document.

**Create a Code:**
1. Click the **Codes** tab
2. Click **New Code** (+ button)
3. Enter:
   - **Code Name** (e.g., "Leadership")
   - **Description** (e.g., "Instances where leaders emerge")
   - **Color** (pick from palette for visual distinction)
4. Click **Create**

**Apply a Code to Text:**
1. Select a text excerpt in your Word document
2. Right-click the code in the list and choose **Use code** (or **Use code with comment** to attach a comment at the same time)
3. The selected text is highlighted with the code's color and labeled with the code name
4. Clicking any coded passage in the document opens its info panel, where you can edit it, add notes/translations, then **save & close**

**Display & organize the code list:**
- Switch between **Grid**, **List**, and **Compact** views
- Use the **search** box to filter codes by name

**Edit or Delete:**
- **Edit** to change name/description/color
- **Delete** to remove the code definition (highlights stay in the document; deleted codes can be restored from the **Trash**)

**Work with a highlight:** A passage can carry **several codes at once** — apply additional codes to the same selection, or **detach** a code you applied by mistake. Selecting a highlight opens its info panel, where you can see and edit:
- the **highlighted text**,
- a **translation** (translate on demand when an AI/translation provider is configured — see [AI & Translation](#ai--translation)),
- a free-text **note**, and
- the list of **codes applied**.

**Layers:** Highlights live in **layers**, which let you keep parallel passes of coding separate — for example an original-language layer and a **translation layer**, or a first-pass and a second-pass coding round. You can **create a new layer**, and show or hide layers independently. Hidden layers stay hidden by default; turn on *Offer to reveal hidden layers* in Settings if you want YaqatW to prompt you when you select a highlight that lives in a hidden one.

**Export your code work:** From the Codes footer you can export the **code book** (your codes and their definitions) and the **coded data** (highlights with their codes, notes, and translations) as Word, Excel, HTML, JSON, or CSV. See [Export & Analysis](#export--analysis).

**Import Comments → Codes:** If your document already has Word review comments, YaqatW can turn them into codes — each comment becomes a code, applied to the text it was attached to. The **Import comments** button appears inside the **Add/Edit code** dialog, and **only when the document actually contains comments**. Open that dialog, click **Import comments**, and pick how each comment maps to a code:
- **First sentence → code name, the rest → description** (best when comments are short)
- **Split on a delimiter** — structure each comment as `code <delimiter> description` using a colon, a line break, or a custom delimiter; text before the delimiter is the code, text after is the description
- **Labeled sections** — mark parts explicitly: `[Code]` …code… `[Description]` …description…

A live preview shows how many comments will become new codes, be applied, or be skipped before you confirm. (For example, a comment that just says "My interesting note" becomes a code of that name on the commented passage.)

**AI Code Agent (optional):** When an AI provider is configured (see [AI & Translation](#ai--translation)), the Codes tab offers AI-assisted coding **Suggestions**. You guide the AI without writing prompts from scratch:
- **Reasoning mode** — *Inductive* (build patterns up from the data), *Deductive* (test predictions from existing theory), or *Abductive* (match to existing codes first, allow new ones to emerge)
- **Analytic stance** — *Descriptive*, *Interpretive*, *Critical*, or *Comparative*
- **Research question** and a free-text **prompt** to focus the AI's attention
- Options: embed/validate against existing codes, include interviewer passages as context only, cap the number of new codes, and output codes in your writing language

Suggested codes are previewed for you to accept, edit, or reject — nothing is applied to your document automatically.

> 📸 **Screenshot:** [Coding mode > Codes > AI Suggestions panel (reasoning mode, analytic stance, research question)]

> 📸 **Screenshot:** [Coding mode > Codes > Import Comments dialog with strategy + preview]

![Coding tab with code list and apply functionality](./assets/coding-tab.png)

#### **Categories** Tab — Organize Codes

**What it does:** Group related codes into categories and sub-categories, creating a hierarchy of concepts.

**Create a Category:**
1. Click the **Categories** tab
2. Click **New Category** (+ button)
3. Enter a **Category Name** and optional **Description**
4. Click **Create**

**Add Codes to a Category:**
1. Open the category
2. Choose **Add Codes to Category**
3. Select codes (checkboxes) and confirm

**Organize Hierarchically:** Expand/collapse categories with the arrow icon and arrange codes within the tree.

**Example Structure:**
```
Leadership (Category)
├── Delegating Authority (Code)
├── Decision Making (Code)
└── Team Motivation (Code)

Communication (Category)
├── Active Listening (Code)
└── Feedback Delivery (Code)
```

![Categories tab with hierarchical code organization](./assets/categories-tab.png)

**Use Case:** After coding a document with 20+ codes, group related codes by theme (Behaviors, Attitudes, Outcomes…) to simplify analysis and reporting.

#### **Relationships** Tab — Document Connections Between Concepts

**What it does:** Create and document relationships between codes/categories to record how concepts connect (cause–effect, temporal, hierarchical, etc.).

**Create a Relationship:**
1. Click the **Relationships** tab
2. Click **New Relationship** (+ button)
3. Name the **Relationship Type** and click **Create** (one "Instance" is auto-created)

**Relationship Type Examples:** Cause → Effect · Then → Now · Example → General · Part Of · Precedes · Contradicts

**Add Codes/Categories to a Relationship:**
1. Open the relationship to expand it
2. On an Instance, choose **Add Code/Category** for each side
3. Relationships work best with categories, but individual codes can be added too

**Create Multiple Instances:** Add another Instance to record more examples of the same relationship type.

**Example:**
```
Relationship: Cause → Effect
├── Instance 1
│   ├── Organizational Stress (Category)
│   └── High Turnover (Category)
└── Instance 2
    ├── Leadership Issues (Category)
    └── Team Morale (Category)
```

![Relationships tab showing connections and instances](./assets/relationships-tab.png)

**Relationships as theme containers:** Thematic analysis usually needs only three levels — **Data → Codes → Themes**. But depending on your coding style you may want a fourth — **Data → Codes → Categories → Themes**. Because a Relationship can hold categories, you can use it as the outer "Themes" container above your categories, giving you that extra level without leaving the add-in.

---

### Mining Mode

**Intended for:** getting to know the raw text itself — searching it, measuring word frequency, mapping which words travel together, and profiling speakers — before, during, or after coding.

Mining reads your document into **parsed turns**: each paragraph is treated as one speaker turn, and YaqatW detects the speaker label and **role** (interviewer vs. interviewee) from the way turns are written. Everything in Mining operates on these turns, which is why keeping *one speaker turn per paragraph* (see [Transcribing](#transcribing-mode)) makes the analysis cleaner. The current document is indexed automatically; use **Settings → Re-index current document** if results look stale.

A **scope** bar at the top of each Mining tab lets you focus the analysis:
- **Global** — analyze all indexed files in the project, not just the current document
- **Files** — narrow to selected files (all files by default)
- **Speakers** — filter to selected speakers

Every tab has its own **Export / Export All** footer, and results can be filtered by speaker **role** (All / Interviewer / Interviewee).

#### **Search** Tab — Full-Text Exploration

**What it does:** Search across your text to locate passages and patterns. Seven search modes cover everything from simple substrings to advanced queries:

| Mode | What it does |
|---|---|
| **Exact** | Match the exact substring |
| **Wildcard** | Use `*` for any characters — e.g. `saka*` matches `sakafo`, `sakafoana` |
| **Boolean** | `AND`, `OR`, `NOT`, and quoted phrases — e.g. `sakafo AND ankizy NOT vary` |
| **Proximity** | `NEAR/N` or `BEFORE/N` — e.g. `sakafo NEAR/5 ankizy` |
| **Fuzzy** | Match approximate spellings and morphological variants |
| **Regex** | Use a JavaScript regular expression |
| **Named** | Upload a YAML file defining named groups of search terms |

**Display options** let you show the full speaker turn, speaker name, role (interviewer/interviewee), match score, turn number, and selected metadata fields on each result. Click a result to jump to that location in your document.

**Named search** is powerful for theory-driven coding: define groups and subgroups of terms in a YAML file, then control deduplication with the **Exclusion** setting — *None* (every match reported), *Exclude turn* (each turn counted at most once), or *Exclude subgroup* (each subgroup captures only turns not already matched).

> 📸 **Screenshot:** [Mining mode > Search > search-mode selector (Exact / Wildcard / Boolean / Proximity / Fuzzy / Regex / Named)]

![Mining search tab with search filters and results list](./assets/mining-search.png)

#### **Frequency** Tab — Word Frequency Analysis

**What it does:** Count the most frequent words (or word pairs/triplets) in your text to surface dominant topics.

**Options:**
- **N-gram** — count single words, consecutive pairs, or triplets
- **Min frequency** — hide words appearing fewer than N times
- **Hapax** — show only words that appear exactly once (hapax legomena)
- **Filter stopwords** — exclude common function words (pronouns, prepositions, fillers)
- View results as a frequency **table** or a **word cloud**

![Mining frequency tab](./assets/mining-frequency.png)

**Use Case:** Understand what your data is "about" before coding. If "stress" appears 47 times and "deadline" 28 times, you know these are likely major themes.

#### **Co-occurrence** Tab — Word Networks

**What it does:** Find which words tend to appear near each other (collocates) and visualize them as a network map.

**Options:**
- **Target word(s)** — separate multiple with `|` (e.g. `build | home | country`)
- **Window** — how many tokens to scan left/right of the target
- **Min frequency** and **Max results** to filter noise
- **Filter stopwords** to drop function words
- Toggle between a ranked **table** and a network **Map**

**Network map controls:**
- **Layout** — Force, Radial, Circular, Clustered, or Tree
- **Edge style** — straight Line or Curve
- **Distant edges** — how to draw cross-community / cross-branch links (gray, dashed, dotted, or none)
- Decorative vs. analytical coloring, node count, and full-map export (PNG/SVG)

![Mining co-occurrence map](./assets/mining-words-co-occurence.png)

#### **Stats** Tab — Corpus Statistics & Visualizations

**What it does:** Quantitative overviews of your text and speakers.

- **Word cloud** — words sized by frequency, with linear/sqrt/log scaling, rotation, quality, and color options; export as PNG or SVG
- **Dispersion plot** — for chosen words, a tick mark on each turn where the word appears, showing whether usage clusters in one section or spreads throughout (optionally split by file)
- **Turn-length distribution** — how many turns fall into each token-length range
- **Speaker statistics** — per speaker: turns, average turn length, vocabulary size, and Type-Token Ratio (lexical diversity)

![Word cloud](./assets/mining-word-cloud.png)

> 📸 **Screenshot:** [Mining mode > Stats > dispersion plot (ticks per turn)]

> 📸 **Screenshot:** [Mining mode > Stats > speaker statistics table (turns, vocab size, TTR)]

**Use Case:** Create a word cloud for a presentation, or use speaker stats to compare how much and how diversely each participant spoke. Word clouds and co-occurrence maps can be **saved as figures** and later inserted into a Writing document (see [Writing Mode](#writing-mode)).

---

### Analyzing Mode

**Intended for:** asking structured questions of your coded data — *does this pattern differ by group?* — by treating codes, categories, metadata, and search results as **variables** and combining them, all without exporting to a separate stats tool.

#### **Analysis** Tab — Variable-Based Exploration

**What it does:** Lets you build an analysis the way you'd design a simple study: pick what you're measuring, pick what might explain it, and (optionally) pick how to break it down — then run it.

**The building blocks.** The left panel lists every **data item** in your project, grouped by kind, each with a colored badge:

| Badge | Kind | What it contributes |
|---|---|---|
| **C** | Code | A single code |
| **Ca** | Category | A group of codes |
| **R** | Relationship | A documented code/category connection |
| **H** | Highlight | An individual coded passage |
| **M** | Metadata | A document/participant metadata field |
| **Co** | Co-occurrence | A word-pair from Mining |
| **G** | Group | A named-search group |

**The three zones.** Drag items from the left into the analysis zones on the right to frame your question:
- **Dependent** — what you want to measure or explain (the outcome, e.g. a code or category)
- **Independent** — the factor you think relates to it (e.g. another category, or a co-occurrence)
- **Group by** — how to split the results into comparable groups (e.g. a metadata field such as region or interview round)

**Run it.** Click **Run** to compute the result — counts and overlaps across the variables you placed, and, when an AI provider is configured, a written **interpretation** of the patterns. Open the result in a dialog and export it. The layout adapts to the pane width (accordion or side-by-side), and your last configuration is remembered.

> 📸 **Screenshot:** [Analyzing mode > Analysis > data items panel + dependent / independent / group-by zones]

> 📸 **Screenshot:** [Analyzing mode > Analysis > result dialog with AI interpretation]

**Use Case:** Put a category in *Dependent*, a metadata field like "Region" in *Group by*, and see how that category is distributed across regions — or place two categories in *Dependent* and *Independent* to see how often they overlap.

> Analyzing mode works for both Analysis and Writing documents, so you can interrogate your data while you draft.

---

### Documenting Mode

**Intended for:** keeping the evidence and the thinking that surround your text — the photos, recordings, and documents you collected in the field, plus the analytic memos you write as you make sense of them.

Where Coding works on text *inside* the Word document, Documenting manages material *alongside* it. It has two tabs: **Artifacts** (evidence files) and **Notes** (memos). Both are searchable and can be pulled into a Writing document via the [Cite](#writing-mode) tab.

#### **Artifacts** Tab — Manage Evidence Files

**What it does:** Catalog evidential materials that aren't plain text — field photos, audio clips, scanned documents — with provenance and your interpretation.

**Each artifact records:**
- **Title** (required) — a short identifying label
- **Source** — where it came from (person, organization, archive, URL)
- **Collected by** — defaults to your user name
- **Session** — optional ID linking it to a fieldwork session or visit
- **Tags** — free-form keywords for filtering
- **Interpretation** — your reading of what the artifact shows (researcher voice)
- **Attachments** — the actual binary files (images, audio, documents)

> **Cloud required:** Artifact attachments are stored in your cloud provider's project folder. You must configure a cloud backend in Settings before adding artifacts. Without it, attachments may be lost on a browser reset. If the cloud provider is disconnected, existing attachments may be temporarily unreachable until you reconnect.

**Lifecycle & sync:** Artifact records sync with the rest of your project, while their attachments are uploaded to the project folder on your cloud provider. Artifacts can be **deprecated** (kept on record with a reason) or **deleted** (marked deleted, recoverable). If an attachment can't be found locally or on the cloud — for example after switching devices — YaqatW flags the **missing attachments** so you can choose to keep or prune them. Saved artifacts can later be inserted into a Writing document as images with captions and a source line.

> 📸 **Screenshot:** [Documenting mode > Artifacts > artifact list]

> 📸 **Screenshot:** [Documenting mode > Artifacts > artifact editor with attachments + interpretation]

#### **Notes** Tab — Analytic Memos

**What it does:** Write and keep analytic notes/memos alongside your project. Notes can be searched and inserted into a Writing document via the Cite tab.

> 📸 **Screenshot:** [Documenting mode > Notes > note editor]

---

### Writing Mode

**Intended for:** drafting the manuscript itself — your paper, report, or chapter — by pulling already-coded evidence out of your project and into the page, correctly attributed, instead of copy-pasting and losing track of sources.

Writing mode is meant to run in its own **Writing document** (see [Document Types](#document-types)), kept under the same project name as your coded sources so it can reach all of their highlights, notes, artifacts, figures, and tables.

#### **Cite** Tab — Search and Insert Quotes, Citations, Figures & Tables

**What it does:** Pull material from anywhere in your project into the document you're drafting.

**Sources you can search and insert:**
- **Highlights** — coded passages, with their text, note, or translation
- **Artifacts** — insert as an image with a caption and source line
- **Notes** — insert analytic memos
- **Tables** and **Figures** — insert saved tables and saved word clouds / co-occurrence maps from Mining

**How to use:**
1. Click the **Cite** tab and choose a source
2. Search for codes, keywords, or passages
3. Review matches with context
4. Insert at your cursor as:
   - **Inline** or **Block** quote
   - **Linked (refreshable)** — stays connected to the source and can be refreshed if the source changes — or **Unlinked (plain paste)**
   - **Plain text** or **Rich text**

**Why "linked" matters:** A **linked (refreshable)** citation stays connected to its source highlight or figure. If you later re-code a passage, fix a translation, or regenerate a word cloud, you can **refresh** the inserted citation instead of finding and replacing it by hand. Choose **unlinked (plain paste)** when you want a one-off snapshot that won't change.

**Attribution:** Quotes are labelled with their source — typically the participant ID drawn from a metadata field. Quotation formatting (the quote characters, the participant/source prefix and suffix, and which metadata field supplies the participant ID) is configurable in **Settings → Appearance & Insertion**, as is how inserted images and tables are captioned, positioned, and aligned.

> 📸 **Screenshot:** [Writing mode > Cite > source picker (Highlights / Artifacts / Notes / Tables / Figures)]

> 📸 **Screenshot:** [Writing mode > Cite > insert options (inline/block, linked/unlinked, plain/rich)]

![Writing mode cite tab with search results and cite button](./assets/writing-cite.png)

**Use Case:** While writing your analysis, search for coded passages that support your argument and insert properly attributed quotes without copy-pasting and losing track of the source.

---

### Transcribing Mode

**Intended for:** producing the transcripts you'll later code — playing back interview audio and typing it into Word with speaker labels and timestamps, helped by keyboard shortcuts, voice enrollment, and automatic speaker diarization.

> **Experimental:** Transcribing mode is still under active development. The other modes are fully usable; expect rough edges here.

The workflow runs across three tabs: **Import** the audio, **Transcribe** it turn by turn, and optionally **Diarize** to detect who spoke when across the whole recording. Lines you insert land in the Word document as one speaker turn per paragraph — exactly the shape [Mining](#mining-mode) expects.

> Like Coding, Transcribing is available only for **Analysis documents**.

#### **Import** Tab — Load Audio Files

**What it does:** Add and preview an audio file for transcription.

1. Click the **Import** tab
2. Choose a file or drag-and-drop it
3. Supported formats: MP3, WAV, OGG, M4A, FLAC, and other Web Audio formats
4. File metadata (type, size, duration) is displayed
5. Go to the **Transcribe** tab to begin

> Transcription and audio features require system file-storage support (on macOS this means Ventura 13 or later). YaqatW will warn you if your system can't store audio.

![Transcribing import tab](./assets/transcribing-import.png)

#### **Transcribe** Tab — Playback, Transcription & Speaker Enrollment

**What it does:** Transcribe audio with customizable keyboard shortcuts, waveform visualization, speaker management, and optional AI transcription of marked segments.

**Playback Controls:** Play/Pause · Stop · Seek Back (−5s) · Seek Forward (+5s) · Speed control (0.5×–2.0×). Toggle **real waveform peaks** in Settings to visualize the actual audio (cached for performance).

**Speaker Management:**
1. Add speakers in the "New speaker name" field and click **Add**
2. Switch the active speaker from the dropdown or with the **Switch Speaker** shortcut
3. Each transcribed line is tagged with the active speaker and timestamp

**Mark a segment & AI transcribe:** Mark a **start** and **end** on the timeline, then **Transcribe** the segment with your configured transcription provider, or **Enroll Speaker** to teach YaqatW that speaker's voice from the segment (used for auto-identification and diarization).

> 📸 **Screenshot:** [Transcribing mode > Transcribe > marked segment with Mark Start/End, Transcribe + Enroll Speaker buttons]

![Transcribing tab with speaker management](./assets/transcribing-speakers.png)

**Keyboard Shortcuts (all customizable):** Shortcuts use `Ctrl+Alt+Key`.

| Action | Default Key |
|--------|-------------|
| Play/Pause | R |
| Stop | X |
| Seek Back / Forward | ← / → |
| Slow Down / Normal / Speed Up | [ / \\ / ] |
| Insert Timestamp | Enter |
| Switch Speaker | T |
| Mark Start / Mark End | (set your own) |

To rebind, click a shortcut cell in the table and press `Ctrl+Alt` + your key (green = saved, red = invalid, × clears it).

**Transcription Workflow:**
1. Play and listen; pause or type live
2. Insert timestamps as needed
3. Type your transcription and **Insert** to add the line to Word with speaker label and timestamp
4. Switch speakers and continue

**Tip:** Use **Enter** to insert (same as the Insert button) and **Shift+Enter** for a line break within a note. Keeping one speaker turn per paragraph helps the Mining parser detect turns correctly.

![Transcribing insertion with speaker label and timestamp](./assets/transcribing-insertion.png)

#### **Diarize** Tab — Automatic Speaker Diarization

**What it does:** Automatically detect *who spoke when* across the whole recording and lay it out as an editable timeline.

**How to use:**
1. Enroll at least one speaker on the **Transcribe** tab first
2. On the **Diarize** tab, click **Analyze** — YaqatW decodes the audio, extracts voice features, clusters unknown voices, and merges segments into a timeline
3. Edit the result directly: select a segment to **split** it at the playhead, **merge** it with the next, **delete** it, **assign** it to a speaker, or **rename** speakers
4. Zoom, undo/redo, and **export** the diarization as JSON

> 📸 **Screenshot:** [Transcribing mode > Diarize > timeline with colored speaker segments]

> 📸 **Screenshot:** [Transcribing mode > Diarize > selected segment editor (split / merge / assign / rename)]

**Engines & remote option:** Choose a speaker-identification engine in Settings — **DIY MFCC** (offline, free) or **Picovoice Eagle** (higher accuracy, requires a free Picovoice AccessKey). For heavier audio, a **Remote** analyze option can offload diarization to a companion app (configure its URL and API key in Settings).

---

### Settings (All Modes)

#### **Settings** Tab — Configuration, Metadata & Cloud Sync

**What it does:** Manage project setup, encryption, cloud connections, AI/translation providers, document metadata, transcription, and appearance.

**1. Document Type** — Analysis document (all modes) or Writing document (Writing/Analyzing/Mining/Documenting). Switching to Writing requires zero highlights. See [Document Types](#document-types).

**2. Operating Mode (yaqatw-mode)** — Coding, Mining, Analyzing, Documenting, Writing, or Transcribing. Your data persists across modes.

**3. Project** — **Project Name** (shared across all files in the project).

**4. Current File** — **File ID** for this document, plus **Re-index current document** to refresh the Mining/Analysis index.

**5. Encryption** (appears once Project Name is set)
- **Data Password** + **Confirm** — encrypts sensitive data
- **Encrypt cloud data** — enable encryption when syncing
- **Remember password on this device** — skips re-entry each session (do **not** enable on shared machines; use **Logout** to clear it)
- ⚠️ Losing your password makes encrypted data **permanently unrecoverable**, and disabling encryption does **not** decrypt existing data

**6. User** — **User Name** (tracks who made each edit).

**7. General** — **Data language**, **Writing language**, and **UI language**.

**8. Coding Data** — **Reload coding data** (pull latest codes/categories/relationships from all project files into this document) and **Clear coding data** (wipe and cleanly re-import to fix duplicates). Option to **reveal hidden layers** when selecting a highlight in a hidden layer.

**9. Cloud Server** — choose a provider (see [Cloud Sync](#cloud-sync)), set the **Sync interval** (0 disables auto-sync), **Sync now**, and **Prepare for offline use** (caches the app shell, Office.js, the Japanese dictionary, and the FFmpeg audio converter so they load without internet).

**10. API Settings** — translation and AI provider keys/models (see [AI & Translation](#ai--translation)).

**11. Transcription** — Speaker-identification **engine** (DIY MFCC / Picovoice Eagle), **Companion Diarizer** URL & key, default **playback speed**, **timestamp format**, and **real waveform peaks**.

**12. Appearance & Insertion** — quote styles, participant label, and how inserted **images/figures** and **tables** are captioned, positioned, and aligned in Writing mode.

![Settings tab](./assets/settings-tab.png)

---

**Metadata: Privacy-First Practices**

Metadata holds structured information *about* the document — most often details about the participant — that you can attach to exports. There are two ways to manage it.

**The quick way — a table in the document:**
1. At the **beginning of the document**, insert a **two-column table**. Make the first row a header: first cell **Metadata**, second cell **Value**.
2. Add one row per entry (e.g. `Participant | P-001`, `Region | Region A`).
3. Go to **Settings → Edit Metadata** and click **Refresh** — YaqatW reads the table and saves every row into the metadata database.
4. Whenever you add or change rows, click **Refresh** again. (It refreshes automatically when the add-in opens, but a manual refresh makes sure.)

**The dialog way — direct editing & encryption:** In the same **Edit Metadata** dialog you can add or edit fields by hand, and click the **lock icon** to encrypt a sensitive field (requires your data password). Locked fields are only visible when you provide the correct password.

**✅ Safe to store in metadata:**
- Analysis phase or round (e.g., "Coding Round 1")
- General time periods (e.g., "Spring 2024") instead of exact dates
- Geographic regions (e.g., "Region A") instead of specific locations
- Non-identifying notes
- Placeholder codes only (e.g., "P-001")

**❌ Do NOT store in YaqatW (even encrypted):**
- Real participant names or contact information
- Real interview dates or specific locations
- Real ID numbers, email addresses, or other direct identifiers

**Keep mapping separate:** Store the key linking placeholder codes (P-001) to real identities in a completely separate, secure file outside of YaqatW.

![Metadata editor with field encryption locks](./assets/metadata-editor.png)

---

## Workflow Guide

![YaqatW main interface](./assets/workflow-main-interface.png)

### Typical Analysis Workflow

**Phase 1: Document Setup**
1. Create/open a Word document and open YaqatW
2. Complete Settings (project name, password, file ID, user name)
3. Confirm Document Type is **Analysis**
4. Connect cloud sync (optional but recommended)

**Phase 2: Get to Know the Data (Mining)**
1. Use **Search** to locate key terms from your research questions
2. Use **Frequency** and **Stats** to see dominant topics and speaker patterns
3. Use **Co-occurrence** to spot which concepts cluster together

**Phase 3: Coding**
1. In **Coding**, read through and create codes as you go
2. Select text and apply codes; adjust colors for clarity
3. Optionally use the **AI Code Agent** for suggestions, then accept/edit

**Phase 4: Organization**
1. Group related codes into **Categories**
2. Document **Relationships** (cause–effect, temporal, etc.)
3. Merge or delete redundant codes (recover from **Trash** if needed)

**Phase 5: Analyze**
1. In **Analyzing**, drag codes/categories/metadata into the analysis zones
2. Run comparisons and review the results (and AI interpretation if configured)

**Phase 6: Document & Sync**
1. Add **Metadata** using placeholders and general descriptors
2. Capture **Artifacts** and **Notes** in Documenting mode
3. Click **Sync Now** to back up to your cloud provider

**Phase 7: Write & Export**
1. In a separate **Writing document**, use **Cite** to insert quotes, figures, and tables
2. Export data to Excel/CSV/JSON for further analysis

---

## Cloud Sync

### Why Sync Your Data?

- **Backup:** Protect your work against accidental deletion or computer failure
- **Multi-device:** Access your project on a laptop, tablet, or another computer
- **Collaboration:** (Experimental) Share projects with research team members
- **Manual:** Click "Sync Now" anytime, or set an automatic interval

### Supported Providers

- **Google Drive™**, **Dropbox**, **OneDrive** (Microsoft 365), and **Nextcloud** (self-hosted) connect via secure sign-in (OAuth)
- **Amazon S3** and **S3-compatible** storage connect with an endpoint, region, bucket, and access keys (use **Test connection** after saving)

### How to Sync

**First Time Setup:**
1. Go to **Settings → Cloud Server** and select a **Back end**
2. For the OAuth providers, click **Connect** and sign in / authorize in the dialog that opens; for S3, fill in the endpoint/region/bucket/keys and **Test connection**
3. Click **Sync Now** — a `YaqatW-DATA` folder is created and your data is uploaded

**Subsequent Syncs:** Just click **Sync Now** (no re-authentication until the token expires).

### What Gets Synced?

- ✅ Codes, categories, relationships
- ✅ Highlights and metadata
- ✅ Notes and artifacts (artifact files are stored in the cloud folder)
- ✅ Per-file settings
- ⚠️ Encrypted fields only if encryption is enabled

### Sync Conflicts

If you edit on two devices before syncing, the **latest edit wins** (by modification timestamp). To be safe, sync before and after working, and back up the document if a change is critical.

### Offline Work

- Without cloud sync, your work stays only on this computer — no cloud backup, no multi-device access. If the document is deleted or the device fails, the work is lost unless you back up the file yourself.
- Use **Settings → Prepare for offline use** to cache the app so it loads without internet (AI, translation, and sync still need a connection).
- **Recommendation:** Use cloud sync, or back up your document regularly to external storage if you prefer to stay offline.

---

## Encryption & Security

### Data Minimization First: De-identify Your Data

**Best practice: Don't store sensitive identifiers in YaqatW at all.**

- **Use placeholder codes** for participants (e.g., "P-001")
- **Keep participant mapping separate** in a secure file outside YaqatW
- **Minimize context data**: use general descriptors (e.g., "Interview Round 2", "Region A")
- Only include metadata that is absolutely necessary

**Important:** When encryption is enabled, only data *sent to the cloud* is encrypted. **Data stored on your computer remains unencrypted.** Protect your local machine:
- ✅ Use a strong password and lock your computer
- ✅ Store documents in your protected user folder
- ✅ Enable disk encryption (BitLocker on Windows, FileVault on macOS)
- ❌ Never leave your computer unlocked or share user accounts

### When to Encrypt?

Enable encryption if your data contains sensitive research content (coded quotes, health/financial information) or must comply with GDPR, HIPAA, or institutional policy. **Don't encrypt to justify storing identifiers** — de-identify first.

### How Encryption Works

1. Go to **Settings → Data Password**, enter a strong password (8+ characters) and confirm
2. Check **Encrypt cloud data**
3. Save

### What Gets Encrypted?

When synced with encryption enabled: text excerpts, translations, comments, and notes are encrypted. Code names and category structure remain readable (structure visible, content hidden).

### ⚠️ Important Warnings

1. **Password Loss = Data Loss** — forgotten passwords mean encrypted data is **permanently unrecoverable**. Store it in a password manager and keep a printed backup.
2. **Cannot Disable Encryption** — once encrypted, disabling encryption will **not** decrypt old data; it appears as unreadable gibberish.
3. **Sharing Encrypted Projects** — all collaborators must use the same password, communicated through a secure channel (not email/chat).

### Encryption Best Practices

- ✅ Use strong passwords like `Res!rch2024Strong`
- ✅ Store the password in a password manager (1Password, Bitwarden, LastPass)
- ❌ Don't use simple passwords or write the password on a sticky note

---

## Export & Analysis

### Export Formats

YaqatW exports from Mining footers and the coding tabs in several formats: **Excel (XLSX)**, **CSV**, **JSON**, **HTML**, and **Word (DOCX)**. Word clouds and co-occurrence maps export as **PNG/SVG images**. Many tabs offer **Export** (current view) and **Export All**.

> **Tip:** Export **as HTML** when you just want to preview the result and copy it elsewhere; export **as Word** when you want to keep the file.

### Export the Code Book

The **code book** is your list of codes and their definitions:
1. Go to the **Codes** tab → **Export** (bottom) → **Save Code Book** → **Options**
2. In the options dialog, tick what to include — e.g. **Code**, **Description**, **Color** — then **Close**
3. **Export → Save Code Book → Save as HTML** (to preview/copy) or **Save as Word** (to keep)

### Export Categories & Relationships

Exporting categories or relationships works the same way, but with richer detail options. Beyond the structure you can include, per coded item: the **selected text**, its **translation**, the **code applied**, the **category** (or relationship), and any of your saved **metadata** fields. Open **Options** to choose exactly which of these columns appear.

### Export to Excel

1. From a coding tab or Settings, open **Export Options**
2. Choose which sheets to include — Data (highlights with codes), Codes, Categories, Relationships, Metadata
3. Choose which columns to include (you can exclude sensitive columns like Date or Participant ID to reduce re-identification risk)
4. Download the workbook

![Export configuration dialog](./assets/export-configuration.png)

### Further Analysis

Once in Excel you can build pivot tables for code frequencies, cross-tabulate codes vs. participants or dates, generate charts, compute co-occurrence, and export to R/SPSS/Python for advanced analysis. (You can also do much of this in-app via [Analyzing Mode](#analyzing-mode).)

---

## AI & Translation

YaqatW integrates optional AI and translation providers. **All keys are stored locally** on your machine — see the security note below.

⚠️ **SECURITY NOTE:** API keys are stored locally in IndexedDB within the YaqatW add-in on your computer. They are not sent to YaqatW servers, but they are accessible to anyone who can open the Word document or the add-in on your machine. Only configure providers if your computer is personally owned, password-protected, locked when unattended, and disk-encrypted (BitLocker/FileVault).

### Translation

For a highlighted quote in another language: select the highlight and **Translate** (when a provider is configured), then optionally save the translation to the highlight.

**Supported translation providers:**
- **DeepL** (recommended; highest quality) — https://www.deepl.com/pro#developer (free tier ~500K chars/month). Paste the key in **Settings → DeepL API Key**.
- **Google Translate™** — create a key in https://console.cloud.google.com/ (enable Cloud Translation API), paste in **Settings → Google API Key**.

![Translation feature](./assets/translation-feature.png)

### AI Providers (for the Code Agent & Analysis interpretation)

Configure any of these in **Settings → API Settings** (each has an API key, a model selector, and an optional max-tokens field):

| Provider | Get a key |
|---|---|
| **OpenAI** | https://platform.openai.com/api-keys |
| **Claude (Anthropic)** | https://console.anthropic.com/ |
| **Groq** | https://console.groq.com/keys |
| **Gemini (Google)** | https://aistudio.google.com/app/apikey |
| **DeepSeek** | https://platform.deepseek.com/api |

A **Custom AI Settings** option lets advanced users point at a custom provider/endpoint. AI is used for the **Code Agent** suggestions (Coding mode), **Analysis** interpretation (Analyzing mode), and optional **segment transcription**. Costs are pay-per-use and tracked in each provider's dashboard.

> All AI, translation, and cloud features require an internet connection. When offline, YaqatW shows a banner and these features are unavailable.

---

## Troubleshooting

### Common Issues & Solutions

| Problem | Cause | Solution |
|---------|-------|----------|
| "Settings not initialized" | Missing required setup fields | Complete Project, Password, File ID, and User, then Save |
| Highlights not appearing | Text not selected / transient error | Re-select text and apply again; refresh the document |
| "Limited storage mode" banner | IndexedDB unavailable | Coding data still saves, but attachments/large files can't be stored — restart Word or update Office/your browser |
| "Audio features unavailable" banner | OS lacks required file storage (macOS < 13) | Update your OS to enable audio import, transcription, and diarization |
| Cloud sync fails | OAuth token expired / S3 credentials wrong | Reconnect the provider in Settings; for S3 use **Test connection** |
| "Password incorrect" | Wrong password | Check CAPS LOCK; confirm it matches the original |
| Diarization won't run | No enrolled speakers | Enroll at least one speaker on the Transcribe tab first |
| Encryption shows gibberish | Encrypted with a different password | Use the original password; if lost, data is unrecoverable |

### Getting Help

- **Report Issues:** https://github.com/yaqalab/yaqatw-support/issues — include the error message (from the F12 console), steps to reproduce, your Word/browser version, and cloud provider if relevant
- **Documentation & Feature Requests:** https://github.com/yaqalab/yaqatw-support

---

## FAQ

**Q: Is my data private?**
A: Yes. Your coding data stays in your Word document, in a local IndexedDB scoped to the add-in on your computer, and in your chosen cloud account. YaqatW never sends your data to our servers — all processing happens locally via Office.js. **YaqatW does not collect usage data, personal information, or research content.** If you enable encryption, sensitive content is protected before being sent to the cloud and cannot be read without your password (keep that password safe — encrypted data can't be recovered if it's lost). **Encryption applies only to cloud sync; local data is unencrypted,** so protect your machine with strong passwords and disk encryption. For full details, see our [Privacy Policy](https://yaqatw.alefa.net/public/privacy.html).

**Q: Can I recover a deleted code?**
A: Yes. Deleting a code doesn't delete its highlights (only the definition). The **Trash** tab shows recently deleted items so you can restore them; you can also permanently delete, after which recovery isn't possible.

**Q: What's the difference between an Analysis document and a Writing document?**
A: An **Analysis document** holds your source data and supports all modes (including Coding and Transcribing). A **Writing document** is your manuscript and exposes only Writing, Analyzing, Mining, and Documenting. You can only switch a document to Writing type if it has no highlights. Keep them under the same project name so they share codes and data.

**Q: Can I share a project with my research team?**
A: Yes. One member creates the project, syncs, and shares the `YaqatW-DATA` cloud folder. Others configure YaqatW with the **same project name**, connect to the shared folder, and **Sync Now** to pull existing codes/data. Each person works on separate documents (different File IDs) sharing the same codes, categories, and relationships. **Never edit the same file simultaneously** — always sync before and after working; the last sync wins. Each researcher uses their own cloud credentials.

**Q: What if I lose my password?**
A: If encryption is enabled, **encrypted data is unrecoverable** without the password. Store passwords securely (password manager or backup).

**Q: Can I use YaqatW in Excel or PowerPoint?**
A: YaqatW is Word-only for now. We're exploring deeper integration with other Office apps (e.g. reading coding data in Excel) for the future.

**Q: How big can my document be?**
A: Keep each document under ~50 MB for best performance. Very large documents (100+ MB) may slow Word and the add-in, since highlights, codes, and annotations are processed in real time. For large projects, split work into multiple documents — ideally one per interview or source.

**Q: Does YaqatW work offline?**
A: Yes — all work is local until you sync. Use **Prepare for offline use** to cache the app. AI, translation, and cloud sync require internet. **Trade-off:** offline means no automatic backup, so back up your document regularly if you stay offline.

**Q: Can I export my data to other formats?**
A: Yes — **Excel (XLSX)**, **CSV**, **JSON**, **HTML**, and **Word (DOCX)**, plus **PNG/SVG** for word clouds and co-occurrence maps. Each data type (codes, categories, relationships, highlights) can be exported separately.

**Q: How much does YaqatW cost?**
A: YaqatW is completely free — no subscription, no accounts, no hidden costs. (Optional AI/translation providers you configure are billed by those third parties, not by YaqatW.)

**Q: Is there a mobile app?**
A: No. Office Add-ins aren't supported on the Word mobile apps for iOS® or Android™ due to Microsoft platform limitations. Use YaqatW on Word for Windows, macOS, or the web. On tablets, use the full desktop or web version of Word.

**Q: Will YaqatW be open source?**
A: YaqatW's source is currently proprietary while we develop it, but we're committed to releasing it as open source once the project reaches broader adoption.

---

## Contributors

**Main Contributors:** [frianasoa](https://github.com/frianasoa)

---

## Thank You!

Thank you for using YaqatW! Your feedback is invaluable. Please share thoughts, issues, and feature requests on [GitHub Issues](https://github.com/yaqalab/yaqatw-support/issues).

Happy coding! 🎓
</content>
</invoke>
