<p align="center">🌐 语言： &nbsp;<a href="README.md">English</a> &nbsp;·&nbsp; <a href="README.zh.md"><b>中文</b></a> &nbsp;·&nbsp; <a href="README.ja.md">日本語</a></p>

<p align="center"><a href="../README.zh.md#-目录">← 返回目录</a></p>

---

### 19. Sliding Window

> *找不含重复字符的最长子串（#3）。找覆盖所有所需字符的最短子串（#76）。*

**🧩 算法**
滑动窗口是一个连续区间 `[left, right]`，沿数据向前滑动。两个指针不是对撞——它们是**协作**的：`right` 扩张，`left` 修复。right 推进到新领地。left 在窗口违规时收缩。

两种模式，区别就是整个洞察：

**最长合法窗口（#3）：** 扩张 `right` 直到窗口变非法（出现重复）。然后收缩 `left` 直到重新合法。修复*之后*更新答案。口诀：**贪心扩张，坏了再缩。**

```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        seen = set()
        left = 0
        ans = 0

        for right in range(len(s)):
            while s[right] in seen:
                seen.remove(s[left])
                left += 1
            seen.add(s[right])
            ans = max(ans, right - left + 1)

        return ans
```

**最短满足窗口（#76）：** 扩张 `right` 直到窗口*满足*要求（所有字符覆盖）。然后在仍然合法时贪心收缩 `left`，找到最紧的拟合。收缩*过程中*更新答案。口诀：**先扩到够，再尽量缩。**

```python
from collections import Counter, defaultdict

class Solution:
    def minWindow(self, s: str, t: str) -> str:
        need = Counter(t)
        window = defaultdict(int)
        left = 0
        valid = 0
        start = 0
        min_len = float("inf")

        for right, ch in enumerate(s):
            if ch in need:
                window[ch] += 1
                if window[ch] == need[ch]:
                    valid += 1

            while valid == len(need):
                if right - left + 1 < min_len:
                    min_len = right - left + 1
                    start = left

                if s[left] in need:
                    if window[s[left]] == need[s[left]]:
                        valid -= 1
                    window[s[left]] -= 1
                left += 1

        return s[start:start + min_len] if min_len != float("inf") else ""
```

> 时间 $O(n)$——`left` 和 `right` 各最多向右走 $n$ 步 · 空间 $O(k)$，$k$ = 字符集大小

更深的原理：**right 扩进未知；left 修复已知。** right 是探索者——永远往前，不回头，不断加入新领地。left 是修理工——只在出问题时行动，而且只做减法，不做加法。它们不协调却配合：right 不等 left，left 不预测 right。窗口的合法性是连接它们的不变量——right 可能打破它，left 必须恢复它，而答案只在不变量成立时才安全更新。

**🏢 职场**
项目就是一个滑动窗口。`right` 是你增长的 scope——每个 sprint 新来的功能、需求、利益相关者。`left` 是你的清理——废弃旧代码、删过时文档、退役遗留系统。

两种模式直接对应：

**最长窗口（#3）：** 你要最大 scope——更多功能、更多覆盖、更多交付价值。激进扩张。但当新加入造成冲突时（两个团队拥有同一个领域、两个功能重叠），*立刻收缩*直到冲突消失。别在坏的窗口上继续扩张。修复重叠，然后继续走。答案——你的最大有效 scope——只在窗口干净时才有效。

**最短窗口（#76）：** 你要最小成本——最小的团队、最紧的预算、最精简的*仍然覆盖所有需求*的流程。扩张到所有需求都满足，然后*挤*——在仍然覆盖一切的前提下，从左修剪：删多余会议、砍重叠职责、去掉已经被前两个审批覆盖的第三个审批。答案——你的最小可行流程——在*挤压中*找到，不是在扩张后。

而纪律在于：**right 永不回头。** right 不重访已扫描的领地。left 也是。两个指针都只往前走。实操上：一旦你加入了一个利益相关者、一个功能、一个流程步骤，你不"撤销"它——你让 left 移除过时的，right 继续推进新的。没有回溯。窗口向前滑动，一个方向，永不反转。

**🌍 人生**
你的注意力就是滑动窗口。`right` 是新的东西——新的兴趣、新的义务、刚进入你生活的新的人。`left` 是你放手的——不再有用的旧承诺、不再适合的旧习惯、你一直在忍受的精力消耗。

**最长窗口（#3）：** 你要最长的不被打断的专注。扩张 `right`——让新体验进来、接受新挑战。但当冲突出现——重复的承诺、反复的义务、打碎你心流的东西——*立刻收缩 `left`*。丢掉造成冲突的旧东西。别容忍生活中的重复。最长的未被打断的专注来自激进扩张 + 即时修复。

**最短窗口（#76）：** 你要最精简的*仍然覆盖所有重要事*的生活。扩张到所有需求满足——健康、关系、工作、意义。然后*挤*——在仍然覆盖一切的前提下，剪掉多余：不再增值的社交义务、出于内疚维持的爱好、和另外三个重叠的承诺。答案——你的最小可行生活——不是靠永远扩张找到的，而是靠扩张到满足然后挤到紧凑。

而通用原理：**right 永不回头。** 你不重访已经走过的领地。你不"回到"旧版本的自己。`right` 推进到新的，`left` 丢掉过时的。你的生活窗口朝一个方向滑动——向前——而艺术在于知道何时扩张、何时收缩，而不是何时反转。

两句人生口诀：
- **最长心流：** 扩到坏了再缩，缩到好了再扩。别容忍重复。
- **最精生活：** 扩到够了就挤，挤到紧了就好。别背着冗余。

**⚠️ 反模式**
*"再加一件事到窗口里——应该没事。"* 那是只扩张 `right` 从不收缩 `left`。窗口增长到破裂——然后继续增长，因为你从不修复。最长窗口要求坏了就缩；最短窗口要求够了就挤。如果你只扩张不收缩，你既得不到最长合法窗口也得不到最短满足窗口——你得到一个溢出的、臃肿的、什么都不满足也什么都不最大化的窗口。纪律不在扩张中；在收缩中。right 很简单——就是"加更多"。left 才是艺术——知道该丢什么、什么时候丢。
