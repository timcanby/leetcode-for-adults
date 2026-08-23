<p align="center">🌐 Language: &nbsp;<a href="README.md"><b>English</b></a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.md#-the-catalog">← Back to Catalog</a></p>

---

### 10. Union Find

> *Track which elements belong to the same disjoint set; merge sets on demand.*

**🧩 Algorithm**
Each element starts in its own set. `Union` merges two sets. `Find` tells you which set an element belongs to (with path compression for efficiency). Over time, individual sets merge into larger clusters.

**🏢 Workplace**
Office politics, partly: who and whom are actually in the same faction. Two people who seem independent may share a mentor, a budget line, or a history of mutual promotion. Union-Find models this: you keep merging sets until the real clusters emerge — and the "surprising" alliances make sense.

**🌍 Life**
Communities form by union. Your gym friend and your work friend seem unrelated until you discover they went to the same college. The sets keep merging, and suddenly your world is smaller and more connected than you thought. That's not coincidence — that's the graph contracting.

**⚠️ Anti-pattern**
*"Everyone is independent until proven otherwise."*
Most people are already in a set you haven't detected yet. Assume hidden union edges exist and probe for them — it's faster than discovering them during a conflict.
