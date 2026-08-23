<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 4. Binary Search

> *Find a target in a sorted array by halving the search space each step.*

**🧩 Algorithm**
Compare the middle element to the target. Discard the half that can't contain the answer. Repeat. $O(\log n)$ instead of $O(n)$.

**🏢 Workplace**
Don't re-investigate everything from scratch each time. Ask: *"Which half of the problem can I eliminate right now?"* Bisect the incident. Bisect the bug. Bisect the org chart to find who actually owns the decision.

**🌍 Life**
When something breaks — a relationship, a habit, a project — don't start from the beginning. Ask *"is the problem in the first half or the second half?"* then zoom in. Most debugging is people-debugging, and people-debugging benefits from bisection too.

**⚠️ Anti-pattern**
*"Let me just re-read the whole thing from the top."*
That's linear search. You're paying $O(n)$ for what should cost $O(\log n)$. Before reading everything, ask which half you can safely ignore.
