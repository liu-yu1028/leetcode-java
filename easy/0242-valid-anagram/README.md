# 242. Valid Anagram

## 題目資訊

- 題號：242
- 題名：Valid Anagram
- 難度：Easy
- 題目連結：https://leetcode.com/problems/valid-anagram/

## 題目理解

給定兩個字串 `s` 和 `t`，判斷 `t` 是否為 `s` 的 anagram。

Anagram 的意思是：

```text
兩個字串使用的字母種類一樣，且每個字母出現次數一樣，只是順序可以不同。
```

例如：

```text
s = "anagram"
t = "nagaram"
```

兩個字串的字母次數相同，所以答案是 `true`。

## 題型判斷

| 分類 | 說明 |
|---|---|
| String | 題目處理兩個字串 |
| Counting | 需要比較每個字母出現次數 |
| Array | 題目限制為小寫英文字母時，可用 `int[26]` 計數 |

這題不是判斷回文。回文是從前往後和從後往前讀一樣；anagram 是比較字母出現次數。

## 使用資料結構

使用 `int[26] count` 記錄小寫英文字母 `a` 到 `z` 的次數。

| 字母 | 對應 index |
|---|---|
| `a` | `0` |
| `b` | `1` |
| `c` | `2` |
| ... | ... |
| `z` | `25` |

Java 中可以用：

```java
s.charAt(i) - 'a'
```

把字元轉成 `0 ~ 25` 的陣列索引。

## 解題思路

1. 如果 `s` 和 `t` 長度不同，直接回傳 `false`。
2. 建立 `int[] count = new int[26];`。
3. 走訪字串：
   - `s` 的字母出現時，對應位置 `+1`。
   - `t` 的字母出現時，對應位置 `-1`。
4. 如果兩個字串是 anagram，最後 `count` 每一格都會抵銷成 `0`。
5. 只要有任一格不是 `0`，回傳 `false`。
6. 全部都是 `0`，回傳 `true`。

## HashMap 解法補充

為了銜接前面練過的 HashMap，也可以用 `HashMap<Character, Integer>` 解這題。

這時候 HashMap 存的是：

```text
字元 -> 出現次數
```

例如：

```text
'a' -> 2
'b' -> 1
```

流程一樣是抵銷：

```java
map.put(c, map.getOrDefault(c, 0) + 1); // s 的字母 +1
map.put(c, map.getOrDefault(c, 0) - 1); // t 的字母 -1
```

要注意：

```java
map.getOrDefault(c, 0) + 1;
```

這行只是算出新的數字，**不會自動更新 map**。  
如果要真的改變 HashMap，必須用：

```java
map.put(c, map.getOrDefault(c, 0) + 1);
```

最後要檢查所有 value：

```java
for (int count : map.values()) {
    if (count != 0) {
        return false;
    }
}
```

`map.values()` 是一整個集合，不能直接拿來跟 `0` 比。

## Java 程式碼

請見 [`Solution.java`](./Solution.java)。目前 `Solution.java` 使用較精簡的 `int[26]` 寫法；上面的 HashMap 解法是為了理解「字元 -> 次數」的延伸概念。

## 解法分頁

為了避免同一題不同解法混在一起，這題的可讀版筆記拆成不同頁面：

| 解法 | 頁面 |
|---|---|
| `int[26]` 計數法 | [`solutions/int-array.html`](./solutions/int-array.html) |
| HashMap 計數法 | [`solutions/hashmap.html`](./solutions/hashmap.html) |

`note.html` 作為本題總覽頁，負責連到各個解法頁。

## 複雜度分析

| 項目 | 複雜度 | 原因 |
|---|---|---|
| 時間複雜度 | O(n) | 走訪字串一次，再檢查 26 個字母 |
| 空間複雜度 | O(1) | `count` 固定長度為 26 |

## 核心一句話

> Valid Anagram：用 `int[26]` 記錄字母次數，`s` 加一、`t` 減一，最後全部為 0 才是 anagram。
