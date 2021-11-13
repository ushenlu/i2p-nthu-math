# Lecture 3-1: Data Type & Formatted Input/Output (3)

## Radix

* Binary `0b0`, `0b1`
* Octal: `00` ~ `07`
* Decimal: `0` ~ `9`
* Hexdecimal: `0x0` ~ `0xf`

example:

``` c++
int d = 42;
int o = 052;
int x = 0x2a;
int X = 0X2A;
int b = 0b101010; // C++14
```

## setfill & setw

### setfill

``` c++
#include <iostream>
#include <iomanip> // include IO Manipulators
int main()
{
  std::cout << "default fill: [" << std::setw(10) << 42 << "]\n"
            << "setfill('*'): [" << std::setfill('*')
            << std::setw(10) << 42 << "]\n";
}
```

output

``` console
$ ./a.out
default fill: [        42]
setfill('*'): [********42]
$
```

### setw

``` c++
#include <iostream>
#include <iomanip>

int main()
{
  std::cout << "no setw: [" << 42 << "]\n"
            << "setw(6): [" << std::setw(6) << 42 << "]\n"
            << "setw(6), several elements: [" << 89 
            << std::setw(6) << 12 << 34 << "]\n";
}
```

``` console
$ ./a.out
no setw: [42]
setw(6): [    42]
setw(6), several elements: [89    1234]
$
```

## scientific representation

format: 10-based

* `1.234567e-10`
* `-1.234567e+10`

### std::scientific, std::fixed

``` c++
#include <iostream>
#include <iomanip>

enum class cap
{
  title,
  middle,
  end
};
void print(const char *text, double num, cap c)
{
  if (c == cap::title)
    std::cout << "┌──────────┬────────────┬──────────────────────────┐\n"
                 "│  number  │   iomanip  │      representation      │\n"
                 "├──────────┼────────────┼──────────────────────────┤\n";
  std::cout << std::left
            << "│ " << std::setw(8) << text << " │ fixed      │ "
            << std::setw(24) << std::fixed << num << " │\n"
            << "│ " << std::setw(8) << text << " │ scientific │ "
            << std::setw(24) << std::scientific << num << " │\n"
            << "│ " << std::setw(8) << text << " │ default    │ "
            << std::setw(24) << std::defaultfloat << num << " │\n";
  std::cout << (c != cap::end ? 
            "├──────────┼────────────┼──────────────────────────┤\n" 
            : "└──────────┴────────────┴──────────────────────────┘\n");
}

int main()
{
  print("0.0", 0.0, cap::title);
  print("0.01", 0.01, cap::middle);
  print("0.00001", 0.00001, cap::end);
}
```

``` console
$ ./a.out
┌──────────┬────────────┬──────────────────────────┐
│  number  │   iomanip  │      representation      │
├──────────┼────────────┼──────────────────────────┤
│ 0.0      │ fixed      │ 0.000000                 │
│ 0.0      │ scientific │ 0.000000e+00             │
│ 0.0      │ default    │ 0                        │
├──────────┼────────────┼──────────────────────────┤
│ 0.01     │ fixed      │ 0.010000                 │
│ 0.01     │ scientific │ 1.000000e-02             │
│ 0.01     │ default    │ 0.01                     │
├──────────┼────────────┼──────────────────────────┤
│ 0.00001  │ fixed      │ 0.000010                 │
│ 0.00001  │ scientific │ 1.000000e-05             │
│ 0.00001  │ default    │ 1e-05                    │
└──────────┴────────────┴──────────────────────────┘
$
```

### pow(base, exponent)

計算 $${base}^{exponment}$$

``` c++
#include <iostream>
#include <cmath> // include cmath for std::pow

int main()
{
  // typical usage
  std::cout << "pow(2, 10) = " << std::pow(2, 10) << '\n'
            << "pow(2, 0.5) = " << std::pow(2, 0.5) << '\n'
            << "pow(-2, -3) = " << std::pow(-2, -3) << '\n';
}
```

``` console
$ ./a.out
pow(2, 10) = 1024
pow(2, 0.5) = 1.41421
pow(-2, -3) = -0.125
$
```

## I/O Buffer & 控制字元(Escape Character)

### I/O Buffer

當你使用 `std::cout` 把資料顯示到螢幕上時，其實並不會立即顯示在螢幕上，而是先送到所謂的 buffer 裡。
要等到下列幾種情況才會做 flushing the buffer 的動作，把 buffer 裡的資料沖到螢幕上：
1. 當 buffer 滿的時候
2. 當 `\n` 字元出現的時候
3. 當接下來是做輸入的動作的時候 (譬如遇到 `std::cin`)。
有時候為了讓資料能立刻顯示到螢幕上，可以用 fflush() 強迫把 buffer 裡的東西送出。
當你發現有時候輸入或輸出的顯示順序會亂掉，可以試著在 `std::cout` 之後用 `std::flush` 來確保資料不會被卡在 buffer 裡。

``` c++
#include <iostream>
int main(int argc, char *argv[])
{
  int a = 0, b = 0, c = '\n';
  std::cout << "a: "
            << a
            //<< std::flush
            << "b: "
            << b
            //<< std::flush
            << "a + b = "
            << c
            << std::endl;
  return 0;
}
```

### 控制字元(Escape Character)

In ASCII: `0 ... 1F, 7F`

``` c++
#include <iostream>
int main(int argc, char *argv[])
{
  char a = 'c', b = '\010', c = 'a';
  std::cout << "a: "
            << a
            << "b: "
            << b
            << "c: "
            << c
            << std::endl;
  return 0;
}
```

## bool

``` c++
#include <iostream>

int main()
{
  std::cout << std::boolalpha
            << true << '\n'
            << false << '\n'
            << std::noboolalpha
            << true << '\n'
            << false << '\n';
}
```

``` console
$ ./a.out
true
false
1
0
$
```

NOTE: 會在 tarnary operator ` ? : ` 使用

Reference:
* [htchen/i2p-nthu by 陳煥宗老師](https://github.com/htchen/i2p-nthu/tree/master/程式設計一)
* [Integer literal - cppreference.com](https://en.cppreference.com/w/cpp/language/integer_literal)
* [std::setfill - cppreference.com](https://en.cppreference.com/w/cpp/io/manip/setfill)
* [std::setw - cppreference.com](https://en.cppreference.com/w/cpp/io/manip/setw)
* [std::fixed, std::scientific, std::hexfloat, std::defaultfloat - cppreference.com](https://en.cppreference.com/w/cpp/io/manip/fixed)
* [std::pow, std::powf, std::powl - cppreference.com](https://en.cppreference.com/w/cpp/numeric/math/pow)
* [ASCII Table](https://www.cs.cmu.edu/~pattis/15-1XX/common/handouts/ascii.html)
* [What is a buffer in C?](https://www.educative.io/edpresso/what-is-a-buffer-in-c)
* [Boolean literals - cppreference.com](https://en.cppreference.com/w/cpp/language/bool_literal)