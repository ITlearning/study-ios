# study-ios

Swift/iOS learning project with interactive skills.

## Skills

Skills are located in `.gemini/skills/` (symlinked from `.agents/skills/`). Each skill has a `SKILL.md` with instructions.

- `/swift-study` - Interactive Swift/iOS tutor (Socratic method)
- `/swift-quiz` - Adaptive quiz with 5 questions, difficulty 1-5
- `/study-summary` - Save learning notes from conversation to `notes/`

## Project Structure

- `notes/` - Saved learning notes (YYYY-MM-DD-topic.md format)
- `.agents/skills/` - Canonical skill definitions

## Conventions

- Bilingual support: Korean and English (user chooses at start)
- Code and Swift keywords always in English
- No emojis in output
- Learning progress tracked in memory or `notes/progress.md`
