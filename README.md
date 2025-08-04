# QuantumCalc: A Modern Scientific Calculator

QuantumCalc is a stylish, feature-rich scientific calculator built entirely with vanilla HTML, CSS, and JavaScript. It features a modern "glassmorphism" design, a dynamic theme switcher, and a comprehensive set of scientific and memory functions.

 \#\# ✨ Features

  * **Standard Operations**: Addition (`+`), Subtraction (`−`), Multiplication (`×`), Division (`÷`), and Modulus (`%`).
  * **Scientific Functions**:
      * Trigonometry: `sin`, `cos`, `tan`, and their inverses (`sin⁻¹`, `cos⁻¹`, `tan⁻¹`).
      * Logarithms: `log` (base 10) and `ln` (natural log).
      * Exponents & Powers: `x²`, `x³`, `10ˣ`, `eˣ`, and custom nth root (`ʸ√x`).
      * Roots: Square root (`√`) and cube root (`∛`).
      * Other: Factorial (`x!`), pi (`π`), and Euler's number (`e`).
  * **Memory Functions**: Memory Add (`M+`), Memory Subtract (`M-`), Memory Recall (`MR`), and Memory Clear (`MC`).
  * **Interactive UI**:
      * **Theme Toggling**: Switch between a bright light mode and a sleek dark mode.
      * **History Panel**: View a list of your recent calculations.
      * **Animations**: Smooth transitions, button pop effects, and a "shake" animation for errors.
  * **Responsive Design**: The layout adapts gracefully to both desktop and mobile screens.
  * **Keyboard Support**: Perform calculations using your physical keyboard for faster input.

## 🚀 How to Use

This project is a single, self-contained file. No installation or build steps are needed\!

1.  Download the `Scientific Calculator.html` file.
2.  Open the file directly in any modern web browser (like Chrome, Firefox, or Edge).
3.  Start calculating\!

## 🛠️ Technologies Used

  * **HTML5**: Structures the calculator's layout, including the display and keypad.
  * **CSS3**: Styles the entire application. It makes extensive use of:
      * **CSS Variables (`:root`)**: To define and manage color schemes for easy theme switching.
      * **Flexbox & Grid**: For responsive layout design.
      * **Backdrop Filter**: To create the "glassmorphism" transparent effect.
      * **Keyframe Animations**: For interactive UI animations.
  * **JavaScript (ES6)**: Powers all the calculator's logic and interactivity, organized within a single `ScientificCalculator` class.
  * **Font Awesome**: Used for icons in the header and on certain buttons (linked via CDN).

-----

## 🔬 Code Breakdown

The entire project is encapsulated within one `.html` file, with CSS and JavaScript embedded.

### 1\. HTML Structure (`<body>`)

The HTML sets up the calculator's user interface.

  * `<div class="calculator-container">`: The main wrapper with the glassmorphism effect.
  * `<header>`: Contains the title ("QuantumCalc") and the light/dark mode theme switcher.
  * `<div class="display">`: The screen of the calculator, with separate elements for the ongoing calculation (`#calculation`) and the final result (`#result`).
  * `<div class="keypad">`: A CSS Grid container for all the calculator buttons.
      * **Buttons (`<button>`)**: Each button is given specific classes (`.num-btn`, `.op-btn`, `.sci-btn`) for styling.
      * **`data-` Attributes**: Custom `data-` attributes (`data-num`, `data-op`, `data-fn`) are used to assign functionality to each button, which JavaScript then uses to identify their purpose.

### 2\. CSS Styling (`<style>`)

The CSS provides the visual appeal and responsiveness.

  * `:root`: Defines two color palettes using CSS variables—one for the default (light) theme and another within a `[data-theme="dark"]` attribute selector for the dark theme.
  * **Glassmorphism**: The `backdrop-filter: blur(10px);` and semi-transparent `background` colors on key elements create the frosted glass look.
  * **Responsiveness**: A media query (`@media (max-width: 500px)`) adjusts the keypad's grid layout for smaller mobile screens.
  * **Animations**: `@keyframes` for `pop` (button press) and `shake` (error) provide visual feedback to the user.

### 3\. JavaScript Logic (`<script>`)

All functionality is handled by the `ScientificCalculator` class.

  * `constructor()`:
      * Initializes the calculator's state (e.g., `currentInput`, `calculation`, `memoryValue`).
      * Gets references to all necessary DOM elements.
      * Calls `initEventListeners()` to activate the calculator.
  * `initEventListeners()`:
      * This method is the central hub for user interaction.
      * It attaches `click` event listeners to all buttons (numbers, operators, functions, memory).
      * It also sets up a `keydown` event listener on the `document` to enable keyboard input.
  * **Core Methods**:
      * `updateDisplay()`: Refreshes the display with the current state after every action.
      * `appendNumber()`, `handleOperator()`, `handleScientificFunction()`: These methods manage the input string and build the calculation expression.
      * `calculateResult()`: This is the evaluation engine.
        1.  It combines the `calculation` string with the `currentInput`.
        2.  It replaces user-friendly symbols (e.g., `÷`, `×`, `sin(`) with their JavaScript equivalents (e.g., `/`, `*`, `Math.sin(`).
        3.  It uses the `eval()` function to compute the result of the final expression string.
        4.  The result is then stored in the history and displayed.
  * **Feature-Specific Methods**:
      * `toggleTheme()`: Toggles a `data-theme` attribute on the `<body>`, which causes the CSS variable colors to change instantly.
      * `memoryAdd()`, `memorySubtract()`, etc.: Handle all memory-related logic.
      * `factorial()`, `nthRoot()`: Implement logic for special functions that require more than a simple expression replacement.
      * `showError()`: Displays an error message and triggers the shake animation if a calculation is invalid.

