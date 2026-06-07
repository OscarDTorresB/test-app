# quiz-cli

Project overview
----------------
quiz-cli is an interactive command-line quiz game built with Node.js ES Modules. It loads quiz questions from a local JSON file, prompts you through a terminal UI, tracks your score and progress, and shows detailed feedback and explanations after each answer. It's lightweight, dependency-free, and designed for learning JavaScript, Node.js, and general programming concepts while practicing in a fun way.

Setup instructions
------------------
Requirements
- Node.js 18 or newer installed on your machine.

Quick start (beginner friendly)
1. Clone or download the repository to your machine.
   - Example:
     - git clone <repository-url>
     - cd quiz-cli
2. (Optional) Install dependencies. This project is dependency-light and does not require external packages, so this step is usually not necessary:
   - npm install
3. Run the app:
   - npm start
   - or directly:
     - node index.js

Notes
- package.json sets "type": "module" so the code uses ES module syntax.
- The application reads questions from `data/questions.json`. You can edit that file to add or change questions.

Usage examples
--------------
Start the app:
```
$ npm start
```

Typical interactive flow (example):
- The app prints a welcome banner and then asks you to choose a category:
  - 1) JavaScript Basics
  - 2) Node.js Fundamentals
  - 3) General Programming
- Choose the number for the category (for example `1`).
- Choose how many questions to attempt (e.g., `3`, `5`, or `all` when available).
- Questions are shown one at a time with multiple-choice options:
  ```
  Question 1 / 3
  What is the result of `typeof []` in JavaScript?
  1) "array"
  2) "object"
  3) "list"
  4) "undefined"

  Select an option number: 2
  ```
- After answering, you immediately see feedback:
  - Correct / Incorrect message
  - The correct answer
  - A short explanation
  - Progress bar and percentage completion
- After the quiz finishes you get a final summary:
  ```
  Quiz Complete!
  Score: 2 / 3 (67%)
  Performance: Good work — keep practicing!
  
  Missed Questions:
  - Question #2: ...
    Your answer: X
    Correct answer: Y
    Explanation: ...
  ```
- Press Enter to exit or follow the prompt to play again (if available).

File structure
--------------
High-level overview of the repository layout:

- .DS_Store
  - macOS metadata file (not part of the application logic)
- package.json
  - Project manifest: start script, module type, and metadata
- index.js
  - Main entry point: loads questions, renders banner, handles category and quiz-length selection, runs the quiz loop, and prints final results
- data/questions.json
  - Quiz data store: categorized question sets with multiple-choice options, correct answer indexes, and explanations
- src/
  - src/colors.js
    - ANSI terminal color utilities for success, error, info, warning, highlight, and basic styles
  - src/input.js
    - Readline-based terminal input helpers: prompt, option selection, confirmation, and press-enter flow
  - src/quiz.js
    - Core quiz engine: shuffling, progress tracking, answer evaluation, score keeping, and final results display

Key features
------------
- Interactive CLI experience with colored terminal output and an ASCII banner
- Category-based question selection (e.g., JavaScript Basics, Node.js Fundamentals, General Programming)
- Configurable quiz length: choose a subset (3 or 5) or all available questions when supported
- Shuffled questions using a Fisher-Yates-like algorithm for varied playthroughs
- Per-question feedback with correct/incorrect messages and helpful explanations
- Progress visual feedback (progress bar and percentage)
- Final score summary with performance messages and review of missed questions
- Clean, modular code: separates input handling, quiz logic, and terminal styling
- Uses modern JavaScript (ES modules, async/await) and Node's built-in APIs (fs/promises, readline)

How it works (brief)
--------------------
- index.js loads `data/questions.json` and prompts the user to pick a category and a number of questions.
- The quiz engine (src/quiz.js) shuffles the selected questions and iterates through them, using src/input.js helpers to capture answers.
- After each submission the engine evaluates the answer, updates the score, shows an explanation, and advances progress.
- On completion, a final result summary and a review of missed questions are shown.

Adding or editing questions
---------------------------
Edit the `data/questions.json` file. Each question includes:
- question text
- an array of options
- index (or similar) for the correct answer
- an explanation for feedback

This makes it easy to extend the quiz with new categories and questions.

Enjoy practicing and learning with quiz-cli!
