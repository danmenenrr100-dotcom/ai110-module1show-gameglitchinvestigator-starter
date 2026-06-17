# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

- [ ] Describe the game's purpose.
- [ ] Detail which bugs you found.
- [ ] Explain what fixes you applied.

## 📸 Demo Walkthrough

Describe your fixed game in numbered steps so a reader can follow along without watching a video:

1. <!-- Describe this step -->
2. <!-- Describe this step -->
3. <!-- Describe this step -->
4. <!-- Describe this step -->
5. <!-- Add more steps as needed -->

**Screenshot** *(optional)*: <!-- Insert a screenshot of your fixed, winning game here -->

## 🧪 Test Results

```
# Paste your pytest output here, e.g.:
# pytest tests/
# ========================= X passed in 0.XXs =========================
```

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, describe the Enhanced UI changes here — a screenshot is optional]

## Documenting

- The game is a Streamlit number guessing game where the player tries to guess a secret number within a limited number of attempts.
-  I found several bugs: the hints were backwards, the Streamlit state was unreliable, and some refactored functions in `logic_utils.py` still raised `NotImplementedError`.
-  I fixed the game by storing the secret number in `st.session_state`, correcting the high/low hint logic, moving core game logic into `logic_utils.py`, and verifying the repairs with pytest and live Streamlit testing.

## 📸 Demo Walkthrough

1. The user runs the app with `python -m streamlit run app.py`.
2. The Streamlit game opens and displays the guessing interface.
3. The user opens Developer Debug Info to view the secret number for testing.
4. The user enters a guess lower than the secret number.
5. The game correctly tells the user to go higher.
6. The user enters a guess higher than the secret number.
7. The game correctly tells the user to go lower.
8. The user enters the exact secret number.
9. The game displays a winning message and shows the final score.
10. The secret number stays the same during the round and only changes when a new game starts.

## Test Results
- 3 passed in 0.02s 
- command used for test results (cat test_results.txt)  