# VERIFY Framework — Tool/Skill Distillation Spec

This file is the **distilled spec used by the interactive tool and the Claude skill**. It is not the canonical framework — that lives in `../guide/02-the-framework.md` and the rest of the Teacher Guide.

**Three categories of content live here:**

1. **Verbatim from source.** The seven F check questions, the Y diagnostic, and the three E failure modes are reproduced verbatim from Sandra Robinson's Teacher Guide. Do NOT modify these. If the source changes, update this file to match.
2. **Verbatim-adjacent.** The "in one sentence" lines per step are verbatim from source in this spec and in the Claude skill. In the interactive tool only, they are rewritten in the second person ("you" instead of "students" or "the student") to address the learner directly. This adaptation is allowed because the tool is the learner-facing surface; the framework spec and the skill stay in the source voice.
3. **Distilled and adapted for tool UX.** The three "guiding questions" per step for V, E, R, I, Y are distilled from the Teacher Guide's practitioner moves (before / during / after task) into a 3-question format suitable for an interactive tool, and adapted for plain-language accessibility so the tool reads cleanly for Year 7 to Year 12 students and adult learners. They preserve the source's meaning in plainer wording.

All three categories are licensed CC BY 4.0.

---

**V**alidate · **E**xamine · **R**eflect · **I**nvestigate · **F**ilter · **Y**our Judgement

> **The framework is a loop, not a line.** If a student arrives at I without having done V, E, or R properly, do not send them back to the start. Use I to work backwards. (Source: Part 2, *I — Investigate Further*, "The retroactive function".)

---

## V — Validate the Task

> **V in one sentence:** *The prompt is where the thinking starts. V is the step that makes sure the thinking has actually started before the prompt is written.* (Verbatim)

Before opening AI, students define what they are actually trying to do — not the topic, but the thinking the task requires.

**Guiding questions (distilled for tool, plain-language):**
1. What is this task actually asking me to show? (Not the topic. The thinking that proves I understood.)
2. Who is this work for? (Who reads it changes how I write it, how much I explain, and what I can leave out.)
3. What kind of thinking does this task want? (Am I describing something? Making an argument? Comparing? Deciding? Name what kind of thinking is being asked for.)

**Mechanism:** Most students have a Meta-Task Awareness gap. They understand what a task says on the surface but not what thinking it requires underneath. A student who has not validated before prompting accepts a generic AI response as an answer to a question they have not properly asked.

---

## E — Examine the Source or System

> **E in one sentence:** *Fluency is not accuracy. E is the step where students learn to treat those as separate questions.* (Verbatim)

AI output is always fluent. Fluency is not accuracy. Students must build a basis for judging output before trusting it.

**Guiding questions (distilled for tool, plain-language):**
1. Would this answer look just as confident if it were wrong?
2. Whose point of view does this answer come from? What would have to be in there to make it the full picture?
3. Are you on the right track, or have you gone the wrong way without noticing?

**The three failure modes (verbatim from source — name each one for students):**
- **Uncritical acceptance.** The student reads the output, decides it looks right, and uses it without question. The teacher move is to show a specific instance of fluent, structured, convincingly wrong output. One concrete example does more than any general warning.
- **Bias blindness.** AI output presents in a generic, authoritative voice that carries no markers of perspective. Students who ask "whose view is this" of human sources do not automatically apply that question to AI output because nothing in the surface signals a perspective is present.
- **Failure to backtrack or pivot.** The student follows a line of AI output that does not serve the task, adds more prompts trying to fix it downstream, and arrives off-target in a direction set at the beginning. They never recognise the trail was wrong and try a different approach.

---

## R — Reflect on Your Needs and Context

> **R in one sentence:** *The output looking finished is not the same as the thinking being done. R is the step that makes that distinction visible.* (Verbatim)

AI output is produced without knowledge of the student's specific context. R asks whether the student is present in the work.

**Guiding questions (distilled for tool, plain-language):**
1. Does this fit the actual task I was given? Not just the topic, but what the task is really asking for.
2. Does this match what I actually think? Could I explain why I believe it, out loud, without looking at my notes?
3. What does this answer not know about my situation or what I am working on?

**Mechanism:** The illusion of mastery — the output looks complete, so the student feels done. The feeling of completion is real. The learning has not happened.

---

## I — Investigate Further

> **I in one sentence:** *Every source leaves something out. I is the step where students go looking for what that is.* (Verbatim)

Every source leaves something out. I asks students to find what is missing rather than assuming completeness.

**Guiding questions (distilled for tool, plain-language):**
1. What can this answer never know? Things like local knowledge, real-life experience, or voices that do not often get heard.
2. Who is not in this answer? Does that matter for what I am trying to do?
3. What would I do if one of the main facts here turned out to be wrong?

**Dual function:** Works as deepening for students who engaged with V / E / R (they arrive with specific gaps to fill), and as an entry point for students who did not (the question "what is this leaving out" is useful regardless).

---

## F — Filter for Quality and Fairness

> **F in one sentence:** *Students cannot filter without a standard. The check questions are the standard made concrete.* (Verbatim)

Students cannot filter without a standard. These seven questions are the standard. Render as interactive toggle cards — each toggle reveals a one-line "What did you find?" reflection field.

**The seven F check questions are VERBATIM from source (Sandra Robinson, *Teaching AI to Ask: The VERIFY Framework, Part 2*). Do not paraphrase. Attribution note from source: "The seven check questions were developed in collaboration with Sandra Robinson and reflect her classroom experience alongside the research principles established in this guide."**

**Quality:**
1. Can I point to a source for the three most important claims in this output?
2. Does this answer the question I actually asked, or an easier version of it?
3. What would someone who disagreed with this say, and does this output mention that?

**Fairness:**
4. Whose experience is this output written from?
5. Who is missing from this answer, and does that matter?
6. Is this written for my specific situation, or for a generic one that may not be mine?

**Combined:**
7. If I took out everything I cannot personally verify or add to, what would be left?

---

## Y — Your Own Judgement

> **Y in one sentence:** *You cannot defend a judgement you did not make. Y is the step where the student finds out whether they made one.* (Verbatim)

You cannot defend a judgement you did not make.

**Guiding questions (distilled for tool, plain-language):**
1. Can you explain what you decided and why, in your own words, without looking at your work?
2. What are the three most important points in your work? Where does each one come from?
3. What would you change if you had to start again?

**Y as diagnostic (verbatim from source) — if the student cannot apply Y, the breakdown maps to:**
- Cannot explain the reasoning → problem started at **V**
- Can explain but cannot defend against challenge → problem started at **E**
- Can defend the argument but it does not fit the task → problem started at **R**
- Has a position but it is entirely generic → problem started at **I**
- Has specific material but cannot evaluate it → problem started at **F**

**Y step structure in the tool:** Two parts — (1) the three guiding questions with textareas, (2) a read-only summary panel showing all responses from previous steps (including F reflection fields). This is the payoff moment. The summary panel uses `textContent` only — no HTML parsing path. See `TOOL_SPEC.md` for the rendering contract.
