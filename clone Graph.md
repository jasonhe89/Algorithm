思路： 通过bfs 遍历得到所有的node 建立一个arrayList

再建立一个hash表 hashMap 用来存储原图的点a 和新图的a’ 之间的索引。

loop arrayList，访问每个节点的边，同时把该边的关系建立到新的图上 eg a—b \<=\> a’—b’

返回a’ （通过hash)

```java
class UndirectedGraphNode {
	int label;
	ArrayList <UndirectedGraphNode> neighbors;
	UndirectedGraphNode(int x) {label = x; neighbors = new ArrayList<UndirectedGraphNode>(); }
}
public class Solution {

	public UndirectedGraphNode cloneGraph (UndirectedGraphNode node){
		if（node == null){
			return node;
		}
		//use bfs algorithm to traverse the graph and get all nodes;
		ArrayList<UndirectedGraphNode> nodes = getNodes(node);

		//copy nodes, store the old-> new mapping information in a hash map
		HashMap<UndirectedGraphNode, UndirectedGraphNode> mapping = new HashMap<>();
		for (UndirectedGraphNode n : nodes){
			mapping.put(n, new UndirectedGraphNode(n.label));
		}
		//copy neighbors(edges)
		for (UndirectedGraphNode n : nodes){
			//for n in nodes, loop all edges and add this edges to new graph.
			UndirectedGraphNode newNode = mapping.get(n);
			for (UndirectedGraphNode neighbor : n.neighbors){
				UndirectedGraphNode newNeighbor = mapping.get(neighbor);
				newNode.neighbors.add(newNeighbor);
			}

		}

		return mapping.get(node);

	}

	private ArrayList<UndirectedGraphNode> getNodes(UndirectedGraphNode node){
		//bfs
		//add initial node to queue
		//while queue is not empty
		//queue.offer => visiting node, add all neighbor visiting node to queue, add node to arraylist
		Queue<UndirectedGraphNode> queue = new LinkedList<UndirectedGraphNode>();
		HashSet<UndirectedGraphNode> set = new HashSet<>();

		queue.offer(node);
		set.add(node);
		while(!queue.isEmpty()){
			UndirectedGraphNode head = queue.poll();
			for (UndirectedGraphNode neighbor : head.neighbors){
				if(!set.contains(neighbor)){
					set.add(neighbor);
					queue.offer(neighbor);
				}
			}

		}

		return new ArrayList<UndirectedGraphNode>(set);
	}


}
```

```python
# Definition for a undirected graph node
# class UndirectedGraphNode:
#     def __init__(self, x):
#         self.label = x
#         self.neighbors = []
class Solution:
    # @param node, a undirected graph node
    # @return a undirected graph node
    def __init__(self):
        self.dict = {}
        
    def cloneGraph(self, node):
        # write your code here
        if node == None:
            return None
        
        if node.label in self.dict:
            return self.dict[node.label]
        #建立与当前node 对应的节点
        root = UndirectedGraphNode(node.label)
        # 把该节点的引用放入到dict 中， key 为node.label, value 为root ***** node.label -> root
        self.dict[node.label] = root
        # 访问node.label的所有neighbor, 创建新node 并连接到root 上
        for item in node.neighbors:
            root.neighbors.append(self.cloneGraph(item))
        
        return root
        
```

```python
from collections import deque
class Solution:
    # @param node, a undirected graph node
    # @return a undirected graph node
    def __init__(self):
        self.dict = {}
        
    def cloneGraph(self, node):
        # write your code here
        if node is None:
            return node
        nodes = self.getNodes(node)
        f = {}
        for n in nodes:
            f[n] = UndirectedGraphNode(n.label)
        
        for n in nodes:
            newNode = f[n]
            for neighbor in n.neighbors:
                newNeighbor = f[neighbor]
                newNode.neighbors.append(newNeighbor)
        return f[node]
        
        
    def getNodes(self,node):
        queue = deque([])
        visited = set()
        queue.append(node)
        visited.add(node)
        while len(queue) != 0:
            head = queue.popleft()
            for neighbor in head.neighbors:
                if neighbor not in visited:
                    visited.add(neighbor)
                    queue.append(neighbor)
        return list(visited)
```