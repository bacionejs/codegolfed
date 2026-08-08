
<a href="//bacionejs.github.io/codegolfed/index.html" target="_blank">
<img src="https://github.com/user-attachments/assets/a109e647-0604-4eda-a94b-597d2598fad6" width="50%" />
</a>

---

👉 [Try it](https://bacionejs.github.io/codegolfed/index.html)   

---

Source code is only 461 bytes (uncompressed) 🤯  

<a href="https://bacionejs.github.io/bacionejs/viewsource.html?b=1&file=https://raw.githubusercontent.com/bacionejs/codegolfed/main/index.html" target="_blank">
<img width="200" src="https://github.com/user-attachments/assets/17101bf1-0632-4bc6-97ab-30d77366f184" />
</a>

---
  
Find a path from Red to Red in exactly 5 steps.  
You can jump to any green square on your axis.  
Refresh the browser for a new random maze.  
Non-interactive, solve in your head.

---

Unlike traditional mazes, this project uses a **custom sparse rook graph**.

It's not great, usually easy, ranging from 5-40 seconds to solve, but was the first amateur insight I had before I learned programming: plotting random points creates a board that looks navigatable, that is, points can be thought of as the corners of a traditional maze. A naive approach can yield a reasonably difficult maze and by adding a path test, can be improved significantly.

The resulting geometry also gives the puzzle a multidimensional character. Although the board is visually two-dimensional, its connectivity exists in an abstract graph space. Edges may cross without intersecting, allowing a solution to pass across its own previous path without revisiting a vertex. The player must therefore distinguish geometric position from graph connectivity, effectively reasoning in two spaces at once.
  
However, Monte Carlo <a href="//bacionejs.github.io/codegolfed/research/montecarlo.html" target="_blank">simulations</a> revealed that parameters were strongly interdependent with a <a href="//bacionejs.github.io/codegolfed/research/chart.html" target="_blank">narrow viable region</a>, and increasing difficulty in some parameters had the paradoxical effect of reducing difficulty [^1], and making the wrong adjustments to some parameters adversely affected path <a href="//bacionejs.github.io/codegolfed/research/analyzer.html" target="_blank">uniqueness</a>. From the range of combinations found, a set was chosen based on established visual and cognitive research.

[^1]: We refer to this phenomenon as the highway effect: as the imposed minimum path length between two terminal vertices increases, conditioned samples of a sparse random spatial graph increasingly exhibit a coherent backbone connecting those terminals.
