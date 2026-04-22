# Maze Generation.En

> ## Overview

Mazele Dazzle supports **multiple maze generation algorithms**, allowing users to compare different maze styles and characteristics. All 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Maze Generation Algorithm Documentation

## Overview

Mazele Dazzle supports **multiple maze generation algorithms**, allowing users to compare different maze styles and characteristics. All algorithms generate perfect mazes - mazes where there is exactly one path between any two points, with no loops or isolated sections.

### Available Algorithms

1. **Recursive Backtracking (Default)** - Long winding corridors, fast generation
2. **Prim's Algorithm** - More branching, shorter passages
3. **Kruskal's Algorithm** - Balanced characteristics, treats maze as graph
4. **Wilson's Algorithm** - Perfectly unbiased, uniform distribution

## Algorithm 1: Recursive Backtracking (Default)

### Description

Recursive backtracking is a depth-first search algorithm that carves passages through a grid of cells by removing walls between adjacent cells. It guarantees the creation of a perfect maze with the following properties:

- **Connectivity**: Every cell is reachable from every other cell
- **No Loops**: There is exactly one path between any two cells
- **No Isolated Areas**: All cells are part of the same connected maze structure

### How It Works

1. **Initialization**
   - Create a grid of cells (rows × columns)
   - Each cell initially has all four walls intact (top, right, bottom, left)
   - Mark all cells as unvisited
   - Choose a starting cell (typically top-left corner)

2. **Main Algorithm Loop**
   ```
   1. Mark current cell as visited
   2. Get list of unvisited neighbors (adjacent cells)
   3. If unvisited neighbors exist:
      a. Choose one neighbor randomly
      b. Remove wall between current cell and chosen neighbor
      c. Push current cell onto stack
      d. Move to chosen neighbor (make it current)
      e. Repeat from step 1
   4. If no unvisited neighbors:
      a. Pop cell from stack
      b. Make it current cell
      c. Repeat from step 1
   5. If stack is empty:
      a. Algorithm complete
   ```

3. **Result**
   - A perfect maze with passages 

*[truncated — see source for full prompt]*