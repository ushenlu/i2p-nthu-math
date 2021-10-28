# Lab 6: 迴圈練習

## Lab 6-1: 特殊數列產生機 (35%)

數列會以以下的方式產生：

$$ \begin{align} a_1 &= 1 \\\\
a_2 &= 2 \\\\
a_n &= a_{n-2} - a_{n-1}, n \ge 3 \end{align}$$

* 輸入：要得到的數列第幾項 \\( n, n \le 92 \\)， \\(n\\) 為自然數。
* 輸出：
  * 從 \\( a_1 \\) 至 \\( a_n \\) 的所有項，並以 `, ` 分隔。
  * 數列最後一項不需輸出 `, `。
* 檔名：lab6_1_<學號>.cpp (e.g. lab6_1_106062802.cpp)

程式需提示使用者輸入要得到的數列第幾項，輸出從 \\( a_1 \\) 至 \\( a_n \\) 的所有項。
使用者會在每次輸入時輸入任意實數，請考慮所有合法 `double` 型態的數字輸入。
若輸入不合法的數字則需顯示 `Invalid input` 並結束程式。

```text
The number of terms: <n>⏎
The series: <a_1>, <a_2>, <a_3>, <a_n>
```

Example:

```console
$ ./a.out
The number of terms: 1⏎
The series: 1

$ ./a.out
The number of terms: 2⏎
The series: 1, 2

$ ./a.out
The number of terms: 10⏎
The series: 1, 2, -1, 3, -4, 7, -11, 18, -29, 47
```
