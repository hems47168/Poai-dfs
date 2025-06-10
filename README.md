# Poai-dfs
class Graph:
    def __init__(self):
        self.adjacency_list = {}

  def add_edge(self, vertex1, vertex2):
        if vertex1 not in self.adjacency_list:
            self.adjacency_list[vertex1] = []
        if vertex2 not in self.adjacency_list:
            self.adjacency_list[vertex2] = []
        self.adjacency_list[vertex1].append(vertex2)
        self.adjacency_list[vertex2].append(vertex1)

   def dfs(self, start_vertex):
        visited = set()
        traversal_order = []
        self._dfs_helper(start_vertex, visited, traversal_order)
        return traversal_order

   def _dfs_helper(self, vertex, visited, traversal_order):
        visited.add(vertex)
        traversal_order.append(vertex)
        for neighbor in self.adjacency_list[vertex]:
            if neighbor not in visited:
                self._dfs_helper(neighbor, visited, traversal_order)


# Example usage
if __name__ == "__main__":
    graph = Graph()
    graph.add_edge('A', 'B')
    graph.add_edge('A', 'C')
    graph.add_edge('B', 'D')
    graph.add_edge('C', 'E')
    graph.add_edge('D', 'F')

  start_vertex = 'A'
    traversal_order = graph.dfs(start_vertex)
    print("DFS Traversal Order:", traversal_order)
