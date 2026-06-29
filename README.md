# LeetCode Java 學習紀錄

這個 repository 用來整理我的 LeetCode Java 練習紀錄。  
重點不只是放答案，而是記錄每一題的：

- 題目理解
- 解題思路
- 使用的資料結構
- Java 實作
- 複雜度分析
- 卡住點與複習提醒
- 較好閱讀的 `note.html` 筆記

## 學習目標

我目前透過 LeetCode 重新建立資料結構與演算法基礎，主要目標是：

1. 熟悉 Java 解題語法。
2. 理解常見資料結構的使用時機。
3. 從暴力解法逐步思考優化方式。
4. 把每題的卡住點整理成可複習的筆記。
5. 建立一個能持續累積的學習作品集。

## Repository 結構

```text
leetcode-java/
├── README.md
└── easy/
    ├── 0001-two-sum/
    │   ├── Solution.java
    │   ├── README.md
    │   ├── review.md
    │   └── note.html
    └── 0217-contains-duplicate/
        ├── Solution.java
        ├── README.md
        ├── review.md
        └── note.html
```

每題資料夾通常包含：

| 檔案 | 用途 |
|---|---|
| `Solution.java` | LeetCode 可提交的 Java 解法 |
| `README.md` | 題目說明、解題思路、複雜度分析 |
| `review.md` | 個人卡住點、錯誤提醒、複習問題 |
| `note.html` | 較容易閱讀的視覺化學習筆記 |

## 已完成題目

| 題號 | 題目 | 難度 | 主題 | 筆記 |
|---|---|---|---|---|
| 1 | [Two Sum](https://leetcode.com/problems/two-sum/) | Easy | Array, HashMap | [資料夾](./easy/0001-two-sum/) |
| 217 | [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/) | Easy | Array, HashSet | [資料夾](./easy/0217-contains-duplicate/) |

## 目前學到的核心觀念

### HashMap

適合用在「需要把一個值對應到另一個資訊」的情境。

例如 Two Sum：

```text
數字 -> index
```

重點是用 `complement` 快速找到之前出現過的數字位置。

### HashSet

適合用在「只需要知道某個值有沒有出現過」的情境。

例如 Contains Duplicate：

```text
看過這個數字 -> 有重複
沒看過 -> 放進 set
```

## 學習方式

每一題會盡量照這個流程整理：

1. 先理解題目真正要回傳什麼。
2. 想出最直覺的暴力解法。
3. 找出暴力解法慢在哪裡。
4. 思考能不能用資料結構改善查找效率。
5. 用 Java 實作。
6. 測試範例與邊界情況。
7. 整理 README、review、note.html。

## 接下來預計練習

| 順序 | 題目 | 主要練習 |
|---|---|---|
| 242 | Valid Anagram | 字元統計、HashMap / 陣列計數 |
| 125 | Valid Palindrome | Two Pointers |
| 121 | Best Time to Buy and Sell Stock | 一次掃描、最小值追蹤 |

## 備註

這個 repository 是我的學習紀錄，所以筆記會刻意保留：

- 當下的思考過程
- 容易混淆的地方
- 實作時犯過或差點犯的錯

因為這些內容比只保存最終答案更有複習價值。
