## Lab 4-2: 計算機四則運算 (40%)

* 輸入：
  1. 要執行的計算功能，分別如下：
     1. 加 (`+`)
     2. 減 (`-`)
     3. 乘 (`*`)
     4. 除 (`/`)
  2. 兩個以 10 為底的實數，以科學記號格式輸入。
     * 實數的正負號 (sign)，正負號輸入大於等於 0 為正數，小於 0 為負數。
     * 實數的尾數 (mantissa)，尾數部分固定 9 位數字，第一位不為 `0`，數值為輸入數字乘以\\( \frac{1}{100,000,000} \\)，。
     * 實數的指數部分 (exponent)，指數部分為 -38 至 +38。
     * 第二個實數為任意非 `0` 的數字。
* 輸出：所選擇的運算子字元 (i.e. `+`, `-`, `*`, `/`)及兩實數的運算結果，以科學記號表示，有效位數為 15 位。
* 檔名：lab4_2_<學號>.cpp (e.g. lab4_2_106062802.cpp)

程式需提示使用者輸入需要的運算功能，輸出該運算功能的運算子字元。

```text
Simple scientific calculator
1) plus (+)
2) minus (-)
3) multiplication (*)
4) division (/)
Please select the operator: <1-4>
You selected: <+, -, *, />
Input real number (a), sign: <sign a>
Input real number (a), mantissa: <mantissa a>
Input real number (a), exponent: <exponent a>
Input real number (b), sign: <sign b>
Input real number (b), mantissa: <mantissa b>
Input real number (b), exponent: <exponent b>
The real number (a) is: <output real number a>
The real number (b) is: <output real number b>
(a) <+, -, *, /> (b) = <result>
```

Example:

```console
$ ./a.out
Simple scientific calculator
1) plus (+)
2) minus (-)
3) multiplication (*)
4) division (/)
Please select the operator: 3
You selected: *
Input real number (a), sign: -100
Input real number (a), mantissa: 123456789
Input real number (a), exponent: 10
Input real number (b), sign: -10
Input real number (b), mantissa: 123456788
Input real number (b), exponent: 10
The real number (a) is: -1.23456789e+10
The real number (b) is: -1.23456788e+10
(a) * (b) = 1.52415786267337e+20
```

Reference Code:

Credit: 張晉赫 (110021109)

``` c++
{{#include lab4_2_110021109.cpp}}
```