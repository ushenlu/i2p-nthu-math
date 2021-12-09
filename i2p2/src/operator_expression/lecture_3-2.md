# Lecture 3-2: Operator & expression (1)

## operators & priority

### increment & decrement

|    opeartor    | syntax |
| :------------: | :----: |
| pre-increment  | `++a`  |
| pre-decrement  | `--a`  |
| post-increment | `a++`  |
| post-decrement | `a--`  |

``` c++
#include <iostream>

int main()
{
  int n1 = 1;
  int n2 = ++n1;
  int n3 = ++++n1;
  int n4 = n1++;
//int n5 = n1++ ++;   // error
//int n6 = n1 + ++n1; // undefined behavior
  std::cout << "n1 = " << n1 << '\n'
            << "n2 = " << n2 << '\n'
            << "n3 = " << n3 << '\n'
            << "n4 = " << n4 << '\n';
}
```

NOTE: demo with debugger

``` console
$ ./a.out
n1 = 5
n2 = 2
n3 = 4
n4 = 4
$
```

### arithmic operators

|    opeartor    | syntax  |
| :------------: | :-----: |
|   unary plus   |  `+a`   |
|  unary minus   |  `-a`   |
|    addition    | `a + b` |
|  subtraction   | `a - b` |
| multiplication | `a * b` |
|    division    | `a / b` |
|     modulo     | `a % b` |

#### `+a` & `-a`

``` c++
#include <iostream>
int main()
{
  char c = 0x6a;
  int n1 = 1;
  unsigned char n2 = 1;
  unsigned int n3 = 1;
  std::cout << "char: " << c << " int: " << +c << '\n'
            << "-1, where 1 is signed: " << -n1 << '\n'
            << "-1, where 1 is unsigned char: " << -n2 << '\n'
            << "-1, where 1 is unsigned int: " << -n3 << '\n';
}
```

``` console
$ ./a.out
char: j int: 106
-1, where 1 is signed: -1
-1, where 1 is unsigned char: -1
-1, where 1 is unsigned int: 4294967295
$
```

#### `a % b`

``` c++
#include <iostream>
int main()
{
  char c = 2;
  unsigned int un = 2;
  int n = -10;
  std::cout << "2 * (-10), where 2 is a char    = " << c * n << '\n'
            << "2 * (-10), where 2 is unsigned  = " << un * n << '\n'
            << "-10 / 2.12  = " << n / 2.12 << '\n'
            << "-10 / 21  = " << n / 21 << '\n'
            << "-10 % 21  = " << n % 21 << '\n';
}
```

``` console
$ ./a.out
2 * (-10), where 2 is a char    = -20
2 * (-10), where 2 is unsigned  = 4294967276
-10 / 2.12  = -4.71698
-10 / 21  = 0
-10 % 21  = -10
$
```


### bitwise operator

|      opeartor       |  syntax  |
| :-----------------: | :------: |
|     bitwise NOT     |   `~a`   |
|     bitwise AND     | `a & b`  |
|     bitwise OR      | `a \| b` |
|     bitwise XOR     | `a ^ b`  |
| bitwise left shift  | `a << b` |
| bitwise right shift | `a >> b` |

#### `~a`, `a & b`, `a | b`, `a ^ b`

Truth table:

|       | `a = 0` | `a = 1` |
| :---: | :-----: | :-----: |
| `~a`  |   `1`   |   `0`   |

| `a & b` | `a = 0` | `a = 1` |
| :-----: | :-----: | :-----: |
| `b = 0` |   `0`   |   `0`   |
| `b = 1` |   `0`   |   `1`   |

| `a \| b` | `a = 0` | `a = 1` |
| :------: | :-----: | :-----: |
| `b = 0`  |   `0`   |   `1`   |
| `b = 1`  |   `1`   |   `1`   |

| `a ^ b` | `a = 0` | `a = 1` |
| :-----: | :-----: | :-----: |
| `b = 0` |   `0`   |   `1`   |
| `b = 1` |   `1`   |   `0`   |

``` c++
#include <iostream>
#include <iomanip>
#include <bitset> // include for display binary number
int main()
{
  uint16_t mask = 0x00f0;
  uint32_t x0 = 0x12345678;
  uint32_t x1 = x0 | mask;
  uint32_t x2 = x0 & ~mask;
  uint32_t x3 = x0 & mask;
  uint32_t x4 = x0 ^ mask;
  uint32_t x5 = ~x0;
  using bin16 = std::bitset<16>;         // display in 16-bit width binary number
  using bin32 = std::bitset<32>;         // display in 32-bit width binary number
  std::cout << std::hex << std::showbase // show in hexdecemal with base number (0x)
            << "Mask: " << mask << std::setw(49) << bin16(mask) << '\n'
            << "Value: " << x0 << std::setw(42) << bin32(x0) << '\n'
            << "Setting bits: " << x1 << std::setw(35) << bin32(x1) << '\n'
            << "Clearing bits: " << x2 << std::setw(34) << bin32(x2) << '\n'
            << "Selecting bits: " << x3 << std::setw(39) << bin32(x3) << '\n'
            << "XOR-ing bits: " << x4 << std::setw(35) << bin32(x4) << '\n'
            << "Inverting bits: " << x5 << std::setw(33) << bin32(x5) << '\n';
}
```

``` console
$ ./a.out
Mask: 0xf0                                 0000000011110000
Value: 0x12345678          00010010001101000101011001111000
Setting bits: 0x123456f8   00010010001101000101011011111000
Clearing bits: 0x12345608  00010010001101000101011000001000
Selecting bits: 0x70       00000000000000000000000001110000
XOR-ing bits: 0x12345688   00010010001101000101011010001000
Inverting bits: 0xedcba987 11101101110010111010100110000111
$
```

#### `a >> b` & `a << b`

``` c++
#include <iostream>
int main()
{
  std::cout << std::hex << std::showbase;
  char c = 0x10;
  unsigned long long ull = 0x123;
  std::cout << "0x123 << 1 = " << (ull << 1) << '\n'
            << "0x123 << 63 = " << (ull << 63) << '\n' // overflow in unsigned
            << "0x10 << 10 = " << (c << 10) << '\n';   // char is promoted to int
  long long ll = -1000;
  std::cout << std::dec << "-1000 >> 1 = " << (ll >> 1) << '\n';
}
```

``` console
$ ./a.out
0x123 << 1 = 0x246
0x123 << 63 = 0x8000000000000000
0x10 << 10 = 0x4000
-1000 >> 1 = -500
$
```

### logical operators

|   opeartor   |   syntax   |
| :----------: | :--------: |
|   negation   |    `!a`    |
|     AND      |  `a && b`  |
| inclusive OR | `a \|\| b` |

Truth table:

|       | `a = false` | `a = true` |
| :---: | :---------: | :--------: |
| `!a`  |   `true`    |  `false`   |

|  `a && b`   | `a = false` | `a = true` |
| :---------: | :---------: | :--------: |
| `b = false` |   `false`   |  `false`   |
| `b = true`  |   `false`   |   `true`   |

| `a \|\| b`  | `a = false` | `a = true` |
| :---------: | :---------: | :--------: |
| `b = false` |   `false`   |   `true`   |
| `b = true`  |   `true`    |   `true`   |

``` c++
#include <iostream>
int main()
{
  bool a = true;
  bool b = false;
  std::cout << std::boolalpha
            << "a: " << a << std::endl
            << "b: " << b << std::endl
            << "!a: " << !a << std::endl
            << "a && b: " << a &&
          b << std::endl
            << "a || b: " << a ||
      b << std::endl;
  return 0;
}
```

``` console
$ ./a.out
a: true
b: false
!a: false
a && b: false
a || b: true
$
```

### comparison operators

|         opeartor         |  syntax  |
| :----------------------: | :------: |
|         equal to         | `a == b` |
|       not equal to       | `a != b` |
|        less than         | `a < b`  |
|       greater than       | `a > b`  |
|  less than or equal to   | `a <= b` |
| greater than or equal to | `a >= b` |

``` c++
#include <iostream>
int main()
{
  std::cout << std::boolalpha;
  int n = -1;

  int n2 = 1;
  std::cout << " -1 == 1? " << (n == n2) << '\n'
            << "Comparing two signed values:\n"
            << " -1  < 1? " << (n < n2) << '\n'
            << " -1  > 1? " << (n > n2) << '\n';

  unsigned int u = 1;
  std::cout << "Comparing signed and unsigned:\n"
            << " -1  < 1? " << (n < u) << '\n'
            << " -1  > 1? " << (n > u) << '\n';
}
```

``` console
$ ./a.out
 -1 == 1? false
Comparing two signed values:
 -1  < 1? true
 -1  > 1? false
Comparing signed and unsigned:
 -1  < 1? false
 -1  > 1? true
$
```

### assign operators

|            opeartor            |  syntax   |   equivalent statements   |
| :----------------------------: | :-------: | :-----------------------: |
|           assignment           |  `a = b`  |          `a = b`          |
|      addition assignment       | `a += b`  | `temp = a + b; a = temp`  |
|     subtraction assignment     | `a -= b`  | `temp = a - b; a = temp`  |
|   multiplication assignment    | `a *= b`  | `temp = a * b; a = temp`  |
|      division assignment       | `a /= b`  | `temp = a / b; a = temp`  |
|       modulo assignment        | `a %= b`  | `temp = a % b; a = temp`  |
|     bitwise AND assignment     | `a &= b`  | `temp = a & b; a = temp`  |
|     bitwise OR assignment      | `a \|= b` | `temp = a \| b; a = temp` |
|     bitwise XOR assignment     | `a ^= b`  | `temp = a ^ b; a = temp`  |
| bitwise left shift assignment  | `a <<= b` | `temp = a << b; a = temp` |
| bitwise right shift assignment | `a >>= b` | `temp = a >> b; a = temp` |

### conditional operators

|       opeartor       |   syntax    |
| :------------------: | :---------: |
| conditional operator | `a ? b : c` |

``` c++
#include <iostream>
int main()
{
  // simple rvalue example
  int n = 1 > 2 ? 10 : 11; // 1>2 is false, so n = 11
  // simple lvalue example
  int m = 10;
  (n == m ? n : m) = 7;                      // n == m is false, so m = 7
  std::cout << "n = " << n << "\nm = " << m; //output the result
}
```

``` console
$ ./a.out
n = 11
m = 7
$
```

### priority

| precedence |                                                          operator                                                           |
| :--------: | :-------------------------------------------------------------------------------------------------------------------------: |
|     1      |                                                        `a++`, `a--`                                                         |
|     2      |                                                        `++a`, `--a`                                                         |
|     3      |                                                         `+a`, `-a`                                                          |
|            |                                                         `!a`, `~a`                                                          |
|            |                                                          `(type)`                                                           |
|     5      |                                                  `a * b`, `a / b`, `a % b`                                                  |
|     6      |                                                      `a + b`, `a - b`                                                       |
|     7      |                                                     `a << b`, `a >> b`                                                      |
|     9      |                                            `a < b`, `a <= b`, `a > b`, `a >= b`                                             |
|     10     |                                                     `a == b`, `a != b`                                                      |
|     11     |                                                           `a & b`                                                           |
|     12     |                                                           `a ^ b`                                                           |
|     13     |                                                          `a \| b`                                                           |
|     14     |                                                          `a && b`                                                           |
|     15     |                                                         `a \|\| b`                                                          |
|     16     | `a ? b : c`, `a = b`, `a += b`, `a -= b`, `a *= b`, `a /= b`, `a %= b`, `a <<= b`, `a >>= b`, `a &= b`, `a ^= b`, `a \|= b` |

``` c++
// Credit: E. Chen
#include <iostream>

int main()
{
  std::cout << !0 + 1 << std::endl;
  std::cout << !(0 + 1) << std::endl;

  int a = 6 % 10 / 2 + 1 % 2 >= 3 || !+4 - 9 <= -1;
  /***
     * step 1 -> int a = 6 % 10 / 2 + 1 % 2 >= 3 || ! (+4) - 9 <= (-1);
      (Unary plus and minus)
     * step 2 -> int a = 6 % 10 / 2 + 1 % 2 >= 3 || (0) - 9 <= (-1);
      (Logical NOT)
     * step 3 -> int a = (6 % 10 / 2) + (1 % 2) >= 3 || 0 - 9 <= (-1);
      (Arithmetic multiplication, division and remainder)
     * step 4 -> int a = (3 + 1) >= 3 || (0 - 9) <= (-1);
      (Arithmetic addition and substraction)
     * step 5 -> int a = (4 > 3) || (-9 <= -1);
      (Relational operators)
     * step 6 -> int a = (true || true);
      (Logical operators)
     * step 7 -> int a = true;
      (assignmnet operators)
    ***/
  std::cout << a << std::endl;

  return 0;
}
```

Reference:
* [htchen/i2p-nthu by 陳煥宗老師](https://github.com/htchen/i2p-nthu/tree/master/%E7%A8%8B%E5%BC%8F%E8%A8%AD%E8%A8%88%E4%B8%80/Introduction%20to%20programming)
* [Fundamental types - cppreference.com](https://en.cppreference.com/w/cpp/language/types)
* [Increment/decrement operators - cppreference.com](https://en.cppreference.com/w/cpp/language/operator_incdec)
* [Arithmetic operators - cppreference.com](https://en.cppreference.com/w/cpp/language/operator_arithmetic)
* [Logical operators - cppreference.com](https://en.cppreference.com/w/cpp/language/operator_logical)
* [Assignment operators - cppreference.com](https://en.cppreference.com/w/cpp/language/operator_assignment)
* [Other operators - cppreference.com](https://en.cppreference.com/w/cpp/language/operator_other)
* [C++ Operator Precedence - cppreference.com](https://en.cppreference.com/w/cpp/language/operator_precedence)
