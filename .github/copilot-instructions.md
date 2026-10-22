# Repository instructions

## Build, test, and lint

The project is a standalone static page. There is no package manager, build step, test runner, or configured linter. Open `index.html` directly in a browser to run it; no server or dependencies are required.

For a browser smoke test, verify that answer buttons are keyboard reachable, correct and incorrect answers show distinct feedback, the score changes only for correct answers, all ten questions can be completed, and the results screen and replay action work. There is no automated single-test command.

## Architecture

`index.html` contains the complete application: semantic page markup, inline CSS, quiz content, and vanilla JavaScript. The page is intentionally self-contained.

The `questions` array is the source of quiz content. Each entry has a prompt, four answer strings, a zero-based `correct` answer index, and a fact shown as answer feedback. `renderQuestion()` updates the prompt, progress, and answer buttons; `chooseAnswer()` locks the current question, updates the score when appropriate, and presents feedback; `showResults()` selects the score-based reaction; `restartQuiz()` resets the quiz.

## Project conventions

- Keep the app dependency-free and self-contained in `index.html` unless the project requirements explicitly change.
- Add or edit questions using the existing `prompt`, `answers`, `correct`, and `fact` shape. Keep `correct` aligned to the matching zero-based answer position.
- Keep visual changes aligned with the CSS custom properties in `:root` and the `prefers-color-scheme: light` override. Add colors as theme tokens so both light and dark themes remain legible.
- Preserve the accessibility patterns: native buttons for answers and actions, visible keyboard focus, a labelled answer group, live feedback, and the progress bar's updated `aria-valuenow`. Keep reduced-motion handling when adding animations.
- Preserve quiz state transitions and focus behavior when changing question navigation, answer feedback, results, or replay.
