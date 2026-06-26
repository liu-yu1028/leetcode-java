# 1. Two Sum

## 題目資訊

- 題號：1
- 題名：Two Sum
- 難度：Easy
- 題目連結：https://leetcode.com/problems/two-sum/

## 題目理解

給定一個整數陣列 `nums` 和一個整數 `target`，要找出陣列中兩個不同位置的數字，使它們相加等於 `target`，並回傳這兩個數字的索引。

重點是：

- 回傳的是 **index**，不是數字本身。
- 同一個元素不能使用兩次。
- 題目保證會有一組答案。

## 題型判斷

| 分類 | 說明 |
|---|---|
| Array | 題目給定的是陣列，需要走訪元素 |
| HashMap | 需要快速查找某個數字是否已經出現過 |

這題的核心不是單純相加，而是：

> 當我看到 `nums[i]` 時，如何快速知道 `target - nums[i]` 是否已經出現過？

## 使用資料結構

使用 `HashMap<Integer, Integer>`：

| key | value |
|---|---|
| 數字 `nums[i]` | 該數字所在的索引 `i` |

例如：

```text
nums = [2, 7, 11, 15]
map = { 2 -> 0 }
```

代表數字 `2` 出現在 index `0`。

這裡最容易混淆的是：

```text
map.get(complement)
```

拿到的不是 `complement` 這個數字本身，而是：

```text
complement 這個數字所在的 index
```

因為 HashMap 的方向是：

```text
數字 -> index
```

## 解題思路

1. 建立一個 HashMap，記錄「數字 -> index」。
2. 從左到右走訪 `nums`。
3. 對每個 `nums[i]`，計算：

   ```java
   complement = target - nums[i]
   ```

4. 檢查 HashMap 裡是否有 `complement`。
5. 如果有，回傳：

   ```java
   new int[] { map.get(complement), i }
   ```

6. 如果沒有，把目前的 `nums[i]` 和 index `i` 放入 HashMap。

## 為什麼要先查再放？

流程要使用：

```text
先檢查 complement
再放入目前 nums[i]
```

這樣可以避免同一個元素被自己配對。

## Java 程式碼

請見 [`Solution.java`](./Solution.java)。

## 複雜度分析

| 項目 | 複雜度 | 原因 |
|---|---|---|
| 時間複雜度 | O(n) | 只走訪陣列一次，HashMap 查找平均 O(1) |
| 空間複雜度 | O(n) | 最壞情況下 HashMap 可能存入接近 n 個元素 |

## 核心一句話

> Two Sum 的核心不是「相加」，而是「如何快速找到另一個需要的數字」。

## 本題記憶點

```text
先查 complement，再放目前數字。
key 放數字，value 放 index。
回傳 index，不回傳數字。
```
