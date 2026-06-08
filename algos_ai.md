1. Characteristics of an Intelligent Algorithm

An intelligent algorithm is one that can make decisions and solve problems efficiently.

Characteristics
1. Goal-Oriented

Works towards achieving a specific objective.

Example:

Google Maps finding shortest route.
Chess AI trying to checkmate opponent.
2. Knowledge-Based

Uses stored information to make decisions.

Example:

Medical diagnosis systems.
3. Rational

Chooses the best possible action.

4. Adaptive

Can learn from experience.

Example:

Recommendation systems.
5. Efficient

Uses minimum time and resources.

2. State Space Representation

A problem can be represented as a collection of states.

Components
Initial State

Starting point.

Goal State

Desired solution.

Operators

Actions that move from one state to another.

State Space

All possible states reachable from the initial state.

Example: 8-Puzzle

Initial State

1 2 3
4 _ 6
7 5 8

Goal State

1 2 3
4 5 6
7 8 _

Every arrangement is a state.

3. Search Space Control

AI uses search techniques to explore state spaces.

Search algorithms are divided into:

A. Uninformed Search

Also called Blind Search.

No information about the goal location.

Algorithms:

BFS
DFS
Iterative Deepening
4. Breadth First Search (BFS)

Explores nodes level by level.

Working
A
|\
B C
|  \
D   E

Traversal:

A → B → C → D → E

Uses Queue (FIFO)

Advantages

✔ Complete

✔ Finds shortest path

Disadvantages

✘ High memory usage

Complexity

Time:

O(b
d
)

where

b = branching factor
d = depth
5. Depth First Search (DFS)

Explores one branch completely before backtracking.

Uses Stack (LIFO)

Traversal

A → B → D → C → E
Advantages

✔ Low memory

✔ Easy implementation

Disadvantages

✘ May get stuck in infinite path

✘ Doesn't guarantee shortest path

Complexity

Time:

O(b
m
)

m = maximum depth

6. Iterative Deepening Search (IDS)

Combination of BFS and DFS.

Idea

Perform DFS repeatedly with increasing depth limits.

Depth 0
A

Depth 1
A B C

Depth 2
A B D C E
Advantages

✔ Complete

✔ Optimal

✔ Less memory

Complexity

Time:

O(b
d
)

Memory:

O(bd)
Informed Search Algorithms

Uses additional knowledge called heuristic information.

7. Heuristics

A heuristic is a rule that estimates how close a state is to the goal.

Represented by:

h(n)

where

h(n) = estimated cost from node n to goal.

Example

In GPS:

Current City → Delhi

Straight-line distance acts as heuristic.

Good Heuristic
Fast
Accurate
Never overestimates
8. Hill Climbing Algorithm

A local search technique.

Moves toward better neighboring state.

Working
Start at current state.
Evaluate neighbors.
Move to best neighbor.
Repeat until goal.
Example

Climbing a hill to reach highest point.

       Peak
      /\
     /  \
    /    \
 Start
Problems
Local Maximum

Gets stuck at a small peak.

Plateau

No improvement possible.

Ridge

Difficult path to climb.

Advantages

✔ Simple

✔ Fast

Disadvantages

✘ Not guaranteed optimal solution

9. A* Algorithm

Most important AI search algorithm.

Combines:

Actual cost
Heuristic cost

Formula:

f(n)=g(n)+h(n)

Where:

g(n) = cost from start to node
h(n) = estimated cost to goal
f(n) = total estimated cost
Example
Start ----5---- A
   \
    2
     \
      B

A* chooses node with minimum f(n).

Advantages

✔ Complete

✔ Optimal

✔ Widely used in games and robotics

Applications
GPS navigation
Robot path planning
Network routing
10. Means-End Analysis

Problem-solving strategy.

Compares:

Current State ↔ Goal State

Finds differences and reduces them step-by-step.

Example

Goal:
Travel from Delhi to Mumbai

Difference:
Not in Mumbai

Action:
Take flight/train

Difference reduced.

Advantages

✔ Human-like reasoning

✔ Efficient

11. Stochastic Search

Uses randomness while searching.

Unlike deterministic search.

Examples
Genetic Algorithms
Simulated Annealing
Random Search
Applications
Machine Learning
Optimization Problems
Scheduling
12. Constraint Satisfaction Problem (CSP)

Problem where variables must satisfy constraints.

Components
Variables

Example:

X, Y, Z
Domain

Possible values.

X = {1,2,3}
Constraints

Rules.

X ≠ Y
Example

Sudoku

Variables:
Cells

Domain:
1–9

Constraint:
No repetition in row/column.

Applications
Timetabling
Scheduling
Map Coloring
Sudoku
Unit 2: Game Playing and Adversarial Search

Used when AI competes against an opponent.

Examples:

Chess
Tic Tac Toe
Checkers
Poker
13. Game Theory Basics

Study of strategic decision-making.

Players

Participants in game.

Actions

Possible moves.

Payoff

Reward received.

Strategy

Plan of action.

Types of Games
Zero-Sum Game

One player's gain = another player's loss.

Example:

Chess

+1 for winner
-1 for loser
Non-Zero Sum

Both can benefit.

Example:

Business negotiations.

14. Min-Max Algorithm

Used in two-player games.

Assumption:

AI = MAX player
Opponent = MIN player
Working

AI chooses move maximizing its score.

Opponent chooses move minimizing AI score.

Example Tree

          MAX
         /   \
       MIN   MIN
      / \    / \
     3   5  2   9

MIN nodes:

min(3,5)=3
min(2,9)=2

MAX node:

max(3,2)=3

Best move = 3

Applications
Chess
Checkers
Tic-Tac-Toe
Limitation

Very slow for large game trees.

15. Alpha-Beta Pruning

Optimization of Min-Max.

Avoids exploring branches that cannot affect final decision.

Parameters

Alpha (α)

Best value for MAX.

Beta (β)

Best value for MIN.

Condition

Prune when:

α≥β

This means further exploration is useless.

Advantages

✔ Same result as Min-Max

✔ Much faster

✔ Searches deeper game trees

Applications
Chess Engines
Go Programs
Strategy Games
