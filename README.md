# Graph-Theory
Learnings and practice

## DFS 
```
// class scope variables 
n - number of nodes
g - adj list representing graph
visited[] // size n, initialized with false

  private void dfs(List<List<Integer>> g, int i) {
        if(visited[i]) {
            return;
        }
        visited[i] = true;
        coloring[i] = count;
        for (int neighbour : g.get(i)) {
            dfs(g, neighbour);
        }
    }
```

## connected components
```
// class scope variables 
n - number of nodes
g - adj list representing graph
visited[] // size n, initialized with false
int count = 0;
int[] coloring;

  private int ccDfs(List<List<Integer>> g) {
        for (int j = 0; j < g.size(); j++) {
            if (!visited[j]) {
                count++;
                dfs(g, j);
            }
        }
        return count;
    }

    private void dfs(List<List<Integer>> g, int i) {
        if(visited[i]) {
            return;
        }
        visited[i] = true;
        coloring[i] = count;
        for (int neighbour : g.get(i)) {
            dfs(g, neighbour);
        }
    }
```




