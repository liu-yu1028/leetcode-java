# Review：121. Best Time to Buy and Sell Stock

## 本題核心觀念

這題的核心是從左到右掃一次，維護兩個狀態：

```text
minPrice：目前看過最低的股票價格
maxProfit：目前看過最大的合法利潤
```

每天都假設今天是賣出日：

```text
profit = 今天價格 - 目前看過最低價格
```

## Liu 這次的理解與卡住點

### 做得好的地方

- 能在 trace 中理解 `price = 5` 時應該用目前看過的 `minPrice = 1` 計算利潤。
- 能說出「要用目前看過的數字來比較，不是用還沒看過的」。這正是本題「先買再賣」的核心限制。
- 能正確理解 `maxProfit` 是目前最高獲利。
- 最後能完整寫出 O(n)、O(1) 的 Java 解法。

### 需要補強的地方

這次主要卡在三個變數的角色：

| 變數 | 是什麼 |
|---|---|
| `price` | 今天的股票價格 |
| `minPrice` | 到目前為止最低的買入價格 |
| `maxProfit` | 到目前為止最大的利潤 |

一開始曾經把還沒走到的價格拿來算，或把 `minPrice` 和 `maxProfit` 混在一起。

要記住：

```text
minPrice 是價格，不是利潤。
maxProfit 是利潤，不是價格。
```

所以：

```java
int profit = price - minPrice;
maxProfit = Math.max(maxProfit, profit);
minPrice = Math.min(minPrice, price);
```

## 下次看到類似題目要想到

如果題目要求：

- 從左到右處理陣列
- 目前決策只能依賴以前看過的資料
- 要維護目前最好/最低/最高狀態

可以先思考：

```text
能不能一邊走，一邊更新狀態？
```

## 關鍵流程

```text
minPrice = prices[0]
maxProfit = 0

for price in prices:
    profit = price - minPrice
    maxProfit = max(maxProfit, profit)
    minPrice = min(minPrice, price)

return maxProfit
```

## 容易犯的錯

1. 用還沒走到的價格來當買入價，違反先買再賣。
2. 把 `maxProfit` 更新成當天價格，而不是最大利潤。
3. 把 `minPrice` 寫成 `Math.min(profit, maxProfit)`，混淆價格與利潤。
4. 讓 `maxProfit` 變成負數；但不能獲利時答案應該是 `0`。

## 複習問題

1. 為什麼 `maxProfit` 一開始是 `0`？
2. 為什麼走到 `price = 5` 時不能用後面的 `3` 當買入價？
3. `minPrice` 和 `maxProfit` 分別代表什麼？
4. 為什麼這題可以只掃一次陣列？
