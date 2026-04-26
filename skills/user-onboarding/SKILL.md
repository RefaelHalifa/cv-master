---
name: user-onboarding
description: >
  This skill should be used when a new user opens the CV Master project for the
  first time, when someone introduces themselves as a new user, or when a user's
  name is not found in the user registry. Triggers automatically from the
  cv-specialist skill when the active user is unrecognized.
metadata:
  version: "0.1.0"
---

Run this flow when the active user is not found in `CV Master/system/user_registry.md`.
Complete all steps before proceeding to any CV work.

## Step 1 — Welcome

Greet the user warmly and set expectations:

> "Welcome! I'm your personal CV specialist. Before we dive in, I'd like to take
> 5 minutes to get to know you — so every CV I create for you is perfectly calibrated.
> Let's start with the basics."

## Step 2 — Gather Information

Run the full intake protocol from `references/intake-protocol.md`.
Collect information one section at a time — never dump a list of questions at once.

Sections in order:
1. Personal info & target role
2. Work experience
3. Technical skills
4. Projects
5. Education
6. Additional (languages, military service, etc.)

## Step 3 — Confirm & Show Summary

Before saving anything:

> "I have everything I need. Here's a quick summary of what I've collected —
> let me know if anything needs adjusting."

Show a structured summary. Wait for explicit confirmation.

## Step 4 — Create Folder Structure

After confirmation, create the user's folders. Derive `<user_id>` from their name:
lowercase, spaces replaced with underscores (e.g. "John Smith" → `john_smith`).

Create:
```
CV Master/users/<user_id>/
  cvs/
    general/
    tailored/
    source/
  profile.md
```

Use the template in `../cv-specialist/references/user-profile-template.md`
to write their `profile.md`.

## Step 5 — Update Registry

Add the new user to `CV Master/system/user_registry.md` following this format:

```markdown
### <N>. <Full Name>
| Field | Value |
|---|---|
| `user_id` | `<user_id>` |
| `display_name` | <Full Name> |
| `onboarded` | <YYYY-MM-DD> |
| `last_active` | <YYYY-MM-DD> |
| `seniority` | <Junior / Mid / Senior> |
| `primary_stack` | <main technologies> |
| `location` | <city, country> |
| `email_on_cv` | <email> |
| `profile` | `users/<user_id>/profile.md` |
| `cvs` | `users/<user_id>/cvs/` |
| `cv_count` | 0 |
| `notes` | <any relevant notes> |
```

## Step 6 — Save Memory Files

Create memory files for this user, namespaced with their user_id:
- `<user_id>_profile.md` — identity, contact, education, experience, seniority
- `<user_id>_skills.md` — full tech stack grouped by category
- `<user_id>_projects.md` — all projects with stacks and key points
- `<user_id>_cv_library.md` — CV versions (starts empty, populated as CVs are made)

Also add a section to `MEMORY.md`:
```markdown
## User: <user_id>
- [<Full Name> — Personal Profile](<user_id>_profile.md) — ...
- [<Full Name> — Technical Skills](<user_id>_skills.md) — ...
- [<Full Name> — Portfolio Projects](<user_id>_projects.md) — ...
- [CV Library — <Full Name>](<user_id>_cv_library.md) — ...
```

## Step 7 — Confirm & Proceed

Confirm completion:
> "You're all set! Your profile has been saved. Now — would you like me to
> write your CV, edit an existing one, or tailor it for a specific role?"

Hand off to the `cv-specialist` skill for the requested service.

## Returning User Flow

If the user IS in the registry (called for updates, not full onboarding):
1. Load their `profile.md`
2. Ask: "Welcome back, [Name]! Anything changed since last time — new experience, new skills, or a different target role?"
3. Update `profile.md` and memory files with any new information
4. Update `last_active` in `user_registry.md`
5. Proceed to the service they want
