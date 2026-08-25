<p align="center">🌐 语言： &nbsp;<a href="README.md">English</a> &nbsp;·&nbsp; <a href="README.zh.md"><b>中文</b></a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.zh.md#-目录">← 返回目录</a></p>

---

### 7. LRU Cache

> *一个固定大小的缓存，满了就淘汰最久没用过的项。*

**🧩 算法**
问题：你有一个硬容量上限的存储。项被访问（`get`）和插入（`put`）。一旦超过容量，你必须扔掉*最近最少使用*的项——不是绝对时间最老的，而是最久没被碰过的。

直觉做法给每个项打时间戳，淘汰时扫一遍找最小值：每次淘汰 $O(n)$。太慢。

诀窍是两个结构配合：
- 一个**哈希表**（`cache`）做 $O(1)$ 查找：key → 节点。
- 一个**双向链表**做 $O(1)$ 排序：左端是 LRU（最久未用），右端是 MRU（最近用过）。

每次访问把节点移到 MRU 端（`_remove` 再 `_insert_mru`）。淘汰时取 `left.next`——当前的 LRU——并从哈希表删掉。

```python
class Node:
    def __init__(self, key=0, value=0):
        self.key = key        # 数据
        self.value = value    # 数据
        self.prev = None      # 前驱指针
        self.next = None      # 后继指针


class LRUCache:
    def __init__(self, capacity: int):
        self.capacity = capacity
        self.cache = {}

        self.left = Node()   # LRU 端 dummy
        self.right = Node()  # MRU 端 dummy

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

> 时间 $O(1)$ 每次操作 · 空间 $O(\text{capacity})$

更深的原理：**dummy 节点存在是为了你永远不用面对空指针。** `self.left` 和 `self.right` 是永久夹住真实链表的哨兵。因为它们一直在， `_remove` 和 `_insert_mru` 永远不会碰到空链表或缺邻居——每个真实节点都有 `prev` 和 `next`，即使在最两端。边界情况不是被处理了；它**消融**了，因为结构保证它不会发生。这和链表删除是同一个 dummy 技巧——但这里不是为了删头节点，而是为了*永远不用推理一个空链表*。

而核心洞见：**recency 是一个位置，不是时间戳。** 你不存"这个什么时候用过"——你存*它在顺序里的位置*。位置*就是* recency。移到 MRU 端*就是*更新；你不用重算任何东西。链表不告诉你时间，它告诉你*排名*——而淘汰策略只需要排名。

**🏢 职场**
你脑中装上下文的工作记忆是有限的。你不可能同时抓住每个项目的状态、每个同事的偏好、每个 API 的怪癖。LRU 的教训：**让陈旧的淡出，并建立一套系统让需要时能快速重载。**

哈希表是你的文档、wiki、书签——$O(1)$ 重载机制。双向链表是你的*注意力*——你当前放在心里的东西，按 recency 排序。当注意力满了（它永远满），最久没碰的项目从你脑子里被淘汰——但它还在 wiki 里。你没失去它；你*重载*它。dummy 节点是你永远在线的系统（日历、笔记 app），夹住你的工作记忆，让你永远碰不到"我没有任何可依赖的东西"的空指针。

会议里的反模式：那些坚持把一切都放在脑子里、拒绝写下来因为"我会记得"的人。他们的缓存溢出，聊到一半丢掉 LRU 项，也没有哨兵接住他们。建立重载系统。自由淘汰。按需重载。

**🌍 人生**
遗忘不是失败——它是垃圾回收。本事不是从不遗忘；是**知道去哪查。**

你的大脑是一个小容量的 LRU 缓存。每天你访问成千上万的事实；只有最近用过的留下。其余被淘汰。那是健康的。问题不是"我怎么记住一切？"——而是"我从哪重载它？"笔记、照片、日记、给朋友的消息——这些是你的 `cache` 表。链表里的位置是你当前的注意力；表是你的长期存储。

人生的 dummy 节点智慧：**在你的记忆周围保留永远在线的结构，让你永远碰不到空。** 每周写的日记。相册。和记得你过去的人之间的消息串。这些哨兵意味着当你淘汰一段记忆，它不是消失——只是不再在链表前端，而你可以在 $O(1)$ 内重载它。"我忘了"在你建好重载路径后毫无成本。

**⚠️ 反模式**
*"我应该记住一切。"* 不。你应该记住*索引*并重载*内容*。那些试图把一切放在脑子里的人，要么 burnout（缓存颠簸——不断重载），要么在缓存溢出时冻结（恐慌、丢上下文）。LRU 缓存教的是相反的事：**刻意的淘汰是特性，不是 bug。** 忘掉陈旧的。保留最近的。重载其余的。容量是固定的——你的工作是让重载 $O(1)$，而不是假装容量无限。
