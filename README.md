# quiz-cli

An interactive command-line quiz game for learning JavaScript and Node.js fundamentals.

## Project overview

Quiz CLI is a Node.js ES module-based command-line application that presents multiple-choice programming questions in an interactive terminal experience. It supports category selection, question-count selection, answer validation, score tracking, progress display, and post-quiz review of incorrect answers. The app uses only built-in Node.js APIs and colorful ANSI terminal output for an engaging, dependency-free experience.

## Key features

- Interactive CLI quiz with colorful terminal output
- Category-based question selection from structured JSON data
- Question count selection for shorter or full runs
- Randomized question order using Fisher–Yates shuffle
- Immediate correctness feedback with explanations
- Progress bar and question counter during gameplay
- Final score summary with performance message and emoji
- Review screen for missed questions with correct answers
- ES module architecture using built-in Node.js APIs only

## Requirements

- Node.js 18.0.0 or newer
- No third-party npm packages are required

## Installation

1. Clone the repository:
   - git clone <repository-url>

2. No external dependencies are declared in `package.json`, so `npm install` is not required for runtime functionality. You may run `npm install` if you want to create a lockfile, but it is not necessary to run the app.

Notes:
- The project uses ES modules via `"type": "module"` in `package.json`.
- The executable entrypoint is `index.js`.
- Questions are stored in `data/questions.json`.

## Usage

Start the quiz:

- npm start
  - This runs `node index.js` and launches the interactive terminal quiz.
- Or run directly:
  - node index.js

Typical run flow:
1. The app clears the terminal and displays a banner.
2. User chooses a category from the JSON question bank.
3. User chooses how many questions to answer (options depend on category size, e.g. all, 3, or 5).
4. Each question is displayed with numbered multiple-choice options.
5. Answers are evaluated immediately and feedback is shown (correct/incorrect and explanation).
6. At the end, results and a review of incorrect answers are displayed.
7. The user can choose to play again.

Testing:
- npm test
  - `package.json` defines `npm test` as `node --test`, but no test files are present in the repository snapshot.

## Usage example (commands)

- Start via npm:
  - npm start

- Start directly:
  - node index.js

The interactive prompts will guide you through selecting a category and number of questions, answering each multiple-choice question, and viewing results.

## Project structure

High-level overview of key files and purpose:

- .DS_Store
  - MacOS filesystem metadata file; not relevant to application logic.
- package.json
  - Project manifest and npm scripts (defines `start` and `test` scripts, Node 18+ engine requirement).
- index.js
  - Main CLI entrypoint that loads questions and runs the interactive quiz flow. Orchestrates the application lifecycle, renders the banner, prompts user, runs quiz loop, and handles retry/exit.
- data/questions.json
  - Question bank organized by category (three categories: JavaScript Basics, Node.js Fundamentals, and General Programming). Each category contains five questions with options, answer index, and explanations.
- src/colors.js
  - ANSI color helper utilities for terminal styling (wrappers like success, error, info, warning, highlight, dim).
- src/input.js
  - Readline-based input helpers for prompts, selection, confirmation, and pause handling (promise-based wrappers).
- src/quiz.js
  - Quiz game class and scoring/progress/result rendering logic (shuffle, current tracking, progress calculation, answer checking, result aggregation, and summary output).

Example tree (informational):

- package.json
- index.js
- data/
  - questions.json
- src/
  - colors.js
  - input.js
  - quiz.js
- .DS_Store

## Scripts

Defined in `package.json`:

- start
  - Runs the CLI: node index.js
- test
  - Runs Node's test runner: node --test
  - Note: No test files are present in the repository snapshot.

## Data model

- `data/questions.json` schema:
  - categories: array of category objects
    - name: string
    - questions: array of question objects
      - question: string
      - options: array of strings
      - answer: numeric index of correct option
      - explanation: string

## Notes

- The app is written as ES modules and uses built-in Node.js modules only (e.g., `fs/promises`, `url`, `path`, `readline`).
- The entrypoint uses a shebang line for direct CLI execution and reads question data from the filesystem at runtime.
- Errors are handled with a catch block that prints a colored error message and exits with status 1.
- No third-party packages or external runtime dependencies are required.