# /quiz-blitz

Create a new blitz quiz for CrazyQuizzes and add it to the data files.

## What to do

You are adding a new timed blitz quiz. Data lives in:
- `src/data/blitzes.json` — full quiz content (10 questions with correct answers)
- `src/data/cards.json` — homepage card listing

## Arguments

The user provides topic + type as `$ARGUMENTS`. Format: `"topic [type]"`
- `type` can be: `trivia`, `true-false`, `emoji-guess`
- Example: `"90s music trivia"`, `"science true-false"`, `"guess the country emoji-guess"`
- If no type given, default to `trivia`

## Question types

### trivia (standard multiple choice)
```json
{ "kind": "TRIVIA", "prompt": "🎯", "text": "Question?", "options": ["A","B","C","D"], "correct": 2 }
```
- `prompt`: 1-2 emojis representing the topic
- 4 options, one correct (`correct` is 0-indexed)
- Make wrong answers plausible but clearly wrong to someone who knows

### true-false
```json
{ "kind": "TRUE OR FALSE", "prompt": "🦩", "text": "Statement that is true or false.", "options": ["TRUE","FALSE"], "correct": 0 }
```
- `correct`: 0 = TRUE, 1 = FALSE
- Statements should be surprising — either a common myth (FALSE) or a shocking true fact (TRUE)
- Mix: aim for 5-6 TRUE and 4-5 FALSE in a 10-question set

### emoji-guess
```json
{ "kind": "GUESS THE [THING]", "prompt": "🎬🦁👑", "text": "Which [movie/show/brand/etc] is this?", "options": ["A","B","C","D"], "correct": 1 }
```
- `prompt`: 2-4 emojis that represent the answer
- `kind`: "GUESS THE MOVIE", "GUESS THE BRAND", "GUESS THE TV SHOW", "GUESS THE SONG", etc.
- Distractors should be in the same category, similarly famous

## Step 1 — Write 10 questions

Write exactly 10 questions all using the same type format. Ensure facts are accurate.

## Step 2 — Generate a slug

Kebab-case id like `music-trivia`, `tf-science`, `emoji-movies-2`.

## Step 3 — Add to blitzes.json

Read `src/data/blitzes.json` and add:
```json
"your-slug": {
  "title": "Quiz Title",
  "questions": [
    { "kind": "...", "prompt": "...", "text": "...", "options": [...], "correct": N },
    ... (9 more)
  ]
}
```

## Step 4 — Add to cards.json

```json
{
  "id": "your-slug",
  "title": "Quiz Title",
  "cat": "EMOJI BLITZ | TRUE / FALSE | TRIVIA",
  "takes": "412K",
  "coverEmoji": "emoji1emoji2",
  "coverBg": "linear-gradient(135deg,#COLOR1 0%,#COLOR2 100%)",
  "badge": "⚡ BLITZ",
  "badgeColor": "#ffd23f",
  "badgeInk": "#1a1430",
  "type": "blitz",
  "categories": ["ALL","TRIVIA","CHAOS"]
}
```

Choose `categories` from: ALL, TRIVIA, CHAOS, SCIENCE, HISTORY, GEOGRAPHY, SPORTS, MUSIC, MOVIES & TV, POP CULTURE, FOOD.

## Accuracy rules
- Double-check all facts before writing them
- For true/false: only use well-established, verifiable facts
- For emoji-guess: make sure the emoji combo clearly hints at the correct answer
- Never include ambiguous trivia where multiple answers could be correct
