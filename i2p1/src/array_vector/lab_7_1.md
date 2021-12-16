# Lab 7: 真・大數四則運算

* 輸入：
  1. 要執行的計算功能，分別如下：
     1. 僅顯示兩數 (`display only`) (35%)
     2. 加 (`+`) (25%)
     3. 減 (`-`) (20%)
     4. 乘 (`*`) (10%)
     5. 除 (`/`) (10%)
  2. 兩整數 \\( a, b \\)，兩整數不多於 10,000 位數字。。
* 輸出：所選擇的功能 (i.e. `display only`, `+`, `-`, `*`, `/`)及兩整數 \\( a, b \\) 的運算結果，結果為整數。。
* 檔名：lab7_1_<學號>.cpp (e.g. lab7_1_106062802.cpp)

程式需提示使用者輸入需要的運算功能，輸出該運算功能及兩整數 \\( a, b \\) 的運算結果。
程式需檢查使用者輸入的是否符合題目要求，不合法的輸入需在當下的輸入完成後顯示 `Invalid input: ` 以及錯誤的輸入並結束程式。
不合法輸出格式範例請參考[以下範例](./lab_7_1.html#exceptions)。
使用者會在每次輸入時輸入任意非空白 (i.e. 非 <kbd>space</kbd>, <kbd>tab</kbd>) 字元。
程式需在 30 秒之內執行完畢，所有測資皆不會超過 30 秒的執行時間。

## Format

```text
Big number calculator
1) display only
2) plus (+)
3) minus (-)
4) multiplication (*)
5) division (/)
Please select the operator: <1-5>⏎
You selected: <display only,+, -, *, />
Input integer number (a): <a>⏎
Input integer number (b): <b>⏎
(a) = <a>
(b) = <b>
(a) <+, -, *, /> (b) = <result>
```

## Example

### Display

```console
$ ./a.out
Big number calculator
1) display only
2) plus (+)
3) minus (-)
4) multiplication (*)
5) division (/)
Please select the operator: 1⏎
You selected: display only
Input integer number (a): 123456789012345678901234567890⏎
Input integer number (b): 987654321098765432109876543210⏎
(a) = 123456789012345678901234567890
(b) = 987654321098765432109876543210

$ ./a.out
Big number calculator
1) display only
2) plus (+)
3) minus (-)
4) multiplication (*)
5) division (/)
Please select the operator: 1⏎
You selected: display only
Input integer number (a): -0000000000000
Input integer number (b): -00000001
(a) = 0
(b) = -1
```

### Plus 

```console
$ ./a.out
Big number calculator
1) display only
2) plus (+)
3) minus (-)
4) multiplication (*)
5) division (/)
Please select the operator: 2⏎
You selected: +
Input integer number (a): 123456789012345678901234567890⏎
Input integer number (b): 987654321098765432109876543210⏎
(a) = 123456789012345678901234567890
(b) = 987654321098765432109876543210
(a) + (b) = 1111111110111111111011111111100

$ ./a.out
Big number calculator
1) display only
2) plus (+)
3) minus (-)
4) multiplication (*)
5) division (/)
Please select the operator: 2⏎
You selected: +
Input integer number (a): 123456789012345678901234567890⏎
Input integer number (b): -987654321098765432109876543210⏎
(a) = 123456789012345678901234567890
(b) = -987654321098765432109876543210
(a) + (b) = -864197532086419753208641975320
```

### Minus

```console
$ ./a.out
Big number calculator
1) display only
2) plus (+)
3) minus (-)
4) multiplication (*)
5) division (/)
Please select the operator: 3⏎
You selected: -
Input integer number (a): 123456789012345678901234567890⏎
Input integer number (b): 987654321098765432109876543210⏎
(a) = 123456789012345678901234567890
(b) = 987654321098765432109876543210
(a) - (b) = -864197532086419753208641975320

$ ./a.out
Big number calculator
1) display only
2) plus (+)
3) minus (-)
4) multiplication (*)
5) division (/)
Please select the operator: 3⏎
You selected: -
Input integer number (a): 123456789012345678901234567890⏎
Input integer number (b): -987654321098765432109876543210⏎
(a) = 123456789012345678901234567890
(b) = -987654321098765432109876543210
(a) - (b) = 1111111110111111111011111111100
```

### Multiplication

```console
$ ./a.out
Big number calculator
1) display only
2) plus (+)
3) minus (-)
4) multiplication (*)
5) division (/)
Please select the operator: 4⏎
You selected: *
Input integer number (a): 123456789012345678901234567890⏎
Input integer number (b): 987654321098765432109876543210⏎
(a) = 123456789012345678901234567890
(b) = 987654321098765432109876543210
(a) * (b) = 121932631137021795226185032733622923332237463801111263526900

$ ./a.out
Big number calculator
1) display only
2) plus (+)
3) minus (-)
4) multiplication (*)
5) division (/)
Please select the operator: 4⏎
You selected: *
Input integer number (a): 123456789012345678901234567890⏎
Input integer number (b): -987654321098765432109876543210⏎
(a) = 123456789012345678901234567890
(b) = -987654321098765432109876543210
(a) * (b) = -121932631137021795226185032733622923332237463801111263526900
```

### Division

```console
$ ./a.out
Big number calculator
1) display only
2) plus (+)
3) minus (-)
4) multiplication (*)
5) division (/)
Please select the operator: 5⏎
You selected: /
Input integer number (a): 987654321098765432109876543210⏎
Input integer number (b): 123456789012345678901234567890⏎
(a) = 987654321098765432109876543210
(b) = 123456789012345678901234567890
(a) / (b) = 8

$ ./a.out
Big number calculator
1) display only
2) plus (+)
3) minus (-)
4) multiplication (*)
5) division (/)
Please select the operator: 5⏎
You selected: /
Input integer number (a): -987654321098765432109876543210⏎
Input integer number (b): 123456789012345678901234567890⏎
(a) = -987654321098765432109876543210
(b) = 123456789012345678901234567890
(a) / (b) = -8

$ ./a.out
Big number calculator
1) display only
2) plus (+)
3) minus (-)
4) multiplication (*)
5) division (/)
Please select the operator: 5⏎
You selected: /
Input integer number (a): -987654321098765432109876543210⏎
Input integer number (b): -123456789012345678901234567890⏎
(a) = -987654321098765432109876543210
(b) = -123456789012345678901234567890
(a) / (b) = 8

$ ./a.out
Big number calculator
1) display only
2) plus (+)
3) minus (-)
4) multiplication (*)
5) division (/)
Please select the operator: 5⏎
You selected: /
Input integer number (a): -123456789012345678901234567890⏎
Input integer number (b): 987654321098765432109876543210⏎
(a) = -123456789012345678901234567890
(b) = 987654321098765432109876543210
(a) / (b) = 0

$ ./a.out
Big number calculator
1) display only
2) plus (+)
3) minus (-)
4) multiplication (*)
5) division (/)
Please select the operator: 5⏎
You selected: /
Input integer number (a): 123456789012345678901234567890⏎
Input integer number (b): -987654321098765432109876543210⏎
(a) = 123456789012345678901234567890
(b) = -987654321098765432109876543210
(a) / (b) = 0
```

### Exceptions

```console
$ ./a.out
Big number calculator
1) display only
2) plus (+)
3) minus (-)
4) multiplication (*)
5) division (/)
Please select the operator: +⏎
Invalid input: +

$ ./a.out
Big number calculator
1) display only
2) plus (+)
3) minus (-)
4) multiplication (*)
5) division (/)
Please select the operator: 00000001⏎
Invalid input: 00000001

$ ./a.out
Big number calculator
1) display only
2) plus (+)
3) minus (-)
4) multiplication (*)
5) division (/)
Please select the operator: 1⏎
You selected: display only
Input integer number (a): +_)(*(&#$)(*@()*@!⏎
Invalid input: +_)(*(&#$)(*@()*@!

$ ./a.out
Big number calculator
1) display only
2) plus (+)
3) minus (-)
4) multiplication (*)
5) division (/)
Please select the operator: 1⏎
You selected: display only
Input integer number (a): 0.0⏎
Invalid input: 0.0

$ ./a.out
Big number calculator
1) display only
2) plus (+)
3) minus (-)
4) multiplication (*)
5) division (/)
Please select the operator: 4⏎
You selected: /
Input integer number (a): 123⏎
Input integer number (b): 0⏎
Invalid input: 0
```

## Pseudo Code

``` c++
{{#include lab7_pseudo.cpp}}
```

Reference:
* [Big Number Calculator](https://www.calculator.net/big-number-calculator.html)

Reference Code: TA

``` c++
{{#include lab7_TA.cpp}}
```