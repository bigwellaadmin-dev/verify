# skill/VERIFY_skill.md — Build Specification

Read `docs/FRAMEWORK.md` for all step content before writing the skill file. Where `FRAMEWORK.md` marks content as verbatim from source (the seven F questions, in-one-sentence lines, Y diagnostic, three E failure modes), do not paraphrase.

## File format

```
---
name: verify-framework
description: Use this skill when asked to apply the VERIFY framework — guiding a student through V-E-R-I-F-Y, reviewing student work for evidence of each step, or generating VERIFY-aligned teacher feedback. Triggers include: "apply VERIFY", "review this student work with VERIFY", "VERIFY framework", "check this AI output for AI literacy", "VERIFY-aligned feedback", "what step did this student skip".
---

# VERIFY Framework — AI Literacy Review

VERIFY is a teaching framework for working with AI in secondary classrooms. It is designed for teacher-led use. When you (Claude) apply this skill, you are standing in for the teacher conversation — asking the questions a teacher would ask at each step.

[Six steps with the in-one-sentence line, the distilled guiding questions, the mechanism, and any verbatim source material — drawn from FRAMEWORK.md.]

## How to apply this skill

### Mode 1 — Student guidance
Walk the student through each step in order. Present the guiding questions one at a time. Wait for a response before moving forward. At Y, reflect the student's answers from V through F back to them before asking the three Y questions. Be willing to backtrack: if a student gives an answer at E or R that suggests V was skipped, gently send them back rather than pushing forward.

### Mode 2 — Work review
Given a submitted piece of student work, identify which VERIFY steps appear to have been applied and which were skipped. Use the Y diagnostic (verbatim from source) to locate the most likely breakdown point. Return structured feedback: what was done well, which step to revisit, and one specific question the student can ask themselves to start.

### Mode 3 — Teacher feedback generation
Given student work and a task description, generate VERIFY-aligned written feedback a teacher can provide. Use the feedback-language phrasings embedded in the skill file itself (the full V/E/R/I/F/Y x Strong/Developing/Weak matrix is inline in `skill/VERIFY_skill.md`, also documented in `guide/04-assessment.md` §4.4). Frame feedback around which step the student needs to revisit and give a concrete next action, not general praise or criticism.

## The 7 Filter check questions

[All 7 from F — drawn from FRAMEWORK.md verbatim. Apply systematically in Mode 1. Check for evidence of each in Mode 2 and Mode 3.]

## Y diagnostic

[Five-point map from FRAMEWORK.md, verbatim from source — use in Mode 2 and Mode 3 to locate where the framework broke down.]

---

*VERIFY Framework © 2026 Sandra Robinson · Big Wella. Licensed CC BY 4.0. Source: https://github.com/bigwellaadmin-dev/verify. Please cite per the CITATION.cff in the repository.*
```

## Notes

- All verbatim content (F questions, in-one-sentence lines, Y diagnostic, E failure modes) must match `docs/FRAMEWORK.md` exactly.
- The skill's `description` field determines when Claude loads this skill — be precise about triggers.
- The licence line at the end is mandatory and must include the repository URL and version.
- Keep the skill file under ~400 lines. If the body grows beyond that, factor reference material into separate files in the same skill folder. Current build is around 325 lines.
