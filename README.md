java c
Computer Science CSC263H
October 23, 2024
Homework Assignment #5
Due:  November 6, 2024, by 11:00 am
• You must submit your assignment through the Crowdmark system. You will receive by email an invitation through which you can submit your work. If you haven’t used Crowdmark before, give yourself plenty of time to figure it out!
• You must submit a separate PDF document with for each question of the assignment.
• To work with one or two partners, you and your partner(s) must form. a group on Crowdmark (one submission only per group). We allow groups of up to three students. Submissions by groups of more than three students will not be graded.
• The PDF file that you submit for each question must be typeset (not handwritten) and clearly legible. To this end, we encourage you to learn and use the LATEX typesetting system, which is designed to produce high-quality documents that contain mathematical notation. You can use other typesetting systems if you prefer, but handwritten documents are not accepted.
• If this assignment is submitted by a group of two or three students, for each assignment question the PDF file that you submit should contain:
1. The name(s) of the student(s) who wrote the solution to this question, and
2. The name(s) of the student(s) who read this solution to verify its clarity and correctness.
• By virtue of submitting this assignment you (and your partners, if you have any) acknowledge that you are aware of the homework collaboration policy for this course, as stated here.
• For any question, you may use data structures and algorithms previously described in class, or in prerequisites of this course, without describing them. You may also use any result that we covered in class (in lectures or tutorials) by referring to it.
• Unless we explicitly state otherwise, you should justify your answers. Your paper will be marked based on the correctness and efficiency of your answers, and the clarity, precision, and conciseness of your presentation.
• The total length of your pdf submission should be no more than 4 pages long in a 11pt font.Question  1.  (20 marks)   A  bag  is a set that allows for multiple instances for each of its elements:  for example, {0, 6, 1} and {1, 1, 6, 0, 6} are different bags.  Consider the abstract data type that consists of a bag of integers S and supports the following operations:
•  Add(S, x): insert integer x into bag S;
•  Reduce(S): delete the「|S|/2l largest integers in S.
(For example, if S = {1, 1, 6, 0, 6}, then, after Reduce(S) is performed, S = {1, 0}.)
A simple data structure for this ADT, and the corresponding algorithms for each operation, are as follows: The elements of a bag S are stored in an unsorted  linked list, and the size of S is stored in a variable n.
•  Add(S, x): Append x at the begining of the list containing S; increment n.
•  Reduce(S):
1. m ← Median(S) {* find the median of the elements in S *}
2.  loop over all elements in S: keep all those < m, delete all those ≥ m
3.  add as many copies of m as required to have exactly  ln/2」elements remaining
4. n ← ln/2」
The above uses a given procedure Median that returns the “median” of any list of integers.
To simplify this question, we use a slightly non-standard definition of  “median”:  Median returns the 「n/2l-th largest integer in the list (including duplicates); for example Median([3, 2, 1, 1, 3, 3, 3]) returns 3. Also for this question, assume that executing Median on any S of size n takes at most (α - 1)n pairwise 	integer comparisons, for some constant integer α > 1.Define the cost of an operation to be the number of pairwise  comparisons between the elements of S that this operation takes to execute. Note that under this measure, the cost of each Add is 0, and the cost of each Reduce(S) is (α - 1)n + n = αn for S of size n.
Prove that when we execute an arbitrary sequence of Add and Reduce operations starting from an empty set S, the amortized cost of an operation is constant.
To prove this, use the accounting method to analyse the amortized complexity of the Add and Reduce algorithms, and:
(a)  State clearly what charge you assign to each operation.
(b)  State and prove an explicit credit invariant.
(c) Use your credit invariant to justify that the amortized cost of an operation is constant.
Question 2.  (20 marks)   Consider an abstract data type that maintains a set S of integers and supports the following three operations:
1.  Insert(x): insert a new integer x into S (assume that x is not already in S).
2.  Delete(x): remove x from S (assume that x is in S).
3.  Search(x): return True if integer x is currently in S, and return False otherwise.
We want to design a data structure for this ADT with a low amortized cost for insertions and searches.
We first consider a very simple data structure: we just store the elements of S in an array A in sorted order.
a.     Give good upper bounds on the following asymptotic time complexities:
1.  The worst-case time to execute a Search(x).
2.  The worst-case time to execute an Insert(x).
3.  The amortized insertion time, defined as follows: starting from an empty set S, the worst-case total time to successively execute a sequence of n Insert()s divided by n.
In the above, use the Θ notation and briefly justify each answer.To lower the amortized insertion time, we now consider the following data structure.  We store S in a doubly linked list L of sorted arrays as follows. Suppose S contains n elements. Let < bk−1, bk−2,..., b0  >
be the binary representation of n. Note that n = Σi(i)0(k)−1bi2i  and k = O(log2 n). For each i = 0, 1,..., k − 1such that bi  = 1, th代 写CSC263H Data Structures and Analysis 2024 Homework Assignment #5Prolog
代做程序编程语言e doubly-linked list L contains a sorted array Ai  of size 2i; Ai  stores 2i  elements of S in increasing sorted order.  The arrays of L are listed in order of increasing size.  Each integer of S is in exactly one of the sorted arrays of L.  Note that although each array of L is sorted, there is no particular relationship between the elements in different arrays of L.
b.     Draw two instances of L, one for S = {4, 6, 2, 11, 7} and one for S = {16, 7, 2, 9, 0, 11, 5}.
In the questions below, you should give as efficient algorithms as possible.  Describe your algorithms in clear and concise English, there is no need to use pseudocode.
c.     Describe an algorithm to perform. a Search(x) operation with this data structure.  Give a good upper bound on the worst-case time complexity of your algorithm (using the O notation) and justify your answer.d.    Describe an algorithm to perform. an Insert(x) operation with this data structure.  Give a good upper bound on the worst-case time complexity of your algorithm (using the O notation) and justify your answer. Hint: Think about how we insert an element in a Binomial Heap, and use the Merge part of MergeSort.
e.        Suppose  that,  starting  from  an empty set  S,  we successively execute a sequence of n Inserts.Determine a good upper bound on the  amortized  time of an Insert  (i.e., the worst-case total time to execute these n Inserts divided by n).  Justify your answer in two different ways, i.e., give two separate proofs, each proof using a different argument (e.g., use aggregate analysis and the accounting method).
f.      Describe an algorithm to perform. a Delete(x) operation in O(n) time in the worst case.  Explain why the worst-case time complexity of your algorithm is O(n).
Question 3.  (20 marks)You are given an undirected and connected graph G = (V, E) that represents a set of houses and hospitals connected by roads as follows:  each node in V is colored white if it represents a house, or black if it represents a hospital, and each edge  (u,v) in E represents a road between nodes u and v that can be traversed in one unit of time. Assume that G is given by its adjacency lists, and by an array clr[..] where clr[v] = white or black (indicating whether node v represents a house or a hospital).
Consider the following problem P: compute for each house node, the shortest time to reach any hospital node. An example of a graph G and the shortest time to hospitals from each house in G is shown below:
Describe a simple algorithm that solves the problem P in O(|V | + |E|) time in the worst-case.  You can assume that there is at least one hospital in G. Do not assume that the number of houses or the number of hospitals is a constant.
Explain each step of your algorithm in clear and concise English. Justify its worst-case time complexity. Overly complex algorithms may get little  or no  credit.
[The questions below will not be corrected/graded.  They are given here as interesting problems that use material that you learned in class.]Question 4.  (0 marks)   Consider the forest implementation of the disjoint-sets abstract data type, with an initial forest of n distinct elements (each one in a one-node tree). Let σ be any sequence of k UNIONs followed by k′  FINDs;  so  all  UNIONs  occur  before the FINDs.   Prove that the  algorithm using Path Compression only (it does not  use the Weighted-Union rule) executes σ in O(k + k′ ) time, i.e., in time proportional to the length of σ, in the worst-case.Do not make assumptions on k or k′  (for example, do not assume that k = n − 1 or that k′  ≤ k).  As we did in class, assume that the parameters of each UNION are two set representatives, i.e., two tree roots (so there are no FINDs “inside” each UNION).Hint: Note that if a vertex becomes a child of a root during the execution of one of the FINDs (because of Path Compression), then it remains a child of this root during all the subsequent FINDs.  To compute the “cost” of executing all the FINDs use an amortization-like charging scheme.Question 5.  (0 marks)   Let G = (V, E) be an undirected graph.  G is bipartite if the set of nodes V can be partitioned into two subsets V0  and V1  (i.e., V0 ∪ V1  = V  and V0  ∩ V1  = 。), so that every edge in E connects a node in V0  and a node in V1 . For example, the graph shown below is bipartite; this can be seen by taking V0  to be the nodes on the left and V1  to be the nodes on the right.
Note that G is bipartite if and only if every connected component of G is bipartite.
a.       Prove that  if G is bipartite then it has no  simple  cycle  of odd  length.    Hint:  Give  a proof by contradiction.b.      Prove that if G has no simple cycle of odd length  (i.e., every simple cycle of G has even length) then G is bipartite.  (Hint:  Suppose every simple cycle of G has even length.  Perform. a BFS starting at any node s. Assume for now that G is connected, so that the BFS reaches all nodes; you can remove this assumption later on. Use the distance of each node from s to partition the set of nodes into two sets, and prove that no edge connects two nodes placed in the same set.)c.     Describe an algorithm that takes as input an undirected graph G = (V, E) in adjacency list form.  If G is bipartite, then the algorithm returns a pair of sets of nodes (V0, V1 ) so that V0 ∪V1  = V , V0 ∩V1  = 。, and every edge in E connects anode in V0  and anode in V1; if G is not bipartite, then the algorithm returns the string  “not bipartite.”  Your algorithm should run in  O(n + m) time, where n =  |V |  and m = |E| .
Explain why your algorithm is correct and justify its running time.  (Hint: Use parts (a) and (b).)

         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
