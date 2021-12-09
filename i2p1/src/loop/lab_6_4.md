## Lab 6-4: 大數最大公因數 (15%)

[Euclidean algorithm - Wikipedia](https://en.wikipedia.org/wiki/Euclidean_algorithm)

可以參考以下 pseudocode：

```
while b != 0
    t = b
    b = a % b
    a = t
return a
```

* 輸入：
  * 兩自然數字 \\( a, b \\) 並且各自不多於 36 位數字。
  * 兩自然數字的前後 18 位數字需分別輸入。
    * \\( a = a_{first} \times 10^{18} + a_{second}, b = b_{first} \times 10^{18} + b_{second} \\)
  * 需偵測不合法的輸入，並輸出 `Invalid input` 後提示使用者再次輸入該自然數。
  * 需支援重複輸入，使用者輸入 `-1` 則結束程式。
* 輸出：兩自然數字 \\( a, b \\) 的最大公因數 \\( gcd(a, b) \\)。
* 檔名：lab6_4_<學號>.cpp (e.g. lab6_4_106062802.cpp)

程式需提示使用者輸入兩數字 \\( a, b \\)，輸出兩數字 \\( a, b \\) 的最大公因數 \\( gcd(a, b) \\)。
使用者會在每次輸入時輸入任意整數，請考慮所有合法 `long long` 型態的數字輸入。

```text
The number a, first part (input -1 to exit): <a_first>⏎
The number a, second part (input -1 to exit): <a_second>
The number a = <a>
The number b, first part (input -1 to exit): <b_first>⏎
The number b, second part (input -1 to exit): <b_second>⏎
The number b = <b>
The gcd(a, b) = <gcd(a, b)>
```

Example:

```console
$ ./a.out
The number a, first part (input -1 to exit): 123492001107001353⏎
The number a, second part (input -1 to exit): 123492001107001353⏎
The number a = 123492001107001353123492001107001353
The number b, first part (input -1 to exit): 99396000891001089⏎
The number b, second part (input -1 to exit): 99396000891001089⏎
The number b = 99396000891001089099396000891001089
The gcd(a, b) = 3012000027000033003012000027000033

The number a, first part (input -1 to exit): 987654321⏎
The number a, second part (input -1 to exit): 200000000000000000⏎
The number a = 987654321200000000000000000
The number b, first part (input -1 to exit): 123456789⏎
The number b, second part (input -1 to exit): 200000000000000000⏎
The number b = 123456789200000000000000000
The gcd(a, b) = 400000000000000000

The number a, first part (input -1 to exit): 1234567890123456789⏎
Invalid input
The number a, first part (input -1 to exit): 123456789123456789⏎
The number a, second part (input -1 to exit): 1234567890123456789⏎
Invalid input
The number a, first part (input -1 to exit): 123456789123456789⏎
The number a, second part (input -1 to exit): 123456789123456789⏎
The number a = 123456789123456789123456789123456789
The number b, first part (input -1 to exit): 1111111110111111111⏎
Invalid input
The number b, first part (input -1 to exit): 111111111111111111⏎
The number b, second part (input -1 to exit): 1111111110111111111⏎
Invalid input
The number b, first part (input -1 to exit): 111111111111111111⏎
The number b, second part (input -1 to exit): 111111111111111111⏎
The number b = 111111111111111111111111111111111111
The gcd(a, b) = 9000000009000000009000000009

The number a, first part (input -1 to exit): -1⏎

$ ./a.out
The number a, first part (input -1 to exit): -2⏎
Invalid input
The number a, first part (input -1 to exit): 1⏎
The number a, second part (input -1 to exit): -2⏎
Invalid input
The number a, first part (input -1 to exit): 2⏎
The number a, second part (input -1 to exit): 2⏎
The number a = 2000000000000000002
The number b, first part (input -1 to exit): -1⏎
```

Reference:
* [Big Number Calculator](https://www.calculator.net/big-number-calculator.html)

Reference Code:

Credit: 林暐晉(110021134)

``` c++
{{#include lab6_4_110021134.cpp}}
```
