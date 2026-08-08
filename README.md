
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
Refresh the browser for a new random puzzle.  

---

Unlike traditional maze algorithms that rely on local grid adjacency, this project uses a **novel sparse rook graph with a minpath constraint**. However, this unique approach has graph creation parameters that are interdependent, with only a small set of valid **setup** combinations, which require extra work upfront, so Monte Carlo <a href="//bacionejs.github.io/codegolfed/research/montecarlo.html" target="_blank">simulations</a> were run to find values for size, density and minpath. Not only were the values coupled in a tight <a href="//bacionejs.github.io/codegolfed/research/chart.html" target="_blank">band</a>, but also increasing difficulty in some parameters had the paradoxical effect of reducing difficulty via the **highway effect**, and making the wrong adjustments to some parameters adversely affected path <a href="//bacionejs.github.io/codegolfed/research/analyzer.html" target="_blank">uniqueness</a>. From the range of valid combinations found, a set of values was chosen based on established visual and cognitive research.
