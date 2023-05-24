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
- [Greedy Algorithm | wiki](https://en.wikipedia.org/wiki/Greedy_algorithm) : any algorithm that follows the problem-solving heuristic of making the locally optimal choice at each stage.
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
- One of the algorithms used to find the shortest path is called [Dijkstra's Algorithm](https://en.wikipedia.org/wiki/Dijkstra%27s_algorithm), which works by 1) picking an unvisited vertex with the lowest distance (from the starting point), 2) calculating the distance through it to each unvisited neighbor, and 3) updating the neighbor's distance if smaller value is calculated.
	- Basically, the algorithm calculates shortest path from a starting point to essentially all points.
	- ![[rjwv8f4g.bmp]]
	- The complexity of this algorithm is $O((m+n)\log n)$, where $m$ is the number of edges and $n$ is the number of nodes.

## Selection Sort
- [Selection Sort | wiki](https://en.wikipedia.org/wiki/Selection_sort) : A sorting algorithm that 1) finds a minimum/maximum value within an input list, 2) switches its place with the unsorted value on the farthest left (marking it as sorted), and 3) repeats the process with the list of remaining unsorted values as the new input list until all values are sorted.
- This algorithm has time complexity of $O(n^2)$.
- ![[Selection-Sort-Animation.gif]]

## Insertion Sort
- [Insertion Sort | wiki](https://en.wikipedia.org/wiki/Insertion_sort) : A sorting algorithm that builds the final sorted array one item at a time by comparisons.
- This algorithm has time complexity of $O(n^2)$.
- ![[Insertion-sort-example-300px.gif]]
- Although Insertion Sort is simple and not as efficient as more advanced sorting algorithms, it has many advantages;
	- Simple implementation : it can be written within 3 lines of C programming
	- Adaptive : it benefits from pre-sortedness of the input sequence
	- Stable : it does not change the relative order of elements with equal keys
	- In-place : it only requires a constant amount of additional memory in space
	- Online : it can sort a list as it receives it (it doesn't have to "know" all items to proceed)
- People naturally use Insertion Sort when they sort a deck of cards.

## Radix Sort
- [Radix Sort | wiki](https://en.wikipedia.org/wiki/Radix_sort) : A non-comparative sorting algorithm that works by distributing elements into buckets according to their radix (significant digit). If there are multiple significant digits, then the process is repeated for each significant digit while piling the buckets top-down left-right order;
- It is also called **Bucket Sort** and **Digital Sort**.
- Example of sorting integers
	- ![[11884_004_fig_014.jpg|400]] (initial values)
	- ![[11884_004_fig_015.jpg|400]] (buckets with the most significant digit)
	- ![[11884_004_fig_016.jpg|400]] (buckets with the second msd)
	- ![[11884_004_fig_017.jpg|400]] (buckets with the third msd)
- Radix Sort is also useful for sorting strings (a sequence of alphanumeric characters).
- The complexity of Radix Sort is $O(wn)$, where $w$ is the number of significant digits and $n$ is the number of items to sort.

## Quicksort
- [Quicksort | wiki](https://en.wikipedia.org/wiki/Quicksort) : A divide-and-conquer sorting algorithm that works by selecting a 'pivot' element from the array and partitioning the other elements into two sub-arrays according to whether they are less than or greater than the pivot.
- It is sometimes called **Partition-Exchange Sort**.
- Non-deterministic : Quicksort degenerates into Selection Sort if the minimum value was chosen for pivot instead of at random. It is important that the pivot is chosen at random. However, this means that the run time is not always the same.
- ![[Sorting_quicksort_anim.gif]]

## Merge Sort
- [Merge Sort | wiki](https://en.wikipedia.org/wiki/Merge_sort) : A comparison-based divide-and-conquer sorting algorithm that works by 1) divide the unsorted list into $n$ sublists containing one item (a list of one item is considered sorted), and 2) repeatedly merge sublists (by comparing items between two adjacent lists) to produce new sorted sublists until there is only one sublist remaining.
	1. ![[11884_004_fig_040.jpg]]
	2. ![[11884_004_fig_041.jpg]]
- Complexity of $O(n\log n)$.
- ![[Merge_sort_algorithm_diagram.svg|300]]
- ![[Merge-sort-example-300px.gif]]

## PageRank
- [Page Rank | wiki](https://en.wikipedia.org/wiki/PageRank)
### Power Method
- finding the importance of each web page based on two basic principles:
	1. The importance of a web page depends on the significance of the web pages that link to it—that is, on the importance of its backlinks.
	2. A web page divides its importance evenly over the web pages to which it links.
- ![[11884_005_fig_001.jpg]]
	- Find the importance of Page 3
		- Its backlinks are 2, 4, and 5
		- Take each backlinks and assume we know their own significance
		- Page 2 divides its importance over Pages 3 and 5. Therefore, Page 2 gives half its importance to Page 3.
		- Page 4 divides its importance over Pages 3 and 1. Therefore, Page 4 gives half its importance to Page 3.
		- Page 5 divides its importance over Pages 2, 3, and 4. Therefore, Page 5 gives a third of its importance to Page 3.
		- Let $r$ be Rank (importance), $P$ be Page, and $i$ be the number of Page.
			- $r(P_{3})$ is the importance of Page 3.
			- $r(P_{3}) = \frac{r(P_{2})}{2} + \frac{r(P_{4})}{2} + \frac{r(P_{5})}{3}$
		- Assume all of the pages start out with equal significance (of 1), and distribute the value to its votes (edges have fraction of its initial value, leaving nodes with 0).
			- ![[11884_005_fig_002.jpg]]
			- $r(P_{3}) = \frac{1}{2} + \frac{1}{2} + \frac{1}{3} = \frac{4}{3}$
	- Find the importance of all Pages
		- $r(P_{1}) = \frac{5}{6}$
		- $r(P_{2}) = \frac{8}{6}$
		- $r(P_{3}) = \frac{8}{6}$
		- $r(P_{4}) = \frac{4}{6}$
		- $r(P_{5}) = \frac{5}{6}$
	- Repeat the vote and distribution of importance with the current importance
		- ex. Page 3 gives $\frac{4}{3}\times\frac{1}{3}=\frac{4}{9}$ to Pages 1, 4, and 5
		- Repeated enough times, importance will remain the same (as shown in example below).
	- Instead of initial importance of 1, start with 0.2 (1 divided by 5). Repeat the vote and distribution six times.
		- ![[Pasted image 20230524110439.png|300]]
		- The result of sixth voting round is the same as the seventh. Voting stops here.
		- the Pages are ranked according to their importance - 3, 2, 5, 1, and 4.
- The graph can be represented as a matrix, which allows for further mathematical operations.
	- ![[11884_005_fig_003.jpg]] (Adjacency Matrix)
	- ![[11884_e1_312.jpg]] (Pagerank Vector)
	- ![[11884_e1_313.jpg]] (Hyperlink Matrix)
	- First Column == $r(P_{1})$ == Pagerank Vector $\times$ Hyperlink Matrix (Column 0)
		- ![[11884_e1_316.jpg]]
	- Let $\pi_{i}$ be the Pagerank Vector at iteration $i$, and $H$ be the Hyperlink Matrix.
		- $\pi_{i}=\pi_{i-1} \times H$
			- $\pi_{2}=\pi_{1} \times H$
			- ![[11884_e1_340.jpg]]
			- ![[11884_e1_341.jpg]]
		- As in every iteration, we multiply the result of the previous iteration by the hyperlink matrix, and in the end this is a series of products of the successive estimates of the pagerank vector by the hyperlink matrix.
		- this is equivalent to multiplying the initial pagerank vector with increasing powers of the hyperlink matrix.
		- this **method of calculating successive approximations** is called the [Power Method/Power Iteration](https://en.wikipedia.org/wiki/Power_iteration).

### Dangling Nodes
- Power Method can fail when a Page does not have any outgoing links, meaning it does not distribute its importance to any other Pages; a Page like this is called a Dangling Node, and it eventually causes all pagerank values to vanish.
- In such case, the solution is to assume this Dangling Node gave its importance to every pages (including itself).
- The distributed importance by voting can be interpreted as a probability that a user chooses one of the outgoing links. This user is referred to as **Surfer**.
- The solution to the Dangling Node is referred to as **Random Surfer**, to signify the fact that the surfer can teleport anywhere even if it is trapped in a page with no way out.

### Google Matrix
- Aside from Dangling Nodes, the Power Method can also fail when some nodes are excluded from a group of nodes, meaning that there aren't outgoing links coming out from the group of nodes. Those excluded nodes ends up with 0 importance.
- ![[11884_005_fig_005.jpg]] (Nodes 1 and 4 are excluded)
- ![[11884_e1_357.jpg]] ($S$ matrix)
	- Once the solution to the Dangling Nodes problem is applied to the Hyperlink Matrix, the resulting matrix is referred to as $S$ matrix.
- The solution to this problem is to modify the solution to the Dangling Nodes. That is, instead of just converting a zero vector to a vector that sums up to 1, increase the zero entries in a vector by some value and decrease the non-zero entries so that the whole row sums up to 1. The converted matrix is referred to as the **Google Matrix**.
	- ![[11884_e1_370.jpg]]

### The Full Definition of PageRank
1. Form the Google matrix of the graph.
2. Start with initial pagerank estimates, giving a pagerank of  $1/n$ to each page, where $n$ is the total number of pages.
3. Apply the power method, multiplying the pagerank vector by the Google matrix until the values of the pagerank vector converge.

## Neural Network

### Activation Function
- Step
	- ![[11884_006_fig_004.jpg]]
	- A neuron that uses the step function is called a **Perceptron**.
- Sigmoid
	- ![[11884_006_fig_005.jpg]]
- Tanh
	- ![[11884_006_fig_006.jpg]]
- Rectifier
	- ![[11884_006_fig_007.jpg]]
	- Neurons are often referred to as Units, and a neuron using the Rectifier is called ReLU (Rectified Linear Unit).
- 