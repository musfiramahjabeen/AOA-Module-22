# AOA Module-22
## Day 1 - DYNAMIC PROGRAMMING-1
### To Write a Python Program to find longest common subsequence using Dynamic Programming

```py
def lcs(x, y):
    m, n = len(x), len(y)
    dp = [[0]*(n+1) for _ in range(m+1)]

    # Build dp table (lengths only)
    for i in range(m): 
        for j in range(n):
            if x[i] == y[j]:
                dp[i+1][j+1] = dp[i][j] + 1
            else:
                dp[i+1][j+1] = max(dp[i][j+1], dp[i+1][j])

    # Reconstruct LCS from dp table
    i, j = m, n
    lcs_str = []
    while i > 0 and j > 0:
        if x[i-1] == y[j-1]:
            lcs_str.append(x[i-1])
            i -= 1
            j -= 1
        elif dp[i-1][j] > dp[i][j-1]:
            i -= 1
        else:
            j -= 1

    return ''.join(reversed(lcs_str))

# Input
x = input()
y = input()
print(lcs(x, y))

```
## Day 2 - DYNAMIC PROGRAMMING-2
### The longest common substring problem is the problem of finding the longest string (or strings) that is a substring (or are substrings) of two strings.
```py
def LCS(X, Y, m, n):
    maxLength = 0
    endingIndex = m
    lookup = [[0 for x in range(n + 1)] for y in range(m + 1)]
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if X[i - 1] == Y[j - 1]:
                lookup[i][j] = lookup[i - 1][j - 1] + 1
                if lookup[i][j] > maxLength:
                    maxLength = lookup[i][j]
                    endingIndex = i
    return X[endingIndex - maxLength: endingIndex]

X = input()
Y = input()
m = len(X)
n = len(Y)
print('The longest common substring is', LCS(X, Y, m, n))
```
## Day 3 - DYNAMIC PROGRAMMING-3
### Given a sequence, find the length of the longest palindromic subsequence in it.
```py
def Lps(X):
    n=len(X)
    dp=[[0 for _ in range(n)] for _ in range(n)]
    for x in range(n):
        dp[x][x]=1
    for l in range(2,n+1):
        for i in range(n-l+1):
            j=i+l-1
            if X[i]==X[j]:
                dp[i][j]=dp[i+1][j-1]+2
            else:
                dp[i][j]=max(dp[i+1][j],dp[i][j-1])
    return dp[0][n-1]
X=input()
print("The length of the LPS is",Lps(X))
```
## Day 4 - DYNAMIC PROGRAMMING-4
### Create a Naive recursive python program to find the minimum number of operations to convert str1 to str2
```py
def ed(x,y,m,n):
    if m==0:
        return n
    if n==0:
        return m
    if x[m-1]==y[n-1]:
        return ed(x,y,m-1,n-1)
    return 1+min(ed(x,y,m-1,n-1),ed(x,y,m,n-1),ed(x,y,m-1,n))
x=input()
y=input()
print("Edit Distance",ed(x,y,len(x),len(y)))
```
