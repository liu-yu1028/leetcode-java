# Review：1. Two Sum

## 本題核心觀念

這題的核心是使用 HashMap 讓「查找另一個需要的數字」變快。

```text
目前數字：nums[i]
需要的另一個數字：target - nums[i]
```

這個 `target - nums[i]` 稱為 `complement`。

## Liu 這次的理解與卡住點

### 做得好的地方

- 有注意到題目最後要回傳的是 **index**。
- 能理解 HashMap 的 value 需要存 index。
- 能說出：key 是 array 裡的 num，value 是該 num 所在的索引位置。

### 需要補強的地方

一開始 Liu 說 HashMap 應該記錄 index，這個方向接近，但還不完整。

更精準的理解是：

```text
HashMap 要記錄「數字 -> index」
```

原因是我們查找時需要用「數字」去查：

```text
map.containsKey(complement)
```

找到後才用 value 取得 index：

```text
map.get(complement)
```

## 下次看到類似題目要想到

如果題目出現這類需求：

- 找兩個數是否符合某個條件
- 需要快速判斷某個值是否出現過
- 暴力法需要兩層迴圈一直找

可以先思考：

```text
能不能用 HashMap 把查找從 O(n) 降到 O(1)？
```

## 關鍵流程

```text
建立 map
走訪 nums
計算 complement = target - nums[i]
如果 map 有 complement：回傳 [map.get(complement), i]
否則：map.put(nums[i], i)
```

## 容易犯的錯

1. 回傳數字本身，而不是 index。
2. HashMap 存成 `index -> 數字`，導致無法快速查 complement。
3. 先放入目前數字再查 complement，可能造成自己配對自己的問題。
4. 忘記 Java 要 import `HashMap` 和 `Map`。

## 複習問題

1. 為什麼 HashMap 的 key 要放數字，而不是 index？
2. `complement` 是什麼意思？
3. 為什麼流程是先查再放？
4. 這題的時間複雜度為什麼是 O(n)？
