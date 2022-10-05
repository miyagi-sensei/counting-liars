# Title: Counting Liars
## Task ID: U004
### Main Statement
```!
Bessie the cow is hiding somewhere along the number line. Each of Farmer John's $N$ other cows ($1≤N≤1000$) have a piece of information to share: the $i$-th cow either says that Bessie is hiding at some location less than or equal to $p_i$, or that Bessie is hiding at some location greater than or equal to $p_i$ ($0≤p_i≤10^9$).

Unfortunately, it is possible that no hiding location is consistent with the answers of all of the cows, meaning that not all of the cows are telling the truth. Count the minimum number of cows that must be lying.

# Input

The first line contains $N$.

The next $N$ lines each contain either L or G, followed by an integer $p_i$. L means that the $i$-th cow says that Bessie's hiding location is less than or equal to $p_i$, and G means that $i$-th cow says that Bessie's hiding location is greater than or equal to $p_i$.

# Output

The minimum number of cows that must be lying.
```

### Constraint for all cases

### Samples
|Number|Input|Output|Explanation|
|---|---|---|---|
|1|<pre>2<br>G 3<br>L 5</pre>|```0```|It is possible that no cow is lying.|
|2|<pre>2<br>G 3<br>L 2</pre>|```1```|At least one of the cows must be lying.|

### Images

### Scoring mode
HKOI

### Judging mode
Plain text comparison

### Solution program
Language: Python 3
```python!
# try all pi's and see which one comes with the fewest liars
N = int(input())
G, L = [], []
for _ in range(N):
    line = input().split()
    if line[0] == 'G':
        G.append(int(line[1]))
    else:
        L.append(int(line[1]))

min_liars = 1000
for h in L + G:
    liars = len([x for x in L if x < h])
    liars += len([x for x in G if x > h])
    min_liars = min(min_liars, liars)
print(min_liars)
```

### Subtasks
|Number|Points|Constraints|# Tests|
|---|---|---|---|
|1|100||12|
