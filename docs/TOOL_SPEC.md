# tool/index.html — Build Specification

Read `docs/FRAMEWORK.md` for all step content before building. All step text comes from `FRAMEWORK.md` — do not invent.

## Positioning

The tool is a **student companion**, not a self-management tool. The student opens it alongside their AI work (chat window, document, printout) and walks through V → Y. The tool **does not capture or store the AI output**; it just provides the structure and the questions.

The teacher's role is to review the **filter log** the tool exports, and to have the verbal-defence conversation the guide describes in Part 3. The tool is the artefact between the student and the teacher — it is not a graded submission, and it is not a worksheet the student completes alone before submitting.

The source framework states: *"VERIFY will not work as a student self-management tool... It is a teaching framework that requires a teacher who is present."* (Guide, Part 1, §1.3.) "Teacher present" here means present in the review and the conversation that follows the filter log, not present in the tool itself.

## Splash screen

Full-screen before tool starts:

- "VERIFY" large in `--font-display`, with the water-flow gradient applied (see Brand tokens section)
- Subheading: *"A framework for thinking with AI, not just using it."*
- Tagline (verbatim, companion model): *"A companion for thinking through AI output. Open this alongside your work and walk through six steps for examining what's in front of you."*
- Single CTA: "Begin"
- Small attribution at bottom: *"Sandra Robinson"* in uppercase tracking
- Below attribution, a quieter link: *"Read the Teacher Guide →"* pointing to the public repo at `https://github.com/bigwellaadmin-dev/verify` so it works whether the tool is opened from `file://`, an LMS iframe, or a hosted location.

## Layout

| Breakpoint | Layout |
|---|---|
| Desktop (≥1200px) | Two columns. Left pane (35%, sticky): student's pasted AI output. Right pane (65%): active VERIFY step. |
| Tablet (768–1199px) | Two columns at narrower ratio (40/60). Left pane sticky. |
| Mobile (<768px) | Single column. AI output collapses to expandable accordion at the top of the active step. |

## Persistent header (fixed)

- "Big Wella" wordmark, text only, top-left
- VERIFY step indicator: 6 letters in a row
  - Active: large, `--font-display`, coloured with `--color-{letter}`
  - Completed: coloured letter + green tick (colour and tick together — never colour alone)
  - Upcoming: `--color-muted`
  - Completed letters are clickable — navigate back, responses preserved within the session

## Each step screen (right pane)

1. Step letter — large, `--font-display`, `--color-{letter}`
2. Step name (e.g., "Validate the Task")
3. **In-one-sentence line** (verbatim from `FRAMEWORK.md`, italic, accent colour)
4. Guiding questions — each with a `<textarea>` and a short prompt label. Not required fields. No submit behaviour.
5. Back / Next — Next always enabled, never locked out.

## F step — toggle cards

Each of the 7 verbatim check questions is a card with a toggle switch.

- Toggling on reveals a one-line "What did you find?" `<input type="text">` beneath the question.
- Toggling off **preserves** the entered text (do not wipe). Re-toggling on shows it again.
- When all 7 toggles have been turned on at least once, the F letter in the header turns green (completion state). Toggling cards off after that point does NOT revert the F-green state — the student has demonstrated they engaged with all seven.

## Y step — reveal moment

Two parts:

1. Three guiding questions with textareas (same pattern as V / E / R / I)
2. Read-only summary panel labelled *"What you found across all six steps."* Renders:
   - Each step letter and name as a small heading
   - Each guiding question
   - The student's response below each question
   - For F: each of the seven check questions and the student's one-line "What did you find?" reflection beside each toggled one

**Rendering contract:** Iterate stored values, assign via `textContent` only. Never use `innerHTML`. The path through `DOMPurify` is unnecessary because `textContent` never parses HTML — and removing the DOMPurify hop keeps the code clearer about what is actually protecting against XSS (the choice of `textContent`).

## Export

"Export Filter Log" button at end of Y:

- Generates plain text: `VERIFY Filter Log — DD/MM/YYYY HH:mm` followed by each step name, each question, and the student's response.
- Uses Australian locale date format (DD/MM/YYYY) and 24-hour time.
- Attempts `navigator.clipboard.writeText()`. On rejection (file://, HTTP, blocked permission), falls back to selecting the text in a hidden `<textarea>` and showing a "Copy with ⌘C / Ctrl-C" prompt.
- Confirmation on success: *"Copied — paste into your LMS or email to your teacher."*
- Secondary "Print" button — triggers `window.print()` with the print stylesheet (see below).

## State management

All state in a single JS object in memory. No persistence of any kind. Page refresh intentionally resets. Banner near the export button reads: *"Your responses are not saved — export before closing."*

## Transitions

200ms ease, opacity fade only. No slides, no transforms on step changes.

```css
@media (prefers-reduced-motion: reduce) {
  /* Disable transitions entirely; show new step instantly. */
  * { transition: none !important; animation: none !important; }
}
```

## Accessibility checklist

- [ ] All inputs and buttons reachable by Tab
- [ ] Enter/Space activates buttons and toggles
- [ ] `aria-label` on all icon buttons and toggle switches
- [ ] `aria-live="polite"` on the step region (announces step changes)
- [ ] Focus ring always visible — never `outline: none` without a replacement
- [ ] Colour + icon/text together for all state indicators
- [ ] Contrast ratio ≥ 4.5:1 for all body text against its background
- [ ] `--color-muted` is used only for non-essential UI chrome, never for prose
- [ ] `prefers-reduced-motion` honoured
- [ ] Tool functions with JavaScript disabled? No — but a `<noscript>` block must explain why and link to the Teacher Guide.

## Print stylesheet

When printing:

- Hide header, step navigation buttons, and export controls
- Show all six steps and responses in full, linear sequence
- Page title at top: `VERIFY Filter Log — DD/MM/YYYY HH:mm`
- Black text on white, no background colours
- F step: render each check question with its toggle state and reflection
- Page break between major steps where natural
