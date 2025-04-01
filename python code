import heapq

class Graph:
    def __init__(self, vertices):
        self.V = vertices
        self.adj_list = {i: [] for i in range(vertices)}

    def add_edge(self, u, v, weight):
        self.adj_list[u].append((v, weight))
        self.adj_list[v].append((u, weight))  # For undirected graphs

    def dijkstra(self, src):
        # Priority Queue (Min-Heap)
        pq = []
        heapq.heappush(pq, (0, src))
        
        # Distance Table
        distances = {i: float('inf') for i in range(self.V)}
        distances[src] = 0

        while pq:
            curr_dist, u = heapq.heappop(pq)

            # Process each neighbor
            for neighbor, weight in self.adj_list[u]:
                new_dist = curr_dist + weight

                # If a shorter path is found
                if new_dist < distances[neighbor]:
                    distances[neighbor] = new_dist
                    heapq.heappush(pq, (new_dist, neighbor))

        return distances

# Example Usage
graph = Graph(5)
graph.add_edge(0, 1, 10)
graph.add_edge(0, 4, 5)
graph.add_edge(1, 2, 1)
graph.add_edge(2, 3, 4)
graph.add_edge(4, 1, 3)
graph.add_edge(4, 2, 9)
graph.add_edge(4, 3, 2)

src = 0
shortest_paths = graph.dijkstra(src)

print(f"Shortest distances from source {src}: {shortest_paths}")
