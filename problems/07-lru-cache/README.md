<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 7. LRU Cache

> *A fixed-size cache that evicts the least recently used item when full.*

**🧩 Algorithm**
The problem: you have a store with a hard capacity limit. Items are accessed (`get`) and inserted (`put`). When you exceed capacity, you must throw out the item that was *used least recently* — not the one oldest in absolute time, but the one that's been untouched the longest.

The naive approach keeps a timestamp on each item and scans for the minimum on eviction: $O(n)$ per eviction. Too slow.

The trick is two structures working together:
- A **hash map** (`cache`) for $O(1)$ lookup: key → node.
- A **doubly-linked list** for $O(1)$ ordering: the left end is the LRU (least recently used), the right end is the MRU (most recently used).

Every access moves the node to the MRU end (`_remove` then `_insert_mru`). Eviction pulls `left.next` — the current LRU — and deletes it from the map.

```python
class Node:
    def __init__(self, key=0, value=0):
        self.key = key        # data
        self.value = value    # data
        self.prev = None      # predecessor pointer
        self.next = None      # successor pointer


class LRUCache:
    def __init__(self, capacity: int):
        self.capacity = capacity
        self.cache = {}

        self.left = Node()   # LRU end dummy
        self.right = Node()  # MRU end dummy

        self.left.next = self.right
        self.right.prev = self.left

    def _remove(self, node):
        prev_node = node.prev
        next_node = node.next
        prev_node.next = next_node
        next_node.prev = prev_node

    def _insert_mru(self, node):
        prev_node = self.right.prev
        prev_node.next = node
        node.prev = prev_node
        node.next = self.right
        self.right.prev = node

    def get(self, key: int) -> int:
        if key not in self.cache:
            return -1
        node = self.cache[key]
        self._remove(node)
        self._insert_mru(node)
        return node.value

    def put(self, key: int, value: int) -> None:
        if key in self.cache:
            old = self.cache[key]
            self._remove(old)
        node = Node(key, value)
        self.cache[key] = node
        self._insert_mru(node)
        if len(self.cache) > self.capacity:
            lru = self.left.next
            self._remove(lru)
            del self.cache[lru.key]
```

> Time $O(1)$ per operation · Space $O(\text{capacity})$

The deeper principle: **the dummy nodes exist so you never have a null pointer.** `self.left` and `self.right` are sentinels that permanently bracket the real list. Because they're always there, `_remove` and `_insert_mru` never hit an empty list or a missing neighbor — every real node has a `prev` and a `next`, even at the very ends. The edge cases don't get handled; they **dissolve**, because the structure guarantees they can't occur. This is the same dummy trick as the linked-list deletion — but here it's not about removing the head, it's about *never having an empty list to reason about*.

And the core insight: **recency is a position, not a timestamp.** You don't store "when was this used" — you store *where it sits in the order*. The position *is* the recency. Moving to the MRU end *is* the update; you don't recompute anything. The list doesn't tell you the time, it tells you the *rank* — and rank is all the eviction policy needs.

**🏢 Workplace**
Your working memory for context is finite. You cannot hold every project's status, every colleague's preference, every API quirk simultaneously. The LRU lesson: **let the stale fade, and build a system to reload it fast when needed.**

The hash map is your docs, wiki, bookmarks — the $O(1)$ reload mechanism. The doubly-linked list is your *attention* — what you're currently holding in mind, ordered by recency. When attention is full (it always is), the least-recently-touched project gets evicted from your head — but it's still in the wiki. You don't lose it; you *reload* it. The dummy nodes are your always-on systems (calendar, notes app) that bracket your working memory so you never hit the "I have nothing to fall back on" null pointer.

The anti-pattern in meetings: people who insist on keeping everything in their head, who refuse to write things down because "I'll remember." Their cache overflows, they drop the LRU item mid-conversation, and there's no sentinel to catch them. Build the reload system. Evict freely. Reload on demand.

**🌍 Life**
Forgetting is not a failure — it's garbage collection. The skill isn't never forgetting; it's **knowing where to look it up**.

Your brain is an LRU cache with a small capacity. Every day you access thousands of facts; only the recently-used ones stay. The rest get evicted. That's healthy. The question isn't "how do I remember everything?" — it's "where do I reload it from?" Notes, photos, journals, a message to a friend — these are your `cache` map. The position in the list is your current attention; the map is your long-term store.

The dummy-node wisdom for life: **keep always-on structures around your memory so you never hit a null.** A journal you write in weekly. A photo album. A message thread with someone who remembers your past. These sentinels mean that when you evict a memory, it's not gone — it's just no longer in the front of the list, and you can reload it in $O(1)$. "I forgot" costs nothing when you've built the reload path.

**⚠️ Anti-pattern**
*"I should remember everything."*
No. You should remember the *index* and reload the *content*. People who try to hold everything in their head either burn out (cache thrashing — constantly re-loading) or freeze when the cache overflows (panic, dropped context). The LRU cache teaches the opposite: **deliberate eviction is a feature, not a bug.** Forget the stale. Keep the recent. Reload the rest. The capacity is fixed — your job is to make reload $O(1)$, not to pretend capacity is infinite.
