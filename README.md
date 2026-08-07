
<a href="//bacionejs.github.io/codegolfed/index.html" target="_blank">
<img src="https://github.com/user-attachments/assets/0dc958f9-1b49-4fc1-8afd-26453fca3d21" width="50%" />
</a>

---

👉 [Try it](https://bacionejs.github.io/codegolfed/index.html)   

---

Source code is only 811 bytes (uncompressed) 🤯  

<a href="https://bacionejs.github.io/bacionejs/viewsource.html?b=1&file=https://raw.githubusercontent.com/bacionejs/codegolfed/main/index.html" target="_blank">
<img width="200" src="https://github.com/user-attachments/assets/9aade7a6-d416-4b1c-aee5-940582fdc183" />
</a>

---

Find a shortest path for blue to red.  
You can click any green square on your axis.  
A blocked click means you are not going a shortest path.  

---

Unlike traditional maze algorithms that rely on local grid adjacency, this project uses a **novel sparse rook graph with a minpath constraint**, to pack multi-dimensional complexity into a small visual space. However, this unique approach has graph creation parameters that are interdependent with only a small set of valid **setup** combinations which require extra work upfront, so Monte Carlo <a href="//bacionejs.github.io/codegolfed/research/montecarlo.html" target="_blank">simulations</a> were run to find values for size, density and minpath. Not only were the values coupled in a tight <a href="//bacionejs.github.io/codegolfed/research/chart.html" target="_blank">band</a>, but also increasing difficulty in some parameters had the paradoxical effect of reducing difficulty via the **highway effect**, and making the wrong adjustments to some parameters adversely affected path <a href="//bacionejs.github.io/codegolfed/research/analyzer.html" target="_blank">uniqueness</a>. From the range of possible combinations found, a set of values was chosen based on established visual and cognitive research.
