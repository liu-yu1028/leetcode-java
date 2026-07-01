# 125. Valid Palindrome

## 題目資訊

- 題號：125
- 題名：Valid Palindrome
- 難度：Easy
- 題目連結：https://leetcode.com/problems/valid-palindrome/

## 筆記介紹

這份筆記整理 **125. Valid Palindrome** 的學習過程。這題的核心是用 **Two Pointers 雙指針** 從字串左右兩端往中間比較。

本題有一個很重要的規則：

```text
只比較英文字母與數字；空格、標點符號等非英數字元要忽略。
大小寫視為相同。
```

可讀版筆記請見 [`note.html`](./note.html)。

## 題目理解

給定一個字串 `s`，判斷它在忽略非英數字元、且不區分大小寫後，是否為回文。

例如：

```text
s = "A man, a plan, a canal: Panama"
```

忽略空格與標點、全部視為小寫後，相當於：

```text
amanaplanacanalpanama
```

從左往右和從右往左讀都一樣，所以答案是 `true`。

## 題型判斷

| 分類 | 說明 |
|---|---|
| String | 題目處理字串中的字元 |
| Two Pointers | 從左右兩端往中間比較 |
| Character Handling | 需要判斷英數字元與轉小寫 |

這題和 **242. Valid Anagram** 不同：

| 題目 | 核心 |
|---|---|
| 242 Valid Anagram | 比較字元出現次數 |
| 125 Valid Palindrome | 比較左右順序是否對稱 |

## 使用資料結構

這題不需要額外資料結構，只需要兩個指標：

```java
int left = 0;
int right = s.length() - 1;
```

Java 中常用的字元工具：

```java
Character.isLetterOrDigit(c) // 判斷是否為英文字母或數字
Character.toLowerCase(c)     // 轉成小寫再比較
```

## 解題思路

1. 設定 `left` 指向字串開頭，`right` 指向字串尾端。
2. 當 `left < right` 時重複檢查：
   - 如果 `left` 指到非英數字元，`left++`，略過它。
   - 如果 `right` 指到非英數字元，`right--`，略過它。
   - 如果兩邊都是英數字元，轉小寫後比較。
3. 如果有效字元不同，回傳 `false`。
4. 如果相同，`left++`、`right--`，繼續往中間走。
5. 全部比較完都沒有衝突，回傳 `true`。

## Java 程式碼

請見 [`Solution.java`](./Solution.java)。

## 複雜度分析

| 項目 | 複雜度 | 原因 |
|---|---|---|
| 時間複雜度 | O(n) | 每個字元最多被左右指標掃過一次 |
| 空間複雜度 | O(1) | 只使用左右指標與暫存字元 |

## 核心一句話

> Valid Palindrome：左右指標往中間走，遇到非英數字元就跳過，只有有效字元才轉小寫後比較。
