# quiz-cli

## Project overview
quiz-cli is a simple, terminal-based interactive quiz game built with Node.js ES Modules. It lets you choose a quiz category, pick how many questions you want to answer, and then walks you through questions one-by-one in the terminal. The app tracks your score, shows per-question feedback, displays a progress bar, and provides a final results summary with a review of any incorrect answers.

This project is intended as an educational example that demonstrates modern JavaScript features (ES modules, async/await, classes) and simple CLI interactions.

## Setup instructions
Requirements:
- Node.js 18.0.0 or newer (package.json declares "type": "module" and requires Node >= 18).

Getting started:
1. Clone the repository:
   ```
   git clone <repo-url>
   cd quiz-cli
   ```
2. No external dependencies are required — the app uses built-in Node modules. If you prefer, you can still run:
   ```
   npm install
   ```
   (There are no runtime packages to install in the provided snapshot.)
3. Make sure the data file is present: `data/questions.json`. This file contains the quiz categories and questions used by the app.
4. Run the app:
   ```
   npm start
   ```
   or directly:
   ```
   node index.js
   ```

The app runs entirely in the terminal and is interactive.

## Usage examples
When you run the app, you will be prompted step-by-step. Example interaction (user input shown after prompts):

1. Start banner and category selection:
   ```
   Welcome to quiz-cli!

   Select a category:
   1) JavaScript Basics
   2) Node.js Fundamentals
   3) General Programming

   Enter number: 1
   ```

2. Choose number of questions:
   ```
   How many questions would you like? (1 - 5): 3
   ```

3. Answer questions by entering the option number:
   ```
   Question 1/3
   What is the output of: typeof [] ?
   1) "array"
   2) "object"
   3) "undefined"

   Enter number: 2

   Correct! ✅
   (Press Enter to continue)
   ```

4. After all questions, a results summary will be shown:
   ```
   Quiz complete!
   Score: 2 / 3 (66%)

   Review of incorrect answers:
   - Question: What is the output of: someQuestion?
     Your answer: option 1
     Correct answer: option 3
     Explanation: [...explanation text...]
   ```

5. Replay prompt:
   ```
   Play again? (y/n): n
   Thanks for playing!
   ```

Notes:
- Select options by typing their number and pressing Enter.
- You may be prompted to press Enter to proceed between questions.
- The app shuffles questions each run, so expect different orders.

## File structure
High-level overview of the repository:

- package.json
  - Project metadata, declares "type": "module" and scripts:
    - start: `node index.js`
    - test: `node --test` (no tests included in snapshot)
  - Node engine requirement: >= 18.0.0

- index.js
  - Main entry point.
  - Loads questions from `data/questions.json`.
  - Orchestrates the CLI flow: category selection, question count, instantiating the Quiz, running quiz loop and replay logic.

- src/colors.js
  - ANSI color and style helper utilities used to colorize terminal output (success, error, info, highlight, etc).

- src/input.js
  - Readline-based input helpers.
  - Renders numbered options, validates user selections, handles yes/no prompts and press-enter pauses.

- src/quiz.js
  - Core quiz logic.
  - Quiz class responsibilities:
    - Shuffles questions (Fisher-Yates).
    - Tracks current index, score and answers.
    - Renders progress bar and question prompts.
    - Evaluates answers, shows feedback, and prints final results + incorrect-answer review.

- data/questions.json
  - Quiz content (categories and questions).
  - Category example structure:
    - id: "javascript"
    - name: "JavaScript Basics"
    - Each question object includes:
      - question (string)
      - options (array of strings)
      - answer (index or value depending on schema)
      - explanation (optional string)

- .DS_Store
  - macOS metadata file (not part of application code).

## Key features
- Interactive terminal UI with colorful ANSI output.
- Category-based quiz selection.
- Configurable question count per session.
- Questions are shuffled for varied runs.
- Progress bar and per-question feedback.
- Final score summary with performance message.
- Review of incorrect answers with the correct choices and explanations.
- Simple replay loop so you can play multiple rounds without restarting the program.

Enjoy learning and testing your knowledge with quiz-cli!
