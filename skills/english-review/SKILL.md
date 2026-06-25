---
name: english-review
description: Helps a language learner review and retain English vocabulary and grammar learned in lessons, reading directly from two Notion databases (a "Vocabulary" database and a "Grammar" database). Use whenever the learner asks to "review English", "test me", "let's practice", "let's have a conversation in English", "add what I learned in my lesson", "register vocabulary/grammar", "how is my English", or "what am I forgetting", or pastes new words/topics to save. Also trigger when they mention their English lesson in the context of studying or reviewing. Conversation happens in the learner's native language, but exercises, examples and model sentences are in English. Has four modes: register (add what was learned to the databases), review (exercises prioritizing weak items), conversation (free dialogue in English with corrections only at the end), and diagnostic (overall state of what they know).
---

# English Second Brain

This skill helps a learner turn what they learn in English lessons into retained knowledge. They register vocabulary and grammar in two Notion databases and use those databases to review with exercises. The skill reads and writes directly to Notion — the learner doesn't need to paste anything.

This skill is built around an **external anchor**: a recurring lesson (e.g. a weekly private class). The natural flow is to register what was learned right after each lesson (register mode), then review throughout the week (review mode). It works best when hung off a fixed commitment that already exists.

> **Setup required.** This skill needs two Notion databases and their IDs filled in below. See the repository README for step-by-step setup. Replace every `<PLACEHOLDER>` before first use.

## Where the data lives

Everything lives on a Notion page in two databases:

- **Page:** ID `<NOTION_PAGE_ID>`
- **"Vocabulary" database:** data source ID `<VOCABULARY_DATA_SOURCE_ID>`
- **"Grammar" database:** data source ID `<GRAMMAR_DATA_SOURCE_ID>`

> If an ID stops working (page moved/recreated), use `Notion:notion-search` for "English" or "Vocabulary" and confirm
