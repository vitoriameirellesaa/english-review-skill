# English Review Skill

A Claude skill that turns your English lessons into retained knowledge. It reads vocabulary and grammar straight from **two Notion databases** and runs spaced-repetition review sessions, conversation practice, and diagnostics — all conversationally, prioritizing what you're weakest at.

Built around an **external anchor** (a recurring lesson, e.g. a weekly class): register what you learned right after the lesson, review across the week.

## Modes

- **Register** — add new vocabulary/grammar to your Notion databases.
- **Review** — ~10-minute sessions of varied exercises, prioritizing low-confidence and long-unreviewed items, woven into your real life.
- **Conversation** — free dialogue in English, corrections held to the end.
- **Diagnostic** — overview of what you know, what's stuck, and what to focus on next.

## Requirements

- Claude with the **Notion connector** enabled (the skill uses `Notion:notion-search`, `notion-fetch`, `notion-create-pages`, `notion-update-page`).
- A Notion workspace where you can create two databases.

## Setup

You need Claude with the **Notion connector** enabled before either path below.

### Quick setup (recommended)

Instead of building the databases by hand, paste the prompt in [`SETUP_PROMPT.md`](SETUP_PROMPT.md) into Claude. It creates both databases with the correct fields and hands you back the three IDs, already formatted to paste into the skill.

Then:
1. Open `skills/english-review/SKILL.md` and replace `<NOTION_PAGE_ID>`, `<VOCABULARY_DATA_SOURCE_ID>` and `<GRAMMAR_DATA_SOURCE_ID>` with the IDs Claude gave you.
2. Install (see step 4 below).

That's it. The manual steps below are the same thing done by hand, if you prefer.

---

### Manual setup

#### 1. Create the two Notion databases

Create a Notion page (e.g. "English") and two databases inside it.

**Vocabulary** database with these properties:

| Property | Type | Notes |
|---|---|---|
| `Term (EN)` | Title | the word/expression |
| `Meaning` | Text | translation in your language |
| `Example` | Text | example sentence in English |
| `Category` | Select | word, phrasal verb, expression, collocation, slang/informal |
| `Confidence` | Select | `1 - just saw it`, `2 - weak`, `3 - medium`, `4 - good`, `5 - mastered` |
| `Learned on` | Date | |
| `Last review` | Date | |

**Grammar** database with these properties:

| Property | Type | Notes |
|---|---|---|
| `Topic` | Title | name of the topic |
| `Rule summary` | Text | the rule, briefly, in your language |
| `Examples` | Text | example sentences in English |
| `Mistakes I make` | Text | your recurring mistakes |
| `Confidence` | Select | same scale as above |
| `Learned on` | Date | |
| `Last review` | Date | |

> You can rename properties, but if you do, update the schema section in `SKILL.md` to match.

#### 2. Get the IDs

For each database, open it in Notion, click **Share → Copy link**. The ID is the 32-character string in the URL. The page ID comes from the parent page's URL the same way.

#### 3. Fill in the placeholders

In `skills/english-review/SKILL.md`, replace:

- `<NOTION_PAGE_ID>` — the parent page ID
- `<VOCABULARY_DATA_SOURCE_ID>` — the Vocabulary database ID
- `<GRAMMAR_DATA_SOURCE_ID>` — the Grammar database ID

#### 4. Install

```
/plugin marketplace add vitoriameirellesaa/english-review-skill
/plugin install english-review@english-review-marketplace
```

## Customizing

The skill is set up for a learner at an intermediate level whose interests/context aren't hardcoded — it asks for fresh context each session. If you want it tuned to your level or with a fixed "base repertoire" of topics (work, hobbies, etc.), edit the relevant lines in `SKILL.md`. It's just a markdown file.

## Notes

- The skill always shows you what it's about to write to Notion and waits for your "ok" before writing.
- A read-only "review queue" view in Notion (sorted by confidence + date) is handy for visual review, though the skill sorts on its own.

## License

MIT — see [LICENSE](LICENSE).

In Claude Code:
