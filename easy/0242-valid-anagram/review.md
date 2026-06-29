# Review：242. Valid Anagram

## 本題核心觀念

這題的核心是比較兩個字串中每個字母的出現次數。

```text
s 的字母：+1
t 的字母：-1
最後全部抵銷成 0 → true
只要有一格不是 0 → false
```

## Liu 這次的理解與卡住點

### 做得好的地方

- 一開始有先想到長度必須一致。
- 能理解需要記錄兩個字串中字母出現次數。
- 能說出 `s` 加一、`t` 減一是互相抵銷的概念。
- 修正後能寫出完整的 Java 骨架。

### 需要補強的地方

#### 1. Anagram 和 Palindrome 不一樣

這次一開始有把 anagram 想成「往後讀跟往前讀一樣」。

這其實比較像回文 Palindrome。

```text
Palindrome：順讀倒讀一樣
Anagram：字母種類和次數一樣，順序可以不同
```

#### 2. Java 陣列建立要用 `new`

```java
int[] count = new int[26];
```

不是：

```java
int[] count = int[26];
```

#### 3. 字元要轉成 0～25 的索引

不能直接寫：

```java
count[s.charAt(i)]++;
```

要寫：

```java
count[s.charAt(i) - 'a']++;
```

因為 `count` 長度只有 26。

#### 4. 要檢查陣列每一格

不能寫：

```java
if (count == 0)
```

因為 `count` 是陣列。換句話說，count 是陣列，不是一個單一數字，所以要逐一檢查：

```java
for (int num : count) {
    if (num != 0) {
        return false;
    }
}
```

## 關鍵流程

```text
長度不同：return false
建立 count[26]
s 的字母 +1
t 的字母 -1
檢查 count 是否全部為 0
```

## 容易犯的錯

1. 把 Anagram 和 Palindrome 混在一起。
2. 長度不同時誤回傳 `true`。
3. 忘記 `new int[26]`。
4. 忘記 `char - 'a'` 的索引轉換。
5. 把 `count` 陣列當成單一數字檢查。
6. 打錯 Java 關鍵字，例如 `return`。

## 複習問題

1. Anagram 和 Palindrome 差在哪裡？
2. 為什麼長度不同可以直接回傳 `false`？
3. `s.charAt(i) - 'a'` 的作用是什麼？
4. 為什麼最後要檢查 `count` 每一格是不是 0？
