## Lab 6-3: 大數取餘數 (15%)

[Division algorithm - Wikipedia](https://en.wikipedia.org/wiki/Division_algorithm)

可以參考以下正整數取餘數的 pseudocode：

```
R = N
while R >= D do
    R = R - D
end
return R
```

* 輸入：
  * 兩自然數字 \\( N, D \\) 並且各自不多於 36 位數字。
  * 兩自然數字的前後 18 位數字需分別輸入。
    * \\( N = N_{first} \times 10^{18} + N_{second}, D = D_{first} \times 10^{18} + D_{second} \\)
  * 需偵測不合法的輸入，並輸出 `Invalid input` 後提示使用者再次輸入該自然數。
  * 需支援重複輸入，使用者輸入 `-1` 則結束程式。
* 輸出：兩自然數字 \\( N, D \\) 及相除的餘數 \\( N % D \\)。
* 檔名：lab6_3_<學號>.cpp (e.g. lab6_3_106062802.cpp)

程式需提示使用者輸入兩自然數字 \\( N, D \\)，輸出兩自然數字相除的餘數 \\( N % D \\)。
使用者會在每次輸入時輸入任意實數，請考慮所有合法 `long long` 型態的數字輸入。

```text
The number N, first part (input -1 to exit): <N_first>⏎
The number N, second part (input -1 to exit): <N_second>⏎
The number N = <N>⏎
The number D, first part (input -1 to exit): <D_first>⏎
The number D, second part (input -1 to exit): <D_second>⏎
The number D = <D>⏎
The reminder N % D = <N % D>⏎
```

Example:

```console
$ ./a.out
The number N, first part (input -1 to exit): 2⏎
The number N, second part (input -1 to exit): 2⏎
The number N = 2000000000000000002⏎
The number D, first part (input -1 to exit): 1⏎
The number D, second part (input -1 to exit): 0⏎
The number D = 1000000000000000000⏎
The reminder N % D = 2⏎
⏎
The number N, first part (input -1 to exit): 1234567890123456789⏎
Invalid input⏎
The number N, first part (input -1 to exit): 123456789123456789⏎
The number N, second part (input -1 to exit): 1234567890123456789⏎
Invalid input⏎
The number N, first part (input -1 to exit): 123456789123456789⏎
The number N, second part (input -1 to exit): 123456789123456789⏎
The number N = 123456789123456789123456789123456789⏎
The number D, first part (input -1 to exit): 1111111110111111111⏎
Invalid input⏎
The number D, first part (input -1 to exit): 111111111111111111⏎
The number D, second part (input -1 to exit): 1111111110111111111⏎
Invalid input⏎
The number D, first part (input -1 to exit): 111111111111111111⏎
The number D, second part (input -1 to exit): 111111111111111111⏎
The number D = 111111111111111111111111111111111111⏎
The reminder N % D = 12345678012345678012345678012345678⏎
⏎
The number N, first part (input -1 to exit): -1⏎

$ ./a.out
The number N, first part (input -1 to exit): -2⏎
Invalid input⏎
The number N, first part (input -1 to exit): 1⏎
The number N, second part (input -1 to exit): -2⏎
Invalid input⏎
The number N, first part (input -1 to exit): 2⏎
The number N, second part (input -1 to exit): 2⏎
The number N = 2000000000000000002⏎
The number D, first part (input -1 to exit): -1⏎
```

Reference:
* [Big Number Calculator](https://www.calculator.net/big-number-calculator.html)