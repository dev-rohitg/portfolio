<!-- Copilot / AI agent instructions for the `portfolio` static site -->

# Purpose
Short, actionable guidance so an AI coding agent can be productive immediately in this repo.

## Big picture
- Type: Static portfolio website (HTML/CSS/JS) built from a Bootstrap template.
- Layout: Single-page + a few inner pages (`index.html`, `inner-page.html`, `portfolio-details.html`).
- Assets: All third-party libraries and the app code live under `assets/` (see `assets/vendor/`, `assets/css/`, `assets/js/`).
- Why: Template focuses on a fast-to-edit static portfolio; dynamic behavior is implemented in `assets/js/main.js` and styling in `assets/css/style.css`.

## Key files & directories (start here)
- `index.html` — main content and examples of markup patterns (nav, sections, projects).
- `assets/css/style.css` — site styles and responsive layout tweaks.
- `assets/js/main.js` — DOM helpers + all client interactivity (scroll, typed text, isotope, sliders).
- `assets/vendor/` — third-party libraries included in the template (AOS, Bootstrap, GLightbox, Swiper, Isotope, Typed.js, etc.).
- `forms/contact.php` — optional PHP endpoint used by the contact form; expects `assets/vendor/php-email-form/php-email-form.php` (pro-only library).

## Common patterns an agent should follow
- DOM helpers: `assets/js/main.js` uses `select()` and `on()` helpers — follow those selectors/classes when adding behavior.
- Animation/data attributes: AOS and Typed.js are wired via `data-` attributes in HTML; prefer adding attributes rather than rebinding code.
- Project items: Follow the `div.project` structure in `index.html` (image container `.projectImg`, description `.projectDesc`, links inside `#ProjLinks`) when adding new portfolio entries.

## Running & debugging locally
- Static preview: open `index.html` in the browser or use VS Code Live Server for quick feedback.
- Recommended (static assets + relative paths): run a local HTTP server from the repo root so relative imports behave correctly:

  - Using Python (works if Python installed):

    `python -m http.server 8000`

  - Using PHP (needed to test `forms/contact.php`):

    `php -S localhost:8000`

  - Or use VS Code Live Server extension to serve the workspace folder.

Debugging: use the browser DevTools console. JS is not minified; changes to `assets/js/main.js` will reload on page refresh.

## Integration notes / gotchas
- Contact form: the template refers to a pro-only `php-email-form` library. `forms/contact.php` will die if `assets/vendor/php-email-form/php-email-form.php` is missing — treat the contact form as optional or add SMTP credentials if using SMTP.
- External CDNs: Google Fonts and Font Awesome are loaded from CDN in `index.html`; offline edits may require adding fallback fonts/icons.
- Do not modify files under `assets/vendor/` unless updating a library deliberately — these are third-party assets.

## Example tasks and how to approach them
- Add a new project entry: copy the existing `.project` block in `index.html`, update the image, description and add links under `#ProjLinks`.
- Change the hero typed text: edit the `data-typed-items` attribute on the element with class `.typed` in `index.html`.
- Add a new JS behavior: prefer appending small helper functions to `assets/js/main.js` following the existing `select()` / `on()` pattern and initialize on `window.load`.

## Where to look for regressions
- Visual regressions: `assets/css/style.css` and Bootstrap defaults. Check header/nav styles and responsive rules (see `#header` and `#main` CSS rules).
- Behaviour regressions: `assets/js/main.js` (scroll activation, mobile nav toggle, portfolio filtering via Isotope).

If anything here is unclear or you want more examples (e.g., a sample PR that adds a new project or a safe way to enable contact emails), tell me which area to expand and I will iterate.
