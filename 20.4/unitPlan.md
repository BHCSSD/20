# Control Flow, Data Structures, & Modular Architecture

### Phase 1: Loops, Strings, & Boolean Logic

**Focus:** Mastering basic syntax, counting loops, text formatting, and evaluating truth conditions.

* **Topics Covered:**
  * **The `while` loop vs. the `for` loop:** Understanding when to use condition-based loops vs. sequence-based loops.
  * **Counting backward with `range()`:** Demystifying the `range(start, stop, step)` syntax to count in reverse.
  * **String Formatting:** Injecting data cleanly into strings using **f-strings**.
  * **Boolean Logic & Comparison Operators:** Using `==`, `!=`, `>`, `<`, and combining statements using `and` / `or` to control program flow.
  * **Conditional Grammar:** Writing `if/else` checks to dynamically format singular vs. plural outputs (e.g., "1 bottle" vs. "2 bottles").

* **Target Assignment:** **`20.4.11.01 ASSIGN Ninety-nine Bottles.md`**
  * *Why:* This project serves as an excellent sandbox for practicing countdown ranges, loop selection, and strict conditional rules for song lyrics.

---

### Phase 2: Function Architecture, Data Isolation, & Type Checking
**Focus:** Writing secure, reusable code, separating user interaction from calculations, and handling runtime inputs safely.

* **Topics Covered:**
  * **Separation of Concerns:** Structuring a program so that user input (`input()`) is handled strictly in `main()`, while computational math lives exclusively inside helper functions.
  * **Variable Scope:** Recognizing that local variables inside functions are isolated from the rest of the application unless passed explicitly.
  * **Parameters & Arguments:** Mastering data flow via parameter passing and utilizing **default parameter values** to write cleaner definitions.
  * **Input Validation:** Using `while` loops alongside string methods like `.isdigit()` to prevent user-induced application crashes.
  * **Type Inspection:** Understanding data types and how to dynamically check them using tools like `isinstance()`.
  * **The Modulo Operator (`%`):** Leveraging math to determine divisibility and factors.

* **Target Assignment:** **`20.4.12 ASSIGN FizzBuzz.md`**
  * *Why:* This assignment places a strict guardrail on keeping `input()` exclusively in `main()` while heavily reinforcing default parameters and nested divisibility logic.

---

### Phase 3: Ordered Sequences, Mappings, & Algorithmic Logic
**Focus:** Structuring data with multi-element collections, building rule engines, automating code testing, and tracking state across loops.

* **Topics Covered:**
  * **Introduction to Lists (`[]`):** Creating, indexing, and manipulating ordered collections of data (e.g., storing a hand of dice rolls).
  * **Mutability vs. Immutability:** Differentiating between data types that can change in place (Lists, Dictionaries) and those that cannot (Strings, Integers), avoiding data leaks across functions.
  * **Built-in Sequence Helpers:** Utilizing math helpers like `max()`, `min()`, and `sum()` to evaluate multi-item collections instantly.
  * **Introduction to Dictionaries (`{}`):** Structuring data using **key-value pairs** for immediate property lookups.
  * **Unit Testing via `assert`:** Writing isolated automated scripts (`testScore()`) to mathematically prove code functions perfectly before full deployment.
  * **State Accumulation:** Using loop iterations to append or sum data to a running variable (crucial for calculating averages over multiple rounds).
  * **Randomization:** Importing and utilizing Python's built-in `random` module to simulate unpredictable outcomes (like rolling dice).


* **Target Assignment:** **`20.4.13.01 ASSIGN Mini Yahtzee.md`**
  * *Why:* This capstone assignment weaves everything together. It forces students to build a tactical strategy engine using `max()`, pass data dynamically, map numbers to elegant Unicode dice visual dictionaries, and mathematically safeguard their logic with custom unit tests.


