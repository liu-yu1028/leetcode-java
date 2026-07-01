# 121. Best Time to Buy and Sell Stock

## 題目資訊

- 題號：121
- 題名：Best Time to Buy and Sell Stock
- 難度：Easy
- 題目連結：https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

## 筆記介紹

這份筆記整理 **121. Best Time to Buy and Sell Stock** 的學習過程。這題的核心是：

```text
每天都假設今天是賣出日，用目前看過最低價格當買入日，更新最大利潤。
```

可讀版筆記請見 [`note.html`](./note.html)。

## 題目理解

給定一個陣列 `prices`，其中 `prices[i]` 代表第 `i` 天的股票價格。

你最多只能完成一次交易：

```text
先買入，再賣出
```

目標是找出最大利潤。如果無法獲利，回傳 `0`。

例如：

```text
prices = [7, 1, 5, 3, 6, 4]
```

最佳交易是：

```text
價格 1 買入，價格 6 賣出，profit = 6 - 1 = 5
```

所以答案是 `5`。

## 題型判斷

| 分類 | 說明 |
|---|---|
| Array | 題目給的是價格陣列 |
| Greedy | 每天保留目前最低買入價，嘗試更新最大利潤 |
| One Pass | 從左到右掃一次即可 |
| DP 入門感 | 維護目前最佳狀態，但不需要開 DP 陣列 |

## 重要限制

這題不能先賣再買，買入日一定要在賣出日之前。

因此走到某一天時，只能使用「目前已經看過的最低價」當買入價，不能偷看後面的價格。

## 使用變數

| 變數 | 意義 |
|---|---|
| `price` | 今天的股票價格 |
| `minPrice` | 到目前為止看過的最低價格 |
| `profit` | 如果今天賣出，可以得到的利潤 |
| `maxProfit` | 到目前為止看過的最大利潤 |

注意：

```text
minPrice 是價格，不是利潤。
maxProfit 是利潤，不是價格。
```

## 解題思路

1. 設定 `minPrice = prices[0]`，代表目前最低買入價。
2. 設定 `maxProfit = 0`，因為如果不能賺錢，可以選擇不交易。
3. 從左到右走訪每個 `price`。
4. 計算如果今天賣出：

```java
int profit = price - minPrice;
```

5. 更新目前最大利潤：

```java
maxProfit = Math.max(maxProfit, profit);
```

6. 更新目前最低價格：

```java
minPrice = Math.min(minPrice, price);
```

7. 最後回傳 `maxProfit`。

## Java 程式碼

請見 [`Solution.java`](./Solution.java)。

## 複雜度分析

| 項目 | 複雜度 | 原因 |
|---|---|---|
| 時間複雜度 | O(n) | 只需要走訪價格陣列一次 |
| 空間複雜度 | O(1) | 只使用幾個變數 |

## 核心一句話

> Best Time to Buy and Sell Stock：邊走邊記錄目前最低買入價，並用今天價格嘗試更新最大利潤。
