<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 11. Dijkstra

> *Find the shortest path in a weighted graph where edges have non-negative costs.*

**🧩 Algorithm**
Maintain a priority queue of unvisited nodes keyed by current best-known distance. Repeatedly pick the closest unvisited node, relax its edges, update neighbors. Guaranteed to find the minimum total cost path.

**🏢 Workplace**
The fastest career path is rarely the sequence of most comfortable steps. Sometimes the shortest route goes through a stretch assignment that costs more *now* but shortens the total distance dramatically. Dijkstra optimizes **cumulative cost**, not per-step comfort.

**🌍 Life**
The shortest path to a goal — a skill, a relationship, a savings target — often includes an uncomfortable edge early. Taking the comfortable route every step of the way tends to produce a long path with high total cost. The algorithm is telling you: minimize the sum, not the current step.

**⚠️ Anti-pattern**
*"Always pick the easiest next step."*
That's greedy, not Dijkstra. Greedy gets stuck in local minima. Dijkstra is willing to take a costly step now because it knows the *total* will be lower. Optimize the path, not the step.
