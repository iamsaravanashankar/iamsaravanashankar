# 🚀 GitHub Profile Page — Setup & Deployment Guide

A complete walkthrough to publish your personal profile page live on GitHub Pages
with a downloadable resume — no paid hosting needed.

---

## What You'll Have When Done

```
https://yourusername.github.io
```
A live, public profile page with:
- Your bio, skills, experience, projects, education, and contact links
- A **Download Resume** button that serves your PDF directly

---

## Prerequisites

| Requirement | How to get it |
|---|---|
| GitHub account | https://github.com/signup (free) |
| Git installed | https://git-scm.com/downloads |
| Your resume as a PDF | Export from Word / Google Docs |
| A text editor | VS Code recommended: https://code.visualstudio.com |

---

## Step 1 — Create the GitHub Repository

1. Log in to **https://github.com**
2. Click the **+** icon (top-right) → **New repository**
3. Set the repository name to exactly:
   ```
   yourusername.github.io
   ```
   ⚠️ Replace `yourusername` with your actual GitHub username (lowercase, exact match)
4. Set visibility to **Public**
5. Leave all other options at their defaults
6. Click **Create repository**

> **Why this name?** GitHub automatically serves repositories named
> `<username>.github.io` as a free website at that URL.

---

## Step 2 — Set Up Your Local Project Folder

Open your terminal (Command Prompt / Terminal / VS Code integrated terminal):

```bash
# Create a folder for your site
mkdir my-github-profile
cd my-github-profile

# Initialize a Git repository
git init

# Connect it to the GitHub repo you just created
git remote add origin https://github.com/yourusername/yourusername.github.io.git
```

---

## Step 3 — Add Your Files

Copy the following files into the `my-github-profile` folder:

```
my-github-profile/
├── index.html          ← The profile page (provided)
└── resume.pdf          ← Your resume PDF
```

> **Naming matters:** The resume file must be named exactly `resume.pdf`
> (or you must update the `href` in `index.html` to match your filename).

---

## Step 4 — Customise `index.html`

Open `index.html` in VS Code. Find and replace every piece of placeholder
content with your real information:

### 4a. Your Name & Title
```html
<!-- Find this line (~line 175) and update: -->
<h1 class="hero-name">Alex<br/>Morgan</h1>
<p class="hero-title">Senior Software Engineer <span>//</span> Full-Stack & Cloud</p>
```

### 4b. Your Bio
```html
<p class="hero-bio">
  Your personal summary here — 2–3 sentences about who you are,
  what you do, and what you care about.
</p>
```

### 4c. Resume Download Filename (appears twice)
```html
<!-- Find both occurrences and update the download="" attribute: -->
<a href="resume.pdf" download="YourName_Resume.pdf">
```

### 4d. Skills Cards
Find the `<!-- ── SKILLS ──>` section and update the `<span class="tag">` items
to reflect your actual skills.

### 4e. Work Experience
Find the `<!-- ── EXPERIENCE ──>` section.
Each job uses this pattern — duplicate or remove blocks as needed:

```html
<div class="exp-item">
  <div class="exp-meta">
    <div class="exp-period">2022 — Present</div>   <!-- ← your dates -->
    <div class="exp-company">Company Name</div>    <!-- ← company -->
  </div>
  <div>
    <div class="exp-role">Your Job Title</div>
    <p class="exp-desc">What you did and achieved here.</p>
    <div class="exp-tags">
      <span class="tag">Skill 1</span>
    </div>
  </div>
</div>
```

### 4f. Projects
Find the `<!-- ── PROJECTS ──>` section and update each `.project-card`.
Update the `href` on the **View on GitHub** links to point to your real repos.

### 4g. Education
Find the `<!-- ── EDUCATION ──>` section and update degrees, institutions, and years.

### 4h. Contact Links
Find the `<!-- ── CONTACT ──>` section and update:
- `href="mailto:..."` → your email
- GitHub, LinkedIn, Twitter `href` values → your profile URLs

### 4i. Footer
```html
<p>Designed & built by <span>Your Name</span> · 2025</p>
```

---

## Step 5 — Preview Locally (Optional but Recommended)

Before publishing, preview the page in your browser:

**Option A — Just open the file:**
- In your file explorer, double-click `index.html` → it opens in your browser

**Option B — Use VS Code Live Server (better):**
1. Install the **Live Server** extension in VS Code
2. Right-click `index.html` → **Open with Live Server**
3. Your browser opens at `http://127.0.0.1:5500`
4. Changes save and refresh automatically

---

## Step 6 — Commit and Push to GitHub

Once you're happy with the page:

```bash
# Stage all files
git add .

# Commit with a message
git commit -m "Initial profile page and resume"

# Push to GitHub (first time requires authentication)
git push -u origin main
```

> **Authentication:** GitHub no longer accepts passwords. Use a Personal Access Token:
> 1. Go to GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic)
> 2. Generate new token with `repo` scope
> 3. Use this token as your password when prompted in the terminal

---

## Step 7 — Enable GitHub Pages

1. Go to your repository on GitHub:
   `https://github.com/yourusername/yourusername.github.io`
2. Click the **Settings** tab
3. In the left sidebar, click **Pages**
4. Under **Source**, select:
   - Branch: `main`
   - Folder: `/ (root)`
5. Click **Save**

GitHub will show a green banner:
> ✅ Your site is live at `https://yourusername.github.io`

⏱ **Wait 1–3 minutes** for the first deployment to complete.

---

## Step 8 — Verify Your Live Site

Visit `https://yourusername.github.io` in an incognito/private browser window.

Check:
- [ ] Page loads correctly with your name and info
- [ ] **Download Resume** button downloads your PDF
- [ ] All contact links open correctly
- [ ] The page looks good on mobile (resize the browser)

---

## Updating Your Site Later

Any time you want to make changes:

```bash
# 1. Edit index.html or replace resume.pdf in your local folder
# 2. Stage and commit:
git add .
git commit -m "Update experience / resume"
# 3. Push:
git push
```
Changes go live automatically within ~30 seconds.

---

## Updating Your Resume Only

To update just the resume without changing the page:
1. Replace `resume.pdf` in your local folder with the new file (keep the same filename)
2. Run:
   ```bash
   git add resume.pdf
   git commit -m "Update resume"
   git push
   ```
The download link on your page will immediately serve the new version.

---

## Optional Enhancements

| Enhancement | How |
|---|---|
| **Custom domain** (e.g. yourname.com) | Buy a domain, then set it in repo Settings → Pages → Custom domain |
| **Add a profile photo** | Add `photo.jpg` to your folder, then add `<img src="photo.jpg">` in the hero section |
| **Google Analytics** | Paste the GA script tag just before `</head>` |
| **Favicon** | Add `favicon.ico` to your folder; it auto-loads for most browsers |
| **Dark/light toggle** | Ask Claude to add a theme toggle to the existing CSS variables |

---

## Troubleshooting

| Problem | Fix |
|---|---|
| Page shows 404 | Wait 3 min; check the repo is named exactly `yourusername.github.io` |
| Resume doesn't download | Confirm `resume.pdf` is in the root folder and filename matches the `href` |
| Styles look broken | Make sure Google Fonts can load (requires internet); the page needs to be online |
| Push rejected | Check you're using a Personal Access Token, not your GitHub password |
| Changes not showing | Hard-refresh the browser: `Ctrl+Shift+R` (Windows) / `Cmd+Shift+R` (Mac) |

---

*Guide version 1.0 · Works with GitHub Pages free tier · No build tools required*
