# 217. Contains Duplicate

## 題目資訊

- 題號：217
- 題名：Contains Duplicate
- 難度：Easy
- 題目連結：https://leetcode.com/problems/contains-duplicate/

## 題目理解

給定一個整數陣列 `nums`，如果陣列中有任何數字出現至少兩次，回傳 `true`；如果每個數字都只出現一次，回傳 `false`。

重點是：

- 這題只需要判斷「有沒有重複」。
- 不需要回傳重複數字的位置。
- 不需要記錄 index。

## 題型判斷

| 分類 | 說明 |
|---|---|
| Array | 題目給定陣列，需要走訪每個元素 |
| HashSet | 需要快速判斷某個數字之前是否出現過 |

這題的核心是：

> 當我看到目前數字 `num` 時，如何快速知道它以前有沒有出現過？

## 暴力解法

最直覺的方法是固定一個 `nums[i]`，再往後檢查有沒有 `nums[j] == nums[i]`。

```text
固定 nums[i]
檢查後面的所有 nums[j]
如果相等，回傳 true
```

這個方法正確，但需要兩層迴圈。

| 項目 | 複雜度 |
|---|---|
| 時間複雜度 | O(n²) |
| 空間複雜度 | O(1) |

## 使用資料結構

使用 `HashSet<Integer>`：

| HashSet 裡存什麼 | 原因 |
|---|---|
| 已經出現過的數字 | 題目只問有沒有重複，不需要 index |

`HashSet` 可以快速判斷某個數字是否已經存在：

```java
set.contains(num)
```

如果已經存在，代表重複出現，直接回傳 `true`。

## 解題思路

1. 建立一個 `HashSet<Integer>`，用來記錄看過的數字。
2. 從左到右走訪 `nums`。
3. 對每個 `num`，先檢查：

   ```java
   set.contains(num)
   ```

4. 如果 `set` 裡已經有 `num`，代表重複，回傳 `true`。
5. 如果沒有，就把 `num` 加進 set：

   ```java
   set.add(num);
   ```

6. 如果整個陣列都走完還沒找到重複，回傳 `false`。

## Java 程式碼

請見 [`Solution.java`](./Solution.java)。

## 複雜度分析

| 項目 | 複雜度 | 原因 |
|---|---|---|
| 時間複雜度 | O(n) | 只走訪陣列一次，HashSet 查找平均 O(1) |
| 空間複雜度 | O(n) | 最壞情況下所有數字都不重複，set 會存入 n 個元素 |

## 核心一句話

> Contains Duplicate：用 HashSet 存看過的數字；看過就 true，沒看過就 add，最後 false。

## 本題記憶點

```text
HashSet<Integer> 只存一種東西：出現過的數字。
set.contains(num) 用來查是否看過。
set.add(num) 用來記錄目前數字。
```
