<p align="center">🌐 言語： &nbsp;<a href="README.md">English</a> &nbsp;·&nbsp; <a href="README.zh.md">中文</a> &nbsp;·&nbsp; <a href="README.ja.md"><b>日本語</b></a></p>

<p align="center"><a href="../README.ja.md#-カタログ">← カタログに戻る</a></p>

---

### 7. LRU Cache

> *容量固定のキャッシュ。満杯になったら最も最近使われていない項目を追い出す。*

**🧩 アルゴリズム**
問題：ハード容量上限のあるストア。項目はアクセス（`get`）され、挿入（`put`）される。容量を超えた時、捨てるべきは*最も最近使われていない*項目——絶対時間で最も古いのではなく、最も長く触られていないもの。

素朴な手法は各項目にタイムスタンプを付け、追い出し時に最小を走査：$O(n)$ 毎の追い出し。遅すぎる。

コツは二つの構造の協働：
- **ハッシュマップ**（`cache`）$O(1)$ 検索のため：key → ノード。
- **双方向連結リスト** $O(1)$ 順序のため：左端は LRU（最も最近使われていない）、右端は MRU（最も最近使われた）。

全アクセスがノードを MRU 端に動かす（`_remove` してから `_insert_mru`）。追い出しは `left.next`——現在の LRU——を取り、マップから削除する。

```python
class Node:
    def __init__(self, key=0, value=0):
        self.key = key        # データ
        self.value = value    # データ
        self.prev = None      # 前駆ポインタ
        self.next = None      # 後続ポインタ


class LRUCache:
    def __init__(self, capacity: int):
        self.capacity = capacity
        self.cache = {}

        self.left = Node()   # LRU 端ダミー
        self.right = Node()  # MRU 端ダミー

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

> 時間 $O(1)$ 毎操作 · 空間 $O(\text{capacity})$

より深い原理：**ダミーノードは、決してヌルポインタに直面しないように存在する。** `self.left` と `self.right` は実リストを永久に挟むセンチネルだ。彼らが常にそこにいるから、`_remove` も `_insert_mru` も空リストや欠けた隣に遭遇しない——全ての実ノードは `prev` と `next` を持つ、端にいても。エッジケースは処理されない；*溶ける*、構造が発生しないことを保証するから。これはリンクドリスト削除と同じダミーのトリック——だがここではヘッド削除のためではなく、*空リストを推理する必要が永遠にない*ためだ。

そして核心の洞察：**最近性はタイムスタンプではなく、位置だ。** 「いつ使われたか」を保存するのではなく、*順序の中の位置*を保存する。位置*が*最近性だ。MRU 端への移動*が*更新だ；何も再計算しない。リストは時間を教えず、*順位*を教える——そして順位こそが追い出しポリシーが必要とする全てだ。

**🏢 職場**
コンテキストを保持するあなたのワーキングメモリは有限だ。全プロジェクトの状態、全同僚の好み、全 API の癖を同時に持てない。LRU の教訓：**古いものを褪せさせ、必要時に素早くリロードするシステムを構築せよ。**

ハッシュマップはドキュメント、wiki、ブックマーク——$O(1)$ リロード機構。双方向リストはあなたの*注意力*——現在心にあるもの、最近性順。注意力が満杯なら（常にそうだ）、最も長く触られていないプロジェクトが頭から追い出される——だが wiki にはまだある。失わない；*リロード*する。ダミーノードは常時稼働のシステム（カレンダー、ノートアプリ）で、ワーキングメモリを挟み、「頼るものが何もない」ヌルポインタに決して直面しない。

会議のアンチパターン：「全て頭に入れておく、書き残さない、『覚えているから』」という人。彼らのキャッシュは溢れ、会話の途中で LRU 項目を落とし、彼らをキャッチするセンチネルもない。リロードシステムを構築せよ。自由に追い出せ。オンデマンドでリロードせよ。

**🌍 人生**
忘却は失敗ではない——ガベージコレクションだ。本領は決して忘れないことではなく、**どこで検索するかを知る**ことだ。

あなたの脳は小容量の LRU キャッシュだ。毎日何千の事実にアクセスする；最近使ったものだけが残る。残りは追い出される。それは健全だ。問いは「どうやって全てを覚えるか？」ではなく、「どこからリロードするか？」だ。ノート、写真、日記、友人へのメッセージ——これらがあなたの `cache` マップ。リスト内の位置は現在の注意力；マップは長期保存だ。

人生のダミーノードの知恵：**記憶の周りに常時稼働の構造を置き、決してヌルに直面しないようにせよ。** 週に書く日記。フォトアルバム。あなたの過去を覚えている人とのメッセージスレッド。これらのセンチネルは、記憶を追い出してもそれが消えないことを意味する——単にリストの先頭にないだけで、$O(1)$ でリロードできる。「忘れた」はリロード経路を築けば無コストだ。

**⚠️ アンチパターン**
*「私は全てを覚えるべきだ。」* 違う。*索引*を覚え、*内容*をリロードせよ。全てを頭に入れようとする人は、バーンアウトする（キャッシュスラッシング——絶え間ないリロード）か、キャッシュが溢れた時に凍りつく（パニック、コンテキスト喪失）。LRU キャッシュが教えるのは反対：**意図的な追い出しはバグではなく機能だ。** 古いものを忘れよ。最近のものを保て。残りをリロードせよ。容量は固定——あなたの仕事はリロードを $O(1)$ にすることであり、容量が無限だと pretend することではない。
