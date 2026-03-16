# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the secret number kept changing" or "the hints were backwards").

  1)I expected when submit a number be able to use the hint to go either higher or lower, which wasn't working properly, it was doing the opposite never leading to the rigth answer.
   
  2)I expected to start from the current attempt number per the difficulty, but instead only resets to correct attempt number, when start new game is clicked, if not it always start in the wrong attempt, a number below of correct.

  3)I expected when clicking new game, it will restart the game, but nothing besides changing the new key is different.

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

1)I used cursor ai, and it suggested me the logic was on the conditional, which i checked and it was the opposite logic, when i changed it worked

2)Ai suggested i change the status when clicling new game to retes all the states like score, attempt, history. While the suggestion was correct, i decided intead of just changing the state inside new game logic, i added a function which i use in the new game function, then it worked fine

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

1)**Error:** I had a bug where clicking “New Game”. The attempts and secret looked okay, but the score didn’t reset the way I expected, and I realized I hadn’t really thought through what “reset” should mean for the score.  
   Fix / How I tested (manual): After talking it through, I noticed I never added clear score reset logic for a new round, so the score was just carrying over. I added logic in my reset helper to control whether the score should reset or be kept, and then manually started several new games in a row to see if the score and other state matched the behavior I wanted. Once I saw consistent behavior across multiple new games, I felt confident the bug was gone.

2)**AI and tests:** AI helped me think about where bugs might be hiding, like off‑by‑one issues in the attempts counter or places where `session_state` might not be updated before the UI shows values. Even though it suggested some ideas, I still relied on my own manual tests to confirm if they were actually correct. 

---

## 4. What did you learn about Streamlit and state?

- In your own words, explain why the secret number kept changing in the original app.
- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
- What change did you make that finally gave the game a stable secret number?
1) In the original app, the secret number was being generated in normal code that ran every time Streamlit reran the script. Since Streamlit re-executes the whole file on almost every button click, that meant a new random number was picked over and over again, so the “secret” didn’t actually stay the same across guesses.

2)I’d tell a friend that Streamlit kind of “starts the file from the top” whenever you interact with the app, so regular variables get reset each time. `st.session_state` is like a little backpack the app carries between reruns, where you can stash values you want to keep, like the secret number, attempts, score, and history. 

3) The key change was to only set the secret number once, inside a check like `if "secret" not in st.session_state:`, and then always read `st.session_state.secret` instead of calling `random` again. Once I moved the secret into session state and stopped regenerating it every run, it finally stayed the same until I explicitly started a new game.
---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.

1)One habit I want to keep is slowing down enough to write out what I expect the app to do before I touch the code. When I compared “what I think should happen” to “what actually happens,” it was way easier to spot off‑by‑one errors and weird state issues. 

2) Next time I use AI on a coding task, I want to treat its answers more like suggestions to test, not instructions to follow blindly. In this project, a couple of ideas were slightly off or incomplete until I combined them with my own understanding and manual testing.

3)This project made me see AI‑generated code as a starting point, not a finished product.