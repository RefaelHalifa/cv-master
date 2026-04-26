---
name: setup
description: >
  This skill should be used when a user installs the CV Master plugin for the
  first time and needs to set up their workspace. Triggers when the user says
  "set up CV Master", "initialize the project", "first time setup", or when
  no CV Master folder is found in their workspace.
metadata:
  version: "0.1.0"
---

Run this skill the first time a user installs the CV Master plugin.
It creates the complete folder structure on their machine and prepares everything
for the first user onboarding.

## Step 1 — Find the Right Location

Ask the user where they want their CV Master folder:

> "Where would you like me to create your CV Master folder?
> I'd suggest your Documents folder — does that work, or would you prefer somewhere else?"

Default: `~/Documents/CV Master/`

## Step 2 — Create Folder Structure

Create the full directory tree at the chosen location:

```
CV Master/
  users/                        ← one subfolder per user, created during onboarding
  templates/
    cv_design_spec.md           ← shared design standard
  system/
    user_registry.md            ← master index of all users
    new_user_onboarding.md      ← intake protocol reference
```

Use Bash to create the directories:
```bash
mkdir -p "<chosen_path>/CV Master/users"
mkdir -p "<chosen_path>/CV Master/templates"
mkdir -p "<chosen_path>/CV Master/system"
```

## Step 3 — Write Starter Files

Write `CV Master/system/user_registry.md` with this starter content:

```markdown
# User Registry

Master index of all users onboarded to this CV Master project.
Update whenever a new user completes onboarding.

## Registered Users

(No users yet — run onboarding to add the first user.)
```

Write `CV Master/system/new_user_onboarding.md` pointing to the skill:

```markdown
# New User Onboarding

Onboarding is handled automatically by the CV Master plugin.
When a new user opens a chat, the user-onboarding skill runs the full intake flow.

See the plugin's user-onboarding skill for the complete protocol.
```

Copy `cv_design_spec.md` content from `references/cv-design-spec.md`
(in the cv-specialist skill) into `CV Master/templates/cv_design_spec.md`.

## Step 4 — Connect the Folder

Instruct the user to connect the new folder as their project workspace:

> "Your CV Master folder is ready at [path]. Now you need to connect it to this
> Claude project so I can read and write files there.
>
> Here's how:
> 1. Click the folder icon in the top-right of this chat
> 2. Select 'Add folder'
> 3. Navigate to [path] and select 'CV Master'
> 4. Click 'Allow access'
>
> Once connected, come back and say 'ready' — I'll kick off your first onboarding session."

## Step 5 — Confirm & Hand Off

When the user confirms the folder is connected:

> "Perfect — everything is in place. Let's get your profile set up."

Trigger the `user-onboarding` skill immediately.
