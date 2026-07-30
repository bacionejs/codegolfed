

<a href="//bacionejs.github.io/codegolfed/index.html" target="_blank"><img src="https://github.com/user-attachments/assets/5da158cd-9ae9-4947-82dd-43f586c531f6" width="50%" /></a>

---

👉 [Try it](https://bacionejs.github.io/codegolfed/index.html)   

---

Source code is only 1k 🤯  

<a href="https://bacionejs.github.io/bacionejs/viewsource.html?b=1&file=https://raw.githubusercontent.com/bacionejs/codegolfed/main/index.html" target="_blank"><img width="200" src="https://github.com/user-attachments/assets/729b1e81-230d-497d-8726-094b644b594d" /></a>

---

**CODEGOLFED** is a maze game  

Find a shortest path to the flag.  
You can click any green square on your axis.  
Red means you are not going a shortest path.  
To learn, click the flag to reveal a shortest path.  

---

**Unminified**
```<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <style>
    * {
      margin: 0;
      padding: 0;
      font-size: 8dvmin;
    }

    #grid {
      display: grid;
      grid-template-columns: repeat(10, 10dvmin);
      grid-template-rows: repeat(10, 10dvmin);
    }
  </style>
</head>
<body>

<div id="grid"></div>

<script>
  let grid = [];
  let playerPos = { row: 0, col: 0 };
  let targetPos = { row: 0, col: 0 };
  
  let isWon = false;
  let isHintActive = false;
  let optimalPathLength = 0;
  let playerPath = [];
  let errorCells = {};

  // Shortest path finder using Breadth-First Search (BFS)
  function findShortestPath(startRow, startCol, returnPath = false) {
    let queue = [[startRow, startCol, 0, [...playerPath, `${startRow},${startCol}`]]];
    let visited = {};

    while (queue.length > 0) {
      let [currentRow, currentCol, distance, path] = queue.shift();

      if (currentRow === targetPos.row && currentCol === targetPos.col) {
        return returnPath ? path : distance;
      }

      let key = `${currentRow},${currentCol}`;
      if (!visited[key]) {
        visited[key] = true;

        for (let i = 0; i < 10; i++) {
          // Check vertical movement along current column
          if (grid[i][currentCol] && i !== currentRow) {
            queue.push([i, currentCol, distance + 1, [...path, `${i},${currentCol}`]]);
          }
          // Check horizontal movement along current row
          if (grid[currentRow][i] && i !== currentCol) {
            queue.push([currentRow, i, distance + 1, [...path, `${currentRow},${i}`]]);
          }
        }
      }
    }

    return returnPath ? [] : 9;
  }

  // Initialize and generate board layout
  function initGame() {
    isWon = false;
    isHintActive = false;
    playerPath = [];
    errorCells = {};

    // Generate grid with 3 random active tiles per row
    for (let row = 0; row < 10; row++) {
      grid[row] = grid[row] || [];
      for (let col = 0; col < 10; col++) {
        grid[row][col] = 0;
      }

      for (let tilesAdded = 0; tilesAdded < 3; ) {
        let randomCol = Math.floor(Math.random() * 10);
        if (!grid[row][randomCol]) {
          grid[row][randomCol] = 1;
          tilesAdded++;
        }
      }
    }

    // Place Player in bottom half (rows 5-9) on a valid tile
    do {
      playerPos.row = Math.floor(Math.random() * 5) + 5;
      playerPos.col = Math.floor(Math.random() * 10);
    } while (!grid[playerPos.row][playerPos.col]);

    // Place Target in top half (rows 0-4) on a valid tile
    do {
      targetPos.row = Math.floor(Math.random() * 5);
      targetPos.col = Math.floor(Math.random() * 10);
    } while (
      !grid[targetPos.row][targetPos.col] ||
      (playerPos.row === targetPos.row && playerPos.col === targetPos.col)
    );

    optimalPathLength = findShortestPath(playerPos.row, playerPos.col);

    // Re-roll level if shortest path is too trivial (less than 4 steps)
    if (optimalPathLength < 4) {
      initGame();
    } else {
      renderGrid();
    }
  }

  // Render game grid and handle tile selection logic
  function renderGrid() {
    const gridElement = document.getElementById("grid");
    gridElement.innerHTML = "";

    for (let row = 0; row < 10; row++) {
      for (let col = 0; col < 10; col++) {
        let cell = document.createElement("div");
        let cellStyle = cell.style;

        let isErrorCell = errorCells[`${row},${col}`];
        let isHintCell = isHintActive && findShortestPath(playerPos.row, playerPos.col, true).includes(`${row},${col}`);
        let isActiveTile = grid[row][col];

        // Color coding cells based on state
        cellStyle.background = isErrorCell
          ? "red"
          : isHintCell
          ? "orange"
          : isActiveTile
          ? "green"
          : "tan";

        cellStyle.display = "flex";
        cellStyle.alignItems = "center";
        cellStyle.justifyContent = "center";

        // Draw Player or Hole
        if (row === playerPos.row && col === playerPos.col) {
          cell.innerHTML = "🏌️";
        } else if (row === targetPos.row && col === targetPos.col) {
          cell.innerHTML = "⛳";
        }

        cell.onclick = () => {
          if (isWon) return;

          // Toggle hint path when clicking target directly
          if (row === targetPos.row && col === targetPos.col && (row !== playerPos.row) === (col !== playerPos.col)) {
            isHintActive = !isHintActive;
            renderGrid();
            return;
          }

          // Move player along valid perpendicular lines
          let isValidMove = (row === playerPos.row) !== (col === playerPos.col) && grid[row][col];

          if (isValidMove) {
            let remainingPath = findShortestPath(row, col);

            // Check if move diverges from optimal path
            if (playerPath.length + 1 + remainingPath > optimalPathLength) {
              errorCells[`${row},${col}`] = 1;
              renderGrid();
              return;
            }

            playerPath.push(`${row},${col}`);
            playerPos = { row: row, col: col };

            // Check win condition
            if (row === targetPos.row && col === targetPos.col) {
              isWon = true;
              initGame();
            } else {
              renderGrid();
            }
          }
        };

        gridElement.appendChild(cell);
      }
    }
  }

  initGame();
</script>

</body>
</html>
```

