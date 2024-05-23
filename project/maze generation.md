[[https://bost.ocks.org/mike/algorithms/]]

The last problem we’ll look at is maze generation. All algorithms in this section generate a [spanning tree](https://en.wikipedia.org/wiki/Spanning_tree) of a two-dimensional rectangular grid. This means there are no loops and there is a unique path from the root in the bottom-left corner to every other cell in the maze.

I apologize for the esoteric subject — I don’t know enough to say why these algorithms are useful beyond simple games, and possibly something about electrical networks. But even so, they are fascinating from a visualization perspective because they solve the same, highly-constrained problem in wildly-different ways.
# Random Traversal
```html
<!DOCTYPE html>
<meta charset="utf-8">
<style>

body {
  background: #000;
}

</style>
<body>
<script src="//d3js.org/d3.v3.min.js"></script>
<script>

var width = 960,
    height = 960;

var N = 1 << 0,
    S = 1 << 1,
    W = 1 << 2,
    E = 1 << 3;

var cellSize = 4,
    cellSpacing = 4,
    cellWidth = Math.floor((width - cellSpacing) / (cellSize + cellSpacing)),
    cellHeight = Math.floor((height - cellSpacing) / (cellSize + cellSpacing)),
    cells = new Array(cellWidth * cellHeight), // each cell’s edge bits
    frontier = [];

var canvas = d3.select("body").append("canvas")
    .attr("width", width)
    .attr("height", height);

var context = canvas.node().getContext("2d");

context.translate(
  Math.round((width - cellWidth * cellSize - (cellWidth + 1) * cellSpacing) / 2),
  Math.round((height - cellHeight * cellSize - (cellHeight + 1) * cellSpacing) / 2)
);

context.fillStyle = "white";

// Add a random cell and two initial edges.
var start = (cellHeight - 1) * cellWidth;
cells[start] = 0;
fillCell(start);
frontier.push({index: start, direction: N});
frontier.push({index: start, direction: E});

// Explore the frontier until the tree spans the graph.
d3.timer(function() {
  var done, k = 0;
  while (++k < 50 && !(done = exploreFrontier()));
  return done;
});

function exploreFrontier() {
  if ((edge = popRandom(frontier)) == null) return true;

  var edge,
      i0 = edge.index,
      d0 = edge.direction,
      i1 = i0 + (d0 === N ? -cellWidth : d0 === S ? cellWidth : d0 === W ? -1 : +1),
      x0 = i0 % cellWidth,
      y0 = i0 / cellWidth | 0,
      x1,
      y1,
      d1,
      open = cells[i1] == null; // opposite not yet part of the maze

  context.fillStyle = open ? "white" : "black";
  if (d0 === N) fillSouth(i1), x1 = x0, y1 = y0 - 1, d1 = S;
  else if (d0 === S) fillSouth(i0), x1 = x0, y1 = y0 + 1, d1 = N;
  else if (d0 === W) fillEast(i1), x1 = x0 - 1, y1 = y0, d1 = E;
  else fillEast(i0), x1 = x0 + 1, y1 = y0, d1 = W;

  if (open) {
    fillCell(i1);
    cells[i0] |= d0, cells[i1] |= d1;
    context.fillStyle = "magenta";
    if (y1 > 0 && cells[i1 - cellWidth] == null) fillSouth(i1 - cellWidth), frontier.push({index: i1, direction: N});
    if (y1 < cellHeight - 1 && cells[i1 + cellWidth] == null) fillSouth(i1), frontier.push({index: i1, direction: S});
    if (x1 > 0 && cells[i1 - 1] == null) fillEast(i1 - 1), frontier.push({index: i1, direction: W});
    if (x1 < cellWidth - 1 && cells[i1 + 1] == null) fillEast(i1), frontier.push({index: i1, direction: E});
  }
}

function fillCell(index) {
  var i = index % cellWidth, j = index / cellWidth | 0;
  context.fillRect(i * cellSize + (i + 1) * cellSpacing, j * cellSize + (j + 1) * cellSpacing, cellSize, cellSize);
}

function fillEast(index) {
  var i = index % cellWidth, j = index / cellWidth | 0;
  context.fillRect((i + 1) * (cellSize + cellSpacing), j * cellSize + (j + 1) * cellSpacing, cellSpacing, cellSize);
}

function fillSouth(index) {
  var i = index % cellWidth, j = index / cellWidth | 0;
  context.fillRect(i * cellSize + (i + 1) * cellSpacing, (j + 1) * (cellSize + cellSpacing), cellSize, cellSpacing);
}

function popRandom(array) {
  if (!array.length) return;
  var n = array.length, i = Math.random() * n | 0, t;
  t = array[i], array[i] = array[n - 1], array[n - 1] = t;
  return array.pop();
}

d3.select(self.frameElement).style("height", height + "px");

</script>
```
## explanation
This maze generation algorithm, sometimes misleadingly called [randomized Prim’s algorithm](http://en.wikipedia.org/wiki/Maze_generation_algorithm#Randomized_Prim.27s_algorithm), is more accurately described as a random traversal. Starting in the bottom-left corner, the algorithm keeps an array of the possible directions the maze could be extended (shown in pink). At each step, the maze is extended in one of these random directions, as long as doing so does not reconnect with another part of the maze.

While this algorithm also generates a [spanning tree](http://en.wikipedia.org/wiki/Spanning_tree), its behavior is radically different from running [Prim’s algorithm](https://gist.github.com/mbostock/11159599) on a randomly-weighted graph! Random traversal generates mazes with a very predictable global structure which can be seen both in the above animation and by [flooding the maze with color](https://gist.github.com/mbostock/11167589).

Random traversal behaves similarly to randomized breadth-first traversal, since typically the maze can only be extended without self-intersecting on a roughly-circular perimeter. Compare to [randomized depth-first traversal](https://gist.github.com/mbostock/1ef3b1fb9eb35ca8ffff).
### my understanding
Certainly! Let's break down the code step by step:

1. **Setting up the HTML Structure**:
    
    - The code begins by including a basic HTML structure with a canvas element. This canvas element will be used to draw the maze.
2. **Initializing Variables**:
    
    - Several variables are initialized:
        - `width` and `height`: Dimensions of the canvas.
        - `N`, `S`, `W`, `E`: Constants representing directions (North, South, West, East).
        - `cellSize`, `cellSpacing`: Size and spacing of each cell in the maze.
        - `cellWidth`, `cellHeight`: Number of cells in the horizontal and vertical directions.
        - `cells`: An array representing each cell's edges.
        - `frontier`: An array representing the frontier of the maze, i.e., edges to explore.
3. **Setting Up Canvas**:
    
    - The canvas element is selected, and its dimensions are set based on the `width` and `height` variables. The canvas context is obtained for drawing.
4. **Initializing Maze**:
    
    - A starting cell is randomly selected, and two initial edges (North and East) are added to the frontier.
5. **Exploring Frontier**:
    
    - The `exploreFrontier` function is repeatedly called using `d3.timer` until the maze is fully generated.
    - Inside `exploreFrontier`, a loop iterates over the frontier array.
    - For each edge in the frontier:
        - It checks the direction of the edge and explores in that direction.
        - It fills the cell and updates the cells array.
        - If the neighboring cell is not yet part of the maze, it adds the edge to the frontier for further exploration.
6. **Drawing Functions**:
    
    - `fillCell`, `fillEast`, and `fillSouth` functions are used to fill cells, east walls, and south walls respectively. They calculate the coordinates based on the cell index and draw rectangles accordingly.
7. **Utility Functions**:
    
    - `popRandom` function pops a random element from an array.
8. **Setting Frame Height**:
    
    - Finally, the height of the frame is adjusted based on the canvas height.


# Randomized Depth-First
This maze generation algorithm uses randomized depth-first traversal. Starting in the bottom-left corner, the algorithm keeps an array of the possible directions the maze could be extended (shown in pink). At each step, the maze is extended in a random direction from the previous cell, as long as doing so does not reconnect with another part of the maze.

Compare this algorithm to [random traversal](https://gist.github.com/mbostock/70a28267db0354261476), [Prim’s algorithm](https://gist.github.com/mbostock/11159599) on a randomly-weighted graph, and [Wilson’s algorithm](https://gist.github.com/mbostock/11357811) for a uniform spanning tree. The global structure of the maze can be more easily seen by [flooding it with color](https://gist.github.com/mbostock/97f1cdb9e0a695cd8df4).

```html
<!DOCTYPE html>
<meta charset="utf-8">
<style>

body {
  background: #000;
}

</style>
<body>
<script src="//d3js.org/d3.v3.min.js"></script>
<script>

var width = 960,
    height = 960;

var N = 1 << 0,
    S = 1 << 1,
    W = 1 << 2,
    E = 1 << 3;

var cellSize = 4,
    cellSpacing = 4,
    cellWidth = Math.floor((width - cellSpacing) / (cellSize + cellSpacing)),
    cellHeight = Math.floor((height - cellSpacing) / (cellSize + cellSpacing)),
    cells = new Array(cellWidth * cellHeight), // each cell’s edge bits
    frontier = [];

var canvas = d3.select("body").append("canvas")
    .attr("width", width)
    .attr("height", height);

var context = canvas.node().getContext("2d");

context.translate(
  Math.round((width - cellWidth * cellSize - (cellWidth + 1) * cellSpacing) / 2),
  Math.round((height - cellHeight * cellSize - (cellHeight + 1) * cellSpacing) / 2)
);

context.fillStyle = "white";

// Add a random cell and two initial edges.
var start = (cellHeight - 1) * cellWidth;
cells[start] = 0;
fillCell(start);
frontier.push({index: start, direction: N});
frontier.push({index: start, direction: E});

// Explore the frontier until the tree spans the graph.
d3.timer(function() {
  var done, k = 0;
  while (++k < 50 && !(done = exploreFrontier()));
  return done;
});

function exploreFrontier() {
  if ((edge = frontier.pop()) == null) return true;

  var edge,
      i0 = edge.index,
      d0 = edge.direction,
      i1 = i0 + (d0 === N ? -cellWidth : d0 === S ? cellWidth : d0 === W ? -1 : +1),
      x0 = i0 % cellWidth,
      y0 = i0 / cellWidth | 0,
      x1,
      y1,
      d1,
      open = cells[i1] == null; // opposite not yet part of the maze

  context.fillStyle = open ? "white" : "black";
  if (d0 === N) fillSouth(i1), x1 = x0, y1 = y0 - 1, d1 = S;
  else if (d0 === S) fillSouth(i0), x1 = x0, y1 = y0 + 1, d1 = N;
  else if (d0 === W) fillEast(i1), x1 = x0 - 1, y1 = y0, d1 = E;
  else fillEast(i0), x1 = x0 + 1, y1 = y0, d1 = W;

  if (open) {
    fillCell(i1);
    cells[i0] |= d0, cells[i1] |= d1;
    context.fillStyle = "magenta";

    var m = 0;
    if (y1 > 0 && cells[i1 - cellWidth] == null) fillSouth(i1 - cellWidth), frontier.push({index: i1, direction: N}), ++m;
    if (y1 < cellHeight - 1 && cells[i1 + cellWidth] == null) fillSouth(i1), frontier.push({index: i1, direction: S}), ++m;
    if (x1 > 0 && cells[i1 - 1] == null) fillEast(i1 - 1), frontier.push({index: i1, direction: W}), ++m;
    if (x1 < cellWidth - 1 && cells[i1 + 1] == null) fillEast(i1), frontier.push({index: i1, direction: E}), ++m;
    shuffle(frontier, frontier.length - m, frontier.length);
  }
}

function fillCell(index) {
  var i = index % cellWidth, j = index / cellWidth | 0;
  context.fillRect(i * cellSize + (i + 1) * cellSpacing, j * cellSize + (j + 1) * cellSpacing, cellSize, cellSize);
}

function fillEast(index) {
  var i = index % cellWidth, j = index / cellWidth | 0;
  context.fillRect((i + 1) * (cellSize + cellSpacing), j * cellSize + (j + 1) * cellSpacing, cellSpacing, cellSize);
}

function fillSouth(index) {
  var i = index % cellWidth, j = index / cellWidth | 0;
  context.fillRect(i * cellSize + (i + 1) * cellSpacing, (j + 1) * (cellSize + cellSpacing), cellSize, cellSpacing);
}

function shuffle(array, i0, i1) {
  var m = i1 - i0, t, i, j;
  while (m) {
    i = Math.random() * m-- | 0;
    t = array[m + i0], array[m + i0] = array[i + i0], array[i + i0] = t;
  }
  return array;
}

d3.select(self.frameElement).style("height", height + "px");

</script>
```
Rather than picking a new random passage each time, this algorithm always extends the deepest passage — the one with the longest path back to the root — in a random direction. Thus, randomized depth-first traversal only branches when the current path dead-ends into an earlier part of the maze. To continue, it backtracks until it can start a new branch. This snake-like exploration leads to mazes with significantly fewer branches and much longer, winding passages.

# Prim’s algorithm
Prim’s algorithm generates a [minimum spanning tree](http://en.wikipedia.org/wiki/Minimum_spanning_tree) from a graph with weighted edges. Starting in the bottom-left corner, the algorithm keeps a heap of the possible directions the maze could be extended (shown in pink). At each step, the maze is extended in the direction with the lowest weight, as long as doing so does not reconnect with another part of the maze. Here the edges are initialized with random weights.

Unlike [Wilson’s algorithm](https://gist.github.com/mbostock/11357811), this does not result in a uniform spanning tree. Sometimes, [random traversal](https://gist.github.com/mbostock/70a28267db0354261476) is misleadingly referred to as randomized Prim’s algorithm; however, the two algorithms exhibit radically different behavior! The global structure of the maze can be more easily seen by [flooding it with color](https://gist.github.com/mbostock/83d1073cb0a45ac158fb).

```html
<!DOCTYPE html>
<meta charset="utf-8">
<style>

body {
  background: #000;
}

</style>
<body>
<script src="//d3js.org/d3.v3.min.js"></script>
<script>

var width = 960,
    height = 960;

var N = 1 << 0,
    S = 1 << 1,
    W = 1 << 2,
    E = 1 << 3;

var cellSize = 4,
    cellSpacing = 4,
    cellWidth = Math.floor((width - cellSpacing) / (cellSize + cellSpacing)),
    cellHeight = Math.floor((height - cellSpacing) / (cellSize + cellSpacing)),
    cells = new Array(cellWidth * cellHeight), // each cell’s edge bits
    frontier = minHeap(function(a, b) { return a.weight - b.weight; });

var canvas = d3.select("body").append("canvas")
    .attr("width", width)
    .attr("height", height);

var context = canvas.node().getContext("2d");

context.translate(
  Math.round((width - cellWidth * cellSize - (cellWidth + 1) * cellSpacing) / 2),
  Math.round((height - cellHeight * cellSize - (cellHeight + 1) * cellSpacing) / 2)
);

context.fillStyle = "white";

// Add a random cell and two initial edges.
var start = (cellHeight - 1) * cellWidth;
cells[start] = 0;
fillCell(start);
frontier.push({index: start, direction: N, weight: Math.random()});
frontier.push({index: start, direction: E, weight: Math.random()});

// Explore the frontier until the tree spans the graph.
d3.timer(function() {
  var done, k = 0;
  while (++k < 50 && !(done = exploreFrontier()));
  return done;
});

function exploreFrontier() {
  if ((edge = frontier.pop()) == null) return true;

  var edge,
      i0 = edge.index,
      d0 = edge.direction,
      i1 = i0 + (d0 === N ? -cellWidth : d0 === S ? cellWidth : d0 === W ? -1 : +1),
      x0 = i0 % cellWidth,
      y0 = i0 / cellWidth | 0,
      x1,
      y1,
      d1,
      open = cells[i1] == null; // opposite not yet part of the maze

  context.fillStyle = open ? "white" : "black";
  if (d0 === N) fillSouth(i1), x1 = x0, y1 = y0 - 1, d1 = S;
  else if (d0 === S) fillSouth(i0), x1 = x0, y1 = y0 + 1, d1 = N;
  else if (d0 === W) fillEast(i1), x1 = x0 - 1, y1 = y0, d1 = E;
  else fillEast(i0), x1 = x0 + 1, y1 = y0, d1 = W;

  if (open) {
    fillCell(i1);
    cells[i0] |= d0, cells[i1] |= d1;
    context.fillStyle = "magenta";
    if (y1 > 0 && cells[i1 - cellWidth] == null) fillSouth(i1 - cellWidth), frontier.push({index: i1, direction: N, weight: Math.random()});
    if (y1 < cellHeight - 1 && cells[i1 + cellWidth] == null) fillSouth(i1), frontier.push({index: i1, direction: S, weight: Math.random()});
    if (x1 > 0 && cells[i1 - 1] == null) fillEast(i1 - 1), frontier.push({index: i1, direction: W, weight: Math.random()});
    if (x1 < cellWidth - 1 && cells[i1 + 1] == null) fillEast(i1), frontier.push({index: i1, direction: E, weight: Math.random()});
  }
}

function minHeap(compare) {
  var heap = {},
      array = [],
      size = 0;

  heap.empty = function() {
    return !size;
  };

  heap.push = function(value) {
    up(array[size] = value, size++);
    return size;
  };

  heap.pop = function() {
    if (size <= 0) return;
    var removed = array[0], value;
    if (--size > 0) value = array[size], down(array[0] = value, 0);
    return removed;
  };

  function up(value, i) {
    while (i > 0) {
      var j = ((i + 1) >> 1) - 1,
          parent = array[j];
      if (compare(value, parent) >= 0) break;
      array[i] = parent;
      array[i = j] = value;
    }
  }

  function down(value, i) {
    while (true) {
      var r = (i + 1) << 1,
          l = r - 1,
          j = i,
          child = array[j];
      if (l < size && compare(array[l], child) < 0) child = array[j = l];
      if (r < size && compare(array[r], child) < 0) child = array[j = r];
      if (j === i) break;
      array[i] = child;
      array[i = j] = value;
    }
  }

  return heap;
}

function fillCell(index) {
  var i = index % cellWidth, j = index / cellWidth | 0;
  context.fillRect(i * cellSize + (i + 1) * cellSpacing, j * cellSize + (j + 1) * cellSpacing, cellSize, cellSize);
}

function fillEast(index) {
  var i = index % cellWidth, j = index / cellWidth | 0;
  context.fillRect((i + 1) * (cellSize + cellSpacing), j * cellSize + (j + 1) * cellSpacing, cellSpacing, cellSize);
}

function fillSouth(index) {
  var i = index % cellWidth, j = index / cellWidth | 0;
  context.fillRect(i * cellSize + (i + 1) * cellSpacing, (j + 1) * (cellSize + cellSpacing), cellSize, cellSpacing);
}

d3.select(self.frameElement).style("height", height + "px");

</script>
```

# Wilson’s algorithm
Wilson’s algorithm uses [loop-erased random walks](http://en.wikipedia.org/wiki/Loop-erased_random_walk) to generate a uniform [spanning tree](http://en.wikipedia.org/wiki/Spanning_tree) — an unbiased sample of all possible spanning trees. Most other maze generation algorithms, such as [Prim’s](https://gist.github.com/mbostock/11159599), [random traversal](https://gist.github.com/mbostock/70a28267db0354261476) and [randomized depth-first traversal](https://gist.github.com/mbostock/1ef3b1fb9eb35ca8ffff), do not have this beautiful property.

The algorithm initializes the maze with an arbitrary starting cell. Then, a new cell is added to the maze, initiating a random walk (shown in magenta). The random walk continues until it reconnects with the existing maze (shown in white). However, if the random walk intersects itself, the resulting loop is erased before the random walk continues.

Initially, the algorithm can be frustratingly slow to watch, as the early random walks are unlikely to reconnect with the small existing maze. However, as the maze grows, the random walks become more likely to collide with the maze and the algorithm accelerates dramatically.

The global structure of the maze can be more easily seen by [flooding it with color](https://gist.github.com/mbostock/c03ee31334ee89abad83).

```html
<!DOCTYPE html>
<meta charset="utf-8">
<style>

body {
  background: #000;
}

</style>
<body>
<script src="//d3js.org/d3.v3.min.js"></script>
<script>

var width = 960,
    height = 960;

var N = 1 << 0,
    S = 1 << 1,
    W = 1 << 2,
    E = 1 << 3;

var cellSize = 4,
    cellSpacing = 4,
    cellWidth = Math.floor((width - cellSpacing) / (cellSize + cellSpacing)),
    cellHeight = Math.floor((height - cellSpacing) / (cellSize + cellSpacing)),
    cells = new Array(cellWidth * cellHeight), // each cell’s edge bits
    remaining = d3.range(cellWidth * cellHeight), // cell indexes to visit
    previous = new Array(cellWidth * cellHeight), // current random walk path
    i0, x0, y0; // end of current random walk

var canvas = d3.select("body").append("canvas")
    .attr("width", width)
    .attr("height", height);

var context = canvas.node().getContext("2d");

context.translate(
  Math.round((width - cellWidth * cellSize - (cellWidth + 1) * cellSpacing) / 2),
  Math.round((height - cellHeight * cellSize - (cellHeight + 1) * cellSpacing) / 2)
);

// Add the starting cell.
context.fillStyle = "white";
var start = remaining.pop();
cells[start] = 0;
fillCell(start);

// While there are remaining cells,
// add a loop-erased random walk to the maze.
context.fillStyle = "magenta";
d3.timer(function() {
  for (var k = 0; k < 50; ++k) {
    if (loopErasedRandomWalk()) {
      return true;
    }
  }
});

function loopErasedRandomWalk() {
  var i1;

  // Pick a location that’s not yet in the maze (if any).
  if (i0 == null) {
    do if ((i0 = remaining.pop()) == null) return true;
    while (cells[i0] >= 0);
    previous[i0] = i0;
    fillCell(i0);
    x0 = i0 % cellWidth;
    y0 = i0 / cellWidth | 0;
    return;
  }

  // Perform a random walk starting at this location,
  // by picking a legal random direction.
  while (true) {
    i1 = Math.random() * 4 | 0;
    if (i1 === 0) { if (y0 <= 0) continue; --y0, i1 = i0 - cellWidth; }
    else if (i1 === 1) { if (y0 >= cellHeight - 1) continue; ++y0, i1 = i0 + cellWidth; }
    else if (i1 === 2) { if (x0 <= 0) continue; --x0, i1 = i0 - 1; }
    else { if (x0 >= cellWidth - 1) continue; ++x0, i1 = i0 + 1; }
    break;
  }

  // If this new cell was visited previously during this walk,
  // erase the loop, rewinding the path to its earlier state.
  if (previous[i1] >= 0) eraseWalk(i0, i1);

  // Otherwise, just add it to the walk.
  else {
    previous[i1] = i0;
    fillCell(i1);
    if (i1 === i0 - 1) fillEast(i1);
    else if (i1 === i0 + 1) fillEast(i0);
    else if (i1 === i0 - cellWidth) fillSouth(i1);
    else fillSouth(i0);
  }

  // If this cell is part of the maze, we’re done walking.
  if (cells[i1] >= 0) {

    // Add the random walk to the maze by backtracking to the starting cell.
    // Also erase this walk’s history to not interfere with subsequent walks.
    context.save();
    context.fillStyle = "#fff";
    fillCell(i1);
    while ((i0 = previous[i1]) !== i1) {
      fillCell(i0);
      if (i1 === i0 + 1) cells[i0] |= E, cells[i1] |= W, fillEast(i0);
      else if (i1 === i0 - 1) cells[i0] |= W, cells[i1] |= E, fillEast(i1);
      else if (i1 === i0 + cellWidth) cells[i0] |= S, cells[i1] |= N, fillSouth(i0);
      else cells[i0] |= N, cells[i1] |= S, fillSouth(i1);
      previous[i1] = NaN;
      i1 = i0;
    }
    context.restore();

    previous[i1] = NaN;
    i0 = null;
  } else {
    i0 = i1;
  }
}

function eraseWalk(i0, i2) {
  var i1;
  context.save();
  context.globalCompositeOperation = "destination-out";
  do {
    i1 = previous[i0];
    if (i1 === i0 - 1) fillEast(i1);
    else if (i1 === i0 + 1) fillEast(i0);
    else if (i1 === i0 - cellWidth) fillSouth(i1);
    else fillSouth(i0);
    fillCell(i0);
    previous[i0] = NaN;
    i0 = i1;
  } while (i1 !== i2);
  context.restore();
}

function fillCell(i) {
  var x = i % cellWidth, y = i / cellWidth | 0;
  context.fillRect(x * cellSize + (x + 1) * cellSpacing, y * cellSize + (y + 1) * cellSpacing, cellSize, cellSize);
}

function fillEast(i) {
  var x = i % cellWidth, y = i / cellWidth | 0;
  context.fillRect((x + 1) * (cellSize + cellSpacing), y * cellSize + (y + 1) * cellSpacing, cellSpacing, cellSize);
}

function fillSouth(i) {
  var x = i % cellWidth, y = i / cellWidth | 0;
  context.fillRect(x * cellSize + (x + 1) * cellSpacing, (y + 1) * (cellSize + cellSpacing), cellSize, cellSpacing);
}

d3.select(self.frameElement).style("height", height + "px");

</script>
```



# color visualization
## Random Traversal II
This maze is generated by [random traversal](https://gist.github.com/mbostock/70a28267db0354261476) and then flooded with color. Hue encodes [Manhattan distance](http://en.wikipedia.org/wiki/Taxicab_geometry) from the starting cell. (This is not an optimal visual encoding, but it suffices and is pretty.)

Color is useful to visually compare the structure of mazes; without color, the black and white alternating cells are too noisy to offer any pre-attentive comparisons. Compare a maze generated by random traversal to [randomized depth-first traversal](https://gist.github.com/mbostock/97f1cdb9e0a695cd8df4), [Wilson’s algorithm](https://gist.github.com/mbostock/c03ee31334ee89abad83) and [Prim’s algorithm](https://gist.github.com/mbostock/83d1073cb0a45ac158fb).

See this color flood applied [directly to the pixel grid](https://gist.github.com/mbostock/11337835).
```html
<!DOCTYPE html>
<meta charset="utf-8">
<style>

body {
  background: #000;
}

</style>
<body>
<script src="//d3js.org/d3.v3.min.js"></script>
<script>

var width = 960,
    height = 960;

var N = 1 << 0,
    S = 1 << 1,
    W = 1 << 2,
    E = 1 << 3;

var cellSize = 4,
    cellSpacing = 4,
    cellWidth = Math.floor((width - cellSpacing) / (cellSize + cellSpacing)),
    cellHeight = Math.floor((height - cellSpacing) / (cellSize + cellSpacing)),
    cells = generateMaze(cellWidth, cellHeight), // each cell’s edge bits
    distance = 0,
    visited = new Array(cellWidth * cellHeight),
    frontier = [(cellHeight - 1) * cellWidth];

var canvas = d3.select("body").append("canvas")
    .attr("width", width)
    .attr("height", height);

var context = canvas.node().getContext("2d");

context.translate(
  Math.round((width - cellWidth * cellSize - (cellWidth + 1) * cellSpacing) / 2),
  Math.round((height - cellHeight * cellSize - (cellHeight + 1) * cellSpacing) / 2)
);

context.fillStyle = "#fff";
for (var y = 0, i = 0; y < cellHeight; ++y) {
  for (var x = 0; x < cellWidth; ++x, ++i) {
    fillCell(i);
    if (cells[i] & S) fillSouth(i);
    if (cells[i] & E) fillEast(i);
  }
}

d3.timer(function() {
  if (!(n0 = frontier.length)) return true;

  context.fillStyle = d3.hsl(distance++ % 360, 1, .5) + "";

  if (distance & 1) {
    for (var i = 0; i < n0; ++i) {
      fillCell(frontier[i]);
    }
  } else {
    var frontier1 = [],
        i0,
        i1,
        n0;

    for (var i = 0; i < n0; ++i) {
      i0 = frontier[i];
      if (cells[i0] & E && !visited[i1 = i0 + 1]) visited[i1] = true, fillEast(i0), frontier1.push(i1);
      if (cells[i0] & W && !visited[i1 = i0 - 1]) visited[i1] = true, fillEast(i1), frontier1.push(i1);
      if (cells[i0] & S && !visited[i1 = i0 + cellWidth]) visited[i1] = true, fillSouth(i0), frontier1.push(i1);
      if (cells[i0] & N && !visited[i1 = i0 - cellWidth]) visited[i1] = true, fillSouth(i1), frontier1.push(i1);
    }

    frontier = frontier1;
  }
});

function fillCell(i) {
  var x = i % cellWidth, y = i / cellWidth | 0;
  context.fillRect(x * cellSize + (x + 1) * cellSpacing, y * cellSize + (y + 1) * cellSpacing, cellSize, cellSize);
}

function fillEast(i) {
  var x = i % cellWidth, y = i / cellWidth | 0;
  context.fillRect((x + 1) * (cellSize + cellSpacing), y * cellSize + (y + 1) * cellSpacing, cellSpacing, cellSize);
}

function fillSouth(i) {
  var x = i % cellWidth, y = i / cellWidth | 0;
  context.fillRect(x * cellSize + (x + 1) * cellSpacing, (y + 1) * (cellSize + cellSpacing), cellSize, cellSpacing);
}

function generateMaze(cellWidth, cellHeight) {
  var cells = new Array(cellWidth * cellHeight),
      frontier = [],
      startIndex = (cellHeight - 1) * cellWidth;

  cells[startIndex] = 0;
  frontier.push({index: startIndex, direction: N});
  frontier.push({index: startIndex, direction: E});

  while ((edge = popRandom(frontier)) != null) {
    var edge,
        i0 = edge.index,
        d0 = edge.direction,
        i1 = i0 + (d0 === N ? -cellWidth : d0 === S ? cellWidth : d0 === W ? -1 : +1),
        x0 = i0 % cellWidth,
        y0 = i0 / cellWidth | 0,
        x1,
        y1,
        d1,
        open = cells[i1] == null; // opposite not yet part of the maze

    if (d0 === N) x1 = x0, y1 = y0 - 1, d1 = S;
    else if (d0 === S) x1 = x0, y1 = y0 + 1, d1 = N;
    else if (d0 === W) x1 = x0 - 1, y1 = y0, d1 = E;
    else x1 = x0 + 1, y1 = y0, d1 = W;

    if (open) {
      cells[i0] |= d0, cells[i1] |= d1;
      if (y1 > 0 && cells[i1 - cellWidth] == null) frontier.push({index: i1, direction: N});
      if (y1 < cellHeight - 1 && cells[i1 + cellWidth] == null) frontier.push({index: i1, direction: S});
      if (x1 > 0 && cells[i1 - 1] == null) frontier.push({index: i1, direction: W});
      if (x1 < cellWidth - 1 && cells[i1 + 1] == null) frontier.push({index: i1, direction: E});
    }
  }

  return cells;
}

function popRandom(array) {
  if (!array.length) return;
  var n = array.length, i = Math.random() * n | 0, t;
  t = array[i], array[i] = array[n - 1], array[n - 1] = t;
  return array.pop();
}

d3.select(self.frameElement).style("height", height + "px");

</script>
```

## Random Traversal III
A [spanning tree](http://en.wikipedia.org/wiki/Spanning_tree) of the canvas is generated using [random traversal](https://gist.github.com/mbostock/70a28267db0354261476) and then flooded with color. Hue encodes [Manhattan distance](http://en.wikipedia.org/wiki/Taxicab_geometry) from the root of the tree. (This is not an optimal visual encoding, but it suffices and is pretty.)

Spanning trees can also be used to generate mazes. See a maze generated with random traversal [flooded with color](https://gist.github.com/mbostock/11167589), and compare color floods of spanning trees generated with random traversal to [randomized depth-first traversal](https://gist.github.com/mbostock/949c772b81296f8e4188), [Wilson’s algorithm](https://gist.github.com/mbostock/11363008) and [Prim’s algorithm](https://gist.github.com/mbostock/11377353).
generate-random-traversal.js
```js
var N = 1 << 0,
    S = 1 << 1,
    W = 1 << 2,
    E = 1 << 3;

self.addEventListener("message", function(event) {
  postMessage(generateMaze(event.data.width, event.data.height));
});

function generateMaze(cellWidth, cellHeight) {
  var cells = new Array(cellWidth * cellHeight),
      frontier = [],
      startIndex = (cellHeight - 1) * cellWidth;

  cells[startIndex] = 0;
  frontier.push({index: startIndex, direction: N});
  frontier.push({index: startIndex, direction: E});

  while ((edge = popRandom(frontier)) != null) {
    var edge,
        i0 = edge.index,
        d0 = edge.direction,
        i1 = i0 + (d0 === N ? -cellWidth : d0 === S ? cellWidth : d0 === W ? -1 : +1),
        x0 = i0 % cellWidth,
        y0 = i0 / cellWidth | 0,
        x1,
        y1,
        d1,
        open = cells[i1] == null; // opposite not yet part of the maze

    if (d0 === N) x1 = x0, y1 = y0 - 1, d1 = S;
    else if (d0 === S) x1 = x0, y1 = y0 + 1, d1 = N;
    else if (d0 === W) x1 = x0 - 1, y1 = y0, d1 = E;
    else x1 = x0 + 1, y1 = y0, d1 = W;

    if (open) {
      cells[i0] |= d0, cells[i1] |= d1;
      if (y1 > 0 && cells[i1 - cellWidth] == null) frontier.push({index: i1, direction: N});
      if (y1 < cellHeight - 1 && cells[i1 + cellWidth] == null) frontier.push({index: i1, direction: S});
      if (x1 > 0 && cells[i1 - 1] == null) frontier.push({index: i1, direction: W});
      if (x1 < cellWidth - 1 && cells[i1 + 1] == null) frontier.push({index: i1, direction: E});
    }
  }

  return cells;
}

function popRandom(array) {
  if (!array.length) return;
  var n = array.length, i = Math.random() * n | 0, t;
  t = array[i], array[i] = array[n - 1], array[n - 1] = t;
  return array.pop();
}
```

index.html
```html
<!DOCTYPE html>
<meta charset="utf-8">
<canvas width="960" height="500"></canvas>
<script src="//d3js.org/d3.v3.min.js"></script>
<script>

var canvas = d3.select("canvas"),
    context = canvas.node().getContext("2d"),
    width = canvas.property("width"),
    height = canvas.property("height");

var worker = new Worker("generate-random-traversal.js");
worker.postMessage({width: width, height: height});
worker.addEventListener("message", function(event) {
  worker.terminate();

  var N = 1 << 0,
      S = 1 << 1,
      W = 1 << 2,
      E = 1 << 3;

  var cells = event.data,
      distance = 0,
      visited = new Array(width * height),
      frontier = [(height - 1) * width],
      image = context.createImageData(width, height);

  function flood() {
    var frontier1 = [],
        i0,
        n0 = frontier.length,
        i1,
        color = d3.hsl((distance += .5) % 360, 1, .5).rgb();

    for (var i = 0; i < n0; ++i) {
      i0 = frontier[i] << 2;
      image.data[i0 + 0] = color.r;
      image.data[i0 + 1] = color.g;
      image.data[i0 + 2] = color.b;
      image.data[i0 + 3] = 255;
    }

    for (var i = 0; i < n0; ++i) {
      i0 = frontier[i];
      if (cells[i0] & E && !visited[i1 = i0 + 1]) visited[i1] = true, frontier1.push(i1);
      if (cells[i0] & W && !visited[i1 = i0 - 1]) visited[i1] = true, frontier1.push(i1);
      if (cells[i0] & S && !visited[i1 = i0 + width]) visited[i1] = true, frontier1.push(i1);
      if (cells[i0] & N && !visited[i1 = i0 - width]) visited[i1] = true, frontier1.push(i1);
    }

    frontier = frontier1;
    return !frontier1.length;
  }

  d3.timer(function() {
    for (var i = 0, done; i < 1 && !(done = flood()); ++i);
    context.putImageData(image, 0, 0);
    return done;
  });
});

</script>
```

## Randomized Depth-First III
A [spanning tree](http://en.wikipedia.org/wiki/Spanning_tree) of the canvas is generated using [randomized depth-first traversal](https://gist.github.com/mbostock/1ef3b1fb9eb35ca8ffff) and then flooded with color. Hue encodes [Manhattan distance](http://en.wikipedia.org/wiki/Taxicab_geometry) from the root of the tree. (This is not an optimal visual encoding, but it suffices and is pretty.)

Spanning trees can also be used to generate mazes. See a maze generated with randomized depth-first traversal [flooded with color](https://gist.github.com/mbostock/97f1cdb9e0a695cd8df4), and compare color floods of spanning trees generated by [random traversal](https://gist.github.com/mbostock/11337835), [Prim’s algorithm](https://gist.github.com/mbostock/11377353), and [Wilson’s algorithm](https://gist.github.com/mbostock/11363008).

generate-randomized-depth-first-traversal.js
```js
var N = 1 << 0,
    S = 1 << 1,
    W = 1 << 2,
    E = 1 << 3;

self.addEventListener("message", function(event) {
  postMessage(generateMaze(event.data.width, event.data.height));
});

function generateMaze(cellWidth, cellHeight) {
  var cells = new Array(cellWidth * cellHeight), // each cell’s edge bits
      frontier = [];

  var start = (cellHeight - 1) * cellWidth;
  cells[start] = 0;
  frontier.push({index: start, direction: N});
  frontier.push({index: start, direction: E});
  shuffle(frontier, 0, 2);
  while (!exploreFrontier());
  return cells;

  function exploreFrontier() {
    if ((edge = frontier.pop()) == null) return true;

    var edge,
        i0 = edge.index,
        d0 = edge.direction,
        i1 = i0 + (d0 === N ? -cellWidth : d0 === S ? cellWidth : d0 === W ? -1 : +1),
        x0 = i0 % cellWidth,
        y0 = i0 / cellWidth | 0,
        x1,
        y1,
        d1,
        open = cells[i1] == null; // opposite not yet part of the maze

    if (d0 === N) x1 = x0, y1 = y0 - 1, d1 = S;
    else if (d0 === S) x1 = x0, y1 = y0 + 1, d1 = N;
    else if (d0 === W) x1 = x0 - 1, y1 = y0, d1 = E;
    else x1 = x0 + 1, y1 = y0, d1 = W;

    if (open) {
      cells[i0] |= d0, cells[i1] |= d1;

      var m = 0;
      if (y1 > 0 && cells[i1 - cellWidth] == null) frontier.push({index: i1, direction: N}), ++m;
      if (y1 < cellHeight - 1 && cells[i1 + cellWidth] == null) frontier.push({index: i1, direction: S}), ++m;
      if (x1 > 0 && cells[i1 - 1] == null) frontier.push({index: i1, direction: W}), ++m;
      if (x1 < cellWidth - 1 && cells[i1 + 1] == null) frontier.push({index: i1, direction: E}), ++m;
      shuffle(frontier, frontier.length - m, frontier.length);
    }
  }
}

function shuffle(array, i0, i1) {
  var m = i1 - i0, t, i, j;
  while (m) {
    i = Math.random() * m-- | 0;
    t = array[m + i0], array[m + i0] = array[i + i0], array[i + i0] = t;
  }
  return array;
}
```
index.html
```html
<!DOCTYPE html>
<meta charset="utf-8">
<canvas width="960" height="500"></canvas>
<script src="//d3js.org/d3.v3.min.js"></script>
<script>

var canvas = d3.select("canvas"),
    context = canvas.node().getContext("2d"),
    width = canvas.property("width"),
    height = canvas.property("height");

var worker = new Worker("generate-randomized-depth-first-traversal.js");
worker.postMessage({width: width, height: height});
worker.addEventListener("message", function(event) {
  worker.terminate();

  var N = 1 << 0,
      S = 1 << 1,
      W = 1 << 2,
      E = 1 << 3;

  var cells = event.data,
      distance = 0,
      visited = new Array(width * height),
      frontier = [(height - 1) * width],
      image = context.createImageData(width, height);

  function flood() {
    var frontier1 = [],
        i0,
        n0 = frontier.length,
        i1,
        color = d3.hsl((distance += .5) % 360, 1, .5).rgb();

    for (var i = 0; i < n0; ++i) {
      i0 = frontier[i] << 2;
      image.data[i0 + 0] = color.r;
      image.data[i0 + 1] = color.g;
      image.data[i0 + 2] = color.b;
      image.data[i0 + 3] = 255;
    }

    for (var i = 0; i < n0; ++i) {
      i0 = frontier[i];
      if (cells[i0] & E && !visited[i1 = i0 + 1]) visited[i1] = true, frontier1.push(i1);
      if (cells[i0] & W && !visited[i1 = i0 - 1]) visited[i1] = true, frontier1.push(i1);
      if (cells[i0] & S && !visited[i1 = i0 + width]) visited[i1] = true, frontier1.push(i1);
      if (cells[i0] & N && !visited[i1 = i0 - width]) visited[i1] = true, frontier1.push(i1);
    }

    frontier = frontier1;
    return !frontier1.length;
  }

  d3.timer(function() {
    for (var i = 0, done; i < 20 && !(done = flood()); ++i);
    context.putImageData(image, 0, 0);
    return done;
  });
});

</script>
```

## Prim’s Algorithm III
A spanning tree of the canvas is generated using Prim’s algorithm and then flooded with color. Hue encodes Manhattan distance from the root of the tree. (This is not an optimal visual encoding, but it suffices and is pretty.)

Spanning trees can also be used to generate mazes. See a maze generated with Prim’s algorithm flooded with color, and compare color floods of spanning trees generated with Prim’s algorithm to random traversal, randomized depth-first traversal and Wilson’s algorithm.
generate-prims.js
```js
var N = 1 << 0,
    S = 1 << 1,
    W = 1 << 2,
    E = 1 << 3;

self.addEventListener("message", function(event) {
  postMessage(generateMaze(event.data.width, event.data.height));
});

function generateMaze(cellWidth, cellHeight) {
  var cells = new Array(cellWidth * cellHeight),
      frontier = minHeap(function(a, b) { return a.weight - b.weight; }),
      startIndex = (cellHeight - 1) * cellWidth;

  cells[startIndex] = 0;
  frontier.push({index: startIndex, direction: N, weight: Math.random()});
  frontier.push({index: startIndex, direction: E, weight: Math.random()});

  while ((edge = frontier.pop()) != null) {
    var edge,
        i0 = edge.index,
        d0 = edge.direction,
        i1 = i0 + (d0 === N ? -cellWidth : d0 === S ? cellWidth : d0 === W ? -1 : +1),
        x0 = i0 % cellWidth,
        y0 = i0 / cellWidth | 0,
        x1,
        y1,
        d1,
        open = cells[i1] == null; // opposite not yet part of the maze

    if (d0 === N) x1 = x0, y1 = y0 - 1, d1 = S;
    else if (d0 === S) x1 = x0, y1 = y0 + 1, d1 = N;
    else if (d0 === W) x1 = x0 - 1, y1 = y0, d1 = E;
    else x1 = x0 + 1, y1 = y0, d1 = W;

    if (open) {
      cells[i0] |= d0, cells[i1] |= d1;
      if (y1 > 0 && cells[i1 - cellWidth] == null) frontier.push({index: i1, direction: N, weight: Math.random()});
      if (y1 < cellHeight - 1 && cells[i1 + cellWidth] == null) frontier.push({index: i1, direction: S, weight: Math.random()});
      if (x1 > 0 && cells[i1 - 1] == null) frontier.push({index: i1, direction: W, weight: Math.random()});
      if (x1 < cellWidth - 1 && cells[i1 + 1] == null) frontier.push({index: i1, direction: E, weight: Math.random()});
    }
  }

  return cells;
}

function minHeap(compare) {
  var heap = {},
      array = [],
      size = 0;

  heap.empty = function() {
    return !size;
  };

  heap.push = function(value) {
    up(array[size] = value, size++);
    return size;
  };

  heap.pop = function() {
    if (size <= 0) return;
    var removed = array[0], value;
    if (--size > 0) value = array[size], down(array[0] = value, 0);
    return removed;
  };

  function up(value, i) {
    while (i > 0) {
      var j = ((i + 1) >> 1) - 1,
          parent = array[j];
      if (compare(value, parent) >= 0) break;
      array[i] = parent;
      array[i = j] = value;
    }
  }

  function down(value, i) {
    while (true) {
      var r = (i + 1) << 1,
          l = r - 1,
          j = i,
          child = array[j];
      if (l < size && compare(array[l], child) < 0) child = array[j = l];
      if (r < size && compare(array[r], child) < 0) child = array[j = r];
      if (j === i) break;
      array[i] = child;
      array[i = j] = value;
    }
  }

  return heap;
}
```
index.html

```html
<!DOCTYPE html>
<meta charset="utf-8">
<canvas width="960" height="500"></canvas>
<script src="//d3js.org/d3.v3.min.js"></script>
<script>

var canvas = d3.select("canvas"),
    context = canvas.node().getContext("2d"),
    width = canvas.property("width"),
    height = canvas.property("height");

var worker = new Worker("generate-prims.js");
worker.postMessage({width: width, height: height});
worker.addEventListener("message", function(event) {
  worker.terminate();

  var N = 1 << 0,
      S = 1 << 1,
      W = 1 << 2,
      E = 1 << 3;

  var cells = event.data,
      distance = 0,
      visited = new Array(width * height),
      frontier = [(height - 1) * width],
      image = context.createImageData(width, height);

  function flood() {
    var frontier1 = [],
        i0,
        n0 = frontier.length,
        i1,
        color = d3.hsl((distance += .5) % 360, 1, .5).rgb();

    for (var i = 0; i < n0; ++i) {
      i0 = frontier[i] << 2;
      image.data[i0 + 0] = color.r;
      image.data[i0 + 1] = color.g;
      image.data[i0 + 2] = color.b;
      image.data[i0 + 3] = 255;
    }

    for (var i = 0; i < n0; ++i) {
      i0 = frontier[i];
      if (cells[i0] & E && !visited[i1 = i0 + 1]) visited[i1] = true, frontier1.push(i1);
      if (cells[i0] & W && !visited[i1 = i0 - 1]) visited[i1] = true, frontier1.push(i1);
      if (cells[i0] & S && !visited[i1 = i0 + width]) visited[i1] = true, frontier1.push(i1);
      if (cells[i0] & N && !visited[i1 = i0 - width]) visited[i1] = true, frontier1.push(i1);
    }

    frontier = frontier1;
    return !frontier1.length;
  }

  d3.timer(function() {
    for (var i = 0, done; i < 3 && !(done = flood()); ++i);
    context.putImageData(image, 0, 0);
    return done;
  });
});

</script>
```

## Wilson’s Algorithm III
A [spanning tree](http://en.wikipedia.org/wiki/Spanning_tree) of the canvas is generated using [Wilson’s algorithm](https://gist.github.com/mbostock/11357811) and then flooded with color. Hue encodes [Manhattan distance](http://en.wikipedia.org/wiki/Taxicab_geometry) from the root of the tree. (This is not an optimal visual encoding, but it suffices and is pretty.)

Spanning trees can also be used to generate mazes. See a maze generated with Wilson’s algorithm [flooded with color](https://gist.github.com/mbostock/c03ee31334ee89abad83), and compare color floods of spanning trees generated with Wilson’s algorithm to [random traversal](https://gist.github.com/mbostock/11337835), [randomized depth-first traversal](https://gist.github.com/mbostock/949c772b81296f8e4188) and [Prim’s algorithm](https://gist.github.com/mbostock/11377353).

generate-wilsons.js
```js
var N = 1 << 0,
    S = 1 << 1,
    W = 1 << 2,
    E = 1 << 3;

self.addEventListener("message", function(event) {
  postMessage(generateMaze(event.data.width, event.data.height));
});

function generateMaze(width, height) {
  var cells = new Array(width * height), // each cell’s edge bits
      remaining = range(width * height), // cell indexes to visit
      previous = new Array(width * height); // current random walk

  // Add the starting cell.
  var start = remaining.pop();
  cells[start] = 0;

  // While there are remaining cells,
  // add a loop-erased random walk to the maze.
  while (!loopErasedRandomWalk());

  return cells;

  function loopErasedRandomWalk() {
    var i0,
        i1,
        x0,
        y0;

    // Pick a location that’s not yet in the maze (if any).
    do if ((i0 = remaining.pop()) == null) return true;
    while (cells[i0] >= 0);

    // Perform a random walk starting at this location,
    previous[i0] = i0;
    while (true) {
      x0 = i0 % width;
      y0 = i0 / width | 0;

      // picking a legal random direction at each step.
      i1 = Math.random() * 4 | 0;
      if (i1 === 0) { if (y0 <= 0) continue; --y0, i1 = i0 - width; }
      else if (i1 === 1) { if (y0 >= height - 1) continue; ++y0, i1 = i0 + width; }
      else if (i1 === 2) { if (x0 <= 0) continue; --x0, i1 = i0 - 1; }
      else { if (x0 >= width - 1) continue; ++x0, i1 = i0 + 1; }

      // If this new cell was visited previously during this walk,
      // erase the loop, rewinding the path to its earlier state.
      if (previous[i1] >= 0) eraseWalk(i0, i1);

      // Otherwise, just add it to the walk.
      else previous[i1] = i0;

      // If this cell is part of the maze, we’re done walking.
      if (cells[i1] >= 0) {

        // Add the random walk to the maze by backtracking to the starting cell.
        // Also erase this walk’s history to not interfere with subsequent walks.
        while ((i0 = previous[i1]) !== i1) {
          if (i1 === i0 + 1) cells[i0] |= E, cells[i1] |= W;
          else if (i1 === i0 - 1) cells[i0] |= W, cells[i1] |= E;
          else if (i1 === i0 + width) cells[i0] |= S, cells[i1] |= N;
          else cells[i0] |= N, cells[i1] |= S;
          previous[i1] = NaN;
          i1 = i0;
        }

        previous[i1] = NaN;
        return;
      }

      i0 = i1;
    }
  }

  function eraseWalk(i0, i2) {
    var i1;
    do i1 = previous[i0], previous[i0] = NaN, i0 = i1; while (i1 !== i2);
  }
}

function range(n) {
  var range = new Array(n), i = -1;
  while (++i < n) range[i] = i;
  return range;
}
```
index.html
```html
<!DOCTYPE html>
<meta charset="utf-8">
<style>

#wait {
  padding: 10px;
}

</style>
<div id="wait">Please wait a moment; this is hard.</div>
<canvas width="960" height="500"></canvas>
<script src="//d3js.org/d3.v3.min.js"></script>
<script>

var canvas = d3.select("canvas"),
    context = canvas.node().getContext("2d"),
    width = canvas.property("width"),
    height = canvas.property("height");

var worker = new Worker("generate-wilsons.js");
worker.postMessage({width: width, height: height});
worker.addEventListener("message", function(event) {
  worker.terminate();

  var N = 1 << 0,
      S = 1 << 1,
      W = 1 << 2,
      E = 1 << 3;

  var cells = event.data,
      distance = 0,
      visited = new Array(width * height),
      frontier = [(height - 1) * width],
      image = context.createImageData(width, height);

  d3.select("#wait").transition()
      .style("opacity", 0)
      .remove();

  function flood() {
    var frontier1 = [],
        i0,
        n0 = frontier.length,
        i1,
        color = d3.hsl((distance += .5) % 360, 1, .5).rgb();

    for (var i = 0; i < n0; ++i) {
      i0 = frontier[i] << 2;
      image.data[i0 + 0] = color.r;
      image.data[i0 + 1] = color.g;
      image.data[i0 + 2] = color.b;
      image.data[i0 + 3] = 255;
    }

    for (var i = 0; i < n0; ++i) {
      i0 = frontier[i];
      if (cells[i0] & E && !visited[i1 = i0 + 1]) visited[i1] = true, frontier1.push(i1);
      if (cells[i0] & W && !visited[i1 = i0 - 1]) visited[i1] = true, frontier1.push(i1);
      if (cells[i0] & S && !visited[i1 = i0 + width]) visited[i1] = true, frontier1.push(i1);
      if (cells[i0] & N && !visited[i1 = i0 - width]) visited[i1] = true, frontier1.push(i1);
    }

    frontier = frontier1;
    return !frontier1.length;
  }

  d3.timer(function() {
    for (var i = 0, done; i < 3 && !(done = flood()); ++i);
    context.putImageData(image, 0, 0);
    return done;
  });
});

</script>
```

## Randomized Depth-First IV

Applying a [tree layout](https://gist.github.com/mbostock/4339184) on [randomized depth-first traversal](https://gist.github.com/mbostock/1ef3b1fb9eb35ca8ffff).
```html
<!DOCTYPE html>
<meta charset="utf-8">
<style>

.link {
  fill: none;
  stroke: #000;
  stroke-width: 1.5px;
}

</style>
<body>
<script src="//d3js.org/d3.v3.min.js"></script>
<script>

var margin = {top: 20, right: 20, bottom: 20, left: 20},
    width = 960 - margin.left - margin.right,
    height = 500 - margin.top - margin.bottom;

var N = 1 << 0,
    S = 1 << 1,
    W = 1 << 2,
    E = 1 << 3;

var root = generateTree(40, 40);

var tree = d3.layout.tree()
    .size([height, width]);

var nodes = tree.nodes(root),
    links = tree.links(nodes);

var svg = d3.select("body").append("svg")
    .attr("width", width + margin.left + margin.right)
    .attr("height", height + margin.top + margin.bottom)
  .append("g")
    .attr("transform", "translate(" + margin.left + "," + margin.top + ")");

svg.selectAll(".link")
    .data(links)
  .enter().append("path")
    .attr("class", "link")
    .attr("d", function(d) { return "M" + d.source.y + "," + d.source.x + "L" + d.target.y + "," + d.target.x; });

function generateTree(width, height) {
  var cells = generateMaze(width, height), // each cell’s edge bits
      visited = d3.range(width * height).map(function() { return false; }),
      root = {index: cells.length - 1, children: []},
      frontier = [root],
      parent,
      child,
      childIndex,
      cell;

  while ((parent = frontier.pop()) != null) {
    cell = cells[parent.index];
    if (cell & E && !visited[childIndex = parent.index + 1]) visited[childIndex] = true, child = {index: childIndex, children: []}, parent.children.push(child), frontier.push(child);
    if (cell & W && !visited[childIndex = parent.index - 1]) visited[childIndex] = true, child = {index: childIndex, children: []}, parent.children.push(child), frontier.push(child);
    if (cell & S && !visited[childIndex = parent.index + width]) visited[childIndex] = true, child = {index: childIndex, children: []}, parent.children.push(child), frontier.push(child);
    if (cell & N && !visited[childIndex = parent.index - width]) visited[childIndex] = true, child = {index: childIndex, children: []}, parent.children.push(child), frontier.push(child);
  }

  return root;
}

function generateMaze(width, height) {
  var cells = new Array(width * height), // each cell’s edge bits
      frontier = [];

  var start = (height - 1) * width;
  cells[start] = 0;
  frontier.push({index: start, direction: N});
  frontier.push({index: start, direction: E});
  shuffle(frontier, 0, 2);
  while (!exploreFrontier());
  return cells;

  function exploreFrontier() {
    if ((edge = frontier.pop()) == null) return true;

    var edge,
        i0 = edge.index,
        d0 = edge.direction,
        i1 = i0 + (d0 === N ? -width : d0 === S ? width : d0 === W ? -1 : +1),
        x0 = i0 % width,
        y0 = i0 / width | 0,
        x1,
        y1,
        d1,
        open = cells[i1] == null; // opposite not yet part of the maze

    if (d0 === N) x1 = x0, y1 = y0 - 1, d1 = S;
    else if (d0 === S) x1 = x0, y1 = y0 + 1, d1 = N;
    else if (d0 === W) x1 = x0 - 1, y1 = y0, d1 = E;
    else x1 = x0 + 1, y1 = y0, d1 = W;

    if (open) {
      cells[i0] |= d0, cells[i1] |= d1;

      var m = 0;
      if (y1 > 0 && cells[i1 - width] == null) frontier.push({index: i1, direction: N}), ++m;
      if (y1 < height - 1 && cells[i1 + width] == null) frontier.push({index: i1, direction: S}), ++m;
      if (x1 > 0 && cells[i1 - 1] == null) frontier.push({index: i1, direction: W}), ++m;
      if (x1 < width - 1 && cells[i1 + 1] == null) frontier.push({index: i1, direction: E}), ++m;
      shuffle(frontier, frontier.length - m, frontier.length);
    }
  }

  function shuffle(array, i0, i1) {
    var m = i1 - i0, t, i, j;
    while (m) {
      i = Math.random() * m-- | 0;
      t = array[m + i0], array[m + i0] = array[i + i0], array[i + i0] = t;
    }
    return array;
  }
}

</script>
```