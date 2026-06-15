python -m streamlit run app.py# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input | Expected Behavior | Actual Behavior | Console Output / Error |
|-------|-------------------|-----------------|------------------------|
| | | | |
| | | | |
| | | | |

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.




## Answers
- ## 1. What was broken when you started?

When I first ran the game, the app looked like a normal Streamlit number guessing game, but the behavior was unreliable. The biggest issue was that the hints were backwards. For example, when the secret number was higher than my guess, the game told me to go lower instead of higher.

I also noticed a state bug where the secret number did not behave consistently during gameplay. Because Streamlit reruns the script after button clicks, the secret number needed to be stored in `st.session_state` so it would not reset during a round. Another issue was that some of the core logic was mixed directly into `app.py`, which made it harder to test and easier for bugs to hide.

| Input | Expected Behavior | Actual Behavior | Console Output / Error |
| Secret was 60, guess was 30 | Game should say “Go HIGHER!” because the guess was lower than the secret | Game said “Go LOWER!” | None |
| Secret was 87, guess was 0 | Game should say “Go HIGHER!” because 0 is below 87 | Game said “Go LOWER!” | None |
| App loaded after moving logic into `logic_utils.py` | Game should open normally and show the guessing screen | App crashed before the game could be played | `NotImplementedError: Refactor this function from app.py into logic_utils.py` |

## 2. How did you use AI as a teammate?

Used the AI to help explain why the game was giving the wrong hints and why the Streamlit app behaved differently from the pytest tests. One helpful suggestion was to move the core game logic into `logic_utils.py` so the functions could be tested separately from the Streamlit interface. That was correct because it made `check_guess()`, `parse_guess()`, `get_range_for_difficulty()`, and `update_score()` easier to verify with pytest.

One misleading part of the process was that the first test fix passed pytest, but the live app still gave the wrong hint. I learned that passing tests does not always mean the full app works if the tests do not match the app’s real behavior. I verified the final fix by running pytest and then manually testing the Streamlit game with Developer Debug Info open. 

## 3. Debugging and testing your fixes

Debugged the game by fixing one issue at a time instead of changing everything randomly. First, I fixed the hint logic so a low guess returns “Go HIGHER!” and a high guess returns “Go LOWER!” Then I fixed the refactor problem by fully implementing the helper functions in `logic_utils.py` instead of leaving `NotImplementedError` placeholders.

I verified the fixes in two ways. First, I ran `pytest -q` and confirmed that all automated tests passed. Then I ran the Streamlit app, opened Developer Debug Info, checked the secret number, and manually tested guesses that were too low, too high, and correct. The final live test worked because the game correctly showed the winning message and final score.

