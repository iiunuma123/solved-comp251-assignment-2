Download Link: https://assignmentchef.com/product/solved-comp251-assignment-2
<br>
Exercise 1 (Disjoint sets ) We want to implement a disjoint set data structure with union and find operations. The template for this program is available on the course website and named

DisjointSets.java.

In this question, we model a partition of <em>n </em>elements with distinct integers ranging from 0 to <em>n </em>− 1 (i.e. each element is represented by an integer in [0<em>,</em>··· <em>,n </em>− 1], and each integer in [0<em>,</em>··· <em>,n </em>− 1] represent one element). We choose to represent the disjoint sets with trees, and to implement the forest of trees with an array named par. More precisely, the value stored in par[i] is parent of the element i, and par[i]==i when i is the root of the tree and thus the representative of the disjoint set.

You will implement union by rank and the <em>path compression </em>technique seen in class. The rank is an integer associated with each node. Initially (i.e. when the set contains one single object) its value is 0. Union operations link the root of the tree with smaller rank to the root of the tree with larger rank. In the case where the rank of both trees is the same, the rank of the new root increases by 1. You can implement the rank with a specific array (called rank) that has been added to the template, or use the array par (this is tricky). Note that path compression does not change the rank of a node.

Download the file DisjointSets.java, and complete the methods find(int i) as well as union(int i, int j). The constructor takes one argument <em>n </em>(a strictly positive integer) that indicates the number of elements in the partition, and initializes it by assigning a separate set to each element.

The method find(int i) will return the representative of the disjoint set that contains i (do not forget to implement path compression here!). The method union(int i, int j) will merge the set with smaller rank (for instance i) in the disjoint set with larger rank (in that case j). In that case, the root of the tree containing i will become a child of the root of the tree containing j), and return the representative (as an integer) of the new merged set. Do not forget to update the ranks. In the case where the ranks are identical, you will merge i into j.

Once completed, compile and run the file DisjointSets.java. It should produce the output available in the file unionfind.txt available on the course website.

Note: You will need to complete this question to implement Exercise 2.

Exercise 2 (Minimum Spanning trees) We will implement the Kruskal algorithm to calculate the minimum spanning tree (MST) of an undirected weighted graph. Here you will use the file

DisjointSets.java completed in the previous question and two other files: WGraph.java and Kruskal.java available on the course website. You will need the classes DisjointSets and WGraph to execute Kruskal.java. Your role will be to complete two methods in the template

Kruskal.java.

The file WGraph.java implements two classes WGraph and Edge. An Edge object stores all informations about edges (i.e. the two vertices and the weight of the edge), which are used to build graphs.

The class WGraph has two constructors WGraph() and WGraph(String file). The first one creates an empty graph and the second uses a file to initialize a graph. Graphs are encoded using the following format. The first line of this file is a single integer <em>n </em>that indicates the number of nodes in the graph. Each vertex is labelled with an number in [0<em>,</em>··· <em>,n </em>− 1], and each integer in [0<em>,</em>··· <em>,n </em>− 1] represents one and only one vertex. The following lines respect the syntax “<em>n</em><sub>1 </sub><em>n</em><sub>2 </sub><em>w</em>”, where <em>n</em><sub>1 </sub>and <em>n</em><sub>2 </sub>are integers representing the nodes connected by an edge, and <em>w </em>the weight of this edge. <em>n</em><sub>1</sub>, <em>n</em><sub>2</sub>, and <em>w </em>must be separated by space(s). An example of such file can be found on the course website with the file g1.txt. These files will be used as an input in the program Kruskal.java to initialize the graphs. Thus, an example of a command line is java Kruskal g1.txt.

The class WGraph also provide a method addEdge(Edge e) that adds an edge to a graph (i.e. an object of this class). Another method listOfEdgesSorted() allows you to access the list of edges of a graph in the increasing order of their weight.

You task will be to complete the two static methods isSafe(DisjointSets p, Edge e) and kruskal(WGraph g) in Kruskal.java. The method isSafe considers a partition of the nodes <em>p </em>and an edge <em>e</em>, and should return True if it is safe to add the edge <em>e </em>to the MST, and False otherwise. The method kruskal will take a graph object of the class WGraph as an input, and return another WGraph object which will be the MST of the input graph.

Once completed, compile all the java files and run the command line java Kruskal g1.txt. An example of the expected output is available in the file mst1.txt. You are invited to run other examples of your own to verify that your program is correct. Note that you need to compile it with the two other files for it to work.

Exercise 3 (Greedy algorithms ) In this exercise, you will plan your homework with a greedy algorithm. The input is a list of homeworks defined by two arrays: deadlines and weights (the relative importance of the homework towards your final grade). These arrays have the same size and they contain integers between 1 and 100. The index of each entry in the arrays represents a single homework, for example, Homework 2 is defined as a homework with deadline deadlines[2] and weight weights[2]. Each homework takes exactly one hour to complete.

Your task is to output a homeworkPlan: an array of length equal to the last deadline. Each entry in the array represents a one-hour timeslot, starting at 0 and ending at ’last deadline – 1’. For each time slot, homeworkPlan indicates the homework which you plan to do during that slot. You can only complete a single homework in one 1-hour slot. The homeworks are due at the beginning of a time slot, in other words if an assignment’s deadline is x, then the last time slot when you can do it is x – 1. For example, if the homework is due at t=14, then you can complete it before or during the slot t=13. If your solution plans to do Homework 2 first, then you should have homeworkPlan[0]=2 in the output. Note that sometimes you will be given too much homework to complete in time, and that is okay.

Your homework plan should maximize the sum of the weights of completed assignments.

To organize your schedule, we give you a class HW_Sched.java, which defines an Assignment object, with a number (its index in the input array), a weight and a deadline.

The input arrays are unsorted. As part of the greedy algorithm, the template we provide sorts the homeworks using Java’s Collections.sort(). This sort function uses Java’s compare() method, which takes two objects as input, compares them, and outputs the order they should appear in. The template will ask you to override this compare() method, which will alter the way in which Assignments will be ordered. You have to determine what comparison criterion you want to use. Given two assignments A1 and A2, the method should output:

<ul>

 <li>0, if the two items are equivalent</li>

 <li>1, if a1 should appear after a2 in the sorted list</li>

 <li>-1, if a2 should appear after a1 in the sorted list</li>

</ul>

The compare method (called by Collections.sort()) should be the only tool you use to reorganize lists and arrays in this problem. You will then implement the rest of the SelectAssignments() method.

Submit all the Java files you modified on codePost.

Exercise 4 (Change-Making Problem) In this problem, we give a formal look at the problem of returning a given amount of money using the minimum number of coins (including bills), for a given coin system.

For example, the best way to give someone 7 dollars is to add up a 5 dollars bill and a 2 dollars coin. For simplicity, we will consider all denominations to be coins.

First, let us define the problem: a coin system is a <em>m</em>-tuple <em>c </em>= (<em>c</em><sub>1</sub><em>,c</em><sub>2</sub><em>,…,c<sub>m</sub></em>) such that <em>c</em><sub>1 </sub><em>&gt; c</em><sub>2 </sub><em>&gt; </em>··· <em>&gt; c<sub>m </sub></em>= 1. For a given coin system <em>c </em>and a positive integer <em>x </em>representing the amount of money we want to gather, we want to find a solution (a <em>m</em>-tuple of non-negative integers) <em>k </em>= (<em>k</em><sub>1</sub><em>,k</em><sub>2</sub><em>,…,k<sub>m</sub></em>) such that so as to minimize.

There exists a greedy algorithm to find the optimal solution for certain coin systems: for a given <em>x</em>, we select the largest coin <em>c<sub>i </sub></em>≤ <em>x</em>. Then, we repeat this step for <em>x </em>− <em>c<sub>i</sub></em>, and continue repeating it until <em>x </em>becomes 0. For instance, with the coin system (10<em>,</em>5<em>,</em>2<em>,</em>1), the algorithm decomposes <em>x </em>= 27 into 10<em>,</em>10<em>,</em>5<em>, </em>and 2.

We describe a coin system as <em>canonical </em>if and only if the solution given by the greedy algorithm described above is optimal for any positive integer <em>x</em>. For example, all systems (<em>a,</em>1) with <em>a &gt; </em>1 are canonical. For any positive integer <em>x</em>, we can express such a change system in the form of Euclidean division: <em>x </em>= <em>aq </em>+<em>r </em>with <em>r &lt; a</em>. The greedy solution for <em>x </em>is then the tuple <em>g </em>= (<em>q,r</em>). To prove that the solution is optimal, we can proceed as follows:

Let’s consider <em>g</em><sup>0 </sup>= (<em>q</em><sup>0</sup><em>,r</em><sup>0</sup>) different than <em>g </em>such that <em>x </em>= <em>aq</em><sup>0 </sup>+ <em>r</em><sup>0</sup>. Because <em>q </em>is already at its highest value under <em>x </em>and cannot be above <em>x</em>, we have <em>q</em><sup>0 </sup><em>&lt; q</em>, otherwise <em>q</em><sup>0 </sup>= <em>q </em>causes <em>g</em><sup>0 </sup>= <em>g</em>. Since (<em>q</em><sup>0 </sup>+<em>r</em><sup>0</sup>)−(<em>q </em>+<em>r</em>) = (<em>q</em><sup>0 </sup>+<em>x</em>−<em>aq</em><sup>0</sup>)−(<em>q </em>+<em>x</em>−<em>aq</em>) = (<em>a</em>−1)(<em>q </em>−<em>q</em><sup>0</sup>) <em>&gt; </em>0, <em>g</em><sup>0 </sup>would sum up to more coins than the initial solution <em>g</em>, for any <em>g</em><sup>0 </sup>satisfying the problem definition. Thus, the solution <em>g </em>is optimal, and the system (<em>a,</em>1) is canonical.

4.1 Design a non-canonical system of 3-tuple <em>c </em>= (<em>c</em><sub>1</sub><em>,c</em><sub>2</sub><em>,c</em><sub>3</sub>) and prove your system is noncanonical.

4.2 Let <em>q </em>and <em>n </em>be two integers ≥ 2. Prove that the system <em>c </em>= (<em>q<sup>n</sup>,q<sup>n</sup></em><sup>−1</sup><em>,…,q,</em>1) is canonical.

4.3 Prove that the Euro system <em>c </em>= (200<em>,</em>100<em>,</em>50<em>,</em>20<em>,</em>10<em>,</em>5<em>,</em>2<em>,</em>1) is canonical. There will be no partial credit for this question.