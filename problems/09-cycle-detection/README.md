<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 9. Cycle Detection

> *Detect whether a traversal enters a node it has already visited — a cycle.*

**🧩 Algorithm**
Use fast and slow pointers (Floyd's algorithm) or a visited set. If the fast pointer catches the slow one, or a node reappears in the visited set, a cycle exists.

**🏢 Workplace**
If you spend every Monday fixing what broke on Friday — the same outage, the same conflict, the same miscommunication — you're not solving problems. You're traversing a cycle. Detect it: mark the nodes, watch for repeats, and **break the loop** instead of re-walking it.

**🌍 Life**
Recurring arguments with the same person about the same thing are cycles. The way out is not "try harder this time"; it's changing the graph so the edge that creates the loop no longer exists. That might mean a new process, a new boundary, or a new conversation entirely.

**⚠️ Anti-pattern**
*"This time it'll be different."*
If the inputs are the same and the structure is the same, the output will be the same. You're not solving — you're iterating. Break the cycle or accept that it will repeat.
