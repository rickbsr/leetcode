# leetcode

這是我的 LeetCode 解題筆記，記錄我對演算法、資料結構與部分資料庫題目的思路與解法。專案分為兩個部分：**解題筆記文章**與**對應的程式碼**，兩者會隨著持續刷題陸續補上。

- 文章：放在 `writes/`，以 Markdown 撰寫，說明每一題的題意、解題思路與不同解法的取捨。
- 程式碼：放在 `codes/`，是一個 Java 25 LTS 的 Maven 專案，保存每一題實際可執行的解法。

> 這是一份持續更新中的筆記，之後會陸續補上更多題目的文章與對應程式碼。

## 專案內容

- 收錄約 200 多題 LeetCode 解法程式碼，並持續補上對應的解題筆記文章。
- 題型包含陣列、字串、linked list、binary tree、hash table、stack、queue、dynamic programming、math 與部分 SQL 題目。
- 解題筆記文章集中在 `writes/`，每題一個資料夾，內含文章與圖片。
- 題目解法程式碼集中在 `codes/src/main/java/com/rick/problems`，共用資料結構集中在 `codes/src/main/java/com/rick/common`。
- 完整題目（程式碼）索引請見 [PROBLEMS.md](PROBLEMS.md)。
- `Main.java` 保留為本機快速測試與臨時實驗用入口。

## 執行環境

- Java 25 LTS
- Maven

Maven compiler 已設定為 `maven.compiler.release=25`，因此編譯與執行時請使用 JDK 25。

可以用以下指令確認目前 Java 版本：

```sh
java -version
```

預期應看到 Java 25 LTS，例如：

```text
openjdk version "25.0.x" ... LTS
```

## 專案結構

```text
leetcode/
  README.md
  PROBLEMS.md         程式碼題目索引
  writes/             解題筆記文章
	L100_SameTree/
	  L100_SameTree.md  文章內容
	  pic/              文章使用的圖片
  codes/              解法程式碼（Maven 專案）
	pom.xml
	src/main/java/com/rick/
	  Main.java       本機快速測試用入口
	  common/         共用資料結構，例如 ListNode、TreeNode
	  constant/       共用常數
	  problems/       各題 LeetCode 解法
```

主要目錄說明：

- `writes/`：解題筆記文章，每一題一個資料夾（命名如 `L{題號}_{題名}`），內含 Markdown 文章與 `pic/` 圖片。
- `codes/src/main/java/com/rick/problems`：每個 class 通常代表一道 LeetCode 題目。
- `codes/src/main/java/com/rick/common`：linked list、binary tree 等題目會使用到的共用節點結構。
- `codes/src/main/java/com/rick/constant`：放置練習過程中抽出的共用常數。
- `codes/src/main/java/com/rick/Main.java`：可用來手動呼叫某個題解方法，方便在本機快速試資料。

## 建置與驗證

進入 Maven 子專案後執行：

```sh
cd codes
mvn test
```

目前這個 repository 以保存解題程式碼為主；尚未補齊完整的單元測試套件。因此 `mvn test` 主要用來確認 Maven 設定與 Java runtime 可正常運作。

## 解題筆記

每一篇解題筆記放在 `writes/` 下的獨立資料夾，命名方式為 `L{題號}_{題名}`，例如 `writes/L100_SameTree/`。資料夾內包含：

- `L{題號}_{題名}.md`：文章本體，說明題意、解題思路與不同解法的比較。
- `pic/`：文章中使用到的圖片。

文章中的程式碼通常會對應到 `codes/` 裡的實際解法，方便對照閱讀與執行。目前已完成的筆記：

- [100. Same Tree](writes/L100_SameTree/L100_SameTree.md)

之後會陸續補上更多題目的筆記。

## 如何瀏覽題解

題解 class 依題名命名，例如：

- `TwoSum.java`
- `ValidParentheses.java`
- `MergeTwoSortedLists.java`
- `MaximumSubarray.java`
- `LongestSubstringWithoutRepeatingCharacters.java`

如果想找某一題，可以直接用 IDE 或命令列搜尋題目的英文名稱：

```sh
find codes/src/main/java/com/rick/problems -name '*TwoSum*'
```

## 如何本機試跑單題

這個專案沒有統一的 CLI 介面。若要臨時測試某一題，可以在 `codes/src/main/java/com/rick/Main.java` 中建立對應 class 的 instance，呼叫題解方法並印出結果。

範例概念如下：

```java
package com.rick;

import com.rick.problems.TwoSum;
import java.util.Arrays;

public class Main {
	public static void main(String[] args) {
		TwoSum solution = new TwoSum();
		int[] result = solution.twoSum(new int[]{2, 7, 11, 15}, 9);
		System.out.println(Arrays.toString(result));
	}
}
```

不同題目的方法命名與參數會依當時練習時的寫法而定，可以直接打開對應 class 查看。

## 命名與整理原則

- 題解 class 使用 PascalCase，盡量對應 LeetCode 英文題名。
- 共用資料結構放在 `common`，避免每題重複定義。
- 早期解法保留原貌，方便回顧當時思路。
- 新增題目時建議延續既有 package：`com.rick.problems`，並重新產生 [PROBLEMS.md](PROBLEMS.md) 索引。
- 新增解題筆記時，於 `writes/` 建立 `L{題號}_{題名}/` 資料夾，文章與圖片放在其中。

## 後續可改進方向

- 持續為既有題目補上 `writes/` 的解題筆記文章。
- 補上 JUnit 測試（`src/test/java`），讓常見題型可以自動驗證。
- 將 `problems/` 依陣列、字串、tree、linked list、DP 等題型分到子 package。
- 為較有代表性的題目補充時間複雜度與空間複雜度說明。
