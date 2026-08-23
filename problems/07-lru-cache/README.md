<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 7. LRU Cache

> *A cache of fixed size that evicts the least recently used item when full.*

**🧩 Algorithm**
Maintain a bounded store. On access, mark the item as recently used. When the store is full and a new item arrives, evict the least recently used one. Capacity is fixed; recency is the policy.

**🏢 Workplace**
Your working memory for context is finite. You can't hold every project, every colleague's preference, every API quirk simultaneously. The healthy move: let the stale stuff fade, and **build a system to reload it fast when needed**. Docs, wikis, and bookmarks are your eviction-aware reload mechanism.

**🌍 Life**
Forgetting is not a failure — it's garbage collection. The skill isn't never forgetting; it's knowing where to look it up. A well-organized note system means "I forgot" costs $O(1)$ to fix instead of $O(\text{awkward})$.

**⚠️ Anti-pattern**
*"I should remember everything."*
No. You should remember the *index* and reload the *content*. People who try to hold everything in their head either burn out or freeze when the cache overflows.
