# /quiz-personality

Create a new personality quiz for CrazyQuizzes and add it to the data files.

## What to do

You are adding a new personality quiz to this Astro site. The quiz data lives in two files:
- `src/data/quizzes.json` — full quiz content (questions + results)
- `src/data/cards.json` — homepage card listing

## Arguments

The user will provide a quiz topic/title as `$ARGUMENTS`. If none given, invent a funny, viral-style personality quiz topic (e.g. "Which Type of Overthinker Are You?", "What's Your Villain Era?").

## Step 1 — Design the quiz

Create a personality quiz with:
- **6 questions**, each with 4 options (A/B/C/D), each option maps to one of 4 result keys
- **4 results** — each should be a funny, distinct personality archetype with:
  - `name` — short ALL-CAPS label (e.g. "THE NIGHT OWL")
  - `kind` — subtitle/archetype name
  - `color` — one of: `#ff3b9a`, `#6c3bff`, `#3bffd2`, `#ffd23f` (use all 4 across the 4 results)
  - `nameInk` — `#fff` for dark colors, `#1a1430` for light colors (`#3bffd2`, `#ffd23f`)
  - `rarity` — percentage (4 should add up to ~100%)
  - `tagline` — one punchy line about this type
  - `traits` — array of 3 short trait labels
  - `desc` — 2-3 sentence funny/accurate personality description

Quiz metadata:
- `title` — engaging question format ("Which X Are You?" or "What's Your X?")
- `cover` — 2-3 word visual description
- `cat` — "PERSONALITY · [SUBCATEGORY]" (use: CHAOS, VIBES, POP CULTURE, FOOD, SPORTS, MUSIC)
- `minutes` — 2
- `qcount` — 6
- `takes` — random viral-looking number like "734K" or "1.1M"
- `desc` — 2-sentence funny description of the quiz

## Step 2 — Generate a slug

Create a kebab-case id like `overthinker-type` or `villain-era`.

## Step 3 — Add to quizzes.json

Read `src/data/quizzes.json` and add the new quiz object at the end (before the closing `}`).

Format:
```json
"your-slug": {
  "title": "...",
  "cover": "...",
  "cat": "PERSONALITY · ...",
  "minutes": 2,
  "qcount": 6,
  "takes": "...",
  "desc": "...",
  "questions": [
    { "text": "Question?", "options": [
      { "label": "Option A", "key": "resultkey1" },
      { "label": "Option B", "key": "resultkey2" },
      { "label": "Option C", "key": "resultkey3" },
      { "label": "Option D", "key": "resultkey4" }
    ]},
    ... (5 more questions)
  ],
  "results": {
    "resultkey1": { "name": "...", "kind": "...", "color": "#ff3b9a", "nameInk": "#fff", "rarity": "27%", "tagline": "...", "traits": ["...", "...", "..."], "desc": "..." },
    "resultkey2": { ... },
    "resultkey3": { ... },
    "resultkey4": { ... }
  }
}
```

## Step 4 — Add to cards.json

Read `src/data/cards.json` and add a new entry:
```json
{
  "id": "your-slug",
  "title": "Quiz Title",
  "cat": "PERSONALITY",
  "takes": "...",
  "coverEmoji": "emoji1emoji2",
  "coverBg": "linear-gradient(135deg,#COLOR1 0%,#COLOR2 100%)",
  "badge": "🔥 HOT",
  "badgeColor": "#ff3b9a",
  "badgeInk": "#fff",
  "type": "personality",
  "categories": ["ALL","PERSONALITY","CHAOS"]
}
```

Choose `categories` to match the quiz topic. Available: ALL, PERSONALITY, CHAOS, VIBES, POP CULTURE, FOOD, SPORTS, MUSIC, MOVIES & TV, Y2K, HISTORY, SCIENCE, GEOGRAPHY, TRIVIA.

Pick 2-3 fun emojis for `coverEmoji`. Choose a gradient that fits the vibe.

## Style guide

- Tone: Funny, self-aware, internet-native. Like BuzzFeed but unhinged.
- Questions should be specific and relatable, not generic
- Result descriptions should feel validating even when they're roasting you
- Options should all feel true to someone — no obviously "wrong" answers
