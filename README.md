# LeetCode Java 學習紀錄

這個 repository 用來整理我的 LeetCode Java 練習紀錄。

主要目標不是只保存答案，而是把每一題的學習過程整理下來，包含：

- 題目理解
- 解題思路
- Java 實作
- 複雜度分析
- 卡住點與複習提醒
- 較好閱讀的 `note.html` 筆記

## Repository 結構

每題會依照難度與題號建立資料夾，例如：

```text
leetcode-java/
└── easy/
    └── 0001-two-sum/
        ├── Solution.java
        ├── README.md
        ├── review.md
        └── note.html
```

| 檔案 | 用途 |
|---|---|
| `Solution.java` | LeetCode 可提交的 Java 解法 |
| `README.md` | 題目說明、解題思路、複雜度分析 |
| `review.md` | 個人卡住點、錯誤提醒、複習問題 |
| `note.html` | 較容易閱讀的視覺化學習筆記 |

## 學習方式

每一題會盡量照這個流程整理：

1. 先理解題目真正要回傳什麼。
2. 想出最直覺的暴力解法。
3. 找出暴力解法慢在哪裡。
4. 思考能不能用資料結構改善查找效率。
5. 用 Java 實作。
6. 測試範例與邊界情況。
7. 整理學習筆記。

## 備註

這份 README 只保留 repository 的固定說明，不追蹤每次完成題目的進度。  
每一題的詳細學習紀錄會放在各自的題目資料夾中。
