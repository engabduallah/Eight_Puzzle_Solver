# Eight_Puzzle_Solver

![image](https://user-images.githubusercontent.com/87785000/126638319-ed14d9b4-b687-4ec3-b871-fe6bb7122316.png)

This Project is done by Eng. Abduallah Damash, and assigned to me by Asst. Prof. Dr. Meryem Erbilek as part of CNG483 (Int. to Comp. Vision) course.

If you have any issues or comments on the project, contact me on Linkedin (https://www.linkedin.com/in/engabduallah).

# Insight about the project:

build an 8-Puzzle solver based on fourth different types of AI algorithms, namely Breadth-First Search (BFS), Depth First Search (DFS),  Iterative Deeping Search (IDS), and A* search algorithms.

In the first part, it is required to create a data representation method to store the data while finding the goal state of the puzzle, such as stack, tree, or queue. 

In the second part, it is required to create a graphic user interface to facilitate the procedures of controlling the steps of the solution. Also, to represent and obtain the effects of using each algorithm in terms of memory usage, elapsed Time to find the solution, movements number to reach goal state, and the number of the nodes used to store the data. 

In the third part, it is required to implement the abovementioned algorithms on the initial state of 346, 108, 725 and observe the differences and results of memory usage and time consumption.

In the last part, it is required to implement the Monte-Carlo simulation by conducting a comprehensive simulation on many intimal states predetermined by the user to observe the disadvantage and advantages of each algorithm.

# Theoretical Background:
In this part, there is an explanation for each algorithm to provide simple background information before representing the implementation results. 

## Breadth-First Search (BFS) Algorithm:
The algorithm is one of the graph traversing techniques, a commonly used methodology for locating the vertex position in the graph or tree structure. The algorithm selects the root node and starts traversing the graph layer-wise so that all the nodes and their respective children's nodes are visited and explored. 

Figure 1 shows the flowchart of the algorithm. First, it starts by labeling the root cell. Second. It checks if there are any adjacent cells; if so, label them. If not, terminate the program. Then, it compares with the goal state; if they are the same, it ends the program. If not, it keeps iterating until it finds it or not. 

In order to implement the algorithm, you need to structure the data in the form of a queue or stack, as BFS selects a single node in a tree and then visits all the nodes adjacent to the selected node. BFS accesses these nodes one by one, increasing the computational load and memory usage as it stores all the data.

![image](https://user-images.githubusercontent.com/87785000/198877570-139603a3-d2ee-4b0e-bf4a-bb22967eed34.png)

## Depth First Search (DFS) Algorithm:
This algorithm is also one of the graph traversing techniques. The algorithm starts at the root node and explores as far as possible along each branch before backtracking. It differs from BFS because it goes deeply into each node rather than exploring all the nodes. In other words, it explores the nodes vertically while BFS explores horizontally layer by layer.

As shown in Figure 2, the algorithm starts by marking the neighborhood and then going deeper into the nodes as it treats the data as a stack by selecting the first element.  

This algorithm is practical when there is a pattern for the solution; that is, the solution tends to occur in the same depth of the tree. However, the algorithm's cost can be the worst when the tree contains cycles or deep solutions. Compared to BFS, this algorithm can find the solution more quickly than BFS with lower memory usage, but there is a risk of going into an infinite loop due to undetermined depth. 

![image](https://user-images.githubusercontent.com/87785000/198878065-b34b2733-2222-4eb6-8708-d37338a997ac.png)

## Iterative Deepening Search (IDS) Algorithm:
This algorithm can be considered more specifically iterative deepening depth-first search  (IDDFS). It also uses the graph traversing techniques in which a depth-limited version of depth-first search is run repeatedly with increasing depth limits until the goal is found. 

The algorithm is optimal like BFS but uses much less memory; at each iteration, it visits the nodes in the search tree in the same order as depth-first search, but the cumulative order in which nodes are first visited is effectively BFS.

The algorithm takes the same Time as DFS and BFS, but it is slower than both because it has a higher constant factor. Figure 3 shows the pseudocode of the algorithm. 

![image](https://user-images.githubusercontent.com/87785000/198878102-478bd984-b41e-4276-bdf9-7b82903b0a59.png)

## A* Search Algorithm: 
This algorithm is an informed search algorithm, or a best-first search, which is formulated in weighted graphs. That is, it starts from a specific starting node of a graph; it aims to find a path to the given goal node having the smallest cost. It does this by maintaining a tree of paths originating at the start node and extending those paths one edge at a time until its termination criterion is satisfied. Each iteration of its main loop needs to determine its paths to extend. It does so based on the path's cost and estimates the cost required to extend the path to the goal. Specifically, it selects the path that minimizes fn=gn+h(n).

Where n is the next node on the path, g(n) is the path's cost from the start node to n, and h(n) is a heuristic function that estimates the cost of the cheapest path from n to the goal. 

The algorithm terminates when the path it chooses to extend is from start to goal or no paths eligible to be extended. 
The heuristic function is problem-specific. If the heuristic function is admissible, meaning it never overestimates the actual cost to get to the goal, the algorithm is guaranteed to return a least-cost path from start to goal, as shown in Figure 4.

It is often used in many fields due to its completeness, optimality, and optimal efficiency. However, one major practical drawback is storing all generated nodes in memory.

![image](https://user-images.githubusercontent.com/87785000/198878136-1c38b999-996c-457d-83d5-5fef804b75e7.png)

**This  project  implemented  two admissible  heuristic  functions:Hamming  distanceand Manhattan distance.**

### Hamming Distance:
It is also known as the number of misplaced tiles. It is admissible since every tile out of place must be moved at least once in order to arrange them into the goal state.

### Manhattan Distance:
The Manhattan distance is calculated as the sum of the absolute differences between the two vectors. The Manhattan distance is an admissible heuristic because every tile has to be moved at least the number of spots in between itself and its correct position.

# Implementation Results:
In this part, there is an explanation for each assignment step. First, it starts with data representation, then GUI design. Second, it describes the implementation of each algorithm. In the end, it shows the Monto-Carlo Simulation with a detailed approach. 

## Data Representation Approach: 
In order to implement the algorithms, we need to keep track of each state. Thus, I created a class called "puzzle" that represents the data in a tree structure using MATLAB language. Puzzle class has the properties state and parent. The state is the current arrangement of the tiles for the 8-puzzle. The parent is the current node's predecessor. Figure 5 shows that the code used to create the tree.

![image](https://user-images.githubusercontent.com/87785000/198878248-b808c158-1a9d-4501-a2d3-5ea2b89d8114.png)

## GUI Design: 
The reason to select MATLAB language is its capabilities in creating GUI applications even though it is weak in object-oriented methods. 
Using App Designer from MATLAB, I created a GUI with three tabs, namely Puzzle Solver, Monte Carlo, and Monte Carlo Simulation for 100 Puzzles. 

### Puzzle Solver Tab: 
Figure 7 shows the tab, which mainly represents the configuration of the 8-puzzle with the options in solving the puzzle using the algorithms mentioned above. 
As shown in Figure 7, the user can enter the initial state of the puzzle as a complete number and then press the Enter button to show the configuration. For example, the state shown in Figure 6 can be entered as 346108725. Notice that the user needs to replace 9 as the blank position and enter the number without spaces. 

Also, another option is pressing the Shuffle button, which generates a random initial state.

![image](https://user-images.githubusercontent.com/87785000/198878396-7d0ffd14-fbc0-46f9-abbc-7b3ca0f572e9.png)


In order to obtain the solution of the entered initial state, the user needs to specify the type of the algorithm and a heuristic method if the algorithm A* is chosen. Then, the user needs to press the Solve button, and if the configuration is solvable, the solution path is shown in the white area. Also, the user can step into the solution step by step by pressing the move buttons. 

![image](https://user-images.githubusercontent.com/87785000/198878439-0ab760eb-c4cb-47aa-8925-4284e021e028.png)

### Monte Carlo Tab: 
Figure 8 shows the tab, which mainly lets the user generate a random number of puzzles based on the true distance from the goal state determined by the user and simulates all the generated puzzles on a selected signal algorithm.

The user should enter the number of puzzles to be generated according to the number of movements entered by the user. Then, the user presses the Generate Puzzle button to generate the puzzle states and press the Simulate button to show the graph. More details on how the puzzles are generated are provided in the upcoming sections. 
The bar graph contains the average memory usage, time consumption, and movement number to achieve the goal state.

![image](https://user-images.githubusercontent.com/87785000/198878451-7115ce68-e41d-453f-b65c-1592704e830b.png)

### Monte Carlo Simulation for 100 Puzzles Tab:
Figure 9 shows the tab, which mainly shows the simulation results over 100 initial states of the puzzles for true movements increasing from 5 to 30 moves away from the goal. 
These 100 puzzles were generated before using the same function to observe a comprehensive study on the effects of each algorithm. 

The tab shows the results in two formats: the histogram for average node usages, memory usage, and time consumption. Another tab to show the plot the performance of each algorithm in terms of time consumption and nodes usages on one graph.

![image](https://user-images.githubusercontent.com/87785000/198878582-a5794904-94aa-42ee-ba62-cb91a544952a.png)



## Algorithms Implementation:
This part discusses the implementation of each algorithm using as initial state the configuration shown in Figure 6. Each function returns four outputs: total Time,  total nodes used, total memory used, and total movements number.

The code tried to implement the flowchart of the algorithm carefully by using the appropriate built-in function in MATLAB.

### Breadth-First Search (BFS) Implementation: 
In order to implement the algorithm, I created a function called 'BFS' that receives the initial states and returns the performance output, as shown in Figure 10. rest of the code in the appendix.

![image](https://user-images.githubusercontent.com/87785000/198878752-c84cd5eb-3504-442e-8617-f72896fbf2e5.png)

After running the algorithm on the initial state asked in the assignment, the simulation result is shown in Figure 11. As shown in Figure 11, the number of nodes is high as the algorithm stores all the trees, overloading the memory spaces as expected. Also, it finds the solution fast as it takes only 0.82 milliseconds. 

![image](https://user-images.githubusercontent.com/87785000/198878792-3d8ce3e6-c25c-46fb-9b40-7da764981ca7.png)

### Depth-First Search (DFS) Implementation: 
In order to implement the algorithm, I created a function called 'DFS' that receives the initial states and returns the performance output, as shown in Figure 12. rest of the code in the appendix.

The problem in implementing this algorithm is that the depth of the tree is not known and is unpredictable, so to overcome this issue, I assumed that any goal state could be reached before the 81st depth, so it stops looking down a branch past the 81st level.

![image](https://user-images.githubusercontent.com/87785000/198878841-c1bca73c-346c-49bf-a12c-a5f1c53de78a.png)

After running the algorithm on the initial state asked in the assignment, the simulation result is shown in Figure 13. As shown in Figure 13, the number of the nodes is less than in BFS as the algorithm stores all the tree nodes vertically, explained before. However, as it goes into all the tree's depth, it consumes a huge amount of time as it is 77.9 milliseconds.

![image](https://user-images.githubusercontent.com/87785000/198878862-a9743910-76d2-46a4-afcf-563dd3ff58b9.png)

### Iterative Deepening Search (IDS) Implementation: 
In order to implement the algorithm, I created a function called 'IDS' that receives the initial states and returns the performance output, as shown in Figure 14. rest of the code in the appendix.

Also, in order to save time, I used the built-in stack structure to store the data instead of the tree structure, as shown in Figure 15.

![image](https://user-images.githubusercontent.com/87785000/198878890-83dd9b9b-6e1a-438e-a134-52da696c06c7.png)

![image](https://user-images.githubusercontent.com/87785000/198878905-6338f80a-f2af-4abb-9dd1-6dbe8149cfcc.png)

After running the algorithm on the initial state asked in the assignment, the simulation result is shown in Figure 16. As shown in Figure 16, the number of the nodes is increasing compared to  BFS and DFS as the algorithm explores until a maximum depth, which overloads the memory. However, as it goes into all the depth layer by layer, it consumes less time than DFS as it is 0.88 milliseconds.

![image](https://user-images.githubusercontent.com/87785000/198878937-dfd1db24-8562-4841-b2fb-01c8c705535e.png)

### A* Search Implementation: 
In order to implement the algorithm, I created a function called 'A_star' that receives the initial states and returns the performance output, as shown in Figure 17. rest of the code in the appendix.
Also, to implement the admissible heuristic function that contains the Manhattan distance and misplaced tiles, I created a function called 'heuristic' that takes the state and distance select and returns the cost, as shown in Figure 18.

![image](https://user-images.githubusercontent.com/87785000/198878961-102c6f8a-770c-407d-a535-3ef6a81db35c.png)

![image](https://user-images.githubusercontent.com/87785000/198878971-8813491a-02ce-4ab2-97ee-70df34da5ae9.png)

After running the algorithm on the initial state asked in the assignment, the simulation result is shown in Figure 19 for misplaced tiles as heuristic function and Figure 20 for Manhattan distance as heuristic function. 
Looking at Figures 19 and 20, one can say that A* is the optimal algorithm that finds the solution very fast. However, it stores many nodes, which is the disadvantage of this algorithm. Also, using Manhattan distance as a heuristic enhances the node's usages as it estimates cost-efficiently.

![image](https://user-images.githubusercontent.com/87785000/198879017-3af3dbde-50e1-404b-87bd-9657509d7ceb.png)

![image](https://user-images.githubusercontent.com/87785000/198879020-604ed1b6-70c0-4a00-b108-1654b83584b2.png)

Before moving on to the next section, in order to show the path to the solution, I create a function called 'reconstruct path' that takes the final node and returns the path, as shown in Figure 21.

![image](https://user-images.githubusercontent.com/87785000/198879036-09398ec8-b864-4a30-8b23-c659c4631e5e.png)














