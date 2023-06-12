# Big-City-Night-Route
Big City Night Route
def solution(city):
    n = len(city)
    frontier = {0}
    back = set()
    distances = [sys.maxsize] * n
    distances[0] = 0
    while frontier:
        u = min(frontier, key=lambda x: distances[x])
        frontier.remove(u)
        back.add(u)
        for v in range(n):
            if city[u][v] != -1 and v not in back:
                new_dist = distances[u] + city[u][v]
                if new_dist < distances[v]:
                    distances[v] = new_dist
                if v not in frontier:
                    frontier.add(v)
    return distances[-1] if distances[-1] != sys.maxsize else -1
