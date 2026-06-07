# YaqatW User Guide

**Yet Another Qualitative Analysis Tool for Word**

Welcome to YaqatW. This guide walks you through qualitative coding, annotation, and thematic analysis inside Microsoft Word — slowly, and from the beginning. You do not need to be technical to follow it. Where something is genuinely fiddly (installation, mostly), I say so and take extra time over it.

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

YaqatW is a Microsoft Word add-in for people who do qualitative analysis — researchers, students, and anyone trying to make sense of interviews, field notes, documents, or transcripts. Instead of moving your text into a separate program, you work where your text already lives: in Word.

The add-in is organized into six **modes**. A mode is not a separate file or a separate project — it is simply a different lens on the same work. You switch modes depending on what stage of the analysis you are in, and your data stays put as you switch. The six modes are:

- **Coding Mode** — read your source text and mark passages: create your own codes, apply them to selections, and organize those codes into categories and relationships. Optional AI assistance can suggest codes for you.
- **Mining Mode** — get to know the raw text before, during, or after coding: search it, count word frequencies, map which words travel together, and look at per-speaker statistics.
- **Analyzing Mode** — ask structured questions of your coded data by treating codes, categories, metadata, and search groups as variables you can combine and compare.
- **Documenting Mode** — keep the material that surrounds your text: the photos, recordings, and documents you collected, plus the analytic notes you write as you think.
- **Writing Mode** — draft your manuscript and pull already-coded quotes, citations, figures, and tables directly into the page, correctly attributed.
- **Transcribing Mode** — turn audio recordings into speaker-labelled, time-stamped text, with playback shortcuts, voice enrollment, and automatic speaker detection.

And underneath every mode, a few things are always true:

- You can **annotate** documents with metadata and field notes.
- You can **sync** your work to cloud storage so it survives a lost laptop or a crashed browser.
- You can **export** your analysis to Excel, CSV, JSON, HTML, or Word.
- You can **encrypt** sensitive data before it leaves your machine.

### Privacy by design

If there is one thing I want you to take away before anything else, it is this: **your data stays with you.** Qualitative data is often the most sensitive material a researcher handles — interviews, life stories, things people told you in confidence — and a tool that asked you to upload all of it to someone else's server would be the wrong tool for the job. YaqatW is built the other way around:

- **Nothing goes to our servers.** There is no YaqatW account and no YaqatW backend holding your data. Everything is processed locally in Word, through Office.js, on your own machine. We do not collect your research content, your usage, or your personal information — there is no mechanism for us to do so.
- **It is your cloud, not ours.** When you sync, you connect *your own* Google Drive, OneDrive, Dropbox, Nextcloud, or S3 account, and your data goes into a `YaqatW-DATA` folder there. We never see it, and you can disconnect or delete it at any time. See [Cloud Sync](#cloud-sync).
- **Bring your own keys.** AI and translation are optional, and when you use them you supply your own API keys. Those keys are stored locally on your machine and are sent only to the provider you chose — never through us. You talk to OpenAI, Claude, DeepL, and the rest directly. See [AI & Translation](#ai--translation).
- **Encryption is yours to control.** If your data is sensitive, you can encrypt the content before it ever leaves for the cloud, with a password only you hold. See [Encryption & Security](#encryption--security).

The practical consequence of all this is that there is no subscription and no account to pay for — but I would rather you remember the design than the price tag. The point was never just that YaqatW is free; it is that your data is *yours*, and the tool is built so that it stays that way.

### A little background

Yaqat used to be a web application on a private server that I have been developing and maintaining for the past ten years. I have been using it with few students and collaborators over the years. I named it Yet Another Qualitative Analysis Tool because there are already countless qualitative analysis tools out there. Rather than trying to reinvent the field, the goal was to create a tool that solves the specific problems I encountered in my own research.

Recently, I decided to bring Yaqat to Microsoft Word as an Add-in in order to make it accessible to a wider audience, especially students who do not have the resources to afford expensive QDA applications, without compromising on quality. It is also a very simple way to introduce coding to students without the hurdle of installing additional software such as dedicated QDA tools. If it happens to make your work a little easier, save you a few hours, or help you discover something new in your data, then it has achieved its purpose.

More documentation is added as the project develops. For more information, visit https://yaqatw.alefa.net/public/about.

---

## Prerequisites

Before you install anything, a few things need to be true about your setup. None of them are unusual, but it is worth checking them now rather than halfway through.

- **Microsoft Office newer than 2019.** Word add-ins are a relatively recent mechanism. They do **not** work on versions before 2019, and they may not work on some 2019 builds either. Please install the latest version of Office available to you — through a university or workplace account if you have one. Office 2019 is no longer supported by Microsoft anyway, so unless you depend on an older version for compatibility reasons, this is a good moment to upgrade.

- **Word for Windows, macOS, or the web.** YaqatW runs on all three. The web version works but has been tested less thoroughly than the desktop versions, so treat it as the more adventurous option. There is **no mobile support** — add-ins do not run in the Word apps for iOS or Android, and that is a Microsoft platform limitation, not something YaqatW can work around.

- **Cloud storage is strongly recommended.** This matters most on the web version, where the data stored in your browser is more easily wiped out than data on your disk. Connecting a cloud provider (Google Drive, OneDrive, Dropbox, Nextcloud, or Amazon S3) means your work survives a browser reset or a device failure. Desktop users are encouraged to enable it too — backups are cheap insurance. Setup is covered later in [Cloud Sync](#cloud-sync).

- **On macOS, cloud storage is *required* for export.** This one is easy to overlook, so I want to be explicit about it. Word add-ins on Mac cannot trigger an ordinary file download. To work around that, YaqatW exports on macOS by uploading the finished file to your connected cloud provider (under a `export/` folder inside your project) and then opening it in your browser so you can save it from there. Without a connected provider and a project name set, export simply does not work on macOS. Windows and Word on the web download files directly and have no such requirement. See [Export & Analysis](#export--analysis) for the details.

---

## Installation

I will be honest with you: installation is a little more involved than a normal one-click install, because YaqatW is not yet in the Microsoft Store. Publishing to the Store comes with a set of technical and administrative requirements that we are not ready to meet just yet — we plan to as the number of users grows. In the meantime, the method below, called **sideloading**, is the standard way to distribute an add-in to a small group of users. Once you have done it once, it is not hard.

The process has two parts: first you obtain the manifest file, then you tell Word to trust it.

### Step 1: Download the Manifest File

Get the `manifest.xml` file from the YaqaLab team (or from wherever you were directed to). When you download it, your browser may warn you that the file "may harm your computer." This is the generic warning browsers show for *any* `.xml` file downloaded from Google Drive — it is not a sign that anything is wrong. The file is plain text and safe. Choose **download anyway**. If you would like to reassure yourself, open it in Notepad or any text editor and read it before you install; it is human-readable.

### Step 2: Trust the Add-in in Word

How you do this depends on whether you are on Windows, macOS, or the web. Follow the section for your platform.

#### Windows

On Windows, the idea is to put the manifest in a shared folder and then register that folder with Word as a trusted source. This is a normal Windows operation; if any individual step gives you trouble, searching the internet for "share a folder Windows" will turn up plenty of help.

References: [Microsoft's guide to sideload from a network share](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/create-a-network-shared-folder-catalog-for-task-pane-and-content-add-ins) · [Video walkthrough (from 2:34)](https://www.youtube.com/watch?v=XXsAw2UUiQo&t=154s)

**A. Create and share a folder containing `manifest.xml`:**

1. Create a folder somewhere stable — under *Documents* is a good choice — and move `manifest.xml` into it.
2. Share the folder with **Everyone**: right-click the folder → **Properties** → the **Sharing** tab → **Share…** → type **Everyone** → click **Add** → **Share**.
3. Once sharing finishes, Windows shows you the network location of the folder, something like `\\DESKTOP-NDMDVHB\Users\You\Documents\My add-ins`. Copy that location. If it appears in a messier form (for example beginning with `file://`), clean it into the backslash form shown below:
   ```
   \\DESKTOP-NDMDVHB\Users\You\Documents\My add-ins
   ```
4. Confirm it actually works before moving on: paste that path into the address bar of a File Explorer window and press Enter. If your folder opens, the share is good. If it does not, the rest will not work either, so fix this first.

**B. Register the folder as a trusted catalog in Word:**

1. Open Word with a blank document. (You will not need the document afterwards.)
2. Go to **File → Options → Trust Center → Trust Center Settings… → Trusted Add-in Catalogs**.
3. Paste the cleaned `\\…` share path into the box, click **Add catalog**, then **OK**, then **OK** again.
4. Close Word completely and reopen it, so the new catalog is picked up.

**C. Load the add-in:**

1. Open a document, go to the **Insert** (or **Home**) tab depending on your version, and find **Add-ins**.
2. Click **Add-ins → Advanced** (it may say **My Add-ins**), open the **SHARED FOLDER** tab, select **YaqatW**, and click **Add**.
3. The YaqatW icon now appears on the ribbon. Click it, and the task pane loads on the right. If the document was empty, you will also see some placeholder text written into it — that is expected.

#### macOS

Sideloading on macOS is actually simpler than on Windows: there is no folder to share, you just drop the manifest into a specific location. Reference: [Microsoft's guide to sideload on Mac](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/sideload-an-office-add-in-on-mac).

1. Download `manifest.xml` as described in Step 1 above (the download step is identical on a Mac).
2. Open Finder, press **Cmd+Shift+G** to open the "Go to Folder" dialog, and enter the path below. If the `wef` folder does not exist yet, create it. Replace `<username>` with your Mac account name:
   ```
   /Users/<username>/Library/Containers/com.microsoft.Word/Data/Documents/wef
   ```
3. Copy `manifest.xml` into this `wef` folder.
4. Open Word — or quit and reopen it if it was already running — and open a document.
5. Go to the **Home** tab, click **Add-ins**, and select **YaqatW** from the menu. On a Mac, sideloaded add-ins appear under **My Add-ins** / **Developer Add-ins**. The pane loads on the right, exactly as it does on Windows.

> **NB:** On some Mac setups you may need to re-add the add-in from the Add-ins menu each time you launch Word. The manifest stays put in the `wef` folder, but Word does not always keep the add-in pinned to the ribbon between sessions. This is a Word quirk, not a problem with your installation.

#### Word on the web

References: [Microsoft's guide for the web](https://learn.microsoft.com/en-us/office/dev/add-ins/testing/sideload-office-add-ins-for-testing?source=recommendations#manually-sideload-an-add-in-to-office-on-the-web) · [Video (from 4:04)](https://youtu.be/XXsAw2UUiQo?si=gOqDAYBVIKPa1heG&t=244)

1. Sign in at https://office.com with your Microsoft 365 account and open Word.
2. Go to **Insert → Add-ins → Upload My Add-in**.
3. Click **Browse**, select your `manifest.xml`, and click **Upload**.
4. YaqatW is now available for this session. Because browser storage is less durable than disk storage, please enable cloud storage so your data is preserved — see [Prerequisites](#prerequisites).

### Future: Microsoft AppSource

Once YaqatW is published to the Microsoft Office Store, all of the above will collapse into a one-click install:

1. Go to **Insert → Get Add-ins**.
2. Search for "YaqatW".
3. Click **Get**.

We are not there yet, but that is the direction.

---

## Getting Started

### Initial Setup (First Time Only)

The first time you click the YaqatW icon, the task pane opens on the right and shows a short **disclaimer**. Read it and click **OK**. If your document was empty, you will also notice some placeholder text appear in it — this is just sample content so the early features have something to work with, and you can delete it later.

A small piece of advice before you start typing: **widen the pane** by dragging its left edge. The interface has a lot to offer, and it is far more comfortable to learn it in a wide pane. Once you are familiar with where everything is, you can shrink the pane back down and work in a narrow strip if you prefer.

You will now see the **Settings** tab with the fields you need to fill in. One thing to understand up front: **YaqatW does not manage usernames or passwords for you.** There is no account to create and no server keeping your credentials. That is good for privacy, but it also means that whatever you set here is yours to remember — so note it somewhere secure.

Here is what each field is for:

1. **Project Name**
   - A name for your research project — for example, `interview-study-2024`.
   - It can contain lowercase letters, numbers, and hyphens.
   - The project name is **shared across every file in the same project**. This is the thread that ties your documents together: two documents with the same project name share the same codes, categories, and relationships.

2. **Data Password** (required if you intend to encrypt sensitive data)
   - Choose a strong password — at least 8 characters, mixing letters and numbers.
   - **Write this down somewhere safe.** If you lose it, any data you encrypted with it cannot be recovered by anyone, including us. There is no reset.
   - Re-enter it in the confirmation field.

3. **Current File (File ID)**
   - A unique label for *this particular document* — for example, `interview-001`.
   - This is what lets you work across several documents inside one project. Codes, categories, and relationships are shared across all files in the project, but the **highlights** (the coded passages themselves) belong to each individual file.

4. **User Name**
   - Your name, in lowercase with no spaces.
   - YaqatW uses this to record who made each edit, which matters when you are collaborating.

![YaqatW initial settings configuration](./assets/initial-settings.png)

5. **Cloud Sync** (optional, but recommended)
   - Choose a provider: Google Drive™, Dropbox, OneDrive, Nextcloud, or Amazon S3 (and S3-compatible storage).
   - Click **Sync now** and follow the sign-in prompts.
   - YaqatW creates a folder called `YaqatW-DATA` in your cloud account and stores your project data there, both as a backup and so you can pick up the same project on another device.

   ![Cloud backend selection dropdown](./assets/select-cloud-backend.png)

**Once these fields are filled in, the rest of the feature tabs unlock.** Until then, only Settings is available — this is deliberate, so that nothing you create ends up unattached to a project.

---

## Document Types

Before you choose a mode, it helps to tell YaqatW what kind of document you are looking at. You set this in **Settings → Document Type**, and your choice decides which modes are even offered to you. There are two types:

- **Analysis document** (the default) — this is your raw material: the interview, the transcript, the source text you are going to code and analyze. For an Analysis document, **all six modes are available.**

- **Writing document** — this is the thing you are *producing*: a manuscript, a report, a chapter you are drafting from data you have already coded. For a Writing document, only **Writing, Analyzing, Mining, and Documenting** are available. Coding and Transcribing are deliberately hidden, so you cannot accidentally start coding your own manuscript.

There is one rule worth knowing: **you can only switch a document to Writing type if it has no highlights.** This keeps your coded source data and your written output cleanly separated, which is exactly what you want. The typical arrangement is one or several Analysis documents holding your interviews and sources, plus a separate Writing document for your paper — all sharing the same project name, so the writing document can reach back into the coded data.

> 📸 **Screenshot:** [Settings > Document Type selector (Analysis document / Writing document)]

---

## Modes & Features

As described earlier, YaqatW is organized into six modes, and a mode is just a different view of the same project — your data does not move or change when you switch. You change mode from **Settings → yaqatw-mode**, or from the pinned header bar at the top. Which modes appear depends on the [document type](#document-types) you set.

Here is the whole map at a glance:

| Mode | Tabs | What it is for |
|---|---|---|
| **Coding** | Codes · Categories · Relationships | Coding source text, then organizing those codes into categories and relationships |
| **Mining** | Search · Frequency · Co-occurrence · Stats | Exploring the raw text — searching, word frequency, collocation networks, corpus statistics |
| **Analyzing** | Analysis | Cross-tabulating codes, categories, metadata, and search groups as variables |
| **Documenting** | Artifacts · Notes | Cataloguing evidence files and writing analytic memos |
| **Writing** | Cite | Drafting a manuscript with quotes, citations, figures, and tables drawn from your project |
| **Transcribing** | Import · Transcribe · Diarize | Turning audio recordings into speaker-labelled, time-stamped text |

*(Every mode also has a **Settings** tab; the table leaves it out to keep things short.)*

The rest of this section takes each mode in turn and explains it properly.

---

### Coding Mode

**What it is for:** turning raw source text into coded data — creating codes, applying them to passages, and organizing those codes into categories and relationships.

This is the heart of the add-in, so let me set out the vocabulary first, because the rest only makes sense once these three words are clear.

A **code** is a label you invent for a concept you care about — "Leadership," "Frustration," "Turning point." A **highlight** is what you get when you apply a code to a passage of text: a colored span in the Word document that carries one or more codes, plus an optional note and translation. The act of coding, then, is reading your document and turning meaningful passages into highlights.

One distinction is worth holding onto: **codes, categories, and relationships are shared across every file in the project**, while **highlights belong to the individual file.** In practice this means a code you create while working on `interview-001` is immediately available when you open `interview-002` under the same project — but the passages you highlighted in `interview-001` stay with `interview-001`.

> Coding mode is available only for **Analysis documents**. It is hidden for Writing documents, which by definition have no highlights.

#### The **Codes** Tab — Mark Up Your Text

**What it does:** lets you create codes and apply them to selections in your document.

**Creating a code:**

1. Click the **Codes** tab.
2. Click **New Code** (the **+** button).
3. Fill in:
   - **Code Name** — e.g. "Leadership"
   - **Description** — e.g. "Instances where a leader emerges or asserts authority"
   - **Color** — pick from the palette; the color is what you will see in the document, so choose something distinct.
4. Click **Create**.

**Applying a code to text:**

1. Select an excerpt in your Word document.
2. Right-click the code in the list and choose **Use code** — or **Use code with comment** if you want to attach a comment in the same step.
3. The selected text is now highlighted in the code's color and labelled with the code name.
4. Click any coded passage in the document and its **info panel** opens. From there you can edit the passage, add notes and a translation, and then **save & close**.

**Viewing and finding codes:**

- Switch the code list between **Grid**, **List**, and **Compact** views, whichever suits the pane width and the number of codes you have.
- Use the **search** box to filter codes by name when the list grows long.

**Editing and deleting:**

- **Edit** changes a code's name, description, or color.
- **Delete** removes the code *definition*. Importantly, this does not remove the highlights already in your document — those stay. And a deleted code is not gone for good: it lands in the **Trash**, from where you can restore it.

**Working with a single highlight:** A passage can carry **more than one code at a time** — apply additional codes to the same selection, or **detach** a code you applied by mistake. Selecting a highlight opens its info panel, where you can see and edit:

- the **highlighted text** itself,
- a **translation** (translate on demand when an AI or translation provider is configured — see [AI & Translation](#ai--translation)),
- a free-text **note**, and
- the list of **codes applied** to that passage.

**Layers:** Highlights live in **layers**, and layers are how you keep parallel passes of coding from colliding. For instance, you might keep an original-language layer and a separate **translation layer**, or a first-pass and a second-pass round of coding. You can **create a new layer** and **show or hide layers independently**. Hidden layers stay hidden by default; if you would like YaqatW to offer to reveal a hidden layer when you click a highlight that lives in one, turn on *Offer to reveal hidden layers* in Settings.

**Exporting your coding work:** From the Codes footer you can export both the **code book** (your codes and their definitions) and the **coded data** (the highlights, with their codes, notes, and translations) as Word, Excel, HTML, JSON, or CSV. The details are in [Export & Analysis](#export--analysis).

**Importing comments as codes:** If your document already carries Word review comments, YaqatW can turn them into codes — each comment becoming a code applied to the text it was attached to. This is genuinely useful if you have already done a first pass of commenting in Word and do not want to redo it.

The **Import comments** button appears inside the **Add/Edit code** dialog, and **only when the document actually contains comments** — so if you do not see it, that is why. Open the dialog, click **Import comments**, and choose how each comment should map to a code:

- **First sentence → code name, the rest → description.** Best when your comments are short.
- **Split on a delimiter.** Structure each comment as `code <delimiter> description`, using a colon, a line break, or a custom delimiter; the text before the delimiter becomes the code, the text after becomes the description.
- **Labeled sections.** Mark the parts explicitly: `[Code]` …the code… `[Description]` …the description…

Before you confirm, a live preview tells you how many comments will become new codes, how many will simply be applied, and how many will be skipped. (For example, a comment that just reads "My interesting note" becomes a code of that name on the commented passage.)

**The AI Code Agent (optional):** When an AI provider is configured (see [AI & Translation](#ai--translation)), the Codes tab can offer AI-assisted coding **Suggestions**. You do not have to write prompts from scratch; instead you steer the AI with a few structured choices:

- **Reasoning mode** — *Inductive* (build patterns up from the data), *Deductive* (test predictions from existing theory), or *Abductive* (match to your existing codes first, and let new ones emerge where nothing fits).
- **Analytic stance** — *Descriptive*, *Interpretive*, *Critical*, or *Comparative*.
- A **research question** and a free-text **prompt** to focus the AI's attention.
- Options to embed and validate against your existing codes, include interviewer passages as context only, cap how many new codes the AI may propose, and output codes in your writing language.

Nothing is applied to your document automatically. Suggested codes are shown to you first, so you can accept, edit, or reject each one.

> 📸 **Screenshot:** [Coding mode > Codes > AI Suggestions panel (reasoning mode, analytic stance, research question)]

> 📸 **Screenshot:** [Coding mode > Codes > Import Comments dialog with strategy + preview]

![Coding tab with code list and apply functionality](./assets/coding-tab.png)

#### The **Categories** Tab — Organize Your Codes

**What it does:** groups related codes into categories, building a hierarchy of concepts on top of your flat list of codes.

The interface here looks a little different from the Codes tab, but it is straightforward.

**Creating a category:**

1. Click the **Categories** tab.
2. Click **New Category** (the **+** button).
3. Enter a **Category Name** and, if you like, a **Description**.
4. Click **Create**.

**Adding codes to a category:**

1. Open the category (or right-click it).
2. Choose **Add Codes to Category**.
3. Tick the codes you want and confirm.

Repeat until every code that belongs to the category has been added. You can expand and collapse categories with the arrow icon to keep the tree tidy.

**An example of what you are building:**

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

**Why bother:** After coding a document you may have twenty or more codes, which is a lot to reason about. Grouping them by theme — Behaviors, Attitudes, Outcomes, and so on — gives you a smaller number of larger ideas to analyze and report against.

#### The **Relationships** Tab — Document Connections Between Concepts

**What it does:** records *how* concepts connect — cause and effect, before and after, part and whole — rather than just what concepts exist.

Relationships behave a little differently from categories, and the difference is the useful part. A relationship is a **type** (for example, "Cause → Effect"), and within that type you create **instances** — concrete examples of that relationship found in your data. So one relationship type can hold many instances.

**Creating a relationship:**

1. Click the **Relationships** tab.
2. Click **New Relationship** (the **+** button).
3. Name the **Relationship Type** and click **Create**. One Instance is created for you automatically.

**Some relationship types you might use:** Cause → Effect · Then → Now · Example → General · Part Of · Precedes · Contradicts.

**Adding codes or categories to a relationship:**

1. Open the relationship to expand it.
2. On an Instance, choose **Add Code/Category** for each side of the relationship.
3. Relationships work best with categories, but you can add individual codes too.

**Adding more instances:** to record another concrete example of the same relationship type, just add another Instance.

**An example:**

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

**Using relationships as theme containers:** Thematic analysis usually needs only three levels — **Data → Codes → Themes**. But depending on your coding style, you sometimes want a fourth level — **Data → Codes → Categories → Themes**. Because a relationship can hold categories, you can use it as the outer "Themes" container sitting above your categories. That gives you the extra level without leaving the add-in or bending the tool out of shape.

---

### Mining Mode

**What it is for:** getting to know the raw text itself — searching it, measuring word frequency, mapping which words travel together, and profiling who said what — before, during, or after you code.

To do any of this, Mining first has to read your document into something it can analyze. It does this by parsing the text into **turns**, and it is worth understanding how, because the cleaner your document, the cleaner the analysis.

YaqatW treats **each paragraph as one potential speaker turn**. A paragraph counts as a turn if it contains a colon: the text *before* the colon is taken as the speaker label (uppercased), and the text *after* it is the spoken content. The speaker is then classified as an **interviewer** or an **interviewee** by checking the label against a list of known interviewer names (you can extend that list through document metadata). A trailing timestamp in the form `[HH:MM:SS]` is recognized and stored too. So a paragraph like:

```
INTERVIEWER: What happened next? [00:04:12]
```

is read as an interviewer turn, with the timestamp pulled out automatically.

What if your document is not a transcript at all — just prose, with no speaker labels? YaqatW notices: if fewer than about a third of the paragraphs look like turns, it concludes the document is plain text and treats the whole thing as a single speaker called `SOURCE`, one turn per paragraph. Either way, Mining ends up with a clean list of turns to work on, which is why **keeping one speaker turn per paragraph** (see [Transcribing](#transcribing-mode)) makes everything downstream tidier.

The current document is indexed automatically when you open it. If results ever look stale, use **Settings → Re-index current document** to rebuild the index.

At the top of each Mining tab there is a **scope** bar that lets you decide how wide to cast your net:

- **Global** — analyze every indexed file in the project, not just the document in front of you.
- **Files** — narrow to particular files (all of them, by default).
- **Speakers** — filter to particular speakers.

Every tab has its own **Export / Export All** footer, and results can be filtered by speaker **role** (All / Interviewer / Interviewee).

#### The **Search** Tab — Full-Text Exploration

**What it does:** searches across your text to find passages and patterns. There are seven search modes, ranging from a plain substring to fairly advanced queries:

| Mode | What it does |
|---|---|
| **Exact** | Matches the exact substring you type |
| **Wildcard** | `*` stands for any characters — e.g. `saka*` matches `sakafo`, `sakafoana` |
| **Boolean** | `AND`, `OR`, `NOT`, and quoted phrases — e.g. `sakafo AND ankizy NOT vary` |
| **Proximity** | `NEAR/N` or `BEFORE/N` — e.g. `sakafo NEAR/5 ankizy` finds the two words within five tokens of each other |
| **Fuzzy** | Matches approximate spellings and morphological variants |
| **Regex** | A full JavaScript regular expression, for when you need precise control |
| **Named** | A YAML file defining named groups of search terms — see below |

**Display options** let you show, on each result, the full speaker turn, the speaker's name, their role, the match score, the turn number, and selected metadata fields. Click any result to jump straight to that location in your document.

**Named search** deserves a closer look, because it is the most powerful mode for theory-driven work. You define groups and subgroups of search terms in a YAML file, then control how matches are deduplicated with the **Exclusion** setting:

- **None** (the default) — every match is reported. If one turn matches two different groups, you get two results.
- **Exclude turn** — once a turn matches any subgroup, it is set aside and not counted again for the remaining subgroups. Each turn appears at most once across all results.
- **Exclude subgroup** — once a subgroup has captured a match anywhere, that subgroup stops searching. Each subgroup captures at most one turn in total.

The right choice depends on whether you want exhaustive coverage (None) or a clean, non-overlapping tally (the Exclude options).

> 📸 **Screenshot:** [Mining mode > Search > search-mode selector (Exact / Wildcard / Boolean / Proximity / Fuzzy / Regex / Named)]

![Mining search tab with search filters and results list](./assets/mining-search.png)

#### The **Frequency** Tab — Word Frequency Analysis

**What it does:** counts the most frequent words (or word pairs, or triplets) in your text, so the dominant topics surface on their own.

**Options:**

- **N-gram** — count single words, consecutive pairs (bigrams), or triplets (trigrams).
- **Min frequency** — hide anything appearing fewer than N times, to cut down on noise.
- **Hapax** — show only the words that appear exactly once (the *hapax legomena*), which can be revealing in their own way.
- **Filter stopwords** — drop common function words (pronouns, prepositions, fillers) that would otherwise dominate the list without telling you anything.
- View the result as a frequency **table** or as a **word cloud**.

![Mining frequency tab](./assets/mining-frequency.png)

**Why it helps:** It tells you what your data is "about" before you have read every word of it. If "stress" appears 47 times and "deadline" 28 times, those are very likely to be major themes — and now you know to watch for them as you code.

#### The **Co-occurrence** Tab — Word Networks

**What it does:** finds which words tend to appear near each other (their *collocates*) and draws them as a network you can read at a glance.

**Options:**

- **Target word(s)** — separate several with `|`, e.g. `build | home | country`.
- **Window** — how many tokens to scan to the left and right of the target word.
- **Min frequency** and **Max results** — to keep the network from becoming an unreadable hairball.
- **Filter stopwords** — to drop function words.
- Toggle between a ranked **table** and the network **Map**.

**Map controls:**

- **Layout** — Force, Radial, Circular, Clustered, or Tree.
- **Edge style** — straight Line or Curve.
- **Distant edges** — how to draw cross-community or cross-branch links (gray, dashed, dotted, or hidden).
- Decorative versus analytical coloring, the number of nodes shown, and full-map export to PNG or SVG.

![Mining co-occurrence map](./assets/mining-words-co-occurence.png)

#### The **Stats** Tab — Corpus Statistics & Visualizations

**What it does:** gives you quantitative overviews of your text and your speakers.

- **Word cloud** — words sized by frequency, with linear / sqrt / log scaling, rotation, quality, and color options; exportable as PNG or SVG.
- **Dispersion plot** — for words you choose, a tick mark on every turn where the word appears. This shows you *where* in the data a word is used: clustered in one section, or spread evenly throughout. You can optionally split it by file.
- **Turn-length distribution** — how many turns fall into each token-length band, so you can see whether people gave short answers or long ones.
- **Speaker statistics** — per speaker: number of turns, average turn length, vocabulary size, and Type-Token Ratio (a standard measure of lexical diversity).

![Word cloud](./assets/mining-word-cloud.png)

> 📸 **Screenshot:** [Mining mode > Stats > dispersion plot (ticks per turn)]

> 📸 **Screenshot:** [Mining mode > Stats > speaker statistics table (turns, vocab size, TTR)]

**Why it helps:** You might build a word cloud for a presentation, or use the speaker statistics to compare how much — and how diversely — each participant spoke. And both word clouds and co-occurrence maps can be **saved as figures** and later inserted into a Writing document (see [Writing Mode](#writing-mode)), so the picture you make while exploring can go straight into your paper.

---

### Analyzing Mode

**What it is for:** asking structured questions of your coded data — *does this pattern differ by group?* — by treating your codes, categories, metadata, and search results as **variables** that you can combine and compare. The point is to do this without exporting everything to a separate statistics package.

#### The **Analysis** Tab — Variable-Based Exploration

**What it does:** lets you build an analysis the way you would sketch out a small study. You pick what you are measuring, pick what might explain it, optionally pick how to break it down, and run it.

**The building blocks.** The left panel lists every **data item** in your project, grouped by kind, each marked with a colored badge:

| Badge | Kind | What it contributes |
|---|---|---|
| **C** | Code | A single code |
| **Ca** | Category | A group of codes |
| **R** | Relationship | A documented code/category connection |
| **H** | Highlight | An individual coded passage |
| **M** | Metadata | A document or participant metadata field |
| **Co** | Co-occurrence | A word-pair from Mining |
| **G** | Group | A named-search group |

**The three zones.** You drag items from the left panel into one of three zones on the right to frame your question:

- **Dependent** — what you want to measure or explain (the outcome — a code or category, for instance).
- **Independent** — the factor you suspect relates to it (another category, say, or a co-occurrence).
- **Group by** — how to split the results into comparable groups (a metadata field such as region or interview round).

**Running it.** Click **Run** to compute the result: counts and overlaps across the variables you placed, and — when an AI provider is configured — a written **interpretation** of the patterns. You can open the result in a dialog and export it. The layout adapts to the width of the pane (it switches between an accordion and a side-by-side view), and your last configuration is remembered, so you do not have to rebuild it each time.

> 📸 **Screenshot:** [Analyzing mode > Analysis > data items panel + dependent / independent / group-by zones]

> 📸 **Screenshot:** [Analyzing mode > Analysis > result dialog with AI interpretation]

**A concrete example:** put a category in *Dependent*, drop a metadata field like "Region" into *Group by*, and you will see how that category is distributed across regions. Or place two categories in *Dependent* and *Independent* to see how often they overlap in the data.

> Analyzing mode works for both Analysis and Writing documents, so you can interrogate your data even while you are drafting your paper.

---

### Documenting Mode

**What it is for:** keeping the evidence and the thinking that surround your text — the photos, recordings, and documents you collected in the field, plus the analytic memos you write as you make sense of it all.

The distinction from Coding is worth drawing clearly. Coding works on text *inside* the Word document. Documenting manages material that sits *alongside* it. It has two tabs — **Artifacts** (evidence files) and **Notes** (memos) — and both are searchable and can be pulled into a Writing document through the [Cite](#writing-mode) tab.

#### The **Artifacts** Tab — Manage Evidence Files

**What it does:** catalogues evidential material that is not plain text — field photos, audio clips, scanned documents — together with where it came from and what you make of it.

**Each artifact records:**

- **Title** (required) — a short identifying label.
- **Source** — where it came from (a person, organization, archive, or URL).
- **Collected by** — defaults to your user name.
- **Session** — an optional ID linking it to a fieldwork session or visit.
- **Tags** — free-form keywords for filtering later.
- **Interpretation** — your reading of what the artifact shows. This is the researcher's voice, kept distinct from the raw material.
- **Attachments** — the actual files (images, audio, documents).

> **Cloud required:** Artifact attachments are stored in your cloud provider's project folder, so you must configure a cloud backend in Settings before you add artifacts. Without one, attachments may be lost on a browser reset. And if the cloud provider is disconnected, existing attachments may be temporarily unreachable until you reconnect.

**Lifecycle and sync:** Artifact records sync with the rest of your project, while their attachments are uploaded to the project folder on your cloud provider. An artifact can be **deprecated** (kept on the record, with a reason) or **deleted** (marked deleted, and still recoverable). If an attachment cannot be found either locally or in the cloud — which can happen after you switch devices — YaqatW flags the **missing attachments** and lets you decide whether to keep or prune them. A saved artifact can later be inserted into a Writing document as an image with a caption and a source line.

> 📸 **Screenshot:** [Documenting mode > Artifacts > artifact list]

> 📸 **Screenshot:** [Documenting mode > Artifacts > artifact editor with attachments + interpretation]

#### The **Notes** Tab — Analytic Memos

**What it does:** lets you write and keep analytic notes and memos alongside your project. Like artifacts, notes can be searched and inserted into a Writing document through the Cite tab — so the thought you have while coding does not get lost before you write it up.

> 📸 **Screenshot:** [Documenting mode > Notes > note editor]

---

### Writing Mode

**What it is for:** drafting the manuscript itself — your paper, report, or chapter — by pulling already-coded evidence out of your project and into the page, correctly attributed, instead of copy-pasting and losing track of where each quote came from.

Writing mode is meant to run in its own **Writing document** (see [Document Types](#document-types)), kept under the same project name as your coded sources. That shared project name is what lets the writing document reach all of their highlights, notes, artifacts, figures, and tables.

#### The **Cite** Tab — Search and Insert Quotes, Citations, Figures & Tables

**What it does:** pulls material from anywhere in your project into the document you are drafting.

**What you can search and insert:**

- **Highlights** — your coded passages, with their text, note, or translation.
- **Artifacts** — inserted as an image with a caption and a source line.
- **Notes** — your analytic memos.
- **Tables** and **Figures** — saved tables, and the saved word clouds and co-occurrence maps from Mining.

**How to use it:**

1. Click the **Cite** tab and choose a source.
2. Search for codes, keywords, or passages.
3. Review the matches in context.
4. Insert at your cursor, choosing:
   - **Inline** or **Block** quote
   - **Linked (refreshable)** or **Unlinked (plain paste)**
   - **Plain text** or **Rich text**

**Why "linked" matters.** A **linked (refreshable)** citation stays connected to its source highlight or figure. If you later re-code a passage, fix a translation, or regenerate a word cloud, you can simply **refresh** the inserted citation instead of hunting it down and replacing it by hand. Choose **unlinked (plain paste)** when you want a one-off snapshot that will not change no matter what happens to the source. Both have their place: linked for living drafts, unlinked for final or quoted-verbatim material.

**Attribution.** Quotes are labelled with their source — typically the participant ID drawn from a metadata field. The formatting of all this (the quotation characters, the prefix and suffix around the participant label, and which metadata field supplies the participant ID) is configurable under **Settings → Appearance & Insertion**, as is how inserted images and tables are captioned, positioned, and aligned.

> 📸 **Screenshot:** [Writing mode > Cite > source picker (Highlights / Artifacts / Notes / Tables / Figures)]

> 📸 **Screenshot:** [Writing mode > Cite > insert options (inline/block, linked/unlinked, plain/rich)]

![Writing mode cite tab with search results and cite button](./assets/writing-cite.png)

**In practice:** while writing your analysis, you search for the coded passages that support the argument you are making and insert them as properly attributed quotes — without copy-pasting and without losing track of which interview each one came from.

---

### Transcribing Mode

**What it is for:** producing the transcripts you will later code — playing back interview audio and typing it into Word with speaker labels and timestamps, helped along by keyboard shortcuts, voice enrollment, and automatic speaker detection.

> **A note of caution:** Transcribing mode is still experimental and under active development. The other modes are fully usable; here you should expect rough edges.

The work runs across three tabs: you **Import** the audio, **Transcribe** it turn by turn, and optionally **Diarize** it to detect who spoke when across the whole recording. The lines you insert land in the Word document as one speaker turn per paragraph — which, not coincidentally, is exactly the shape that [Mining](#mining-mode) expects.

> Like Coding, Transcribing is available only for **Analysis documents**.

#### The **Import** Tab — Load Audio Files

**What it does:** adds and previews an audio file for transcription.

1. Click the **Import** tab.
2. Choose a file or drag and drop it in.
3. Supported formats include MP3, WAV, OGG, M4A, FLAC, and other Web Audio formats.
4. The file's metadata (type, size, duration) is shown so you can confirm you have the right file.
5. Move to the **Transcribe** tab to begin.

> Transcription and audio features need system-level file storage to work. On macOS this means Ventura 13 or later. If your system cannot store audio, YaqatW will warn you rather than fail silently.

![Transcribing import tab](./assets/transcribing-import.png)

#### The **Transcribe** Tab — Playback, Transcription & Speaker Enrollment

**What it does:** lets you transcribe audio with customizable keyboard shortcuts, a waveform display, speaker management, and optional AI transcription of segments you mark.

**Playback controls:** Play/Pause · Stop · Seek Back (−5s) · Seek Forward (+5s) · Speed control (0.5×–2.0×). You can toggle **real waveform peaks** in Settings to visualize the actual audio (it is cached so performance stays reasonable).

**Managing speakers:**

1. Type a name in the "New speaker name" field and click **Add**.
2. Switch the active speaker from the dropdown, or with the **Switch Speaker** shortcut.
3. Every transcribed line is tagged with the active speaker and a timestamp.

**Marking a segment and transcribing it with AI:** Mark a **start** and an **end** on the timeline, then either **Transcribe** that segment with your configured transcription provider, or **Enroll Speaker** to teach YaqatW that speaker's voice from the segment. Enrollment is what makes automatic speaker identification and diarization possible later.

> 📸 **Screenshot:** [Transcribing mode > Transcribe > marked segment with Mark Start/End, Transcribe + Enroll Speaker buttons]

![Transcribing tab with speaker management](./assets/transcribing-speakers.png)

**Keyboard shortcuts (all customizable):** shortcuts use `Ctrl+Alt+Key`.

| Action | Default Key |
|--------|-------------|
| Play/Pause | R |
| Stop | X |
| Seek Back / Forward | ← / → |
| Slow Down / Normal / Speed Up | [ / \\ / ] |
| Insert Timestamp | Enter |
| Switch Speaker | T |
| Mark Start / Mark End | (set your own) |

To rebind a shortcut, click its cell in the table and press `Ctrl+Alt` plus your chosen key (green means saved, red means invalid, and × clears it).

**The transcription workflow, step by step:**

1. Play and listen; pause, or type live as you go.
2. Insert timestamps where you want them.
3. Type your transcription and click **Insert** to add the line to Word with its speaker label and timestamp.
4. Switch speakers and carry on.

**A tip:** Use **Enter** to insert (it does the same thing as the Insert button) and **Shift+Enter** for a line break within a note. Keeping one speaker turn per paragraph helps the Mining parser detect turns correctly later — it is the same convention described back in [Mining Mode](#mining-mode).

![Transcribing insertion with speaker label and timestamp](./assets/transcribing-insertion.png)

#### The **Diarize** Tab — Automatic Speaker Diarization

**What it does:** automatically works out *who spoke when* across the whole recording, and lays it out as an editable timeline. "Diarization" is just the technical word for that who-spoke-when segmentation.

**How to use it:**

1. First, enroll at least one speaker on the **Transcribe** tab — diarization needs a voice to recognize.
2. On the **Diarize** tab, click **Analyze**. YaqatW decodes the audio, extracts voice features, clusters the unknown voices, and merges the result into a timeline.
3. Edit the timeline directly: select a segment to **split** it at the playhead, **merge** it with the next one, **delete** it, **assign** it to a speaker, or **rename** speakers.
4. Zoom in and out, undo and redo, and **export** the diarization as JSON.

> 📸 **Screenshot:** [Transcribing mode > Diarize > timeline with colored speaker segments]

> 📸 **Screenshot:** [Transcribing mode > Diarize > selected segment editor (split / merge / assign / rename)]

**Engines and the remote option:** You choose a speaker-identification engine in Settings — **DIY MFCC** (offline and free) or **Picovoice Eagle** (more accurate, and needing a free Picovoice AccessKey). For heavier recordings, a **Remote** analyze option can hand the diarization off to a companion app; you set its URL and API key in Settings.

---

### Settings (All Modes)

#### The **Settings** Tab — Configuration, Metadata & Cloud Sync

**What it does:** this is where you manage everything that is not a mode in itself — project setup, encryption, cloud connections, AI and translation providers, document metadata, transcription, and appearance. It is present in every mode. Here is each section:

1. **Document Type** — Analysis document (all modes) or Writing document (Writing / Analyzing / Mining / Documenting). Switching to Writing requires zero highlights. See [Document Types](#document-types).
2. **Operating Mode (yaqatw-mode)** — Coding, Mining, Analyzing, Documenting, Writing, or Transcribing. Your data persists across modes.
3. **Project** — the **Project Name**, shared across all files in the project.
4. **Current File** — the **File ID** for this document, plus **Re-index current document** to refresh the Mining and Analysis index.
5. **Encryption** (appears once a Project Name is set)
   - **Data Password** + **Confirm** — encrypts sensitive data.
   - **Encrypt cloud data** — turns on encryption when syncing.
   - **Remember password on this device** — skips re-entry each session. Do **not** enable this on a shared machine; use **Logout** to clear it.
   - ⚠️ Losing your password makes encrypted data **permanently unrecoverable**, and disabling encryption does **not** decrypt data that was already encrypted.
6. **User** — your **User Name**, used to track who made each edit.
7. **General** — **Data language**, **Writing language**, and **UI language**.
8. **Coding Data** — **Reload coding data** (pull the latest codes, categories, and relationships from all project files into this document) and **Clear coding data** (wipe and cleanly re-import, which fixes duplicates). There is also the option to **reveal hidden layers** when you select a highlight that lives in one.
9. **Cloud Server** — choose a provider (see [Cloud Sync](#cloud-sync)), set the **Sync interval** (0 disables auto-sync), **Sync now**, and **Prepare for offline use** (this caches the app shell, Office.js, the Japanese dictionary, and the FFmpeg audio converter, so they load even without internet).
10. **API Settings** — translation and AI provider keys and models (see [AI & Translation](#ai--translation)).
11. **Transcription** — speaker-identification **engine** (DIY MFCC / Picovoice Eagle), **Companion Diarizer** URL and key, default **playback speed**, **timestamp format**, and **real waveform peaks**.
12. **Appearance & Insertion** — quote styles, the participant label, and how inserted **images/figures** and **tables** are captioned, positioned, and aligned in Writing mode.

![Settings tab](./assets/settings-tab.png)

---

**Metadata, and a word about privacy**

Metadata is structured information *about* the document — most often details about the participant — that you can attach to your exports. There are two ways to manage it, and I will describe both.

**The quick way — a table in the document:**

1. At the **very beginning of the document**, insert a **two-column table**. Make the first row a header: the first cell reads **Metadata**, the second reads **Value**.
2. Add one row per entry — for example, `Participant | P-001`, `Region | Region A`.
3. Go to **Settings → Edit Metadata** and click **Refresh**. YaqatW reads the table and saves every row into the metadata database.
4. Whenever you add or change rows, click **Refresh** again. It refreshes automatically when the add-in opens, but a manual refresh is the way to be sure.

**The dialog way — direct editing and encryption:** In the same **Edit Metadata** dialog you can add or edit fields by hand, and you can click the **lock icon** to encrypt a sensitive field (this needs your data password). Locked fields are only readable when you supply the correct password.

Now the privacy part, which I would ask you to take seriously:

**✅ Safe to store in metadata:**

- The analysis phase or round (e.g. "Coding Round 1")
- General time periods (e.g. "Spring 2024") rather than exact dates
- Geographic regions (e.g. "Region A") rather than specific locations
- Non-identifying notes
- Placeholder codes only (e.g. "P-001")

**❌ Do NOT store in YaqatW, even encrypted:**

- Real participant names or contact information
- Real interview dates or specific locations
- Real ID numbers, email addresses, or other direct identifiers

**Keep the mapping separate.** The key that links a placeholder code (P-001) to a real identity should live in a completely separate, secure file, outside of YaqatW entirely.

![Metadata editor with field encryption locks](./assets/metadata-editor.png)

---

## Workflow Guide

![YaqatW main interface](./assets/workflow-main-interface.png)

The modes are designed to be used on their own, but they also fit together into a full workflow. The sequence below is roughly how I work through a project myself; treat it as a suggestion rather than a rule, and reorder it to suit your own style.

**Phase 1: Set up the document**

1. Create or open a Word document and open YaqatW.
2. Complete Settings (project name, password, file ID, user name).
3. Confirm the Document Type is **Analysis**.
4. Connect cloud sync (optional, but recommended).

**Phase 2: Get to know the data (Mining)**

1. Use **Search** to locate the key terms from your research questions.
2. Use **Frequency** and **Stats** to see the dominant topics and the speaker patterns.
3. Use **Co-occurrence** to spot which concepts cluster together.

**Phase 3: Code**

1. In **Coding**, read through and create codes as you go.
2. Select text and apply codes; adjust colors for clarity.
3. Optionally use the **AI Code Agent** for suggestions, then accept or edit them.

**Phase 4: Organize**

1. Group related codes into **Categories**.
2. Document **Relationships** (cause–effect, temporal, and so on).
3. Merge or delete redundant codes — and recover from **Trash** if you change your mind.

**Phase 5: Analyze**

1. In **Analyzing**, drag codes, categories, and metadata into the analysis zones.
2. Run comparisons and review the results (and the AI interpretation, if configured).

**Phase 6: Document and sync**

1. Add **Metadata** using placeholders and general descriptors.
2. Capture **Artifacts** and **Notes** in Documenting mode.
3. Click **Sync Now** to back up to your cloud provider.

**Phase 7: Write and export**

1. In a separate **Writing document**, use **Cite** to insert quotes, figures, and tables.
2. Export data to Excel / CSV / JSON for any further analysis you want to do elsewhere.

---

## Cloud Sync

### Why sync at all?

- **Backup.** It protects your work against an accidental deletion or a dead computer.
- **Multiple devices.** You can reach your project from a laptop, a tablet, or another machine.
- **Collaboration.** (Experimental.) You can share a project with the rest of a research team.
- **On your terms.** Click "Sync Now" whenever you like, or set an interval and let it happen automatically.

### Supported providers

- **Google Drive™**, **Dropbox**, **OneDrive** (Microsoft 365), and **Nextcloud** (self-hosted) all connect through a secure sign-in (OAuth) — you log in once and authorize the add-in.
- **Amazon S3** and **S3-compatible** storage connect with an endpoint, region, bucket, and access keys. After saving those, use **Test connection** to confirm they work.

### How to sync

**The first time:**

1. Go to **Settings → Cloud Server** and select a **Back end**.
2. For the OAuth providers, click **Connect** and sign in or authorize in the dialog that opens. For S3, fill in the endpoint, region, bucket, and keys, then **Test connection**.
3. Click **Sync Now**. A `YaqatW-DATA` folder is created in your account and your data is uploaded into it.

**Every time after that:** just click **Sync Now**. You will not be asked to sign in again until the token expires.

### What gets synced?

- ✅ Codes, categories, relationships
- ✅ Highlights and metadata
- ✅ Notes and artifacts (artifact files are stored in the cloud folder)
- ✅ Per-file settings
- ⚠️ Encrypted fields, but only if encryption is enabled

### When syncs collide

If you edit the same project on two devices before syncing, the **most recent edit wins**, decided by modification timestamp. To stay out of trouble, get into the habit of syncing both before and after you work — and if a particular change is critical, keep a separate backup of the document too.

### Working offline

- Without cloud sync, your work lives only on this one computer. There is no cloud backup and no access from another device, so if the document is deleted or the machine fails, the work is gone unless you have backed up the file yourself.
- Use **Settings → Prepare for offline use** to cache the app so it loads without an internet connection. (AI, translation, and sync still need a connection — only the app itself works offline.)
- **My recommendation:** use cloud sync. If you genuinely prefer to stay offline, then back up your document regularly to external storage.

---

## Encryption & Security

### Start by not storing the sensitive thing at all

I want to lead with this because it is the most important point, and encryption is no substitute for it: **the safest sensitive data is the data you never put into YaqatW.**

- **Use placeholder codes** for participants (e.g. "P-001").
- **Keep the participant mapping in a separate, secure file** outside YaqatW.
- **Minimize context data** — use general descriptors like "Interview Round 2" or "Region A" instead of specifics.
- Only include the metadata that is genuinely necessary.

And here is a point that catches people out, so I want to be very clear: **when encryption is enabled, only the data sent to the cloud is encrypted. The data stored on your own computer remains unencrypted.** So you must protect the machine itself:

- ✅ Use a strong account password and lock your computer when you step away.
- ✅ Store documents in your protected user folder.
- ✅ Enable full-disk encryption (BitLocker on Windows, FileVault on macOS).
- ❌ Never leave the computer unlocked or share a user account.

### When should you encrypt?

Turn encryption on if your data contains sensitive research content (coded quotes, health or financial information) or if you must comply with GDPR, HIPAA, or an institutional policy. But **do not reach for encryption as a way to justify storing identifiers** — de-identify first, then encrypt what remains.

### How to turn it on

1. Go to **Settings → Data Password**, enter a strong password (8+ characters) and confirm it.
2. Check **Encrypt cloud data**.
3. Save.

### What gets encrypted

When you sync with encryption enabled, the *content* is encrypted — text excerpts, translations, comments, and notes. The *structure* stays readable: code names and category structure remain visible. In other words, someone with access to your cloud folder could see that you have a code called "Leadership," but not read the quotes you attached to it.

### ⚠️ Three warnings worth repeating

1. **Lost password means lost data.** A forgotten password makes encrypted data **permanently unrecoverable**. Store it in a password manager, and keep a printed backup somewhere safe.
2. **Encryption cannot be undone after the fact.** Disabling encryption later does **not** decrypt the data you already encrypted — it will simply appear as unreadable gibberish.
3. **Shared projects need a shared password.** Every collaborator must use the same password, and you should communicate it through a secure channel — never over email or chat.

### Good habits

- ✅ Use a strong password such as `Res!rch2024Strong`.
- ✅ Keep it in a password manager (1Password, Bitwarden, LastPass).
- ❌ Do not use a simple password, and do not write it on a sticky note.

---

## Export & Analysis

### Formats

YaqatW exports from the Mining footers and the coding tabs in several formats: **Excel (XLSX)**, **CSV**, **JSON**, **HTML**, and **Word (DOCX)**. Word clouds and co-occurrence maps export as **PNG / SVG** images. Many tabs offer both **Export** (the current view) and **Export All**.

> **A tip on HTML vs. Word:** export **as HTML** when you just want to preview the result and copy it somewhere else, and export **as Word** when you want to keep the file itself.

> **macOS note (please read if you are on a Mac):** unlike Windows and the web, which download exports straight to your machine, macOS cannot trigger a file download from inside a Word add-in. So on macOS, YaqatW uploads each export to your connected cloud provider under `<project>/export/` and opens it in a browser window, where you can **Save As**. This means that on a Mac, **a cloud provider must be connected** (Settings → Cloud) and **a project name must be set** before export will work — otherwise it fails and prompts you to connect one.

### Exporting the code book

The **code book** is your list of codes and their definitions:

1. Go to the **Codes** tab → **Export** (at the bottom) → **Save Code Book** → **Options**.
2. In the options dialog, tick what to include — for example **Code**, **Description**, and **Color** — then **Close**.
3. **Export → Save Code Book → Save as HTML** (to preview and copy) or **Save as Word** (to keep).

### Exporting categories and relationships

Exporting categories or relationships works the same way, but with richer options. Beyond the structure itself, you can include, for each coded item: the **selected text**, its **translation**, the **code applied**, the **category** (or relationship), and any of your saved **metadata** fields. Open **Options** to choose exactly which of these columns appear.

### Exporting to Excel

1. From a coding tab or from Settings, open **Export Options**.
2. Choose which sheets to include — Data (highlights with codes), Codes, Categories, Relationships, Metadata.
3. Choose which columns to include. You can deliberately leave out sensitive columns (Date, Participant ID) to reduce the risk of re-identification.
4. Download the workbook.

![Export configuration dialog](./assets/export-configuration.png)

### Going further

Once your data is in Excel you can build pivot tables for code frequencies, cross-tabulate codes against participants or dates, generate charts, compute co-occurrence, and export onward to R, SPSS, or Python for heavier analysis. (You can also do much of this without leaving the add-in, in [Analyzing Mode](#analyzing-mode).)

---

## AI & Translation

YaqatW can connect to optional AI and translation providers. They are entirely optional — everything else works without them — and **all keys are stored locally on your machine.** Please read the security note before you configure anything.

⚠️ **SECURITY NOTE:** API keys are stored locally, in IndexedDB inside the YaqatW add-in on your computer. They are never sent to YaqatW servers. But that also means they are accessible to anyone who can open the Word document or the add-in on your machine. Only configure providers if your computer is personally owned, password-protected, locked when unattended, and disk-encrypted (BitLocker / FileVault).

### Translation

To translate a highlighted quote in another language: select the highlight and click **Translate** (this appears once a provider is configured), then optionally save the translation back onto the highlight.

**Supported translation providers:**

- **DeepL** (recommended — the highest quality) — https://www.deepl.com/pro#developer (the free tier covers around 500K characters a month). Paste the key into **Settings → DeepL API Key**.
- **Google Translate™** — create a key at https://console.cloud.google.com/ (enable the Cloud Translation API), then paste it into **Settings → Google API Key**.

![Translation feature](./assets/translation-feature.png)

### AI providers (for the Code Agent and Analysis interpretation)

Configure any of these under **Settings → API Settings**. Each has an API key, a model selector, and an optional max-tokens field:

| Provider | Where to get a key |
|---|---|
| **OpenAI** | https://platform.openai.com/api-keys |
| **Claude (Anthropic)** | https://console.anthropic.com/ |
| **Groq** | https://console.groq.com/keys |
| **Gemini (Google)** | https://aistudio.google.com/app/apikey |
| **DeepSeek** | https://platform.deepseek.com/api |

There is also a **Custom AI Settings** option that lets advanced users point at a custom provider or endpoint. AI is used for the **Code Agent** suggestions (Coding mode), the **Analysis** interpretation (Analyzing mode), and optional **segment transcription**. Costs are pay-per-use and are tracked in each provider's own dashboard, not by YaqatW.

> All AI, translation, and cloud features need an internet connection. When you are offline, YaqatW shows a banner and these particular features are unavailable.

---

## Troubleshooting

### Common issues and what to do

| Problem | Likely cause | What to do |
|---------|-------|----------|
| "Settings not initialized" | A required setup field is missing | Complete Project, Password, File ID, and User, then Save |
| Highlights not appearing | No text was selected, or a transient error | Re-select the text and apply again; refresh the document |
| "Limited storage mode" banner | IndexedDB is unavailable | Coding data still saves, but attachments and large files cannot — restart Word, or update Office / your browser |
| "Audio features unavailable" banner | The OS lacks the required file storage (macOS < 13) | Update your OS to enable audio import, transcription, and diarization |
| Cloud sync fails | An OAuth token expired, or S3 credentials are wrong | Reconnect the provider in Settings; for S3, use **Test connection** |
| "Password incorrect" | The wrong password | Check CAPS LOCK and confirm it matches the original |
| Diarization will not run | No enrolled speakers | Enroll at least one speaker on the Transcribe tab first |
| Encryption shows gibberish | The data was encrypted with a different password | Use the original password; if it is lost, the data is unrecoverable |

### Getting help

- **Report an issue:** https://github.com/yaqalab/yaqatw-support/issues — please include the error message (from the F12 console), the steps to reproduce it, your Word or browser version, and your cloud provider if it is relevant.
- **Documentation and feature requests:** https://github.com/yaqalab/yaqatw-support

---

## FAQ

**Q: Is my data private?**
A: Yes. Your coding data lives in three places, all of which are yours: your Word document, a local IndexedDB scoped to the add-in on your computer, and your own cloud account. YaqatW never sends your data to our servers — all processing happens locally through Office.js. **YaqatW does not collect usage data, personal information, or research content.** If you enable encryption, sensitive content is protected before it is sent to the cloud and cannot be read without your password — so keep that password safe, because encrypted data cannot be recovered if it is lost. **Encryption applies only to cloud sync; local data is unencrypted,** so protect your machine with a strong password and disk encryption. For the full details, see our [Privacy Policy](https://yaqatw.alefa.net/public/privacy.html).

**Q: Can I recover a deleted code?**
A: Yes. Deleting a code removes only the definition, not its highlights, which stay in the document. The **Trash** tab shows recently deleted items so you can restore them. You can also permanently delete an item from there, and after that there is no recovery.

**Q: What is the difference between an Analysis document and a Writing document?**
A: An **Analysis document** holds your source data and supports every mode, including Coding and Transcribing. A **Writing document** is your manuscript and exposes only Writing, Analyzing, Mining, and Documenting. You can switch a document to Writing type only if it has no highlights. Keep both under the same project name so they share codes and data.

**Q: Can I share a project with my research team?**
A: Yes. One member creates the project, syncs, and shares the `YaqatW-DATA` cloud folder. The others configure YaqatW with the **same project name**, connect to the shared folder, and click **Sync Now** to pull in the existing codes and data. Each person works on separate documents (different File IDs) while sharing the same codes, categories, and relationships. **Never edit the same file at the same time** — always sync before and after working, and remember the last sync wins. Each researcher uses their own cloud credentials.

**Q: What if I lose my password?**
A: If encryption is enabled, the encrypted data is **unrecoverable** without the password. Store the password securely — in a password manager, with a backup.

**Q: Can I use YaqatW in Excel or PowerPoint?**
A: Not yet — YaqatW is Word-only for now. We are exploring deeper integration with other Office apps (for example, reading coding data in Excel) for the future.

**Q: How big can my document be?**
A: For the best performance, keep each document under about 50 MB. Very large documents (100+ MB) can slow Word and the add-in down, because highlights, codes, and annotations are processed in real time. For large projects, split the work across several documents — ideally one per interview or source.

**Q: Does YaqatW work offline?**
A: Yes — all your work is local until you sync. Use **Prepare for offline use** to cache the app itself. AI, translation, and cloud sync still need internet. The trade-off is that offline means no automatic backup, so back up your document regularly if you stay offline.

**Q: Can I export my data to other formats?**
A: Yes — **Excel (XLSX)**, **CSV**, **JSON**, **HTML**, and **Word (DOCX)**, plus **PNG / SVG** for word clouds and co-occurrence maps. Each data type (codes, categories, relationships, highlights) can be exported separately.

**Q: What is the catch — how do you make money from my data?**
A: We don't, and that is the point. There is no YaqatW account, no YaqatW server holding your research, and no usage or personal data collected — see [Privacy by design](#privacy-by-design). The model is bring-your-own: your own cloud account for sync, your own API keys for any AI or translation, and your own password for encryption. Because there is no backend to run on your behalf, there is also nothing to subscribe to — YaqatW is free to use, with no account and no hidden costs. The only money that ever changes hands is what you pay your AI or translation provider directly, if you choose to use one, and that is billed by them, not by us.

**Q: Is there a mobile app?**
A: No. Office Add-ins are not supported in the Word mobile apps for iOS® or Android™, owing to Microsoft platform limitations. Use YaqatW on Word for Windows, macOS, or the web. On a tablet, use the full desktop or web version of Word.

**Q: Will YaqatW be open source?**
A: The source is proprietary for now, while we develop it, but we are committed to releasing it as open source once the project reaches broader adoption.

---

## Contributors

**Main contributors:** [frianasoa](https://github.com/frianasoa)

---

## Thank You

Thank you for using YaqatW. Your feedback genuinely matters to a project this size — please share your thoughts, problems, and feature requests on [GitHub Issues](https://github.com/yaqalab/yaqatw-support/issues).

Happy coding. 🎓
