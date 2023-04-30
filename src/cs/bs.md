# Backtracing
also called recursive backtracing. may be called "clever brute force" (i don't know)
## Remember things
- satisfied some constraints.
- explicit and implicit constriants.
- brute force make explicit n² 
- bound function make imlicit n!
- live node
- E node
- dead node
- answer node

## N-Queen Psudocode

=== "Place"
    ```python3
    place(k,i)
    for j = 1 to k-1 
        if x[j]=i or Abs(x[j]-i) = Abs(j-k)
             do return false
    return true
    ```
=== "Nqueen"
    ```python3
    Nqueen(k,n)
    for i = 1 to k
        if place(k,i)
            then x[k] = i
                 if k = n
                   do write  x[1:n]
                 else
                   Nqueen(k+1,n) 
    ```
## N-Queen Implement 

=== "Python(place)"
    ```python3
    def place(k,i):
	for j in range(1,k):
		if x[j] == i or abs(x[j]-i) == abs(j-k):
			return False
	return True
    ```
=== "Python(Nqueen)"
    ```python3
    def nqueen(k,n):
	for i in range(1,n+1):
		if place(k,i):
			x[k]=i
			if k==n:
				print(x[1:n+1])
			else:
				nqueen(k+1,n)
    ```
=== "Python(full code)"
    ```python3
    def place(k,i):
	for j in range(1,k):
		if x[j] == i or abs(x[j]-i) == abs(j-k):
			return False
	return True
    def nqueen(k,n):
	for i in range(1,n+1):
		if place(k,i):
			x[k]=i
			if k==n:
				print(x[1:n+1])
			else:
				nqueen(k+1,n)
    n=int(input())
    x=[0]*(n+1)
    nqueen(1,n)

    ```
## Related Problems
- [UVa 725 - Division](https://onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&category=9&page=show_problem&problem=666)
