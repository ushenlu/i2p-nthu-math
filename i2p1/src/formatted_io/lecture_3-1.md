# Lecture 2: Data Type & Formatted Input/Output (2)

## 細部拆解一個 C++ 程式碼

``` c++
#include <iostream>

int main(void){
    int a = 0, b = 0, c = 0;
    std::cout << "input a:";
    std::cin >> a;
    std::cout << "input b:";
    std::cin >> b;
    c = a + b;
    std::cout << "a: " << a << std::endl
                << "b: " << b << std::endl
                << "a + b = " << c << std::endl;
    return 0;
}
```

## Coding Style

### intend & spacing

### variable naming rule

## 變數格式 & 型態轉換

### int, long, long long

### unsigned int

### float, double, double double

### floating point precision

### cast

### char

## I/O Buffer & 控制字元

Reference:
* [htchen/i2p-nthu by 陳煥宗老師](https://github.com/htchen/i2p-nthu/tree/master/%E7%A8%8B%E5%BC%8F%E8%A8%AD%E8%A8%88%E4%B8%80/Introduction%20to%20programming)
* [Fundamental types - cppreference.com](https://en.cppreference.com/w/cpp/language/types)