# CMPS 6610 Extra Credit Answers
  
In this extra credit assignment, we will test and review concepts you
   have learned since the midterm exam. Please add your written answers
   to `answers.md` which you can convert to a PDF using
   `convert.sh`. Alternatively, you may scan and upload written
   answers to a file named `answers.pdf`.



1. **Algorithmic Paradigms**
I would say Dynamic Programming. At first I found DP pretty hard to code, but once I got used to the structure, such as define a state / write the recurrence / then fill a table, it started to feel very systematic. That same pattern applies to many problems I’ve seen, especially on LeetCode. I also like that DP is often much more efficient than brute force and gives a reliable alternative when greedy algorithms don’t work.

2. **Divide and Conquer**
This is a pretty hard problem.
No. Even though we can use Divide and Conquer for optimization, it doesn't strictly follow the optimal substructure property.
For example, if I want to find the closest pair of numbers from {1,9,10,50}. The solution should be [9,10] since the distance is smallest (1). 
For divided and conquer, I have to divided to $S_l = [1,9]$ $S_r = [10,50]$ The optimal of $S_l = 8$ and optimal of $S_r = 40$, but the global optimal is [9,10]. 
We can find out that the global solution doesn't "contain" the sub-solutions. It actually ignores them. Since the algorithm has to check the boundary to find the real answer instead of just using the sub-results, the optimal substructure property isn't there.


1. **Randomization**

- 3a. 
we know that $E[x]\leq nlogn$
$P[x\geq cn^2] \leq \frac{E[x]}{cn^2} \leq \frac{O(n\log n)}{cn^2} = O(\frac{\log n}{cn})$ , c is constant
the value goes to 0 when n grows, so the probability goes to 0 when n grows.
- 3b.
$P[x\geq 10^c n\ln n]\leq \frac{kn\ln n}{10^c n\ln n}\leq \frac{k}{10^c} = O(10^{-c})$ 
So the probability that Quicksort uses $10^{c} n\ln n$ comparisons is at most $\frac{k}{10^c}$, which decreases like $10^{-c}$ as c grows. The runtime of Quicksort is concentrated around its expected value.

4. **Greedy Algorithms**
let $T(S) = p_1 + p_2 + .. + p_n$ be the total processing time, and $\frac{T(S)}{n} = C(S)$. n is constant, so the question is minimizing $C(s)$, which same as minimizing T(S). So I would compare the total cost below.\
Let consider 2 neighbor jobs $p_a > p_b$. The time before them would be $X$.
so for order of (...,a,b), waiting time for a would be $X$ and waiting time for b would be $X+p_a$, total would be $X+(X+p_a) = 2X+p_a$
If in order of (...,b,a), total would be $2X+p_b$
we know that $2X+p_b < 2X+p_a$, so the order of (...,b,a) would be a better solution. 
Therefore, optimal schedule must be a short job first order.

5. **Dynamic Programming**
- Maximum Span
Consider computing the sum of a array sequentially. The recurrence would be
$$OPT(i) = OPT(i-1)+c_i$$ 
Each step depends on step before it. The span is clearly $O(n)$
- Polylogarithmic Span
Consider finding the minumum element in a array with divid and conquer, and let $m = \frac{l+r}{2}$
$$OPT[l,r] = min(OPT(l,m), OPT(m+1,r))$$ 
The two subproblems are independent and can be run on separate processors at the same time. so this is same as $S(n) = S(\frac{n}{2})+O(1)$ .The span would be $O(\log n)$

6. **Graphs**
Let C be a cycle in G and let e be the maximum-weight edge on C. Suppose, for contradiction, that there is an MST T with $e \in T$. Removing e from T disconnects it into components A and B. Since e lies on the cycle C, there is another edge $f \in C$ that also has one endpoint in A and one in B.
Consider $T’ = T - \{e\} + \{f\}$. This graph has $|V|-1$ edges and is connected, so it is a spanning tree. Because e is the heaviest edge on C, $w(f) \le w(e)$, so
$w(T’) = w(T) - w(e) + w(f) \le w(T)$.
If $w(f) < w(e)$, then $w(T’) < w(T)$, contradicting the minimality of T. Thus $w(f) = w(e)$ and T’ is also a minimum spanning tree that does not contain e. Hence the maximum-weight edge on a cycle cannot be in every MST.
