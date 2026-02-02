# YaqatW User Guide

**Yet Another Qualitative Analysis Tool for Word**

Welcome to YaqatW! This guide will help you get started with qualitative coding, annotation, and thematic analysis in Microsoft Word.

## Table of Contents

1. [What is YaqatW?](#what-is-yaqatw)
2. [Installation](#installation)
3. [Getting Started](#getting-started)
4. [Key Features](#key-features)
5. [Workflow Guide](#workflow-guide)
6. [Cloud Sync](#cloud-sync)
7. [Encryption & Security](#encryption--security)
8. [Export & Analysis](#export--analysis)
9. [AI & Translation](#ai--translation)
10. [Troubleshooting](#troubleshooting)
11. [FAQ](#faq)

---

## What is YaqatW?

YaqatW is a Microsoft Word add-in designed for researchers, students, and analysts who conduct qualitative analysis. It enables you to:

- **Code** text excerpts with custom codes and colors
- **Organize** codes into categories and hierarchies
- **Document** relationships between codes and concepts
- **Annotate** documents with metadata and field notes
- **Sync** your work across devices via cloud storage
- **Export** your analysis to Excel for further investigation
- **Secure** sensitive data with encryption

---

## Installation

### For Beta Testers

**Step 1: Download the Manifest File**
- Request the `manifest.xml` file from the YaqaLab team

**Step 2: Trust the Add-in in Word**

**Windows:**
1. Open Microsoft Word
2. Create a new blank document
3. Go to **File → Options → Trust Center → Trust Center Settings → Trusted Add-in Catalogs**
4. Select **Shared Folder Catalog** from the dropdown
5. Click **Browse** and navigate to the folder containing `manifest.xml`
6. Click **OK**
7. Close and reopen Word

**Mac:**
1. Open Microsoft Word
2. Go to **Word → Preferences → Security → Trusted Add-ins**
3. Click the folder icon and select the folder containing `manifest.xml`
4. Click **OK**

**Step 3: Load the Add-in**
1. Open or create a Word document
2. Go to **Insert → Get Add-ins → My Add-ins → Shared Folder**
3. Click **YaqatW** to load the add-in

### Future: Microsoft AppSource

Once YaqatW is published to the Microsoft Office Store, installation will be one-click:
1. Go to **Insert → Get Add-ins**
2. Search for "YaqatW"
3. Click **Get**

---

## Getting Started

### Initial Setup (First Time Only)

When you open YaqatW for the first time, you'll see the Settings tab with required configuration:

1. **Project Name**
   - Enter a name for your research project (e.g., "interview-study-2024")
   - Can contain letters (lowercase), numbers, and hyphens
   - **Note:** Project name is shared across all files in the same project

2. **Data Password**
   - Create a strong password (8+ characters, mix of letters/numbers)
   - **Important:** Write this down securely. If lost, encrypted data cannot be recovered
   - Confirm the password in the next field

3. **Current File (File ID)**
   - Give this specific document a unique identifier (e.g., "interview-001")
   - Allows you to work on multiple documents within the same project
   - Each document gets its own codes and highlights, which will be shared with other documents.

4. **User Name**
   - Enter your name (lowercase, no spaces)
   - Tracks who made each edit (future feature)

5. **Cloud Sync** (Optional but Recommended)
   - Choose a cloud provider: Google Drive, Dropbox, OneDrive, or Nextcloud
   - Click "Connect" and follow the OAuth login prompts
   - YaqatW will create a `YaqatW-DATA` folder in your cloud account
   - This folder stores your coding data for backup and multi-device sync

**Once these fields are filled, all feature tabs will become available.**

---

## Key Features

### 1. **Coding** Tab - Mark Up Your Text

**What it does:** Create custom codes (concepts/tags) and apply them to text selections in your document.

**How to use:**

**Create a Code:**
1. Click the **Coding** tab
2. Click **New Code** (+ button)
3. Enter:
   - **Code Name** (e.g., "Leadership")
   - **Description** (e.g., "Instances where leaders emerge")
   - **Color** (pick from palette for visual distinction)
4. Click **Create**

**Apply a Code to Text:**
1. Select a text excerpt in your Word document (the text you want to annotate)
2. Right-click on the code in the list (or click the code name)
3. Click **Apply Code** (or icon button)
4. The selected text is now highlighted with the code's color and labeled with the code name
5. The highlight appears as a box around the text in Word

**View Your Codes:**
- **Code List** shows all codes with color indicators
- **Count** column shows how many times each code is used
- **Search** box filters codes by name

**Edit or Delete:**
- Right-click a code → **Edit** to change name/description/color
- Right-click a code → **Delete** to remove (does not delete highlights, just the code definition)

---

### 2. **Categories** Tab - Organize Codes

**What it does:** Group related codes into categories and sub-categories, creating a hierarchy of concepts.

**How to use:**

**Create a Category:**
1. Click the **Categories** tab
2. Click **New Category** (+ button)
3. Enter:
   - **Category Name** (e.g., "Leadership Behaviors")
   - **Description** (optional)
4. Click **Create**

**Add Codes to a Category:**
1. Right-click the category or click the expand arrow
2. Click **Add Codes to Category**
3. Select codes from the list (checkboxes)
4. Click **Add Selected**

**Organize Hierarchically:**
- Drag and drop codes within the tree to create sub-hierarchies
- Expand/collapse categories by clicking the arrow icon

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

**Use Case:** After coding a document with 20+ codes, group related codes by theme (Behaviors, Attitudes, Outcomes, etc.) to simplify analysis and reporting.

---

### 3. **Relationships** Tab - Document Connections Between Concepts

**What it does:** Create and document relationships between codes/categories to keep track of how concepts connect (cause-effect, temporal, hierarchical, etc.). This helps you organize your thinking and preserve connections you identify in your data.

**How to use:**

**Create a Relationship:**
1. Click the **Relationships** tab
2. Click **New Relationship** (+ button)
3. Enter a **Relationship Type** (name the relationship)
4. Click **Create** (one "Instance" is auto-created)

**Relationship Type Examples:**
- **Cause → Effect** (X causes Y)
- **Then → Now** (temporal progression)
- **Example → General** (specific instances of a concept)
- **Part Of** (hierarchical composition)
- **Precedes** (sequential order)
- **Contradicts** (conflicting ideas)

**Add Codes/Categories to a Relationship:**
1. Click the relationship to expand it
2. Right-click an Instance (numbered box)
3. Click **Add Code/Category** to add categories (or codes) to each side
4. Relationships work best with categories, but individual codes can be added too

**Create Multiple Instances:**
- Click **Add Instance** to create another pairing
- Useful for multiple examples of the same relationship type

**Example:**
```
Relationship: Cause → Effect
├── Instance 1
│   ├── Organizational Stress (Category1)
│   └── High Turnover (Category2)
├── Instance 2
│   ├── Leadership Issues (Category1)
│   └── Team Morale (Category2)
└── Instance 3
    ├── Goal Clarity (Code1)
    └── Performance (Category2)
```

**Use Case:** As you read and code, you'll notice connections between concepts. Use this tab to document those relationships (e.g., "Job Stress → High Turnover") so you have a record of patterns you've identified.

---

### 4. **Metadata** Tab - Document Details

**What it does:** Add structured notes and attributes to your document (interview date, participant ID, location, notes, etc.).

**How to use:**

1. Click the **Settings** tab
2. Scroll to **Metadata** section
3. Click **Edit Metadata** or the pencil icon
4. Add fields and values:
   - **Field Name:** (e.g., "Interview Date", "Participant ID", "Location")
   - **Value:** (e.g., "2024-01-15", "P-001", "Remote")
5. Click the lock icon to lock sensitive metadata (encrypted)
6. Click **Save**

**Locked (Encrypted) Metadata:**
- Sensitive info (names, IDs, locations) can be encrypted
- Only visible if you know the data password (set in initial settings)
- Encrypted when synced to cloud

**Use Case:** Track interview metadata (date, location, duration), participant codes, or research phase without cluttering your document.

---

### 5. **Settings** Tab - Configuration & Cloud Sync

**What it does:** Manage user settings, cloud account connections, AI integrations, and encryption.

**Main Settings:**

1. **Project Name** - Change the project you're working on
2. **Data Password** - Encrypt sensitive data in the cloud
3. **User Name** - Your researcher identity
4. **File ID** - This document's unique identifier
5. **Data Language** - Language of your codes/data (default: Malagasy)
6. **Writing Language** - Language for UI text (default: English)

**Cloud Sync:**

1. Choose a provider:
   - **Google Drive** (most common)
   - **Dropbox**
   - **OneDrive** (Microsoft 365)
   - **Nextcloud** (self-hosted)

2. Click **Connect** → authenticate with your cloud account
3. Click **Sync Now** to upload/download your coding data
4. YaqatW creates a `YaqatW-DATA` folder automatically

**Encryption:**
- If you enter a data password, enable **Encrypt Cloud Data**
- Sensitive fields (text excerpts, translations, comments) are encrypted
- ⚠️ **WARNING:** If you lose your password, encrypted data is **unrecoverable**
- ⚠️ **CAUTION:** Disabling encryption cannot decrypt previously encrypted data; the data will appear as gibberish

**AI Integration (Optional):**

For advanced features, configure AI provider API keys:

**OpenAI (GPT-3.5, GPT-4):**
1. Visit https://platform.openai.com/api-keys
2. Create an API key
3. Paste in Settings → "OpenAI API Key"
4. Select a model (e.g., "gpt-3.5-turbo")
5. **Cost:** Pay-per-use; track spending in OpenAI dashboard

**DeepL Translation:**
1. Visit https://www.deepl.com/pro#developer
2. Sign up for a free account (500K characters/month) or Pro ($4.99/month)
3. Copy your API key
4. Paste in Settings → "DeepL API Key"
5. Translations are now available for highlighted text

**Google Translate:**
- Free but rate-limited
- No API key required for basic use
- If you have your own API key, paste it in Settings

**DeepSeek:**
1. Visit https://platform.deepseek.com/api
2. Create an API key
3. Paste in Settings → "DeepSeek API Key"
4. Select model: "DeepSeek Chat" or "DeepSeek Reasoner"

---

## Workflow Guide

### Typical Analysis Workflow

**Phase 1: Document Setup (5 min)**
1. Create a new Word document and open it
2. Open YaqatW add-in
3. Complete Settings (project name, password, file ID, user name)
4. Connect to cloud sync (optional but recommended)

**Phase 2: Initial Coding (30-60 min)**
1. Read through your document
2. Identify key themes, concepts, or ideas
3. Create codes as you go (Coding tab → New Code)
4. Select text and apply codes (right-click code → Apply)
5. Adjust colors for visual clarity

**Phase 3: Organization (10-15 min)**
1. Review all codes (Coding tab)
2. Group related codes into Categories
3. Delete or merge redundant codes
4. Build a category hierarchy

**Phase 4: Document Relationships (10-15 min)**
1. Review your codes and identify patterns or connections
2. Create Relationships (cause-effect, temporal, etc.) to document what you notice
3. Link codes/categories to show how they connect
4. Note any recurring patterns or outliers

**Phase 5: Metadata & Documentation (5-10 min)**
1. Add Metadata about the document (date, participant, location, etc.)
2. Lock sensitive fields if needed
3. Add notes or context

**Phase 6: Cloud Sync & Backup (2 min)**
1. Click Settings → Sync Now
2. Verify data uploaded to cloud provider
3. Cross-project sync now available on other devices

**Phase 7: Export & Further Analysis (10 min)**
1. Go to Settings → Export
2. Export to Excel for pivot tables, statistical analysis, or visualizations
3. Use Excel to generate frequency counts, cross-tabs, or charts

---

## Cloud Sync

### Why Sync Your Data?

- **Backup:** Protect your work against accidental deletion or computer failure
- **Multi-device:** Access your project on laptop, tablet, or different computer
- **Collaboration:** (Future) Share projects with research team members
- **Manual:** Click "Sync Now" anytime to upload/download your coding data

### How to Sync

1. Go to **Settings** tab
2. Under "Cloud Provider," select your provider (Google Drive, Dropbox, OneDrive, Nextcloud)
3. Click **Connect** and authenticate
4. Click **Sync Now**
5. A `YaqatW-DATA` folder is created in your cloud account
6. All coding data is uploaded as JSON files

### What Gets Synced?

- ✅ Codes, categories, relationships (always)
- ✅ Highlights and metadata (always)
- ✅ Settings (per-file, not global)
- ⚠️ Encrypted fields only if encryption enabled

### Sync Conflicts

If you edit on two devices before syncing:
- **Latest edit wins** (based on modification timestamp)
- No data loss; older versions overwritten
- If critical, manually backup files before sync

### Offline Work

- Work offline without syncing; all data stored locally
- Next time you sync, changes upload automatically
- **Caution:** If you lose your document without syncing, all work is lost

---

## Encryption & Security

### When to Encrypt?

**Enable encryption if your data contains:**
- Participant names or contact info
- Sensitive personal information (health, financial, etc.)
- Confidential quotes or identifiers
- Any data that must comply with GDPR, HIPAA, or institutional policy

### How Encryption Works

1. Go to **Settings** → **Data Password**
2. Enter a strong password (8+ characters, mix of types)
3. Confirm the password
4. Check **Encrypt Cloud Data**
5. Click **Save**

### What Gets Encrypted?

When synced to cloud with encryption enabled:
- Text excerpts (highlighted passages)
- Translations
- Comments and notes
- **NOT encrypted:** Code names, category structure (readable but content hidden)

### ⚠️ Important Warnings

1. **Password Loss = Data Loss**
   - If you forget your password, encrypted data is **permanently unrecoverable**
   - Write your password down and store securely (password manager, printed backup)

2. **Cannot Disable Encryption**
   - Once encrypted, you **cannot decrypt** by disabling encryption
   - Old encrypted data will appear as unreadable gibberish
   - Plan ahead: encrypt from the start or never encrypt

3. **Sharing Encrypted Projects**
   - If sharing with collaborators, all must use the same password
   - Communicate password securely (NOT via email/chat)
   - Use password manager or secure channel

### Encryption Best Practices

- ✅ Use passwords like: `Res!rch2024Strong`
- ✅ Store password in a password manager (1Password, Bitwarden, LastPass)
- ✅ Keep a printed backup in a locked drawer
- ❌ Don't use simple passwords like "123456" or "password"
- ❌ Don't share password via email or chat
- ❌ Don't write password on a Post-it on your monitor

---

## Export & Analysis

### Export to Excel

1. Go to **Settings** tab
2. Scroll to **Export** section
3. Click **Export to Excel**
4. Choose which sheets to include:
   - ✅ Data (all highlights with codes)
   - ✅ Codes (code inventory)
   - ✅ Categories (category definitions)
   - ✅ Relationships (relational analysis)
   - ✅ Metadata (document info)
5. Choose columns to include:
   - ✅ Text excerpts
   - ✅ Code names
   - ✅ Category
   - ✅ Participant ID
   - ✅ Date
6. Click **Download Excel**

### Excel Features

The exported workbook includes:

**Data Sheet:**
| Highlight | Text | Code | Category | Participant | Date |
|-----------|------|------|----------|-------------|------|
| 1 | "Quote here..." | Leadership | Behaviors | P-001 | 2024-01-15 |

**Code Summary Sheet:**
- Frequency of each code (count)
- Color coding
- Descriptions

**Pivot Tables (Manual):**
- Create pivots in Excel: Data → Pivot Table
- Cross-tabulate: Codes vs. Participants, Codes vs. Dates, etc.
- Generate charts for visualization

### Further Analysis

Once in Excel, you can:
- Create pivot tables for code frequencies
- Generate charts (bar, pie, timeline)
- Calculate co-occurrence (when codes appear together)
- Filter by participant, date, or category
- Export to statistical software (R, SPSS) for advanced analysis

---

## AI & Translation

### Translation (DeepL Recommended)

**For highlighting a quote in a foreign language:**

1. Select the highlighted text
2. Right-click → **Translate** (if API key configured)
3. Choose target language (e.g., English)
4. Translated text appears in a tooltip/sidebar
5. Option to save translation to metadata

**Supported Providers:**
- **DeepL** (recommended; highest quality) - https://www.deepl.com/pro
- **Google Translate** (free but limited) - https://translate.google.com
- **Custom** (your own API) - Configure in Settings

### How to Get DeepL API Key

1. Go to https://www.deepl.com/pro#developer
2. Click "Sign up" for Free or Pro plan
3. Free plan: 500,000 characters/month
4. Copy your API key from the dashboard
5. Paste in YaqatW Settings → "DeepL API Key"

### Future AI Features (Coming Soon)

- **Auto-suggest Codes** - AI reads a highlight and suggests relevant codes
- **Theme Discovery** - ML identifies themes you may have missed
- **Relationship Inference** - AI suggests relationships between codes

**Note:** These features are in beta and will be announced when available.

---

## Troubleshooting

### Common Issues & Solutions

| Problem | Cause | Solution |
|---------|-------|----------|
| "Settings not initialized" error | Missing required fields in initial setup | Complete all 4 required fields (Project, Password, File ID, User) and click Save |
| Highlights not appearing | Text selection issue or script error | Try again, ensuring you've selected text; if persistent, refresh document |
| "IndexedDB quota exceeded" | Document too large with too many highlights | Archive old documents; delete non-essential highlights; ask support |
| Cloud sync fails | OAuth token expired | Go to Settings, click "Connect" for cloud provider again |
| "Password incorrect" | Wrong password entered | Check CAPS LOCK; confirm password matches initial setup |
| Document won't save | Office permission issue | Save manually with Ctrl+S (Windows) or Cmd+S (Mac) |
| Add-in crashes | Memory limit or code error | Close and reopen Word; clear browser cache; restart computer if needed |
| Encryption shows gibberish | Previously encrypted with different password | Confirm you're using the original password; if lost, data unrecoverable |

### Getting Help

- **Report Issues:** Visit https://github.com/yaqalab/yaqatw-support/issues and create a new issue with:
  - Error message (from F12 console)
  - Steps to reproduce
  - Browser/Word version
  - Cloud provider (if applicable)

- **Documentation:** https://github.com/yaqalab/yaqatw-support
- **Feature Requests:** Discuss in [GitHub Issues](https://github.com/yaqalab/yaqatw-support/issues)

---

## FAQ

**Q: Is my data private?**
A: Yes. Your coding data stays in your Word document, in a local IndexedDB scoped to the addin inside your computer, and your chosen cloud account. YaqatW never sends your data to our servers. All processing happens locally in your browser via Office.js. If you enable encryption, sensitive data in your content is protected before being sent to the cloud and cannot be read without your password. However, always remember to keep your password safe, as encrypted data cannot be recovered if the password is lost.

**Q: Can I recover a deleted code?**
A: Deleting a code doesn't delete highlights (only the code definition). Highlights remain in the document but will not show in export. The "Trash" tab shows recently deleted items and you can restore deleted code. You can also "permanently delete". In that case, you will not be able to recover the code.

**Q: Can I share a project with my research team?**
A: Collaboration is possible if each team member works on a separate file within the same project. Do not edit the same file together. Each user should be in charge of one file to avoid conflicts or data loss. Each data insertion is auto-synced to the cloud. Before starting work, use "Sync Now" in Settings to ensure you have the latest data from the cloud. The principal investigator should share the YaqatW-DATA cloud folder with other researchers after initial creation from YaqatW. There is not need to share cloud accounts. Each user has access to all project data (codes, highlights, etc.) and can export as needed.

**Q: What if I lose my password?**
A: If encryption is enabled, **encrypted data is unrecoverable** if you lose your password. There is no way to recover encrypted data without the password. Please store passwords securely (password manager or backup).

**Q: Can I use YaqatW on Excel or PowerPoint?**
A: YaqatW is Word-only for now. We are exploring other Office apps for future releases, but it will be just extension of feature like accessing data directly in excel for analysis, etc. 

**Q: How big can my document be?**
A: The practical size limit depends on your computer's memory and processing power, but we recommend keeping each Word document under 50 MB for best performance. Very large documents (100+ MB) may cause Word and the add-in to slow down or become unstable, since all highlights, codes, and annotations must be processed in real time. For large projects, split your work into multiple documents, ideally, one document per interview or source. This approach keeps everything fast, reliable, and easy to manage.

**Q: Does YaqatW work offline?**
A: Yes, all work is local until you sync. If you do not sync, data stays in your document. Syncing to cloud requires internet connection.

**Q: Can I export my data to other formats?**
A: Word, Excel, HTML, CSV, and JSON export is available. Each type of data is exported separately.

**Q: How much does YaqatW cost?**
A: YaqatW is free to use. While we are evaluating future monetization models to cover costs such as domain name and hosting. All current features remain at no cost. Any future changes will be announced with plenty of notice.

**Q: Is there a mobile app?**
A: No. Office Add-ins (including YaqatW) are not supported on the Word mobile app for iOS or Android, due to Microsoft platform limitations. You can use YaqatW on Word for Windows, Mac, and the web (Office 365 in a browser). On tablets, you must use the full desktop or web version of Word—add-ins do not run in the mobile app. If Microsoft adds support for add-ins on mobile in the future, we will announce it.

---

## Thank You!

Thank you for being a YaqatW beta tester! Your feedback is invaluable. Please share thoughts, issues, and feature requests on [GitHub Issues](https://github.com/yaqalab/yaqatw-support/issues).

Happy coding! 🎓
