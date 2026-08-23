<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 8. Graph / DFS

> *Traverse all reachable nodes from a starting point via depth-first search.*

**🧩 Algorithm**
From a start node, go as deep as possible along each branch before backtracking. You visit every node reachable through the edges — not just the ones in your immediate tree.

**🏢 Workplace**
Org charts are trees; actual relationships are graphs. You think A reports to B, but A also lunches with C, went to school with D, and owes E a favor. To understand how information and decisions actually flow, traverse the graph — the hidden edges are where the real influence lives.

**🌍 Life**
Your social world is not a tree. Your friend's friend's colleague is two hops away and might be exactly the connection you need. Depth-first exploration of your network — following one thread to its end before backtracking — surfaces opportunities that breadth-first scrolling never will.

**⚠️ Anti-pattern**
*"The org chart tells me who talks to whom."*
It tells you who *reports* to whom. It does not tell you who *trusts* whom. Trust edges are invisible in the chart and decisive in reality. Map the graph, not the tree.
