<!-- 仓库横幅 -->
<p align="center">
  <img src="assets/banner.png" alt="LeetCode for Adults — 算法、职场政治，以及没人提前告诉你的那些事。" width="100%">
</p>

<h1 align="center">LeetCode for Adults</h1>

<p align="center">
  <strong>算法、职场政治，以及没人提前告诉你的那些事。</strong>
</p>

<p align="center">
  🌐 <b>语言：</b>
  &nbsp;<a href="README.md">English</a>
  &nbsp;·&nbsp;<a href="README.zh.md"><b>中文</b></a>
  &nbsp;·&nbsp;<a href="README.ja.md">日本語</a>
</p>

<p align="center">
  <a href="#-这是什么"><b>这是什么？</b></a> &nbsp;·&nbsp;
  <a href="#-模板"><b>模板</b></a> &nbsp;·&nbsp;
  <a href="#-如何添加新条目"><b>添加条目</b></a> &nbsp;·&nbsp;
  <a href="#-目录"><b>目录</b></a> &nbsp;·&nbsp;
  <a href="#-许可证"><b>许可证</b></a>
</p>

---

## 🧠 这是什么？

**LeetCode 不是算法题集——它是成年人生存模拟器。**

每道经典题目背后都藏着一个模式，这个模式在面试结束很久之后依然会浮现：在你管理团队的方式里，在你和一个瓶颈博弈的过程里，在你清理一周会议日程的取舍里，在你决定该忘掉什么的时候。

这个仓库把知名的算法题重新表述为**职场课、人生课和反模式**——使用一套可复用的模板。结构每次都一样，这样你的大脑是在模式匹配，而不是死记硬背。任何人随时都可以按下面的模板添加新条目。

---

## 📐 模板

每个条目遵循**统一的四幕结构**——外加一个可选的附加幕：

| 幕 | 必填？ | 图标 | 它回答的问题 |
|-----|--------|------|-------------|
| **算法** | ✅ 是 | 🧩 | 这个算法到底在做什么？ |
| **职场** | ✅ 是 | 🏢 | 这个模式在工作中哪里会出现？ |
| **人生** | ✅ 是 | 🌍 | 在日常生活中哪里会出现？ |
| **反模式** | ✅ 是 | ⚠️ | 什么样的做法听起来对但其实错了？ |
| **权力博弈** | ⬜ 可选 | 🪞 | 当职场动态足够精彩、值得单独开一段时使用（例如权力、审批关卡、派系博弈） |

### 空白模板

复制以下代码块，填写后保存为 `problems/NN-slug/README.zh.md`：

```markdown
<p align="center">🌐 语言： &nbsp;<a href="README.md">English</a> &nbsp;·&nbsp; <a href="README.zh.md"><b>中文</b></a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.zh.md#-目录">← 返回目录</a></p>

---

### N. [题目名]

> *[一句话描述题目。]*

**🧩 算法**
[用通俗的语言解释算法在做什么。如果复杂度能增加直觉理解，就提一下。]

**🏢 职场**
[这个模式在工作中哪里出现？要具体——说出场景，而不仅仅是感觉。]

**🪞 权力博弈**  <!-- 可选：仅当权力动态才是真正核心时才写 -->
[当权力、审批权或派系结构是瓶颈时，在这里点出来。]

**🌍 人生**
[在工作之外哪里会出现？保持接地气——精力、人际关系、习惯、时间。]

**⚠️ 反模式**
[人们本能地会做什么、听起来对但其实是错的做法？用引号框出来，然后反驳它。]
```

### 怎样填得好

- **算法** → 先用大白话说清楚，再给复杂度记号。读者应该先理解*想法*，再看到 Big-O。
- **职场** → 说一个具体的场景（"两个例会讨论的是同一份议程"），不要说感觉（"沟通很难"）。
- **人生** → 一个接地气的例子。不要列清单。读者应该点头，而不是记笔记。
- **反模式** → 先用引号框出错误直觉，然后解释*为什么*错了。格式：*"错误直觉"* → 为什么错 → 正确做法。
- **权力博弈** → 只有当真正的瓶颈是*权力*而非*努力*时才用。如果职场课讲的是流程而非政治，就跳过。

---

## ➕ 如何添加新条目

1. 选一道算法题（经典 LeetCode、教科书、或真实场景）。
2. 创建新目录：`problems/NN-slug/`（例如 `problems/13-valid-palindrome/`）。
3. 把[空白模板](#空白模板)复制到 `README.md`、`README.zh.md`、`README.ja.md` ——每个语言一个文件。
4. 填写四个必填幕。只在合适时加上**权力博弈**。
5. 在下方[目录](#-目录)中加一行：序号、题目名、一句话核心教训。
6. 提交信息：`docs: add [题目名] entry`。

> **经验法则：** 如果你没法用具体的例子填满全部四幕，说明这道题还没准备好。等比喻真正"对上"了再回来。

---

## 📖 目录

每道题有独立的目录（`problems/NN-slug/`），包含三个语言版本。点击进入查看完整内容。

### 索引

| # | 题目 | 核心教训 |
|---|------|---------|
| 1 | [Two Sum](problems/01-two-sum/README.zh.md) | 找互补资源，别一个人硬算 |
| 2 | [Container With Most Water](problems/02-container-with-most-water/README.zh.md) | 瓶颈决定上限 |
| 3 | [Sliding Window](problems/03-sliding-window/README.zh.md) | 精力窗口有限——及时清理旧任务 |
| 4 | [Binary Search](problems/04-binary-search/README.zh.md) | 别每次都从头排查 |
| 5 | [Merge Intervals](problems/05-merge-intervals/README.zh.md) | 重叠的责任范围应该合并 |
| 6 | [Top K Frequent](problems/06-top-k-frequent/README.zh.md) | 不需要回应每一个声音 |
| 7 | [LRU Cache](problems/07-lru-cache/README.zh.md) | 忘了没关系，能快速重新加载就行 |
| 8 | [Graph / DFS](problems/08-graph-dfs/README.zh.md) | 组织架构是图，不是树 |
| 9 | [Cycle Detection](problems/09-cycle-detection/README.zh.md) | 如果你在修昨天搞出来的问题，你已经在循环里了 |
| 10 | [Union Find](problems/10-union-find/README.zh.md) | 谁和谁其实是一派的？ |
| 11 | [Dijkstra](problems/11-dijkstra/README.zh.md) | 最短路径 ≠ 每一步都最舒服 |
| 12 | [Dynamic Programming](problems/12-dynamic-programming/README.zh.md) | 最优解取决于你当前的状态 |
| 13 | [Two Sum II](problems/13-two-sum-ii/README.zh.md) | 先建立秩序，再调整战略 |
| 14 | [Boats to Save People](problems/14-boats-to-save-people/README.zh.md) | 先解决瓶颈，简单的事留作灵活填充 |
| 15 | [Move Zeroes](problems/15-move-zeroes/README.zh.md) | 别搬噪声——压实重要的 |
| 16 | [Remove Duplicates](problems/16-remove-duplicates-from-sorted-array/README.zh.md) | 先排序，再去重 |
| 17 | [Linked List Cycle](problems/17-linked-list-cycle/README.zh.md) | 检测环不需要记忆——需要动力学 |
| 18 | [3Sum](problems/18-3sum/README.zh.md) | 思绪理清后就往前走，不要回头 |
| 19 | [Sliding Window](problems/19-sliding-window/README.zh.md) | right 扩进未知，left 修复已知 |
| 20 | [Find All Anagrams](problems/20-find-all-anagrams-in-a-string/README.zh.md) | 框架固定就别改——滑过去，查一查 |
| 21 | [Longest Repeating Character Replacement](problems/21-longest-repeating-character-replacement/README.zh.md) | 不需要零噪声——需要噪声在预算以内 |
| 22 | [Find First and Last Position](problems/22-find-first-and-last-position-in-sorted-array/README.zh.md) | 找边界不等于找值 |
| 23 | [Bubble Sort](problems/23-bubble-sort/README.zh.md) | 最大的问题最先浮现——摩擦消失就是完成的信号 |
| 24 | [Selection Sort](problems/24-selection-sort/README.zh.md) | 看清一切再承诺——承诺了就不回头 |
| 25 | [Insertion Sort](problems/25-insertion-sort/README.zh.md) | 不在真空中选择——在已安定中找到自己的层级 |
| 26 | [Merge Sort](problems/26-merge-sort/README.zh.md) | 大问题只是你还没对半切的小问题 |

> 💡 想添加新题目？参见上方的[如何添加新条目](#-如何添加新条目)。

---

## 🧭 元教训

> **算法不是关于代码的。它们是关于决策的形状。**

上面的每道题都有一个结构——而那个结构会在会议中、在关系中、在你怎么安排一个周日下午时反复出现。面试结束了。模式没有。

---

## 📄 许可证

[MIT](LICENSE) ——因为生存技巧理应开源。

---

<p align="center">
  <sub>用咖啡因、图论和轻度组织创伤写成。</sub>
</p>
