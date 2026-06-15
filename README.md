# Word Reveal Battle

## Overview

Word Reveal Battle is a multiplayer word-guessing game played on a single device. One player becomes the Word Holder and enters a secret word. The remaining players take turns guessing words of the same length. Correctly matched letters in the correct positions are revealed on the board. Players earn points by revealing letters and guessing the final word.

---

## Features

* 3 or more players
* Multiple rounds
* Random Word Holder selection
* No repeated holders until all players have been holders once
* Easy and Hard modes
* Real-time scoreboard
* Duplicate guess prevention
* Dictionary validation
* Round timer
* Final leaderboard

---

## Game Setup

1. Enter number of players.
2. Enter player names.
3. Select number of rounds.
4. Select game mode:

   * Easy (Category Visible)
   * Hard (Category Hidden)
5. Start the game.

---

## Round Flow

### 1. Select Word Holder

A player is randomly selected as the Word Holder.

### 2. Enter Secret Word

The Word Holder enters:

* Secret Word
* Optional Category

Example:

```text
Category: Fruit
Word: FRUIT
```

### 3. Lock Word

The device is passed to the next player.

### 4. Guessing Phase

Guessers take turns entering words.

Example:

```text
Secret Word: FRUIT

Board:
_ _ _ _ _
```

Player Guess:

```text
SWEET
```

Result:

```text
_ _ _ _ T
```

---

## Scoring

| Action                       | Points |
| ---------------------------- | ------ |
| Reveal a new letter          | +10    |
| Correctly guess the word     | +50    |
| Holder survives entire round | +10    |

---

## Round End Conditions

A round ends when:

* A player correctly guesses the word.
* All letters are revealed.
* The timer expires.

---

## Validation Rules

### Players

* Minimum players: 3
* Player names cannot be empty.
* Player names must be unique.

### Secret Word

* Required.
* Only alphabetic characters allowed.
* Length must be between 3 and 15 characters.
* Automatically converted to uppercase.

Valid:

```text
FRUIT
MANGO
ELEPHANT
```

Invalid:

```text
FRUIT123
FRUIT!
APPLE PIE
```

### Dictionary Validation

* Secret word must exist in the built-in dictionary.
* Guesses must also exist in the built-in dictionary.
* Invalid words are rejected.

Example:

Valid:

```text
FRUIT
APPLE
MANGO
```

Invalid:

```text
ZXQWV
AAAAA
QWERT
```

Recommended Implementation:

* Store a built-in word list in JavaScript.
* Do not use external dictionary APIs.

### Guesses

* Must contain only letters.
* Must match the secret word length.
* Cannot be guessed more than once in the same round.

Example:

Secret Word:

```text
FRUIT
```

Valid Guess:

```text
SWEET
```

Invalid Guess:

```text
CAR
```

Reason:

```text
Length does not match.
```

### Duplicate Guesses

Already guessed:

```text
SWEET
```

Rejected:

```text
sweet
SWEET
Sweet
```

---

## Timer

* Default timer: 5 minutes per round.
* Round ends automatically when time expires.

---

## Leaderboard

Scores are updated after every turn.

Example:

| Player  | Score |
| ------- | ----- |
| Arun    | 80    |
| Ravi    | 60    |
| Aswin   | 50    |
| Karthik | 30    |

---

## Tie Breaker

If players have the same score:

1. Most correct word guesses.
2. Most letters revealed.
3. Shared winner.

---

## Winner

After all rounds are completed:

* Scores are sorted in descending order.
* The highest-scoring player is declared the winner.

