# Bollywood Feud · Diwali Edition

A Bollywood-themed **survey game show** for Diwali night: two teams race to guess the most popular answers. It has a host, survey-style answer boards, three strikes, steals and a **Fast Money** finale, all wrapped in diyas, marigold garlands, rangoli and fireworks.

**Play it:** https://jitenruparelia-rgb.github.io/bollywood-feud/

It's one self-contained `index.html` file. No install and no build step. It also works offline: download the file and double-click it.

## How a game works

The game follows the classic TV survey-show format:

1. **Face-off.** One player from each team buzzes in. The host reveals any answer they hit, then picks which team plays.
2. **Play.** The playing team names answers one at a time. Correct answers flip over and their points go into the round bank.
3. **Three strikes.** After three wrong answers, the other team gets **one** guess to steal the whole bank.
4. **Round win.** Clear the board, or win the steal, and the bank is yours.
5. **Fast Money** (optional). The winning team sends two players for five rapid-fire questions: 20 seconds for Player 1, 25 for Player 2. Together they must reach the target, which defaults to 200.

### Game length and points

Choose 4, 6, 8, 10, 12 or 15 rounds. The default is 10, about 45 minutes with Fast Money. Every board adds up to 100, like a survey of 100 people. As in classic TV game shows, later rounds multiply every answer:

| Rounds | ×1 | ×2 | ×3 |
|---|---|---|---|
| 4 | 1–2 | 3 | 4 |
| 6 | 1–2 | 3–4 | 5–6 |
| 8 | 1–4 | 5–6 | 7–8 |
| 10 (default) | 1–4 | 5–7 | 8–10 |
| 12 | 1–4 | 5–8 | 9–12 |
| 15 | 1–5 | 6–10 | 11–15 |

A tie at the end triggers a sudden-death board at triple points.

### Mostly easy, never repetitive

About half of every game is easy questions anyone can play, with some medium ones and roughly one hard question per 10 rounds, in a random order. Nothing on screen says which is which.

No two questions in a game share an answer, so you won't hear "DDLJ" on two different boards. Fast Money, Skip and sudden death follow the same rule. Back-to-back games also avoid recently played questions, so about five 10-round games in a row get all-new questions.

The bank has 78 boards and 23 Fast Money questions in three kinds:

- **Easy** boards need zero Bollywood knowledge: Diwali parties, Indian weddings, aunty questions, dance moves.
- **Medium** boards are for people who've seen a few films: the Khans, SRK movies, villains, train scenes.
- **Hard** boards are for true filmi fans: composers, remakes, the Oscars, golden-era actresses, iconic dialogues.

**Newcomer hints** add a short explanation under each question, and Hindi titles and dialogues show an English translation when revealed.

## Typing in answers

During the face-off, play and steal, a typing box sits at the bottom of the screen. Type what the player says and press **Enter**:

- **On the board:** the tile flips. If it was a close match, such as a misspelling or a different wording, a pop-up shows the real answer and what was said.
- **Not on the board:** a big red X appears with the guess underneath. During play that counts as a strike. During a steal it means the steal fails.
- **Already revealed:** a pop-up says so, and the team doesn't get a strike.

Matching accepts small typos ("amitab bachan"), nicknames ("SRK", "Big B"), other spellings ("laddu" for Ladoo) and similar phrasings ("are you married yet"). Unrelated answers that only share one word, like "chicken nuggets" for Chicken tikka masala, don't count. If the game ever gets one wrong, press **Undo**.

Press **Esc** to leave the typing box and use the single-key shortcuts.

## Hosting tips

- **One screen:** the host controls sit along the bottom. Click the board tiles or use the keyboard.
- **Two screens (recommended):** click **Host screen** to open a private window with every answer. Put the main window on the TV, keep the host window on your laptop, and press **H** on the TV to hide the controls. Both windows stay in sync.
- **Paper:** **Answer sheet** opens a printable list of this game's answers.
- The game saves after every action, so refreshing never loses the score. **Undo** (Z) reverses any mistake.
- **Rematch** picks questions you haven't just played.

### Keyboard shortcuts

| Key | Action |
|---|---|
| Type + Enter | Check an answer against the board |
| Esc | Leave the typing box to use the keys below |
| Space | Reveal the question |
| 1–8 | Reveal an answer |
| X | Strike (in a face-off, a wrong-answer buzzer) |
| A / B | Team 1 / Team 2 play |
| F | Steal fails |
| R | Reveal remaining answers after a round |
| N or Enter | Next round |
| S | Skip to a different board before any answer is shown |
| Z | Undo |
| H | Hide or show controls on the TV |
| M | Sound on or off |
| ? | Help |

In Fast Money, type what the player says and press Enter. The game suggests the matching answer and buzzes on a repeat of Player 1's answer. The host can fix any match with **Fix a match** before the totals are final.

## Adding your own questions

Open `index.html` and find `const BOARDS` near the bottom. Each board looks like this:

```js
{tier:'easy', q:"Name something you'd see at a Diwali party",
 hint:"A line of help for newcomers.",
 a:[["Diyas / candles",28,"optional note shown under the answer",["lamps","diya"]],["Sweets (mithai)",24], ...]},
```

- `tier` is `easy`, `medium` or `hard`.
- Answers go from most to least popular. Their points should add up to 100.
- Up to 8 answers fit on a board.
- The optional last list holds other answers to accept when typed, like nicknames or other spellings. Use `null` for the note if an answer has alternates but no note.

Fast Money questions live in `const FASTMONEY`. Each answer can list other spellings the host might type, for example `["Shah Rukh Khan",36,["srk","shahrukh"]]`.

Survey values are the author's best guesses for party fun, not results from a real poll.

Happy Diwali! 🪔
