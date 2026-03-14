# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
  - Simple UI, tell user how many guesses they have, has an input box to type guess, has two buttons to submit guess and start a new game, has a toggle to show hint.
- List at least two concrete bugs you noticed at the start  
  (for example: "the secret number kept changing" or "the hints were backwards").
  - Hints were backwards (I guessed a number and it said 'GO LOWER' when I actually needed to 'GO HIGHER')
  - New game button is not creating a new game to start over (Expected it to clear the input and reset the game but it does not do anything)
  - Normal level has range 1-100 while Hard level has range 1-50 (does not really make sense as it would be expected for hard mode to be 1-100 and normal to be 1-50)
  - Easy mode range is 1-20 but the secret number was 44 (does not make sense again as the number should stay within the range of 1-20)
  - Message at top always says "Guess a number between 1 and 100" regardless of level chosen
  - Game ended after certain number of attempts but still says I have one attempt remaining (not counting first attempt as an attempt)
    - Reveals secret number even if one attempt is still left + submitting that last attempt (to make it 0) reveals a 'Game Over' message
    - First guess is not counting as attempt 1
    - Attempts only counts every other attempt unless "Submit Guess" button is clicked multiple times after one input has been given (Expected to count every guess as an attempt)
  - Guessing a number that is "Too High" rewards points instead of subtracting on every other "Too High" guess

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
  - I used Claude Code and ChatGPT. I primarily used Claude Code to fix bugs and I used ChatGPT to understand the code in app.py
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
  - One suggestion it gave that was correct was making the "New Game" button work as intended. The initial code skipped resetting some settings when the button was clicked which is why the button did not necessarily simulate a new game. Claude Code added in the missing states and reset them to their initial value which caused the New Game button to work as intended (such as status, history, score, feedback, and also generated a new game id to start a fresh game). I verified this result by clicking the "New Game" button on the app and verified if the input field was cleared as well as if the above settings were empty / 0.
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).
  - One suggestion that was misleading was that Claude Code initially had some trouble fixing the incorrect counting of attempts. At first, when the user entered a guess, the app would not count that initial guess as 1 attempt. The fix it gave was to refactor many lines of code which did not seem ideal for such a simple issue. I then created a new chat and described the issue I was facing in more detail and it was able to fix the issue with one line which was adding a simple rerun command towards the end of the file. However, this line lef to another bug which was that the hints were no longer showing and the secret number was not revealed when the game was over. To fix this, Claude suggested to sav the feedback in a variable and display it after the rerun() is called so that the messages would persist / show even if the app was rerun.
---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
- What change did you make that finally gave the game a stable secret number?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
