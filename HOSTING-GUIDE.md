# Arabic.AI Article Hub: Hosting & Maintenance Guide

---

## Folder Structure

```
arabic-ai-hub/
├── index.html                                      ← Homepage (article index)
├── HOSTING-GUIDE.md                                ← This file
├── assets/
│   └── css/
│       └── style.css                               ← All styles (shared across all pages)
└── articles/
    ├── _TEMPLATE.html                              ← Copy this for every new article
    ├── enterprise-ai-agents-still-fail.html
    ├── breaking-rl-performance-ceiling.html
    ├── how-human-preference-data-should-be-collected.html
    └── hierarchy-of-agentic-capabilities.html
```

---

## How to Add a New Article

### Step 1: Copy the template
Duplicate `articles/_TEMPLATE.html` and rename it.
Use lowercase, hyphens instead of spaces. Example: `articles/my-new-article.html`

### Step 2: Update the HEAD section
Change the `<title>` and `<meta name="description">` at the top.

### Step 3: Fill in the HERO section
Update:
- Breadcrumb category label
- Category tag text
- H1 title
- Subtitle paragraph
- Byline: date, read time, source paper

### Step 4: Write the article body
Inside `<main class="article-body">`, use:
- `<p>` for body paragraphs
- `<h2 id="section-slug">` for section headings (the id is used by the TOC)
- `<h3>` for sub-headings
- `<blockquote><p>...</p><cite>...</cite></blockquote>` for pull quotes
- `<div class="stat-grid">` for 3-up numbers (copy from template)
- `<div class="data-callout">` for a single highlighted stat
- `<hr class="divider">` before the source note
- `<p class="source-note">` for the attribution at the end

### Step 5: Update the sidebar TOC
Match each `<li><a href="#section-slug">` to your `<h2 id="section-slug">` headings.

### Step 6: Update the Related Articles sidebar
Link to 2-3 other articles in the same folder.

### Step 7: Update the Related Articles section at the bottom
Copy the 3-card grid. Replace title, tag, href, and excerpt for each card.

### Step 8: Add the new article to index.html
In `index.html`, add a new card to the `<div class="article-grid">`.
Also add a footer link to the article in the footer `<ul class="site-footer__links">`.

### Step 9: Update the footer links across all existing articles
Open each existing article. In the footer `<ul class="site-footer__links">`, add a link
to the new article. This keeps the footer consistent across all pages.

---

## How to Link Articles to Each Other

All article files are in the `articles/` folder. Link between them like this:

**From index.html to an article:**
```html
<a href="articles/your-article-name.html">...</a>
```

**From one article to another (both in articles/):**
```html
<a href="another-article-name.html">...</a>
```
Note: no `articles/` prefix needed when linking between articles, because
they are in the same folder.

**From an article back to the homepage:**
```html
<a href="../index.html">...</a>
```
Note: the `../` moves up one folder level.

---

## Hosting on GitHub Pages (Recommended for Beginners)

GitHub Pages hosts static HTML/CSS sites for free. Your URL will be:
`https://YOUR-USERNAME.github.io/arabic-ai-hub/`

### Step 1: Create a GitHub account
Go to https://github.com and click "Sign up".
Choose a username, add your email, and set a password.
Verify your email address.

### Step 2: Create a repository
After logging in, click the green "New" button (top left, or go to https://github.com/new).
- Repository name: `arabic-ai-hub`
- Set to: Public (required for free GitHub Pages)
- Leave all other settings as default
- Click "Create repository"

### Step 3: Upload your files
On the repository page, click "uploading an existing file" (or drag files).
Upload the entire contents of this folder:
- index.html
- HOSTING-GUIDE.md
- assets/ folder (and everything inside it)
- articles/ folder (and everything inside it)

GitHub requires you to maintain the folder structure. If uploading via the web interface,
you may need to upload the CSS file first, then the HTML files.

Alternatively, use GitHub Desktop (https://desktop.github.com) which is easier for
non-technical users and lets you drag entire folders.

Click "Commit changes" after uploading.

### Step 4: Enable GitHub Pages
1. On your repository page, click "Settings" (top right area)
2. In the left sidebar, click "Pages"
3. Under "Source", select: Deploy from a branch
4. Under "Branch", select: main
5. Folder: / (root)
6. Click Save

### Step 5: Get your live URL
Wait 1-3 minutes. Refresh the Pages settings page.
You will see: "Your site is live at https://YOUR-USERNAME.github.io/arabic-ai-hub/"
Click that link to see your live site.

### Step 6: Update the site later
To update any file, go to your repository on GitHub.
Navigate to the file, click the pencil icon to edit it, or upload a new version.
Click "Commit changes". The live site updates automatically within 1-2 minutes.

---

## Hosting on Netlify (Easiest Drag-and-Drop Option)

1. Go to https://netlify.com and sign up with your email
2. On the dashboard, find the box that says "Drag and drop your site folder here"
3. Drag your entire `arabic-ai-hub` folder onto it
4. Netlify deploys it instantly and gives you a URL like `https://random-name.netlify.app`
5. To update: drag and drop again, or connect to a GitHub repository for automatic updates

**To get a custom subdomain:**
Go to Site settings > Domain management > Change site name
You can change it to something like `arabic-ai-articles.netlify.app`

---

## Hosting on Vercel

1. Go to https://vercel.com and sign up
2. Click "Add New Project"
3. Import from GitHub (connect your GitHub account first)
4. Select your `arabic-ai-hub` repository
5. Click Deploy. Vercel gives you a URL like `https://arabic-ai-hub.vercel.app`

Updates happen automatically every time you push changes to GitHub.

---

## Which Option Is Easiest?

| Option | Easiest for | Free URL you get |
|--------|-------------|-----------------|
| GitHub Pages | Anyone who can follow steps | github.io/arabic-ai-hub |
| Netlify drag-and-drop | Complete beginners | netlify.app |
| Vercel | Developers with GitHub | vercel.app |

**Recommendation:** Use Netlify drag-and-drop if you want the site live in under 5 minutes
with no accounts to configure. Use GitHub Pages if you want a more permanent home that
is easy to update and widely recognized.

---

## Do You Need to Buy a Domain?

No. All three options give you a free subdomain that works immediately.

If you later want a custom domain like `articles.arabic.ai`:
1. You need to own the domain (arabic.ai already exists, so your IT/web team controls it)
2. In Netlify or Vercel, go to Domain settings and add your custom domain
3. Your DNS provider (whoever manages arabic.ai) will need to add a CNAME record
4. This is a 15-minute task for whoever manages your DNS

---

## How to Move This to the Official Arabic.AI Website

When ready to migrate:
1. The HTML files are self-contained and use standard HTML/CSS
2. Copy the `assets/css/style.css` file to your main site
3. Each article HTML file can be opened as a standalone page, converted to a CMS template,
   or adapted into whatever framework your main site uses (WordPress, Webflow, React, etc.)
4. Internal links will need to be updated to reflect the new URL structure
5. No JavaScript is used, so there are no framework dependencies to manage

---

## Maintenance Checklist for Each New Article

- [ ] Copied _TEMPLATE.html with a new filename
- [ ] Updated `<title>` and `<meta name="description">`
- [ ] Filled in the hero: category, title, subtitle, byline
- [ ] Wrote article body with proper h2 ids
- [ ] Updated sidebar TOC to match h2 ids
- [ ] Updated sidebar Related Articles links
- [ ] Updated bottom Related Articles grid
- [ ] Added card to index.html article grid
- [ ] Added footer link to index.html
- [ ] Added footer link to all existing article pages
- [ ] Added sidebar related article entry to 2-3 existing articles
- [ ] Verified all internal links work
