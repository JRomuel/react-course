# React Course

Learning project for React fundamentals. Each top-level `.html` file is a **standalone**
page — there is no bundler, build step, or `package.json`. React, ReactDOM, and Babel are
loaded directly from the `supersimpledev` CDN, and JSX is written inline inside
`<script type="text/babel">` tags, transpiled in-browser.

Served via XAMPP (`htdocs/react-course`), so pages are opened through Apache
(e.g. `http://localhost/react-course/chatbot.html`), not a dev server.

## Files

- `react-basics.html` — minimal JSX/render example.
- `chatbot.html` — small chat UI (`ChatInput`, `ChatMessage`, `ChatMessages`, `App`)
  using `React.useState` and the `Chatbot` global from `supersimpledev/chatbot.js`.
- `robot.png`, `user.png` — avatar images referenced by `chatbot.html`.

## Conventions

- Keep the CDN `<script>` include order: react.js → react-dom.js → (feature lib, e.g.
  chatbot.js) → babel.js → the inline `text/babel` script.
- Components are plain functions in the inline script block, PascalCase, one
  responsibility each (e.g. `ChatInput` only handles the input + send button).
- Use `React.useState`, not class components.
- Always pass a stable `key` when rendering lists (see `ChatMessages`).
- New pages should follow the same self-contained, no-build pattern unless the user
  explicitly asks to introduce tooling (npm, a bundler, a framework CLI).

## Coding principles

Apply these to every change, not just new files:

- **DRY** — don't copy-paste markup/logic across components or files; extract a
  function or component instead. But don't fight three near-identical lines into an
  abstraction that doesn't pay for itself.
- **KISS** — prefer the plain, obvious React/JS solution over a clever one. This is a
  learning codebase; clarity beats abstraction.
- **YAGNI** — don't add state, props, or config for hypothetical future lessons.
  Build only what the current page needs.
- **Single responsibility** — each component does one thing (input handling, message
  list, single message render, etc.); split components when they start doing two.
- **No dead code** — remove unused variables, props, and commented-out JSX rather
  than leaving them in place.
- **Readable over terse** — descriptive names (`chatMessages`, `setInputText`) over
  abbreviations; this mirrors the existing style in `chatbot.html`.
