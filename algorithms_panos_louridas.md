# Algorithms
Algorithms by Panos Louridas

## Problem : Distribution of Two Sets
- Suppose we have two sets of objects; our goal is to spread the objects of one of the two sets (a set of X's) as evenly as possible among the objects of the other set (a set of O's).
- Case 1 (division w/o remainder) : If we have 3 X's and 9 O's, then we can place 1 X and 3 O and repeat 3 times; as such, we get an even distribution of two sets `XOOOXOOOXOOO`.
	- 9 divided by 3 is 3. So, we can place 3 O's for each X
- Case 2 (division w/ remainder) : we have 5 X's and 7 O's. The divisor is divided by the remainder (or vice versa, depending on which number is smaller), until the remainder is 1 or 0.
	- ![[11884_e1_004.jpg]]
	- ![[11884_e1_005.jpg]] (7/5 = 1 .. 2)
	- ![[11884_e1_006.jpg]] (5/2 = 1 .. 3)
	- ![[11884_e1_007.jpg]] (3/2 = 1 .. 1)
	- ![[11884_e1_008.jpg]] (concatenate, final result)
	- Not an even distribution, but it is distributed *as evenly as possible*.
- "Distribution of Two Sets" is a pattern that is often explored in music (rhythm); it can be interpreted mathematically, which means it can be written as an algorithm.
	- [Clave](<https://en.wikipedia.org/wiki/Clave_(rhythm)>) is a rhythmic pattern used as a tool for temporal organization in Cuban music.
	- [Godfried Toussaint](https://en.wikipedia.org/wiki/Godfried_Toussaint) (a Research Professor of Computer Science) made several mathematical analysis of clave and related African bell patterns using [Computational Geometry](https://en.wikipedia.org/wiki/Computational_geometry) and [Euclid's Algorithm](https://en.wikipedia.org/wiki/Euclidean_algorithm).
	- "Distribution of Two Sets" problem can be solved with Euclid's Algorithm, an algorithm which is used to compute a [Greatest Common Divisor (GCD)](https://en.wikipedia.org/wiki/Greatest_common_divisor) of two integers. 

## Measuring Algorithms
- We want to find the shortest path from the upper-left corner of the grid to the lower-right corner, without visiting the same place twice.
	- ![[11884_001_fig_003.jpg]] (3x3 grid)
	- The length of each path is equal to the number of links between points on the grid.
- One way to solve this problem is to "find all paths, measure how long each of them is, and pick up the shortest (or any of the shortest)".
	- Solving 3x3 grid with this method gives us 12 total paths, with 5 paths of length 4 (shortest).
	- 5x5 grid gives 8,512 paths. Larger grids gives exponentially bigger number of total paths.
	- The procedure for enumerating all paths and picking the shortest one is **undoubtedly correct**, and will always give us the shortest path—or any of the shortest paths, if there are many equally short ones—yet it is definitely **impractical**.
- When we study a problem and candidate algorithms for tackling it, we do it always with the size of the problem under consideration.
- The time required by an algorithm is related to its computational complexity. The computational complexity of an algorithm is the amount of resources it requires to run.
- two main kinds of resources here: time, how long it takes, and space, how much storage it requires in terms of computer memory.
	- The speed of a computer depends on the time it takes to execute basic operations. To get around such specificities, we instead choose to talk about the number of operations required to run an algorithm, not the actual time it takes on a specific computer to run these operations.

## The Big O Notation
- [Big O Notation | wiki](https://en.wikipedia.org/wiki/Big_O_notation) : a mathematical notation that describes the limiting behavior of a function when the argument tends towards a particular value or infinity.
	- The letter O stands for *Ordnung*, which means the [Order of Approximation](https://en.wikipedia.org/wiki/Order_of_approximation).
	- In Computer Science, big O notation is used to classify algorithms according to how their run time or space requirements grow as the input size grows.
- [Table of Common Time Complexities | wiki](https://en.wikipedia.org/wiki/Time_complexity#Table_of_common_time_complexities)
- Time == Complexity
- $O(1)$, **Constant Time** : The complexity notation used for algorithms that run in no more than constant time, no matter the input. It is the "fastest".
- $O(n)$, **Linear Time** : The complexity notation used for algorithms that run in unordered sequence - the time required to find a particular one in them will not be more than a multiple of the number of items.
- $O(n^2)$ , **Quadratic Time** : The complexity notation used for algorithms that multiply two $n$ digit numbers using long multiplication - the time required for the multiplication will not be more than a multiple of the square of the size of the numbers.
- $O(\log_{2}n)$, **Logarithmic Time** : The complexity notation used for algorithms that solve a problem by splitting it in two equal smaller problems (*Divide and Conquer*, aka *Binary Search*); most efficient way to search for something in a sorted group of items is denoted with this notation, and it is the 2nd fastest (first being Constant Time).
	- $\log_{2}n$ is referred to as [Binary Logarithm](https://en.wikipedia.org/wiki/Binary_logarithm), which is the [inverse function](https://en.wikipedia.org/wiki/Inverse_function) of the [Power of Two](https://en.wikipedia.org/wiki/Power_of_two) function.
		- #개인노트 the first application of binary logarithms was in Music Theory, by Leonhard Euler who discovered that the binary logarithm of a frequency ratio of two musical tones gives the number of octaves by which the tones differ.
		- In this book, the notation is written as $\lg n$
- $O(n\log_{2}n)$, **Loglinear/Linearithmic Time** : The complexity notation used for algorithms that have combined linear and logarithmic time, where their time grows by $n$ multiplied by its logarithm - the best algorithms for sorting (putting items in order) have this complexity.
	- An algorithm that sorts a list of items by comparing each item with all other items has time complexity of $O(n^2)$. Compared to that, $O(n\log_{2}n)$ is considerably better. In fact, it is the fastest possible for a comparison sort.
	- Fast Fourier transform has Loglinear Complexity.
- $O(n^k)$, **Polynomial Time** : The complexity notation used for algorithms where their time grows by $n$ raised to a constant power $k$. This complexity is considered efficient - except when $k$ is too big.
	- Not sure why, but the notation used in wiki is $2^{O(\log n)} = \textrm{poly}(n)$ .
- $O(k^n)$, **Exponential Time (with linear exponent)** : Not much explanation here, other than the fact any algorithm with this complexity is very expensive. Exponential growth is just nuts.
- $O(n!)$, **Factorial Time** : Factorial Growth is even worse than Exponential Growth because it is the product of all the natural numbers up to and INCLUDING that number.
	- This complexity occurs in a problem called **Traveling Salesman Problem** - which asks "if we have a list of cities and the distances between each pair of them, what is the shortest possible route that one should take to visit each city once and return to the origin city"; the simplest and the obvious way to solve it is to examine every possible path, and it runs on Factorial Time.
	- There aren't any practical way to solve the Traveling Salesman Problem, and problems that does not have any practical algorithm to solve them are said to be **intractable**.
	- The only way to solve any intractable problem in an acceptable time is **Approximation**.
- ![[11884_e1_181.jpg]]

## Graphs
- **Königsberg Bridge Problem** : Is it possible to make a tour of the city crossing all 7 bridges exactly once?
	- ![[11884_002_fig_001.jpg]]
	- Leonhard Euler said "NOPE", and explained it with *GRAPH*, making Euler the first to recognize graphs as a structure and explore their properties.
		- ![[11884_002_fig_002.jpg]]
		- ![[11884_002_fig_003.jpg]] (A graph consisting of Nodes/Vertices and Edges/Links)
- A **Path** in a graph is a sequence of edges that connect a sequence of nodes.
- **Eulerian Path (Eulerian Walk)** : a trail through a graph such that each edge is visited exactly once.
- The Königsberg Bridge Problem is a problem that requires finding a Eulerian Path.
- **Circuit (Tour)** refers to a closed path where the path ends where it starts.
- A graph is said to have a **Cycle** when it is possible to start from a node, traverse edges, and come back to the same node. Such a graph is referred to as **Cyclic Graph**.
- A graph without a cycle is called an **Acyclic Graph**.
- **Directed Acyclic Graphs (dags)** have many uses, such as using them to represent priorities between tasks, dependency relations, prerequisites, and other similar arrangements.

## Problem : Scheduling a Tournament
- Suppose you are organizing a tournament in which the contestants will compete in pairs, so we’ll have a series of matches. We have **eight contestants**, and **each contestant will play four matches**. Our problem is how to schedule the tournament. We want to schedule the matches so that **each contestant plays only one match per day**.
- This problem is solved by 1) take a match that hasn't been scheduled (stop if all matches are scheduled), and 2) schedule the match on the earliest day so that neither of the two players has another match on that day, and return to step 1.
- ![[11884_002_fig_008.jpg]]
- This kind of problem is referred to as the **Edge Coloring Problem**, which is a problem that asks us to assign colors to edges so that no two adjacent edges have the same color.

## Greedy Algorithm
- The "Algorithm" that was used to solve the "Scheduling a Tournament Problem" is referred to as **Greedy Algorithm**, which is an algorithm that solves a problem by finding the best solution at *each stage* instead of an optimal solution in general.
- Greedy Algorithms are useful when there is a choice to make at each stage, and the choice depends on "what looks best now".
- Strategies that guide our choices in the evolution of an algorithm are called **Heuristics**.
- "What looks best now" may not really be the best strategy, as it could lead to a trap later down the line.
	- Example : imagine climbing a mountain. The greedy heuristic would be to "select the steepest path at each point". This does not always lead to the top, as it could lead to a plateau where there isn't any other steep path available.
		- This example is referred to as **Hill Climbing Approach**. The plateau is referred to as Local Optimum (the trap), and the top is referred to as Global Optimum (the highest peak).
- The greedy algorithm that was used to solve the "Scheduling a Tournament Problem" is not guaranteed to give the optimal solution - that is, the solution requiring the *smallest* number of days.
	- One advantage of this algorithm is that it is an **Online Algorithm**, which is an algorithm that works even if the inputs are not known at the start but instead arrive on the scene as it progresses. The algorithm does not need to know all the edges at the start because it works on one edge at a time.
		- If players sign up after the scheduling has already begun, the algorithm has no problem scheduling the "late" participants.

## Shortest Path
- ![[11884_002_fig_010.jpg]]
- Finding the shortest path from A to F using a greedy heuristic would result with a path A-C-E-F with the length of 8. It is not the shortest path.
- One of the algorithms used to find the shortest path is called [Dijkstra's Algorithm](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm).
- 