
Find a path between the red squares in **exactly 5 steps**.  
**Jump to any green square on your axis**.  
Refresh the browser for a new random maze.  
Non-interactive, solve in your head.

<img src="https://github.com/user-attachments/assets/7f0c7e31-6c62-4031-bf57-c8659920b4f9" width="40%" />

<img width="40%" src="https://github.com/user-attachments/assets/a1b704a9-b93b-48e2-9141-04a39c771d88" />

👉 [Try it](https://bacionejs.github.io/rookmaze/index.html)   

---

## Research 🧑‍🎓

Unlike traditional mazes, this project uses a **custom sparse rook graph**.

It's not great, usually easy, ranging from 5-40 seconds to solve, but was the first amateur insight I had before I learned programming: plotting random points creates a board that looks navigatable, that is, points can be thought of as the corners of a traditional maze. A naive approach can yield a reasonably difficult maze and by adding a path test, can be improved significantly.
  
However, Monte Carlo <a href="//bacionejs.github.io/rookmaze/research/montecarlo.html" target="_blank">simulations</a> revealed that parameters were strongly interdependent with a <a href="//bacionejs.github.io/rookmaze/research/chart.html" target="_blank">narrow viable region</a>, and increasing difficulty in some parameters had the paradoxical effect of reducing difficulty [^1], and making the wrong adjustments to some parameters adversely affected path <a href="//bacionejs.github.io/rookmaze/research/analyzer.html" target="_blank">uniqueness</a>. 

[^1]: We refer to this phenomenon as the highway effect: as the imposed minimum path length between two terminal vertices increases, conditioned samples of a sparse random spatial graph increasingly exhibit a coherent backbone connecting those terminals.
