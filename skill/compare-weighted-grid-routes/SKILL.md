---
name: compare-weighted-grid-routes
description: "Compute and verify routes through a supplied bounded weighted grid, comparing total cost and search behavior under declared movement rules."
---

# Compare weighted grid routes

## When to use

A user or agent needs a least-cost route or a check of a pathfinding implementation on a discrete grid.

## Required inputs

- Grid cells, obstacles, start/goal and allowed moves
- Nonnegative cost semantics, including whether cost is paid on entry
- Desired algorithms and resource bounds

## Workflow

1. Validate the start/goal and traversable cells. Fix whether diagonal moves are allowed and what they cost before comparing algorithms.
2. Use Dijkstra as the reference for nonnegative costs. For A*, choose a heuristic admissible for the actual movement/cost model; Manhattan distance times minimum entry cost applies to an orthogonal grid.
3. Preserve deterministic tie-breaking for reproducible paths. Keep expanded-node count separate from measured runtime.
4. Recompute every returned route cost directly from its cells, check adjacency and obstacles, and compare with the reference optimum. A different path can have the same optimal cost.
5. Return no-route explicitly when appropriate. Do not alter walls or weights to manufacture a solution.

### Separate path validity from optimality

For each returned path, check endpoints, every move and every traversed cell before comparing cost. Then sum costs under the supplied convention. A path can be valid but nonoptimal, or optimal under the wrong cost convention. Record whether the start cell contributes cost.

Use a consistent tie-break only for reproducibility, not as part of the optimality claim. When benchmarking, separate wall-clock measurements from expanded-node counts and include enough repeated runs to avoid presenting timer noise as a performance conclusion.

### Preserve the A* optimality argument

Keep the grid, costs and heuristic fixed during one search, with h(goal)=0. Admissibility bounds the remaining cost; consistency additionally requires h(u) ≤ cost(u,v) + h(v) for every allowed move. An admissible but inconsistent heuristic can reach an already expanded cell more cheaply later. Reopen that cell and propagate the improved cost and predecessor, unless consistency has been established and the implementation's closed-set rule is justified. See the primary study [Inconsistent Heuristics](https://cdn.aaai.org/AAAI/2007/AAAI07-192.pdf), especially its reopening example.

Maintain the best discovered cost for each cell, relax only strict improvements, and discard obsolete priority-queue entries. Do not settle a cell when first enqueuing it or stop merely because the goal has been discovered. For standard A* with the conditions above and required reopening, stop when a current goal entry is removed at minimum g+h. The [NetworkX A* implementation](https://networkx.org/documentation/stable/_modules/networkx/algorithms/shortest_paths/astar.html) provides a concrete reference for improved-cost handling and goal removal. If a heuristic's admissibility is unverified, use h=0 or withhold the optimality claim.

**Fictional illustration, not executed:** An orthogonal two-row grid has top row S, A, X, G with entry costs 0, 4, 1, 5 and bottom row B, C, D, wall with entry costs 1, 1, 1. Start at S and target G. Let h(B)=8, h(C)=7, h(D)=6 and all other heuristic values be zero. These estimates never exceed the true remaining costs, but D to X violates consistency. A* first expands A and X, reaching X at cost 5. The later route S–B–C–D–X reaches X at cost 4. Reopening X allows cost 9 to G; permanently closing X can retain the cost-10 route. A proposed check should compare both implementations with Dijkstra and replay each route. No search was run for this illustration.

## Output

Routes, exact cost convention, verified total costs, search metrics and no-route cases. This is a discrete model, not real-world navigation.

## Verification and limits

Test same start/goal, disconnected regions, an expensive short route versus a cheaper longer route, and A* against Dijkstra across bounded generated grids.

## No-route result

Include the unchanged grid and the explored boundary when useful. No route is a legitimate outcome; do not remove user-specified obstacles to produce a visually satisfying answer.

A resource cutoff is not a no-route result. If time, memory, expansion limits or cancellation stop the search while work remains, report incomplete and preserve any independently verified route as feasible with optimality unresolved. A maximum permitted route cost is a separate constraint: exhausted search under that bound can establish only that no qualifying route was found within the bound, unless unrestricted unreachability is separately proved. Record which stopping condition applied; [NetworkX's cutoff contract](https://networkx.org/documentation/stable/reference/algorithms/generated/networkx.algorithms.shortest_paths.astar.astar_path.html) illustrates how cost pruning can exclude otherwise reachable paths.

## Worked example

An orthogonal 2×3 grid has start at top-left and goal at top-right. Entry costs across the top are [start, 9, 1], and all three bottom cells cost 1. The start costs 0 and there are no walls.

The direct top route enters the middle and goal for total 10. The route down, right, right, up enters four cells at cost 1 each, totaling 4. Dijkstra returns cost 4; a Manhattan heuristic multiplied by the minimum entry cost 1 is admissible for A* here. A* may choose the same path or another cost 4 path if one exists.

The report lists the cells and recomputed cost 4. It does not call the two-move direct route cheapest merely because it has fewer steps. If diagonal movement is later allowed, both the neighbor model and heuristic must be reconsidered.

## Evidence status

The worked example illustrates the stated inputs and reasoning. Unless an execution result is explicitly identified, it is not a claim that external services, real devices or user data were tested. Report actual checks and unrun stages on each use.
