# CV Master Plugin

A world-class CV specialist for tech professionals. Writes, edits, and tailors CVs
with a clean one-page design optimized for ATS and human recruiters alike.

Supports multiple users on the same installation — each person gets their own
profile, CV library, and tailoring history.

## What It Does

- **Write from scratch** — full information gathering, then a polished PDF CV
- **Edit & enhance** — review an existing CV and rewrite it with improvements
- **Tailor to a job** — restructure and re-angle a CV for a specific role or company
- **Multi-user** — automatically detects new vs. returning users and manages profiles separately

## Skills

| Skill | Trigger | What it does |
|---|---|---|
| `cv-specialist` | Asking for CV help (or session start) | Core specialist — routes to write/edit/tailor mode, generates CVs |
| `user-onboarding` | New user detected | Full intake flow, creates profile and folder structure |
| `setup` | First-time install | Creates the CV Master folder on the user's machine |

## First-Time Setup

1. Install the plugin in Claude desktop
2. Open a new chat and say: **"set up CV Master"**
3. Claude will create your `CV Master/` folder, connect it, and run onboarding
4. Answer the intake questions — takes about 5 minutes
5. Done — your profile is saved and you're ready to generate CVs

## Adding a New User

Have the new person open a chat and say:
> "Hi, I'm [their name] — I'm a new user"

Claude will detect they're not in the registry and run onboarding automatically.

## Returning User Flow

Just open a chat and start talking. Claude loads your profile from the registry,
greets you by name, and asks if anything has changed since last time.

## CV Design

All CVs use the approved design spec in `CV Master/templates/cv_design_spec.md`:
- Dark navy name, corporate blue section headers, clean gray body text
- Helvetica font family, A4 format, 16mm margins
- Generated with Python + ReportLab
- Strictly one page — always

## File Organization

```
CV Master/
  users/<your_name>/
    profile.md          ← your profile
    cvs/
      general/          ← non-targeted CVs
      tailored/         ← company-specific CVs
      source/           ← editable source files
  templates/            ← shared design standards
  system/               ← user registry and onboarding docs
```

## Requirements

- Claude desktop app with Cowork mode
- Python 3 + ReportLab installed (for PDF generation)
  Install: `pip install reportlab`
- A connected `CV Master/` workspace folder

## Version

0.1.0 — Initial release
