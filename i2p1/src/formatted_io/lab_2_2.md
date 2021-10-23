## Lab 2-2: 正實數加法 (30%)

* 輸入：兩正實數的整數部分、正實數的小數部分（輸入數字乘以\\( \frac{1}{1,000,000} \\)），正實數的小數部分不超過 6 位數。
* 輸出：兩正實數數值、兩正實數的和，並且以 `double` 形式搭配 `std::fixed` 輸出。
* 檔名：lab2_2_<學號>.cpp (e.g. lab2_2_106062802.cpp)

程式需提示使用者輸入兩正實數的整數部分、正實數的小數部分，程式需輸出兩正實數數值、兩正實數的和。

```text
Input real number (a), before decimal point: <(a) before decimal point>
Input real number (a), after decimal point: <(a) after decimal point>
The real number (a) is: <real number (a)>
Input real number (b), before decimal point: <(b) before decimal point>
Input real number (b), after decimal point: <(b) after decimal point>
The real number (b) is: <real number (b)>
(a) + (b) = <real number (a) + (b)>
```

Example:

```console
$ ./a.out
Input real number (a), before decimal point: 1
Input real number (a), after decimal point: 234560
The real number (a) is: 1.234560
Input real number (b), before decimal point: 12345
Input real number (b), after decimal point: 6
The real number (b) is: 12345.000006
(a) + (b) = 12346.234566
```
