# Lab 4: 簡易科學計算機

## Lab 4-1: 計算機功能選擇 (40%)

* 輸入：要執行的計算功能，分別如下：
  1. 加 (`+`)
  2. 減 (`-`)
  3. 乘 (`*`)
  4. 除 (`/`)
* 輸出：所選擇的運算子字元 (i.e. `+`, `-`, `*`, `/`)
* 檔名：lab4_1_<學號>.cpp (e.g. lab4_1_106062802.cpp)

程式需提示使用者輸入需要的運算功能，輸出該運算功能的運算子字元。

```text
Simple scientific calculator
1) plus (+)
2) minus (-)
3) multiplication (*)
4) division (/)
Please select the operator: <1-4>
You selected: <+, -, *, />
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
```

Reference Code:

`if ... else ...`: Credit: 許景煬 (107071017)

``` c++
{{#include lab4_1_107071017.cpp}}
```

`switch ... case ...`: Credit: 陳欣妤 (110021108)

``` c++
{{#include lab4_1_110021108.cpp}}
```