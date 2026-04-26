# New User Intake Protocol — Full Question Scripts

## Section 1: Personal Info & Target Role

Ask one at a time:
1. "What's your full name as it should appear on your CV?"
2. "What city and country are you based in?"
3. "Which email address should appear on your CVs?"
4. "And your phone number?"
5. "Do you have a LinkedIn profile? If so, what's the URL?"
6. "Do you have a GitHub profile you'd like included?"
7. "What kind of role are you applying for — backend, frontend, full-stack, mobile, DevOps, something else?"
8. "How would you describe your level — Junior, Mid, or Senior?"
9. "Any specific companies or industries in mind?"

## Section 2: Work Experience

Open with: "Tell me about your work experience. For each role, I'll need the company
name, your job title, the dates you worked there, and what you did."

For each role, push for achievements:
- "Did you improve anything measurable — speed, cost, reliability, user numbers?"
- "Did you build something from scratch or lead any part of the work?"
- "What were you most proud of in that role?"

If they have no formal experience:
"That's completely fine — tell me about any freelance work, volunteer projects,
or personal projects you've done instead."

## Section 3: Technical Skills

"What technologies do you work with? Walk me through your main programming
languages, frameworks, databases, and tools."

Follow up:
- "Which of these are you strongest in?"
- "Which have you used professionally vs. personally?"
- "Any AI or developer tools you use day-to-day?"

## Section 4: Projects

"Tell me about any personal, academic, or freelance projects you're proud of."

For each project collect:
- What does it do? (one sentence)
- What's the tech stack?
- What was your specific role?
- Is there a GitHub link or live demo?
- Any notable achievements? (users, performance, complexity)

## Section 5: Education

"What's your educational background? Include degrees, bootcamps, certifications —
anything relevant to tech."

For each: institution name, field of study, graduation year (or expected year).

Note: intensive programs (bootcamps, military tech programs) can sometimes be listed
as work experience rather than education — flag this possibility if relevant.

## Section 6: Additional

- "What languages do you speak, and at what level?"
  (Native / Fluent / Professional / Conversational)
- "Any military service worth mentioning?"
  (especially relevant for Israeli candidates)
- "Any other credentials, awards, or activities worth including?"

## Deriving user_id

From the user's full name: lowercase all letters, replace spaces with underscores.
Examples:
- "John Smith" → `john_smith`
- "María García" → `maria_garcia`
- "Refael Halifa" → `refael_halifa`

If two users would have the same user_id, append `_2` to the second.
