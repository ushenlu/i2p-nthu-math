# Lecture 1-2: Data Type & Formatted Input/Output (1)

## 變數 & 格式化輸出

``` c++
// import std::cout & std::endl
#include <iostream>
// start of define main function
// void: no input arguments
// int: return value in int type
int main(void){
    // define variable `year`, `month`, and `day`
    // and assign value with `2021`, `9`, and `23`
    int year = 2021, month = 9, day = 23;
    // print "Hello world!" and today's date on the terminal
    std::cout << "Hello world!" 
            << std::endl
            << "Today is "
            << year << "/"
            << month << "/"
            << day << "."
            << std::endl;
    return 0;
}
```

```console
$ ./a.out
Hello world!
Today is 2021/9/23.
$
```

### `int year = 2021, month = 9, day = 23;`

#### 變數命名規則

### `std::cout << year;`

## 從鍵盤讀取: `std::cin`

``` c++
#include <iostream>

int main(void){
    int input_number = 0;
    std::cin >> input_number;
    std::cout << "Hello world! " 
                << input_number 
                << std::endl;
    return 0;
}
```

### `std::cin >> input_number;`

## 數字運算

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

### `c = a + b;`

Reference:
* [htchen/i2p-nthu by 陳煥宗老師](https://github.com/htchen/i2p-nthu/tree/master/%E7%A8%8B%E5%BC%8F%E8%A8%AD%E8%A8%88%E4%B8%80/Introduction%20to%20programming)