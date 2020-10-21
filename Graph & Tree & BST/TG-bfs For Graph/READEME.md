## Breadth First Traversal or BFS for a Graph
- Unlike trees, graphs may contain cycles, so we may come to the same node again.

- To avoid processing a node more than once, using a boolean visited array. 

- A Breadth First Traversal of the following graph is 2, 0, 3, 1. (root = 2)

```
    0     -- > 1
    ^ |     /
    | v    v
        2   --> 3 
```


```java
// A directed graph using adjacency listrep resentation 
class Graph 
{ 
    private int V;   // No of vertices 
    private LinkedList<Integer> adj[]; //Adjacency Lists 
  
    // Constructor 
    Graph(int v) 
    { 
        V = v; 
        adj = new LinkedList[v]; 
        for (int i=0; i<v; ++i) 
            adj[i] = new LinkedList(); 
    } 
  
    // Add an edge into the graph 
    void addEdge(int v,int w) 
    { 
        adj[v].add(w); 
    } 
  
    /* *************************************************** 
        prints BFS traversal from a given source s 
    *************************************************** */
    void BFS(int s) 
    { 
        // 1. Mark all the vertices as not visited (Default is false)
        boolean visited[] = new boolean[V]; 
  
        // 2. Create a queue for BFS 
        LinkedList<Integer> queue = new LinkedList<Integer>(); 
  
        // 3. Mark the current node as visited 
        visited[s]=true; 
        
        // 4. Enqueue given vertices
        queue.add(s); 


        //Traversal
        while (queue.size() != 0) 
        { 
            // Dequeue a vertex from queue and print it 
            s = queue.poll(); 
            System.out.print(s+" "); 

            
            // Get all adjacent vertices of the dequeued vertex s 
            // If a adjacent has not been visited, then mark it 
            // visited and enqueue it 
            Iterator<Integer> i = adj[s].listIterator(); 
            while (i.hasNext()) 
            { 
                int n = i.next(); 
                if (!visited[n]) 
                { 
                    visited[n] = true; 
                    queue.add(n); 
                } 
            } 
        } 
    } 
  
    // Driver method to 
    public static void main(String args[]) 
    { 
        Graph g = new Graph(4); 
  
        g.addEdge(0, 1); 
        g.addEdge(0, 2); 
        g.addEdge(1, 2); 
        g.addEdge(2, 0); 
        g.addEdge(2, 3); 
        g.addEdge(3, 3); 
  
        System.out.println("Following is Breadth First Traversal "+ 
                           "(starting from vertex 2)"); 
  
        g.BFS(2); 
    } 
} 
```


