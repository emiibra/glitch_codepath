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

- [ ] Describe the game's purpose. eb: Purpos is to document the guessings of the user of a secret key, and guiding them trough higher lower until number is reach, while documenting the number of tries, the tries, the score
- [ ] Detail which bugs you found.eb:bugs: 1) higher and lower not working correctly, 2)history only shows up the logs after first attempt, 3)score start deducting 5 after first attempt, 4)attepmts left only start substracting after first attempt
- [ ] Explain what fixes you applied. 1) i delete the logic when changing the type of guess when the attempt is even, i left it on int, also i change the logic of check guess, it was the opposite, is higher go lower, and if is lower go higher

## 📸 Demo

- [ ] [Insert a screenshot of your fixed, winning game here]

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, insert a screenshot of your Enhanced Game UI here]
