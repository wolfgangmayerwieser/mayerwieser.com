# mayerwieser.com — Project Notes

## Stack
- **Site generator**: Hugo (static site)
- **Hosting**: GitHub Pages (free)
- **CI/CD**: GitHub Actions — auto-deploys on push to `main`
- **Theme**: Custom (in `layouts/`), no external theme dependency

## Key URLs
- **Live site**: https://mayerwieser.com
- **Repo**: https://github.com/wolfgangmayerwieser/mayerwieser.com
- **Pages settings**: https://github.com/wolfgangmayerwieser/mayerwieser.com/settings/pages

## Domain & DNS (Ionos)
Domain `mayerwieser.com` is registered at Ionos. DNS records:

| Type  | Host | Value | Purpose |
|-------|------|-------|---------|
| A     | @    | 185.199.108.153 | GitHub Pages |
| A     | @    | 185.199.109.153 | GitHub Pages |
| A     | @    | 185.199.110.153 | GitHub Pages |
| A     | @    | 185.199.111.153 | GitHub Pages |
| CNAME | www  | wolfgangmayerwieser.github.io | GitHub Pages |
| MX    | @    | mx01.mail.icloud.com | iCloud email — don't touch |
| MX    | @    | mx02.mail.icloud.com | iCloud email — don't touch |
| TXT   | @    | apple-domain=... | iCloud email — don't touch |
| TXT   | @    | v=spf1 include:icloud.com ... | SPF — don't touch |
| CNAME | sig1._domainkey | sig1.dkim... | DKIM — don't touch |

**HTTPS**: Managed by GitHub Pages (Let's Encrypt). Enable "Enforce HTTPS" in Pages settings.

## Local Development
```bash
hugo server --buildDrafts
```
Opens at http://localhost:1313

## Deployment
Push to `main` branch → GitHub Actions builds with Hugo → deploys to GitHub Pages.
Workflow file: `.github/workflows/deploy.yml`

## Adding a New Project
Create a Markdown file in `content/projects/`:

```markdown
---
title: "Project Name"
summary: "Short description for the project card"
tags: ["tag1", "tag2"]
date: 2025-02-12
---

Project content here...
```

## Site Structure
```
content/
├── about.md                 # About page
└── projects/
    ├── _index.md            # Projects listing intro text
    └── my-project.md        # Individual project

layouts/
├── index.html               # Home page (hero + project grid)
├── _default/
│   ├── baseof.html          # Base HTML template
│   ├── single.html          # Single page template
│   └── list.html            # Section listing template
└── partials/
    ├── header.html          # Navigation
    └── footer.html          # Footer

static/css/
└── style.css                # All styles
```

## Future Ideas
- **Nested sub-projects**: e.g. `content/projects/photography/street-vienna/index.md`
  — templates need updating to support nested sections
- Image galleries for photo projects (Hugo can resize images via page bundles)
