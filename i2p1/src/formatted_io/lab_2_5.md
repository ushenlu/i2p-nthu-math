## Lab 2-5: 大正實數乘法 (10%)

* 輸入：兩正實數的整數部分、正實數的小數部分（輸入數字乘以\\( \frac{1}{1,000,000,000} \\)），整數及小數各不超過 9 位數字
* 輸出：兩正實數數值、兩正實數的積，整數及小數各不超過 18 位數字，小數部分固定顯示 18 位。
* 檔名：lab2_5_<學號>.cpp (e.g. lab2_5_106062802.cpp)

程式需提示使用者輸入兩正實數的整數部分、正實數的小數部分，程式需輸出兩正實數數值、兩正實數的積。

### Format

```text
Input real number (a), before decimal point: <(a) before decimal point>⏎
Input real number (a), after decimal point: <(a) after decimal point>⏎
The real number (a) is: <real number (a)>
Input real number (b), before decimal point: <(b) before decimal point>⏎
Input real number (b), after decimal point: <(b) after decimal point>⏎
The real number (b) is: <real number (b)>
(a) * (b) = <real number (a) * (b)>
```

### Example

```console
$ ./a.out
Input real number (a), before decimal point: 123456789⏎
Input real number (a), after decimal point: 123456789⏎
The real number (a) is: 123456789.123456789000000000
Input real number (b), before decimal point: 987654321⏎
Input real number (b), after decimal point: 987654321⏎
The real number (b) is: 987654321.987654321000000000
(a) * (b) = 121932631356500531.347203169112635269

$ ./a.out
Input real number (a), before decimal point: 1⏎
Input real number (a), after decimal point: 1⏎
The real number (a) is: 1.000000001000000000
Input real number (b), before decimal point: 2⏎
Input real number (b), after decimal point: 2⏎
The real number (b) is: 2.000000002000000000
(a) * (b) = 2.000000004000000002
```

Reference:
* [Big Number Calculator](https://www.calculator.net/big-number-calculator.html)

Reference Code:

Credit: 金昆樂 (110021111)

``` c++
{{#include lab2_5_110021111.cpp}}
```