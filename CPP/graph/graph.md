undirected-node,edge
and directed graph- in degree and out degre

adjacency matrix
adjacency list

![[Pasted image 20240428012228.png]]

```c
vector<int> ans[n];
for(int i=0;i<n;i++){
int u = edges[i][0];
int v = edges[i][0];

ans[u].push_back[v];
ans[v].push_back[u];
}
```
BFS
queue , visited


```c

void bfs(vector<vector<int> >& adjList, int startNode,
         vector<bool>& visited)
{
 
    queue<int> q;

    visited[startNode] = true;
    q.push(startNode);

    while (!q.empty()) {
        // Dequeue a vertex from queue and print it
        int currentNode = q.front();
        q.pop();
     
        for (int neighbor : adjList[currentNode]) {
            if (!visited[neighbor]) {
                visited[neighbor] = true;
                q.push(neighbor);
            }
        }
    }
}


```

DFS
visited,
```c
voidDFS(){
component.push_back(node);
visited[node]=true;
for(auto i:adj[node]){
if(!visited[i]){
dfs(ike liye)
		}
	}
}
vector<vector<int>> ans;
unordered_map<int,bool> visited;
for(int i=0;i<V;i++){
if(!visited[i]){
vector<int>component;
dfs(i,visited,adjlist,component);
ans.push_back(component);
}
}
return ans;
```

cycle detection


```c
bool isCycleBFS( int src,undererred_map<int,bool> &visited, undererred_map<int, list<int>>adj ){

undererred_map<int,int> parent;      //map of parent

parent[src]=-1;

visited[src]=1;

queue<int>q;

q.push{src};

while(!q.empty()){

int front = q.front();

q.pop();

for(auto neigbour: adj[front]{

	if(visited[neigbour]==true && neigbour != parent){      //base
	
	return true;

}

else if(!visited[neigbour]){

q.push[neigbour];

visited[neigbour]=1;

parent[neigbour]=front;
}}}return false;}
string cycleDetection (vector<vector<int>>& edges, int n, int m)
{
//ADJ LIST
undererred_map<int, list<int>>adj;

for(int i=0;i<m;i++){

int u = edges[i][0];

int v = edges[i][1];

adj[u].push_back(v);

adj[v].push_back(u);
}

undererred_map<int,bool> visited;

for(int i=0;i<n; i++){

if(!visited[i]){

bool ans=isCycleBFS(i , visited,adj);

if(ans==1)

return "Yes";

}

}

return "No";

}
```

cycle detection (directed graph)
visited , dfs visited
***else if(dfsVisited[i]){
return true;
}
```C
bool checkCycle(node,  visited , dfs visited, adj){
visited[node]=true;
dfsvisited[node]=true;
for(auto i:adj[node]){
if(!visited[i]){
bool cycleDetected = checkCycle(nbr , visited , dfs visited , adj );// call
if(cycleDetected){
return true;}
else if(dfsVisited[i]){
return true;}}}
dfsvisited[node]=false;
return false;
}
unordered_map<int,bool> visited;
unordered_map<int,bool> dfs visited;
fot(int i=1i<=1;i++)
if(!visited[i]){
bool cycleFound = checkCycle(i, visited,dfs visited,adj);
if(cycleFound){
return true;}}
```
topological sort-use stack and dfs{DIRECTED ACYCLIC GRAPH}
```c

void topologicalSortUtil(int v, vector<vector<int> >& adj,
                         vector<bool>& visited,
                         stack<int>& Stack)
{    visited[v] = true;

    for (int i : adj[v]) {
        if (!visited[i])
            topologicalSortUtil(i, adj, visited, Stack);
    }
    Stack.push(v);
}
void topologicalSort(vector<vector<int> >& adj, int V)
{
    stack<int> Stack; // Stack to store the result
    vector<bool> visited(V, false);
    for (int i = 0; i < V; i++) {
        if (!visited[i])
            topologicalSortUtil(i, adj, visited, Stack);
    }
    while (!Stack.empty()) {
        cout << Stack.top() << " ";
        Stack.pop();
    }
}

```
khans algo topological sort{BFS}
1. INDGREE NIKALO
2. QUEUE BANA LO/ 0 indegree walo ko queue main
3. 3. top-pop-top.nbr ko indegree -1 go to step 2
```c
// ADJ LIST
FOR{INT I =0; i<e; i++}{
int u = edges[i][0];
int v = edges[i][1];
adj[u].push_back(v);
}

//find all indgree
vector<int => indegree(v);
for(auto i : adj){
for{auto j: i.second}{
indgree[j]++;
}
}
//0 indegree ko push kar do
queue<int>q;
for(int i = 0 ;i<v;i++){
if(indgree(i)==0){
q.push(i);
}
}
// do BFS
vecot<int>ans;
while(!q.empty()){
int front= q.front();
q.pop();
}
//ans store
ans.push_back(front);
// neigbour indgree update
for(auto neighbour: adj[front])
{
indgree[neighbour]--;
if(indgree[neighbour]==0)
q,push(neighbour);
}
reutrn ans;
```

==shortest path bitween two nodes ==
using parent visited 

```c
#include <unordered_map>

#include <queue>

#include<list>
vector<int> shortestPath( vector<pair<int,int>> edges , int n , int m, int s , int t){
// Write your code here
unordered_map<int, list<int>> adj;
for(int i=0;i<edges.size();i++){
int u = edges[i].first;
int v =edges[i].second;
adj[u].push_back(v);
adj[v].push_back(u);}

unordered_map<int , bool>visited;
unordered_map<int, int >parent;
queue<int >q;
q.push(s);
visited[s]= true;
while(!q.empty()){
int front = q.front();
q.pop();
for(auto i : adj[front]){
if(!visited[i]){
visited[i]=true;
parent[i]=front;
q.push(i);}}}
vector<int >ans;
int currnode=t;
ans.push_back(t);
while(currnode != s){
currnode = parent[currnode];
ans.push_back(currnode);}
reverse(ans.begin() , ans.end());
return ans;}
```


==shortest path in directed acyclic graph\==
====stack== 
==visited==
==adj + waight unorderd_map<int ,list<pair<int,int>> adj;==

dijkstra shortest path
```c
vector<int> dijkstra(vector<vector<int>> &vec, int vertices, int edges, int source) {
//adj list
unordered_map<int, list<pair<int,int>>> adj;
for(int i = 0 ; i < edges; i++){
int u = vec[i][0];
int v = vec[i][1];
int w = vec[i][2];
adj[u].push_back(make_pair(v,w));
adj[v].push_back(make_pair(u,w));}
//creation of distance array
vector<int> dist(vertices, INT_MAX);
dist[source] = 0;
set<pair<int,int>> st;

st.insert(make_pair(0,source));
while(!st.empty()){
auto top = *(st.begin());
int nodeDistance = top.first;
int topNode = top.second;
st.erase(st.begin());
for(auto neighbour: adj[topNode]){
if(nodeDistance + neighbour.second < dist[neighbour.first]){
auto record = st.find(make_pair(dist[neighbour.first],neighbour.first));
if (record != st.end()) {
st.erase(record);}
dist[neighbour.first] = nodeDistance + neighbour.second;
st.insert(make_pair(dist[neighbour.first], neighbour.first));
}}}return dist;}```.
```

MINIMUM SPANNING TREE

![[Pasted image 20240512151826.png]]
```c++
#include <bits/stdc++.h>
using namespace std;
vector<pair<pair<int, int>, int>> calculatePrimsMST(int n, int m, vector<pair<pair<int, int>, int>> &g)
{  // Write your code here.
    unordered_map<int, list<pair<int, int>>> adj; // Fixed typo here
    for (int i = 0; i < g.size(); i++)
    {
        int u = g[i].first.first; // Fixed typo here
        int v = g[i].first.second;
        int w = g[i].second; // Fixed variable name here
        adj[u].push_back(make_pair(v, w));
        adj[v].push_back(make_pair(u, w));
    }
    vector<int> key(n + 1, INT_MAX); // Initialize key vector with INT_MAX
    vector<bool> mst(n + 1, false);  // Initialize mst vector with false
    vector<int> parent(n + 1, -1);   // Initialize parent vector with -
    key[1] = 0; // Initialize key of the first vertex as 0
    parent[1] = -1; // Initialize parent of the first vertex as -1
    for (int i = 1; i < n; i++)
    {
        int mini = INT_MAX;
        int u;
        for (int v = 1; v <= n; v++)
        {
            if (mst[v] == false && key[v] < mini)
            {
                u = v;
                mini = key[v];
            }
        }
        mst[u] = true;
        for (auto it : adj[u])
        {
            int v = it.first;
            int w = it.second;
            if (mst[v] == false && w < key[v])
            {
                parent[v] = u;
                key[v] = w;
            }
        }
    }
    vector<pair<pair<int, int>, int>> result;
    for (int i = 2; i <= n; i++)
    {
        result.push_back({{parent[i], i}, key[i]});
    }
    return result;
}

```
minimum Spanning tree (Kuskal's algo Disjoin set) !!! 97  dhel le fir se

```c++
#include <algorithm>
#include <vector>
using namespace std;
bool cmp(vector<int>& a, vector<int>& b) {
    return a[2] < b[2];
}
void makeSet(vector<int>& parent, vector<int>& rank, int n) {
    for (int i = 0; i < n; i++) {
        parent.push_back(i);
        rank.push_back(0);
    }
}
int findParent(vector<int>& parent, int node) {
    if (parent[node] == node) {
        return node;
    }
    return parent[node] = findParent(parent, parent[node]);
}
void unionSet(int u, int v, vector<int>& parent, vector<int>& rank) {
    u = findParent(parent, u);
    v = findParent(parent, v);
    if (rank[u] < rank[v]) {
        parent[u] = v;
    } else if (rank[v] < rank[u]) {
        parent[v] = u;
    } else {
        parent[v] = u;
        rank[u]++;
    }
}
int minimumSpanningTree(vector<vector<int>>& edges, int n) {
    sort(edges.begin(), edges.end(), cmp);   //sepecial cmp
    vector<int> parent;
    vector<int> rank;
    makeSet(parent, rank, n);
    int minWeight = 0;
    for (int i = 0; i < edges.size(); i++) {
        int u = findParent(parent, edges[i][0]);
        int v = findParent(parent, edges[i][1]);
        int wt = edges[i][2];
        if (u != v) {
            minWeight += wt;
            unionSet(u, v, parent, rank);
        }
    }
    return minWeight;
}``
```

bridge  int timer// disc,low,parent,vis

```C++


using namespace std;
void dfs(int node, int parent, int &timer, vector<int> &disc, vector<int> &low,
vector<vector<int>> &result, unordered_map<int, unordered_set<int>> &adj,
unordered_map<int, bool> &vis) {
vis[node] = true;
disc[node] = low[node] = timer++;
for (auto nbr : adj[node]) {
if (nbr == parent) continue;
if (!vis[nbr]) {
dfs(nbr, node, timer, disc, low, result, adj, vis);
low[node] = min(low[node], low[nbr]);
if (low[nbr] > disc[node]) {
vector<int> ans;
ans.push_back(node);
ans.push_back(nbr);
result.push_back(ans);}
} else {
low[node] = min(low[node], disc[nbr]);}}}
vector<vector<int>> findBridges(vector<vector<int>> &edges, int v, int e) {
unordered_map<int, unordered_set<int>> adj;
for (int i = 0; i < edges.size(); i++) {
int u = edges[i][0];
int v = edges[i][1];
adj[u].insert(v);
adj[v].insert(u);}
int timer = 0;
vector<int> disc(v);
vector<int> low(v);
int parent = -1;
unordered_map<int, bool> vis;
for (int i = 0; i < v; i++) {
disc[i] = -1;
low[i] = -1;}
vector<vector<int>> result;
for (int i = 0; i < v; i++) {
if (!vis[i]) {
dfs(i, parent, timer, disc, low, result, adj, vis);}}
return result;}
```

==articulation point //99 phir se code kar==
```c++
void dfs(vector<int> adj[], int V, vector<int>& vis,
         int i, int curr)
{
    vis[curr] = 1;
    for (auto x : adj[curr]) {
        if (x != i) {
            if (!vis[x]) {
                dfs(adj, V, vis, i, x);}}}}
// Function to find Articulation Points in the graph
void AP(vector<int> adj[], int V)
{
    // Iterating over all the vertices and for each vertex i
    // remove the vertex and check whether the graph remains
    // connected.
    for (int i = 1; i <= V; i++) {
        // To keep track of number of components of graph
        int components = 0;
        // To keep track of visited vertices
        vector<int> vis(V + 1, 0);
        // Iterating over the graph after removing vertex i
        // and its associated edges
        for (int j = 1; j <= V; j++) {
            if (j != i) {
                // If the jth vertex is not visited it will
                // form a new component.
                if (!vis[j]) {
                    // Increasing the number of components.
                    components++;
                    // dfs call for the jth vertex
                    dfs(adj, V, vis, i, j);}}}
        // If number of components is more than 1 after
        // removing the ith vertex then vertex i is an
        // articulation point.
        if (components > 1) {
            cout << i << "\n";}}}
```

kosaraju algo
```c++
void dfs(int node, unordered_map<int, bool>& vis, stack<int>& st, unordered_map<int, list<int>>& adj) {
    vis[node] = true;
    for (auto nbr : adj[node]) {
        if (!vis[nbr]) {
            dfs(nbr, vis, st, adj);}}
    st.push(node);}
void revdfs(int node, unordered_map<int, bool>& vis, unordered_map<int, list<int>>& adj) {
    vis[node] = true;
    for (auto nbr : adj[node]) {
        if (!vis[nbr]) {
            revdfs(nbr, vis, adj); // Fixed the function call to revdfs}}}
int stronglyConnectedComponents(int v, vector<vector<int>>& edges) {
    unordered_map<int, list<int>> adj;
    for (int i = 0; i < edges.size(); i++) {
        int u = edges[i][0];
        int v = edges[i][1];
        adj[u].push_back(v);}
    stack<int> st;
    unordered_map<int, bool> vis;
    // Step 1: Perform DFS to fill the stack with vertices in the finishing order of the original graph
    for (int i = 0; i < v; i++) {
        if (!vis[i]) {
            dfs(i, vis, st, adj);}}
    // Step 2: Create the transpose graph
    unordered_map<int, list<int>> transpose;
    for (int i = 0; i < v; i++) {
        vis[i] = false; // Reset the visited map for the second pass
        for (auto nbr : adj[i]) {
            transpose[nbr].push_back(i);}}
    // Step 3: Process all vertices in order defined by the stack
    int count = 0;
    while (!st.empty()) {
        int top = st.top();
        st.pop();
        if (!vis[top]) {
            count++;
            revdfs(top, vis, transpose);}}
    return count;
}
```

Bellman ford
```c++
/* 
Time complexity: O(N * M)
Space complexity: O(N)
where 'N' is the number of vertices in the graph and 'M' is the number of edges in the graph.
*/
vector<int> bellmonFord(int n, int m, int src, vector<vector<int>> &edges) {
// Create a vector to store the distances from source.
vector<int> d(n + 1, 1e8);
// Distance of source to source is 0.
d[src] = 0;
// Apply bellmonford algorithm.
for (int i = 1; i < n; i++){
for (int j = 0; j < m; j++){
int u = edges[j][0];
int v = edges[j][1];
int w = edges[j][2];
if (d[u] != 1e9 && d[v] > (d[u] + w)) {
d[v] = d[u] + w;
}}}
// Return the distance of destination.
return d;
}
``` 