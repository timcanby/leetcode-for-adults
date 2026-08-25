<!-- リポジトリバナー -->
<p align="center">
  <img src="assets/banner.png" alt="LeetCode for Adults — アルゴリズム、オフィス政治、そして誰も教えてくれなかったこと。" width="100%">
</p>

<h1 align="center">LeetCode for Adults</h1>

<p align="center">
  <strong>アルゴリズム、オフィス政治、そして誰も教えてくれなかったこと。</strong>
</p>

<p align="center">
  🌐 <b>言語：</b>
  &nbsp;<a href="README.md">English</a>
  &nbsp;·&nbsp;<a href="README.zh.md">中文</a>
  &nbsp;·&nbsp;<a href="README.ja.md"><b>日本語</b></a>
</p>

<p align="center">
  <a href="#-これ何"><b>これ何？</b></a> &nbsp;·&nbsp;
  <a href="#-テンプレート"><b>テンプレート</b></a> &nbsp;·&nbsp;
  <a href="#-新しいエントリーの追加方法"><b>エントリー追加</b></a> &nbsp;·&nbsp;
  <a href="#-カタログ"><b>カタログ</b></a> &nbsp;·&nbsp;
  <a href="#-ライセンス"><b>ライセンス</b></a>
</p>

---

## 🧠 これ何？

**LeetCode はアルゴリズム問題集ではない——大人のためのサバイバルシミュレータだ。**

面接が終わってもずっと後に現れるパターンが、どの古典的問題にもエンコードされている：チームのマネジメントの中に、ボトルネックとの交渉の中に、一週間の会議のトリアージの中に、何を忘れるべきかの判断の中に。

このリポジトリは有名なアルゴリズム問題を**職場の教訓、人生の教訓、アンチパターン**として再構成する——一つの再利用可能なテンプレートを使って。構造は毎回同じだから、脳は暗記ではなくパターンマッチできる。誰でもいつでも、以下のテンプレートに埋めるだけで新エントリーを追加できる。

---

## 📐 テンプレート

各エントリーは**同じ四幕構成**に従う——プラス任意のボーナス幕：

| 幕 | 必須？ | 絵文字 | 答える問い |
|-----|--------|--------|-----------|
| **アルゴリズム** | ✅ はい | 🧩 | そのアルゴリズムは実際に何をするのか？ |
| **職場** | ✅ はい | 🏢 | このパターンは職場のどこに現れるか？ |
| **人生** | ✅ はい | 🌍 | 日常生活のどこに現れるか？ |
| **アンチパターン** | ✅ はい | ⚠️ | 正しそうに見えて実は間違っているやり方とは？ |
| **権力闘争** | ⬜ 任意 | 🪞 | 職場の力学が独自のセクションに値する場合に使用（権限、ゲートキーピング、派閥力学など） |

### 空白テンプレート

以下のブロックをコピーし、記入して `problems/NN-slug/README.ja.md` として保存する：

```markdown
<p align="center">🌐 言語： &nbsp;<a href="README.md">English</a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md"><b>日本語</b></a></p>

<p align="center"><a href="../README.ja.md#-カタログ">← カタログに戻る</a></p>

---

### N. [問題名]

> *[一文で問題の説明。]*

**🧩 アルゴリズム**
[アルゴリズムが何をするかを平易に説明。直感を増すなら計算量にも言及。]

**🏢 職場**
[職場でこのパターンはどこに現れるか？ 具体的に——雰囲気ではなくシナリオを述べる。]

**🪞 権力闘争**  <!-- 任意：権力の力学が本当の核心の時のみ記載 -->
[権限、許認可、派閥構造がボトルネックの場合、ここで指摘する。]

**🌍 人生**
[職場以外でどこに現れるか？ 共感できるものを——体力、人間関係、習慣、時間。]

**⚠️ アンチパターン**
[人が本能的にやってしまう、正しそうに見えて実は間違っているやり方とは？ 引用で囲んでから否定する。]
```

### うまく書くコツ

- **アルゴリズム** → まず平易な言葉、計算量はその後。読者は Big-O の前に*アイデア*を理解すべき。
- **職場** → 具体的なシナリオを言う（「同じ議題を扱う二つの定例会議」）。雰囲気を言わない（「コミュニケーションは難しい」）。
- **人生** → 共感できる例を一つ。リストにしない。読者はメモを取るのではなく、頷くべき。
- **アンチパターン** → まず間違った直感を引用で囲み、次に*なぜ*間違っているかを説明。形式：*"間違った直感"* → なぜ間違っているか → 正しいやり方。
- **権力闘争** → 本当のボトルネックが*努力*ではなく*権力*の時のみ使用。職場の教訓が政治ではなくプロセスに関するものならスキップ。

---

## ➕ 新しいエントリーの追加方法

1. アルゴリズム問題を選ぶ（古典的 LeetCode、教科書、または実世界）。
2. 新しいディレクトリを作成：`problems/NN-slug/`（例：`problems/13-valid-palindrome/`）。
3. [空白テンプレート](#空白テンプレート)を `README.md`、`README.zh.md`、`README.ja.md` にコピー——各言語一つずつ。
4. 四つの必須幕をすべて記入する。**権力闘争**は適切な場合のみ追加。
5. 下の[目次](#-カタログ)に `#`、問題名、一行の核心的教訓を追記する。
6. コミットメッセージ：`docs: add [問題名] entry`。

> **経験則：** 四幕すべてを具体例で埋められないなら、その問題はまだ準備ができていない。比喩がクリックした時にまた戻ってこよう。

---

## 📖 カタログ

各問題は独自のディレクトリ（`problems/NN-slug/`）にあり、三つの言語版が含まれている。クリックして詳細を読む。

### 目次

| # | 問題 | 核心的教訓 |
|---|------|-----------|
| 1 | [Two Sum](problems/01-two-sum/README.ja.md) | 補完リソースを探せ、一人で総当たりするな |
| 2 | [Container With Most Water](problems/02-container-with-most-water/README.ja.md) | ボトルネックが上限を決める |
| 3 | [Sliding Window](problems/03-sliding-window/README.ja.md) | 精力の窓は有限——古いものは適時に捨てる |
| 4 | [Binary Search](problems/04-binary-search/README.ja.md) | 毎回最初から調査するな |
| 5 | [Merge Intervals](problems/05-merge-intervals/README.ja.md) | 重なる責任範囲は統合すべき |
| 6 | [Top K Frequent](problems/06-top-k-frequent/README.ja.md) | 全ての声に答える必要はない |
| 7 | [LRU Cache](problems/07-lru-cache/README.ja.md) | 忘れても大丈夫、リロードできれば |
| 8 | [Graph / DFS](problems/08-graph-dfs/README.ja.md) | 組織図は木ではなくグラフだ |
| 9 | [Cycle Detection](problems/09-cycle-detection/README.ja.md) | 昨日のトラブルを直しているなら、もうループに入っている |
| 10 | [Union Find](problems/10-union-find/README.ja.md) | 誰と誰が本当は同じ陣営なのか？ |
| 11 | [Dijkstra](problems/11-dijkstra/README.ja.md) | 最短経路 ≠ 各ステップが最も快適 |
| 12 | [Dynamic Programming](problems/12-dynamic-programming/README.ja.md) | 最善の手は現在の状態に依存する |
| 13 | [Two Sum II](problems/13-two-sum-ii/README.ja.md) | 先に秩序を確立し、それから戦略を調整する |
| 14 | [Boats to Save People](problems/14-boats-to-save-people/README.ja.md) | 先にボトルネックを解決し、柔軟な充填材は最後に残す |
| 15 | [Move Zeroes](problems/15-move-zeroes/README.ja.md) | ノイズを動かすな——大事なものを圧縮せよ |
| 16 | [Remove Duplicates](problems/16-remove-duplicates-from-sorted-array/README.ja.md) | 先にソートし、それから重複を排除する |
| 17 | [Linked List Cycle](problems/17-linked-list-cycle/README.ja.md) | サイクルの検出に記憶は不要——力学が必要 |
| 18 | [3Sum](problems/18-3sum/README.ja.md) | 思考がソートされたら前に進め——振り返るな |
| 19 | [Sliding Window](problems/19-sliding-window/README.ja.md) | right は未知に拡張し、left は既知を修復する |
| 20 | [Find All Anagrams](problems/20-find-all-anagrams-in-a-string/README.ja.md) | フレームが固定なら変えるな——スライドして確認する |
| 21 | [Longest Repeating Character Replacement](problems/21-longest-repeating-character-replacement/README.ja.md) | ノイズゼロは要らない——予算に収まるノイズが要る |
| 22 | [Find First and Last Position](problems/22-find-first-and-last-position-in-sorted-array/README.ja.md) | 境界を見つけることは値を見つけることと同じではない |
| 23 | [Bubble Sort](problems/23-bubble-sort/README.ja.md) | 最大の問題が最初に表面化する——摩擦の不在が完了のシグナル |
| 24 | [Selection Sort](problems/24-selection-sort/README.ja.md) | 全てを見てからコミットする——そして取り消し不能に |
| 25 | [Insertion Sort](problems/25-insertion-sort/README.ja.md) | 孤立して選ぶのではない——安定したものの中で自分のレベルを見つける |
| 26 | [Merge Sort](problems/26-merge-sort/README.ja.md) | 大きな問題はまだ半分に切っていない小さな問題にすぎない |
| 27 | [Quick Sort](problems/27-quick-sort/README.ja.md) | 進歩には完璧なバランスは要らない——ピボットが要る |
| 28 | [Heap Sort](problems/28-heap-sort/README.ja.md) | データを直接ソートするのではない——構造を課し、構造が代わりにソートする |
| 29 | [Counting Sort](problems/29-counting-sort/README.ja.md) | 数えられるものを比較する必要はない——範囲が答えだ |
| 30 | [Bucket Sort](problems/30-bucket-sort/README.ja.md) | 散らしてからソートせよ——分解が部分をソート可能にする |
| 31 | [Delete a Value from a Linked List](problems/31-delete-a-value-from-a-linked-list/README.ja.md) | ノードを破壊するのではない——それに届くポインタをリダイレクトする |

> 💡 新しい問題を追加したい？ 上の[新しいエントリーの追加方法](#-新しいエントリーの追加方法)を参照。

---

## 🧭 メタレッスン

> **アルゴリズムはコードについてではない。決定の形についてだ。**

上のどの問題にも構造がある——そしてその構造は会議の中、人間関係の中、日曜の午後の過ごし方の中に再現する。面接は終わった。パターンは終わっていない。

---

## 📄 ライセンス

[MIT](LICENSE) ——サバイバルの知恵はオープンソースであるべきだから。

---

<p align="center">
  <sub>カフェイン、グラフ理論、そして軽度の組織トラウマで構築。</sub>
</p>
