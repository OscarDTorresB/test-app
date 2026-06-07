# Project overview

Quiz CLI is an interactive terminal-based quiz game designed to help you learn JavaScript and general programming concepts. You run it in your terminal, pick a category and how many questions you want, then answer multiple-choice questions. It tracks your score, shows explanations, and lets you review any incorrect answers at the end.

# Setup instructions

Requirements
- Node.js 18.0.0 or newer (ES module support).
- No external npm dependencies are required.

Quick start (beginner friendly)
1. Install Node.js (if you don't have it). Download from https://nodejs.org/ or use your system package manager.
2. (Optional) From the project root, run:
   ```
   npm install
   ```
   This is optional because the project uses only built-in Node.js modules. Running this will generate a lockfile if you prefer.
3. Run the quiz:
   ```
   npm start
   ```
   or directly:
   ```
   node index.js
   ```

Notes
- `npm start` runs `node index.js` for convenience.
- A test script is configured to run Node's built-in test runner (`node --test`), but the current repository snapshot does not include test files.

# Usage examples

Below are example interactions you will see in the terminal. Prompts and colors may vary depending on your terminal.

Starting the app:
```
$ npm start
Welcome to Quiz CLI!
Select a category:
  1) JavaScript Basics
  2) Node.js Fundamentals
  3) General Programming
Enter choice (1-3):
```

Selecting a category and number of questions:
```
Enter choice (1-3): 1
How many questions? (all/3/5): 3
Starting quiz: JavaScript Basics — 3 questions
```

Sample question flow:
```
Question 1/3:
What does 'const' do in JavaScript?
  a) Declares a block-scoped constant
  b) Declares a function
  c) Creates a global variable
  d) Replaces 'let'
Your answer (a-d): a

Correct! Explanation: 'const' creates a block-scoped variable whose binding cannot be reassigned.
Progress: [▓▓░░░░░░░░░] 33%
(press Enter to continue)
```

End-of-quiz summary and review:
```
Quiz complete!
Score: 2/3 (66%)
Message: Nice work — keep studying to boost your score!

Review incorrect answers? (y/n): y

Review - Question 3:
Question: Which event loop phase runs timers?
Your answer: 'check' — Incorrect
Correct answer: 'timers'
Explanation: The timers phase executes callbacks scheduled by setTimeout and setInterval.
(press Enter to continue)
```

Replay prompt:
```
Play again? (y/n): n
Thanks for playing Quiz CLI!
```

# File structure

High-level overview of repository contents:

- package.json
  - Project manifest (scripts, module type, Node engine requirement).
- index.js
  - Application entrypoint: startup, loading questions, handling category selection and replay loop.
- src/
  - src/colors.js
    - ANSI color styling helpers for terminal output (success, error, info, highlight).
  - src/input.js
    - Readline-based input utilities (prompts, selections, confirmations, pauses).
  - src/quiz.js
    - Quiz game logic: question selection, scoring, progress display, answer tracking, result rendering.
- data/
  - data/questions.json
    - Question bank organized by category. Each question includes text, options, answer index, and optional explanation.
- .DS_Store
  - macOS metadata file (not part of app logic).

# Key features

- Interactive category selection (JavaScript Basics, Node.js Fundamentals, General Programming).
- Choice of question count: all questions, 3, or 5 (when available).
- Randomized question order using Fisher–Yates shuffle for varied practice.
- Real-time scoring and progress feedback with a terminal progress bar.
- Colored terminal UI (success, error, warning, info, highlight) for clear feedback.
- Immediate answer validation and optional explanations after each question.
- End-of-quiz summary with a percentage score and a tailored performance message.
- Review mode to go over incorrect answers and reinforce learning.
- Clean separation of concerns: input handling, UI styling, and quiz logic are modularized.
