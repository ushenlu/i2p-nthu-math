## Lab 3-2: 科學記號比大小 (30%)

* 輸入：兩個以 10 為底的實數。
實數的正負號 (sign)、實數的尾數 (mantissa，1/100,000,000)、實數的指數部分 (exponent)。
正負號輸入大於等於 0 為正數，小於 0 為負數。
尾數部分固定 9 位數字，第一位不為 `0`。
指數部分為 -126 至 +127。
* 輸出：兩實數的科學記號表示，有效位數 (precision) 顯示固定為 9 位。
兩實數比較結果，如果第一數較大則輸出 '1'，相同則輸出 '0'，第一數較小則輸出 '-1'
* 檔名：lab3_2_<學號>.cpp (e.g. lab3_2_106062802.cpp)

程式需提示使用者輸入兩個實數的正負號 (sign)、實數的尾數 (mantissa, 1/100,000,000)、實數的指數部分 (exponent)，程式需輸出數字顯示比較結果。

```text
Input real number (a), sign: <sign a>
Input real number (a), mantissa: <mantissa a>
Input real number (a), exponent: <exponent a>
Input real number (b), sign: <sign b>
Input real number (b), mantissa: <mantissa b>
Input real number (b), exponent: <exponent b>
The real number (a) is: <output real number a>
The real number (b) is: <output real number b>
Compare result: <1, 0, or -1>
```

Example:

```console
$ ./a.out
Input real number (a), sign: -100
Input real number (a), mantissa: 123456789
Input real number (a), exponent: 10
Input real number (b), sign: -10
Input real number (b), mantissa: 123456788
Input real number (b), exponent: 10
The real number (a) is: -1.23456789e+10
The real number (b) is: -1.23456788e+10
Compare result: -1
```
