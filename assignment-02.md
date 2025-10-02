# CMPS 2200 Assignment 2

**Name:**Davis Voelkel

In this assignment we'll work on applying the methods we've learned to analyze recurrences, and also see their behavior
in practice. As with previous
assignments, some of of your answers will go in `main.py` and `test_main.py`. You
should feel free to edit this file with your answers; for handwritten
work please scan your work and submit a PDF titled `assignment-02.pdf`
and push to your github repository.


## Part 1. Asymptotic Analysis

Derive asymptotic upper bounds of work for each recurrence below.

* $W(n)=2W(n/3)+1$
* = $\sum 2^k$ , from k=0 to k= log3 n
* = $2^{log_3 2} -1 \in O(n^{log_3 2})$
.  
. 
.  
. 
.  
. 
 
* $W(n)=5W(n/4)+n$
* = $\sum (5/4)^k$ , from k =0 to k= log4 n
* Since, $n^{log_4 5}$ dominates n, by Master's Theorem Case 1,
* $W(n) \in O(n^{log_4 5})$
.  
.
.  
. 
.  
. 
.  
.  
. 

* $W(n)=7W(n/7)+n$
* Balanced like W(n) = 2W(n/2) + n, therefore
* $W(n)=7W(n/7)+n \in O(nlogn)$
.  
. 
.  
.  
. 
.  
.

* $W(n)=9W(n/3)+n^2$
* = $\sum n* 9^{k}$ , from k =0 to k=log3 n.
* Since $n^{log_3 9}$ = $f(x)$ = $n^2$ , by Master's Theorem Case 2,
* = $n^2 * log n \in O(n^2  logn)$
.  
.
. 
.  
. 
.  
.  
.  
.

* $W(n)=8W(n/2)+n^3$
* Since $n^{log_2 8}$ = f(x)= $n^3$ , by Master's Theorem Case 2,
* = $n^3 * log n \in O(n^3 logn)$
.  
.
.  
.  
.  
.  
. 
.  
. 


* $W(n)=49W(n/25)+n^{3/2}\log n$
* Since $n^{log_25 49}$ is less than $n^{3/2} logn$ , by the Master's Theorem Case 3,
* $W(n) \in O(n^{3/2} logn)$ 
.  
.  
. 
.  
. 
.  
.  
.  

* $W(n)=W(n-1)+2$
* = $2n \in O(n)$
.  
.  
. 
.  
. 
.  
.  
.  

* $W(n)= W(n-1)+n^c$, with $c\geq 1$
* = $n * n^c \in O(n^{c+1})$
.  
.  
.  
.  
.  
. 
.  
. 

* $W(n)=W(\sqrt{n})+1$
* $n^{1/2^k} < 2$
* = $ln(n) /2^k$ < ln(2)$
* $2^k > ln(n)/ln(2) = log_2 n$
* $k > log_2(log_2 n)$, therefore
* $W(n) \in O(log(log n))$
.  
.  
.  
.  
.  
. 
. 


## Part 2. Algorithm Comparison

Suppose that for a given task you are choosing between the following three algorithms:

  * Algorithm $\mathcal{A}$ solves problems by dividing them into
      five subproblems of half the size, recursively solving each
      subproblem, and then combining the solutions in linear time.
    
  * Algorithm $\mathcal{B}$ solves problems of size $n$ by
      recursively solving two subproblems of size $n-1$ and then
      combining the solutions in constant time.
    
  * Algorithm $\mathcal{C}$ solves problems of size $n$ by dividing
      them into nine subproblems of size $n/3$, recursively solving
      each subproblem, and then combining the solutions in $O(n^2)$
      time.

    What are the asymptotic running times of each of these algorithms?
    Which algorithm would you choose?

    Algorithm A is O(n^log_2 5) by the first case of Master's Theorem. Algorithm B is O(2^n) since W(n) = 2W(n-1) +1. The work is 2^k, where k =n since the recursion is iterative. Algorithm C is O(n^2 logn) as shown above. I would choose Algorithm C since log_2 5 is greater than 2, therefore making n^log_2 5 greater than n^2.


.  
.  
.  
.  
. 
. 



## Part 3: Parenthesis Matching

A common task of compilers is to ensure that parentheses are matched. That is, each open parenthesis is followed at some point by a closed parenthesis. Furthermore, a closed parenthesis can only appear if there is a corresponding open parenthesis before it. So, the following are valid:

- `( ( a ) b )`
- `a () b ( c ( d ) )`

but these are invalid:

- `( ( a )`
- `(a ) ) b (`

Below, we'll solve this problem three different ways, using iterate, scan, and divide and conquer.

**3a. iterative solution** Implement `parens_match_iterative`, a solution to this problem using the `iterate` function. **Hint**: consider using a single counter variable to keep track of whether there are more open or closed parentheses. How can you update this value while iterating from left to right through the input? What must be true of this value at each step for the parentheses to be matched? To complete this, complete the `parens_update` function and the `parens_match_iterative` function. The `parens_update` function will be called in combination with `iterate` inside `parens_match_iterative`. Test your implementation with `test_parens_match_iterative`.


.  
. 



**3b.** What are the recurrences for the Work and Span of this solution? What are their Big Oh solutions?  
* W(n) = W(n+1) +1 which is O(n). The span is the exact same since this is a sequential algorithm, making it O(n) as well.



.  
. 



**3c. scan solution** Implement `parens_match_scan` a solution to this problem using `scan`. **Hint**: We have given you the function `paren_map` which maps `(` to `1`, `)` to `-1` and everything else to `0`. How can you pass this function to `scan` to solve the problem? You may also find the `min_f` function useful here. Implement `parens_match_scan` and test with `test_parens_match_scan`

.  
. 



**3d.** Assume that any `map`s are done in parallel, and that we use the efficient implementation of `scan` from class. What are the recurrences for the Work and Span of this solution? 

* Map:
    - $W(n) = O(n)$
    - $S(n) = O(1)$
* Scan:
    - $W(n) = O(n)$
    - $S(n) = O(logn)$
* Reduce:
    - W(n) = O(n)
    - S(n) = O(logn)
* Total:
    - W(n) = O(n)
    - S(n) = O(logn)

.  
.  




**3e. divide and conquer solution** Implement `parens_match_dc_helper`, a divide and conquer solution to the problem. A key observation is that we *cannot* simply solve each subproblem using the above solutions and combine the results. E.g., consider '((()))', which would be split into '(((' and ')))', neither of which is matched. Yet, the whole input is matched. Instead, we'll have to keep track of two numbers: the number of unmatched right parentheses (R), and the number of unmatched left parentheses (L). `parens_match_dc_helper` returns a tuple (R,L). So, if the input is just '(', then `parens_match_dc_helper` returns (0,1), indicating that there is 1 unmatched left parens and 0 unmatched right parens. Analogously, if the input is just ')', then the result should be (1,0). The main difficulty is deciding how to merge the returned values for the two recursive calls. E.g., if (i,j) is the result for the left half of the list, and (k,l) is the output of the right half of the list, how can we compute the proper return value (R,L) using only i,j,k,l? Try a few example inputs to guide your solution, then test with `test_parens_match_dc_helper`.



.  
. 





**3f.** Assuming any recursive calls are done in parallel, what are the recurrences for the Work and Span of this solution? What are their Big Oh solutions?

* W(n) = 2W(n/2)+1 = O(n)
* S(n) = W(n/2) +1 = O(logn)

 
 


