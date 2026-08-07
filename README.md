
<a href="//bacionejs.github.io/codegolfed/index.html" target="_blank"><img src="https://github.com/user-attachments/assets/5cf35f29-f62a-42a1-9570-62c88502a049" width="50%" />

---

👉 [Try it](https://bacionejs.github.io/codegolfed/index.html)   

---

Source code is only 811 bytes (uncompressed) 🤯  

<a href="https://bacionejs.github.io/bacionejs/viewsource.html?b=1&file=https://raw.githubusercontent.com/bacionejs/codegolfed/main/index.html" target="_blank"><img width="200" src="https://github.com/user-attachments/assets/9aade7a6-d416-4b1c-aee5-940582fdc183" /></a>

---

Find a shortest path for blue to red.  
You can click any green square on your axis.  
A blocked click means you are not going a shortest path.  

---

Unlike traditional maze algorithms that rely on local grid adjacency, this project uses a **novel sparse rook graph**, packing multi-dimensional complexity into a small visual space. However, this unique approach has graph creation parameters that are interdependent with only a small set of valid **setup** combinations which require extra work upfront, so **Monte Carlo simulations** were run to find values for density, size, and minpath. Not only were the values coupled in a tight band, but also increasing difficulty in some parameters had the paradoxical effect of reducing difficulty via the **highway effect**, and making the wrong adjustments to some parameters adversely affected **path uniqueness**. From the range of possible combinations found, a set of values was chosen based on established visual and cognitive research.
