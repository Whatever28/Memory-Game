# Documentation for Memory Game Code

## Overview
This code implements a memory-matching game where players flip cards to find matching pairs. The game includes a timer, move counter, and win detection logic. It dynamically generates the game board and handles user interactions.

---

## Key Components

### 1. Selectors (`selectors`)
This object contains references to essential DOM elements for the game:
- **`boardContainer`**: The container holding the game board.
- **`board`**: The game board element.
- **`moves`**: Displays the number of moves made.
- **`timer`**: Displays elapsed game time.
- **`start`**: The start button.
- **`win`**: The element that displays the victory message.

### 2. State (`state`)
Tracks the current state of the game:
- **`gameStarted`**: Boolean indicating if the game has started.
- **`flippedCards`**: Number of currently flipped cards.
- **`totalFlips`**: Total number of card flips.
- **`totalTime`**: Total elapsed game time in seconds.
- **`loop`**: Reference to the timer interval.

---

## Functions

### a. Utility Functions
#### `shuffle(array)`
Shuffles the input array using the Fisher-Yates algorithm.
- **Parameters**:
  - `array`: An array of items to shuffle.
- **Returns**: A new array with items in random order.

#### `pickRandom(array, items)`
Selects a specified number of random items from the input array.
- **Parameters**:
  - `array`: Source array.
  - `items`: Number of items to select.
- **Returns**: An array of randomly selected items.

### b. Game Setup
#### `generateGame()`
Generates the game board with shuffled cards.
- **Logic**:
  1. Reads board dimensions from a data attribute.
  2. Ensures dimensions are even.
  3. Picks random emojis and duplicates them to form pairs.
  4. Shuffles the pairs and creates HTML for the cards.
  5. Replaces the existing board with the new one.
- **Throws**: An error if dimensions are not even.

### c. Game Logic
#### `startGame()`
Starts the game by:
- Setting `gameStarted` to `true`.
- Disabling the start button.
- Initializing a timer to update `totalTime` and `totalFlips`.

#### `flipCard(card)`
Handles card-flipping logic:
- Increments `flippedCards` and `totalFlips`.
- Starts the game if not already started.
- Checks for a match when two cards are flipped.
  - If matched, marks them with the `matched` class.
  - If not, flips them back after 1 second.
- Checks for victory when all cards are matched.

#### `flipBackCards()`
Flips back all unmatched cards.
- Resets `flippedCards` to 0.

### d. Event Handling
#### `attachEventListeners()`
Attaches event listeners to handle user interactions:
- **Card Clicks**: Flips the card if it is not already flipped.
- **Start Button**: Starts the game when clicked.

---

## Core Logic

1. **Initialization**:
   - `generateGame()` creates the game board.
   - `attachEventListeners()` sets up event listeners for interactions.

2. **Game Play**:
   - Players click cards to flip them.
   - When two cards are flipped:
     - If they match, they remain flipped.
     - If not, they flip back after 1 second.

3. **Victory**:
   - When all cards are matched, a victory message is displayed.
   - Timer stops.

---

## Example Workflow
1. User clicks the start button.
2. The timer starts, and the board becomes interactive.
3. User flips cards to find matches.
4. The game ends when all pairs are matched.
   - A victory message displays the number of moves and elapsed time.

---

## Customization
- **Card Content**: Modify the `emojis` array in `generateGame()` to use different symbols.
- **Board Dimensions**: Change the `data-dimension` attribute of the board element.
- **Styles**: Customize CSS classes like `card`, `flipped`, and `matched`.

---

## Error Handling
- Ensures board dimensions are even to allow pairing.
- Validates user interactions (e.g., prevents flipping matched cards).

---

## Notes
- The game is responsive and dynamically adjusts based on board dimensions.
- Designed with modular, reusable functions for maintainability.

