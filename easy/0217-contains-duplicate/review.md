# Review：217. Contains Duplicate

## 本題核心觀念

這題的核心是使用 HashSet 快速判斷「目前數字以前有沒有出現過」。

```text
看過這個數字 → 有重複 → return true
沒看過這個數字 → 放進 set
全部看完都沒重複 → return false
```

## Liu 這次的理解與卡住點

### 做得好的地方

- 能先想出暴力解法：固定一個數字，再檢查後面的數字有沒有相同。
- 能判斷這題只需要存「出現過的數字」。
- 能說出因為題目回傳 boolean，所以不需要存 index。
- 能正確選擇 enhanced for loop：`for (int num : nums)`。
- 最後完整 Java 程式邏輯正確。

### 需要補強的地方

這次主要卡在 HashSet 的 Java 語法和方法名稱：

```text
HashSet<Integer>
```

不是：

```text
HashSet<Integer, Integer>
```

原因是：

| 結構 | 存法 |
|---|---|
| HashMap | key -> value |
| HashSet | 只存元素本身 |

另外，HashSet 加入元素要用：

```java
set.add(num);
```

不是：

```java
set.push(num);
```

`push` 比較常出現在 Stack。

## 下次看到類似題目要想到

如果題目只需要判斷：

- 某個值有沒有出現過
- 有沒有重複
- 不需要 index、不需要次數

可以先思考：

```text
能不能用 HashSet？
```

如果題目需要記錄「值對應到什麼資料」，例如 index 或次數，才再考慮 HashMap。

## 關鍵流程

```text
建立 set
走訪 nums
如果 set.contains(num)：return true
否則：set.add(num)
走完：return false
```

## 容易犯的錯

1. 把 `HashSet<Integer>` 寫成 `HashSet<Integer, Integer>`。
2. 把 `set.add(num)` 寫成 `set.push(num)`。
3. 忘記 Java 要 import `HashSet`。
4. 在不需要 index 的題目中，過度使用 HashMap。

## 複習問題

1. 為什麼這題不用存 index？
2. `HashSet<Integer>` 和 `HashMap<Integer, Integer>` 差在哪裡？
3. `set.contains(num)` 的用途是什麼？
4. 為什麼這題可以從 O(n²) 優化成 O(n)？
