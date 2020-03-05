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

## Connected components
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

## BFS
Good for searching path in unweighted graph
```
    boolean[] visited;
    Integer[] path;
    public List<Integer> findPath(List<List<Integer>> g, int source, int destination) {
        visited = new boolean[g.size()];
        path = new Integer[g.size()];
        Queue<Integer> queue = new LinkedList<>();
        queue.add(source);
        visited[source] = true;

        while (!queue.isEmpty()) {
            int currNode = queue.poll();
            List<Integer> neighbours = g.get(currNode);
            for (int next : neighbours) {
                if (!visited[next]) {
                    path[next] = currNode;
                    queue.add(next);
                    visited[next] = true;
                    if (next == destination) {
                        queue.clear();
                        break;
                    }
                }
            }
        }
        return reconstructPath(path, source, destination);
    }

    private List<Integer> reconstructPath(Integer[] path, Integer source, Integer destination) {
        List<Integer> result = new LinkedList<>();
        while (destination != null) {
            result.add(0, destination);
            destination = path[destination];
        }
        if (result.get(0) == source) return result;
        return Arrays.asList();
    }
    ```




