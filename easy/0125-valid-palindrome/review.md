# Review：125. Valid Palindrome

## 本題核心觀念

這題的核心是使用 **Two Pointers** 從左右兩端往中間比較。

```text
左邊不是英數 → left++ 跳過
右邊不是英數 → right-- 跳過
兩邊都是英數 → 轉小寫後比較
不同 → return false
全部比完 → return true
```

## Liu 這次的理解與卡住點

### 做得好的地方

- 能正確從 `"race a car"` 判斷第一組有效比較是 `r` 和 `r`。
- 能理解比較成功後要讓 `left++`、`right--` 往中間靠近。
- 能判斷右邊遇到空格時應該 `right--`，因為空格要忽略。
- 能正確寫出大小寫不敏感的比較：

```java
if (Character.toLowerCase(leftChar) != Character.toLowerCase(rightChar)) {
    return false;
}
```

- 最後能完整寫出 LeetCode-compatible Java 解法。

### 需要補強的地方

一開始容易把「非英數字元」誤判成錯誤：

```java
if (!Character.isLetterOrDigit(leftChar)) {
    return false; // 錯
}
```

這題的規則是：非英數字元不是錯，而是雜訊，要忽略。

正確寫法是：

```java
if (!Character.isLetterOrDigit(leftChar)) {
    left++;
    continue;
}
```

右邊同理：

```java
if (!Character.isLetterOrDigit(rightChar)) {
    right--;
    continue;
}
```

## 下次看到類似題目要想到

如果題目要判斷：

- 字串左右是否對稱
- 從兩端往中間比
- 要忽略某些字元
- 大小寫要統一後比較

可以先思考：

```text
能不能用 Two Pointers？
```

## 關鍵流程

```text
建立 left / right
while left < right
    left 非英數 → left++，continue
    right 非英數 → right--，continue
    轉小寫後比較
    不同 → false
    相同 → left++，right--
return true
```

## 容易犯的錯

1. 遇到空格或標點時直接 `return false`。
2. 忘記題目要求大小寫視為相同。
3. 沒有在跳過非英數字元後 `continue`，導致拿雜訊去比較。
4. 把 Valid Palindrome 和 Valid Anagram 混在一起：Palindrome 看左右順序，Anagram 看字元次數。

## 複習問題

1. 為什麼遇到空格不能直接 `return false`？
2. `Character.isLetterOrDigit(c)` 在這題負責什麼？
3. 為什麼比較前要用 `Character.toLowerCase(c)`？
4. 這題為什麼可以做到 O(1) 空間？
