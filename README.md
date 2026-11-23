# Turk Algorithm · `push_swap` Visualizer

An interactive, step-by-step web visualizer for the **Turk Algorithm** used to solve the 42 School `push_swap` sorting project. Built as a lightweight, zero-dependency single HTML file with full **English** and **Arabic** (`RTL`) support.

🔗 **Live Demo:** [https://velloxide.github.io/Turk_push_swap_visualizer/](https://velloxide.github.io/Turk_push_swap_visualizer/)

---

## ✨ Features

* **Step-by-Step Execution:** Watch every `sa`, `pb`, `pa`, `ra`, `rb`, `rr`, `rra`, `rrb`, and `rrr` operation animated smoothly with clear explanations of *why* each move happens and which C function (`push_b()`, `set_target_a()`, `find_cheapest()`, etc.) triggers it.
* **5 Algorithm Phases Navigation:** Jump directly between the core stages of the Turk algorithm:
  1. **Start** (Initial state)
  2. **Phase 1 · A → B** (Push with descending circular order)
  3. **Sort Three** (Fixed cases for the last 3 numbers in Stack A)
  4. **Phase 2 · B → A** (Push back to exact target positions)
  5. **Finish** (Final rotation to bring the minimum to the top)
* **Interactive Cost Table & 6-Step Cost Breakdown:**
  * Inspect `costA`, `costB`, and total move cost for every element in Stack A.
  * Hover over any row to preview the number and its target directly on the stacks, or click to pin it and walk through a **6-step visual breakdown** of how its cost is calculated.
* **Merge Optimization Toggle (`rr` / `rrr`):** Toggle simultaneous rotations on or off in real time to compare total move counts with and without rotation merging.
* **Custom & Preset Inputs:** Enter your own numbers (`5` to `14` unique integers) or generate **Random**, **Sorted**, and **Reversed** test cases.
* **Playback Controls & Shortcuts:** Play/pause with adjustable speed, scrub through steps, copy the generated instruction list in one click, or use the `←` and `→` arrow keys to step backward and forward.
* **Bilingual & Theme Support:** Instant switching between **English** and **Arabic** interfaces, plus automatic or manual **Light / Dark** mode.

---

## 🚀 Usage

1. Open the [Live Demo](https://velloxide.github.io/Turk_push_swap_visualizer/) in your browser (or open `index.html` locally).
2. Enter space-separated unique integers (e.g., `5 2 9 1 7 3 8`) or click **Random**, **Sorted**, or **Reversed**.
3. Click **Start** (or press `Enter`) and use the playback bar or `←` / `→` arrow keys to inspect each step.

---

## 🧠 How the Turk Algorithm Works

1. **Initial Push:** Push the first two elements from **Stack A** to **Stack B** (`pb`, `pb`) to establish a base.
2. **Cheapest Push (`A → B`):** While more than 3 elements remain in **A**, calculate the target in **B** (largest number smaller than the element, or the maximum in **B** if none exists) and total rotation cost for every element in **A**. Execute the cheapest move sequence (merging `ra`+`rb` into `rr` and `rra`+`rrb` into `rrr` when moving in the same direction) and push to **B**.
3. **Sort Three:** Sort the remaining 3 numbers in **A** in at most 2 operations.
4. **Return (`B → A`):** For each top element of **B**, find its target in **A** (smallest number larger than it, or the minimum in **A**), rotate **A** via the shortest path, and push back (`pa`).
5. **Final Alignment:** Rotate **A** (`ra` or `rra`) until the smallest number sits at the top.