## Lab 6-2: 最大公因數 (35%)

[Euclidean algorithm - Wikipedia](https://en.wikipedia.org/wiki/Euclidean_algorithm)

可以參考以下 pseudocode：

```
while a != b 
    if a > b
        a = a - b
    else
        b = b - a
return a
```

* 輸入：
  * 兩自然數字 \\( a, b \\) 並且各自不多於 18 位數字。
  * 需偵測不合法的輸入，並輸出 `Invalid input` 。
  * 需支援重複輸入，使用者輸入 `0` 則結束程式。
* 輸出：兩自然數字 \\( a, b \\) 的最大公因數 \\( gcd(a, b) \\)。
* 檔名：lab6_2_<學號>.cpp (e.g. lab6_2_106062802.cpp)

程式需提示使用者輸入兩數字 \\( a, b \\)，輸出兩數字 \\( a, b \\) 的最大公因數 \\( gcd(a, b) \\)。
使用者會在每次輸入時輸入任意實數，請考慮所有合法 `double` 型態的數字輸入。

```text
The number a (input 0 to exit): <a>⏎
The number b (input 0 to exit): <b>⏎
The gcd(a, b) = <gcd(a, b)>
```

Example:

```console
$ ./a.out
The number a (input 0 to exit): 15⏎
The number b (input 0 to exit): 17⏎
The gcd(a, b) = 1

The number a (input 0 to exit): 16⏎
The number b (input 0 to exit): 8⏎
The gcd(a, b) = 8

The number a (input 0 to exit): 16⏎
The number b (input 0 to exit): 0⏎

$ ./a.out
The number a (input 0 to exit): -1⏎
Invalid input
The number a (input 0 to exit): 16⏎
The number b (input 0 to exit): -1⏎
Invalid input
The number a (input 0 to exit): 0⏎
```
