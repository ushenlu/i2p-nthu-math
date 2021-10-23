## Lab 3-3: IEEE-754 誤差計算 (20%)

* 輸入：以 10 為底的實數。
實數的正負號 (sign)、實數的尾數 (mantissa，輸入數字乘以\\( \frac{1}{100,000,000} \\))、實數的指數部分 (exponent)。
正負號輸入大於等於 0 為正數，小於 0 為負數。
尾數部分不超過 9 位數字。
指數部分為 -126 至 +127。
* 輸出：該實數的科學記號表示，有效位數為 9 位。
該實數的 IEEE-754 single precision 數值，以科學記號表示，有效位數為 9 位。
該實數與 IEEE-754 single precision 數值的差異絕對值，以科學記號表示，有效位數為 9 位。
* 檔名：lab3_3_<學號>.cpp (e.g. lab3_3_106062802.cpp)

程式需提示使用者輸入實數的正負號 (sign)、實數的尾數 (mantissa，輸入數字乘以\\( \frac{1}{100,000,000} \\))、實數的指數部分 (exponent)，輸出該實數的科學記號表示、該實數的 IEEE-754 single precision 數值、該實數與 IEEE-754 single precision 數值的差異絕對值。

```text
Input real number, sign: <sign>
Input real number, mantissa: <mantissa>
Input real number, exponent: <exponent>
The real number is: <output real number>
The IEEE-754 single precision number is: <output float value>
The difference (absolute value): <difference in abs>
```

Example:

```console
$ ./a.out
Input real number, sign: -100
Input real number, mantissa: 123456789
Input real number, exponent: 10
The real number is: -1.23456789e+10
The IEEE-754 single precision number is: -1.23456788e+10
The difference (absolute value): 1.00000000e+02
```
