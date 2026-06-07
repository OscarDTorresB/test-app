# quiz-cli

## Project overview
quiz-cli is a simple, interactive terminal quiz game that helps you learn JavaScript, Node.js, and general programming concepts. You run it from your terminal, pick a category and how many questions you want, and answer multiple-choice questions one by one. It requires no external dependencies and is built using only Node.js standard APIs.

## Setup instructions

Requirements
- Node.js 18 or newer.

Steps to run
1. Clone the repository:
   ```
   git clone <repo-url>
   cd quiz-cli
   ```
2. (Optional) Create a lockfile by running:
   ```
   npm install
   ```
   The app does not require external packages, but this step is useful if you want a lockfile.
3. Start the quiz:
   ```
   npm start
   ```
   Or run directly with Node:
   ```
   node index.js
   ```

Notes
- The project is an ES module app (`"type": "module"` in package.json).
- Quiz content lives in `data/questions.json`. You can add or edit questions there without changing application code.
- A basic test command exists:
  ```
  npm test
  ```

## Usage examples

When you run the app (with `npm start` or `node index.js`) it guides you through a session. Example interaction:

1. Welcome banner appears.
2. Choose a category by entering its number:
   ```
   Pick a category:
   1) JavaScript Basics
   2) Node.js Fundamentals
   3) General Programming
   Enter number: 1
   ```
3. Choose how many questions to answer (type a number):
   ```
   How many questions would you like? (1-10): 5
   ```
4. Answer each question by typing the option number:
   ```
   1/5  What does `===` mean in JavaScript?
   1) Assignment
   2) Strict equality
   3) Structure
   Enter number: 2
   Correct! ✅
   ```
5. At the end you'll see a summary:
   ```
   Quiz complete!
   Score: 4/5 (80%)
   Performance: Great job! You have a solid understanding.
   ```
6. If any answers were incorrect, the app displays them with the correct answer and optional explanation:
   ```
   Review - Incorrect answers:
   Q: What is the purpose of `node:fs/promises`?
   Your answer: Synchronous file read
   Correct answer: Asynchronous file operations with promises
   Explanation: `node:fs/promises` provides promise-based file system methods.
   ```
7. The app prompts to play again or exit.

These are illustrative lines — exact wording and messages may vary slightly in the live CLI.

## File structure

High-level overview of the repository contents:

- package.json
  - Project manifest, scripts and Node.js engine requirement.
- index.js
  - Main CLI entry point. Loads question data, renders the banner and controls the quiz flow.
- src/
  - colors.js
    - ANSI color helpers used to style terminal output (success, error, info, dim, highlight).
  - input.js
    - Readline-based utilities for prompting text, selecting numbered options, yes/no confirmation, and pause.
  - quiz.js
    - Quiz engine (shuffling, progress, scoring, tracking incorrect answers and rendering results).
- data/
  - questions.json
    - Quiz content organized into categories. Each entry contains questions, multiple-choice options, the correct answer, and optional explanations.
- .DS_Store
  - macOS metadata file (not part of the application logic).

## Key features

- Interactive CLI gameplay: Answer multiple-choice questions directly in the terminal.
- Multiple categories: Includes JavaScript Basics, Node.js Fundamentals, and General Programming.
- Question shuffling: Questions are randomized each run to keep practice fresh.
- Progress tracking: Shows textual progress and question count during the quiz.
- Score and performance feedback: Final score percentage and a tailored performance message.
- Answer review: Incorrect answers are collected and shown at the end with correct responses and explanations (when available).
- No external dependencies: Uses only Node.js built-in modules and ANSI escape codes for colors.
- Modular code: Input handling, color styling, and quiz logic are separated for clarity and easy maintenance.
