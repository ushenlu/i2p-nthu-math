# Lab 2: 正實數加/乘法器

## Lab 2-1: 正實數顯示 (30%)

* 輸入：正實數的整數部分、正實數的小數部分（輸入數字乘以\\( \frac{1}{1,000,000} \\)），正實數的小數部分不超過 6 位數。
* 輸出：該正實數，並且以 `float` 形式輸出。
* 檔名：lab2_1_<學號>.cpp (e.g. lab2_1_106062802.cpp)

程式需提示使用者輸入正實數的整數部分、正實數的小數部分，程式需輸出該正實數。

```text
Input real number, before decimal point: <before decimal point>
Input real number, after decimal point: <after decimal point>
The real number is: <output real number>
```

Example:

```console
$ ./a.out
Input real number, before decimal point: 123
Input real number, after decimal point: 456000
The real number is: 123.456

$ ./a.out
Input real number, before decimal point: 654321
Input real number, after decimal point: 0
The real number is: 654321

$ ./a.out
Input real number, before decimal point: 123
Input real number, after decimal point: 456
The real number is: 123
```
