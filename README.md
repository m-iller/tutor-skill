# tutor — a personal tutor skill for Claude

A [Claude skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) that turns Claude into a patient personal tutor for any subject, with specialist playbooks for **math**, **programming** and **engineering**.

Works in the Claude app (claude.ai, desktop, mobile) and in Claude Code.

## What it does

- **Picks the right mode from what you ask:** Explain · Learn · Deep learn · Problem (hint ladder) · Solve · Debug · Review · Quiz · Mastery path · Cheat sheet.
- **Your sources are the single point of trust.** Lecture PDFs, slides, textbook chapters or methodical guides you attach are what it teaches from and grades against. Open sources only fill gaps.
- **Flags disagreements explicitly.** When the web or a standard textbook differs from your course material, you get a `⚠️ Discrepancy` block with both versions, citations, and which one to use for your course. Nothing is silently "corrected".
- **Always cites.** Every definition, formula, value and reference answer carries a citation (`[file, p.N]`, `[Lecture N]`, or a link), in teaching and in grading. It never invents a citation.
- **Hint ladder, not answer dumps.** One rung at a time on the step you're stuck on, then a twist problem to check transfer.
- **Deep learn loop for engineering:** motivation → model → minimal core → hand trace → gap check → break it on purpose → rebuild closed-book → knowledge chain. Covers circuits and power electronics, mechanisms, tolerances and fits, protocols and embedded.
- **Progress tracking (when files are available):** a study folder per course with a question bank, spaced repetition of failed questions, a mastery gate per topic, and a three-layer learner memory.

## Install

**Claude Code (plugin):**

```
/plugin marketplace add m-iller/tutor-skill
/plugin install tutor@tutor-skill
```

**Claude Code (manual):** copy `skills/tutor/` to `~/.claude/skills/tutor/` (all projects) or `.claude/skills/tutor/` (one project).

**Claude app:** download the repo as a ZIP, zip the `skills/tutor` folder on its own, then upload it under Settings → Customize → Skills.

## Use

Just ask: "teach me buck converters", "quiz me on chapter 3", "check my solution", "I'm stuck on this integral", "prepare me for the exam on Friday".

For the best results, give it your course material:
- **Claude app:** put lecture PDFs in a Project's knowledge, or attach them in the chat.
- **Claude Code:** make a folder per course, drop files into `sources/`, and run `claude` in that folder. The skill builds `question-bank.md`, `progress.md`, `profile.md` and `sessions.md` there.

## Layout

```
.claude-plugin/          plugin + marketplace manifests
skills/tutor/SKILL.md    the router and all core rules
skills/tutor/references/ subject playbooks, misconception lists, pedagogy notes
```

## Credits

- **[DeepTutor](https://github.com/HKUDS/DeepTutor)** (HKUDS, Apache-2.0): design of the learning modes, question bank, mastery gating and layered memory. Design only; no code copied.
- **[claude-tutors](https://github.com/cdmorozov/claude-tutors)** (cdmorozov, MIT): math and programming playbooks, misconception lists and pedagogy notes. License in `skills/tutor/references/LICENSE-claude-tutors.txt`.
- **[engineering-learning-skill](https://github.com/devinhuang2001/engineering-learning-skill)** (devinhuang2001): idea for the deep-learn loop, rewritten in original words.

## License

MIT, see [LICENSE](LICENSE).
