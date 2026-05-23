# VERIFY — interactive companion

A single-file HTML companion to the VERIFY framework. A student opens it alongside their AI work and walks through V → Y, producing a filter log for their teacher to review.

## How to run it

Open `index.html` in any modern browser. There is no build step, no install, no server. Double-click the file or drag it into a browser tab.

For LMS deployment (Moodle, Canvas, school portals), upload `index.html` to your file storage and link or iframe-embed it. The Content Security Policy allows embedding in any origin.

## What it does

- Walks a student through V → E → R → I → F → Y in a single browser tab
- Lives **alongside** the student's actual work — the AI output stays in its native context (chat window, document, printout); the tool does not capture or store it
- F is rendered as seven toggle cards with reflection inputs (questions verbatim from Sandra Robinson's source)
- Y reflects the student's V–F responses back to them before asking the three Y questions
- Exports a plain-text filter log to clipboard or print — this is the artefact the teacher reviews

## What it doesn't do

- Save anything. Refresh clears all state. This is deliberate.
- Track anything. No analytics, no telemetry, no cookies, no localStorage.
- Send anything to a server. There is no server.
- Phone home for fonts. DM Serif Display and Inter are bundled under `tool/fonts/` (SIL Open Font Licence). The page loads with zero third-party requests.
- Replace the teacher. See [`../skill/README.md`](../skill/README.md) for the recursive-honesty note that applies here too.

## Browser support

Chrome, Firefox, Safari current versions. Tested at desktop, tablet, and mobile breakpoints. Honours `prefers-reduced-motion`.

## Accessibility

- WCAG 2.1 AA contrast for all body text
- Keyboard-navigable (Tab through fields, Enter/Space activates buttons and toggles)
- `aria-live` on the step region announces step changes to screen readers
- Focus rings visible at all times
- Colour is never the sole indicator of state (completion has both colour and a tick)

## If you adapt it

The CC BY 4.0 licence permits adaptation. If you change the framework content, the tagline, or the teacher-led framing, please make that explicit in your adaptation. The framework text is canonical to Sandra Robinson; the tool implements one rendering of it.

---

*Sandra Robinson · Big Wella · 2026 · Licensed CC BY 4.0*
