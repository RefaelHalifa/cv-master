# CV Master Folder Structure Reference

## Full Structure (after multiple users onboarded)

```
CV Master/
  users/
    <user_id_1>/
      profile.md                ← full user profile (contact, skills, experience, projects)
      cvs/
        general/                ← non-targeted CVs (Backend, FullStack, etc.)
        tailored/               ← company/role-specific CVs
        source/                 ← editable source files (.pages, .docx)
    <user_id_2>/
      profile.md
      cvs/
        general/
        tailored/
        source/
  templates/
    cv_design_spec.md           ← approved colors, fonts, layout — shared across all users
  system/
    user_registry.md            ← master index: all users, their paths, cv counts
    new_user_onboarding.md      ← intake protocol reference doc
```

## File Naming Convention

All CV files follow this pattern:
```
<FirstName>_<LastName>_<Target>_<Year>.pdf
```

Examples:
- `John_Smith_Backend_2026.pdf`         → general/
- `John_Smith_Google_2026.pdf`          → tailored/
- `John_Smith_Source_2026.pages`        → source/

## user_id Convention

Derived from full name: lowercase, spaces → underscores.
- "John Smith"   → `john_smith`
- "Ana Martínez" → `ana_martinez`
- Collision (two John Smiths): second becomes `john_smith_2`

## user_registry.md Structure

```markdown
# User Registry

## Registered Users

### 1. Full Name
| Field | Value |
|---|---|
| user_id | `<user_id>` |
| display_name | Full Name |
| onboarded | YYYY-MM-DD |
| last_active | YYYY-MM-DD |
| seniority | Junior / Mid / Senior |
| primary_stack | main technologies |
| location | city, country |
| email_on_cv | email@example.com |
| profile | `users/<user_id>/profile.md` |
| cvs | `users/<user_id>/cvs/` |
| cv_count | N |
| notes | any relevant notes |
```
