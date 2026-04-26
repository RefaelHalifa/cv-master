---
name: setup
description: >
  This skill should be used when a user installs the CV Master plugin for the
    first time and needs to set up their workspace. Triggers when the user says
      "set up CV Master", "initialize the project", "first time setup", or when
        no CV Master folder is found in their workspace.
        metadata:
          version: "0.2.0"
          ---

          Run this skill the first time a user installs the CV Master plugin.
          It creates the folder structure on their machine and walks them through connecting it.

          ## Step 0 — Detect the Environment

          Before doing anything else, run this bash command to detect which environment the user is in:

          ```bash
          echo "${CLAUDE_CODE:-not_set}"
          ```

          - If the output is `1` or any non-empty value → the user is in **Claude Code** (terminal)
          - If the output is `not_set` or the command fails → the user is in **Cowork** (desktop app)

          Run the appropriate flow below. Do not run both.

          ---

          ## COWORK FLOW

          ### Step 1 — Choose a Location

          Ask the user:

          > "Where would you like me to create your CV Master folder?
          > I'd suggest your Documents folder — does that work, or would you prefer somewhere else?"

          Default: `~/Documents/CV Master/`

          ### Step 2 — Create the Folder Structure

          Create the full directory tree using Bash:

          ```bash
          mkdir -p "<chosen_path>/CV Master/users"
          mkdir -p "<chosen_path>/CV Master/templates"
          mkdir -p "<chosen_path>/CV Master/system"
          ```

          Then write the starter files (user_registry.md, new_user_onboarding.md, cv_design_spec.md) as described in `references/folder-structure.md`.

          ### Step 3 — Connect the Folder to This Project

          This is the most important step. Claude cannot read or write your files until the folder is connected. Walk the user through it carefully:

          > "Your CV Master folder has been created at [path]. Now I need you to connect it to this project so I can read and write files there. This is a one-time step — follow these instructions carefully:"

          **If the user is in a Project (recommended setup):**

          > "1. Look at the top-left of the Claude window — you will see the name of your current project in the sidebar.
          >
          > 2. Click the project name to open the project settings panel.
          >
          > 3. In the project settings, look for a section called 'Files' or 'Connected folders' — it may show a folder icon with a + button next to it.
          >
          > 4. Click that + button (or 'Add folder' / 'Connect folder').
          >
          > 5. A Finder window will open. Navigate to [path], select the 'CV Master' folder, and click 'Open'.
          >
          > 6. macOS will show a permission dialog asking if Claude can access this folder. Click 'Allow' (or 'Allow Access').
          >
          > 7. The folder name should now appear in the project settings panel.
          >
          > Once you see it listed there, come back and type 'connected' — I'll verify it worked and start your onboarding."

          **If the user is NOT in a Project (regular chat):**

          > "You're currently in a regular chat, not a project. For CV Master to work properly across sessions, I strongly recommend setting it up inside a Project.
          >
          > Here's how to create one:
          > 1. In the Claude sidebar on the left, look for a 'Projects' section
          > 2. Click '+ New Project' and name it 'CV Master'
          > 3. Open the new project, then follow the folder connection steps above
          >
          > If you'd like to continue in this regular chat anyway, you can — but your files and profile won't automatically load in future sessions."

          ### Step 4 — Verify the Connection

          When the user says 'connected', verify it worked:

          ```bash
          ls "<chosen_path>/CV Master/"
          ```

          If the system and users folders appear, the connection is working. Confirm:

          > "Connection verified — I can see your CV Master folder. Let's set up your profile now."

          ### Step 5 — Hand Off to Onboarding

          Trigger the `user-onboarding` skill immediately.

          ---

          ## CLAUDE CODE FLOW

          ### Step 1 — Choose a Location

          Ask the user:

          > "Where would you like me to create your CV Master folder?
          > I'd suggest your Documents folder — does that work, or would you prefer somewhere else?"

          Default: `~/Documents/CV Master/`

          ### Step 2 — Create the Folder Structure

          Create the full directory tree:

          ```bash
          mkdir -p "<chosen_path>/CV Master/users"
          mkdir -p "<chosen_path>/CV Master/templates"
          mkdir -p "<chosen_path>/CV Master/system"
          ```

          Then write the starter files as described in `references/folder-structure.md`.

          ### Step 3 — No Connection Needed

          In Claude Code there is no folder connection step — Claude Code works directly with your filesystem. Explain this to the user:

          > "In Claude Code, there's no need to 'connect' a folder like in the desktop app. I already have full access to your filesystem.
          >
          > For the best experience, run Claude Code from inside your CV Master folder:
          >
          >   cd '<chosen_path>/CV Master'
          >   claude
          >
          > Or, whenever you want to work on your CV, just tell me the full path and I'll work with files there directly.
          >
          > That's it — you're ready to go."

          ### Step 4 — Hand Off to Onboarding

          Trigger the `user-onboarding` skill immediately.
