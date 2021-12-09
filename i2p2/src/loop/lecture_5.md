# Lecture 5: Loop Statement (1)

## What is Loop?

要重複執行特定指令，並在滿足特定條件下結束重複執行

example: check lager than `0`, equal to `0`, or less than `0`

``` c++
#include <iostream>

int main()
{
    int input = 0;

    std::cout << "Input a integer: ";
    std::cin >> input;

    if (input < 0)
    {
        std::cout << "The input is negative" << std::endl;
    }
    else if (input == 0)
    {
        std::cout << "The input is zero" << std::endl;
    }
    else // input > 0
    {
        std::cout << "The input is positive" << std::endl;
    }

    std::cout << "Input a integer: ";
    std::cin >> input;

    if (input < 0)
    {
        std::cout << "The input is negative" << std::endl;
    }
    else if (input == 0)
    {
        std::cout << "The input is zero" << std::endl;
    }
    else // input > 0
    {
        std::cout << "The input is positive" << std::endl;
    }
}
```

## `for (;;) {}`

``` c++
#include <iostream>

int main()
{
    int input = 0;
    int type_counts = 3; // check input three times

    for (int i = 0; i < type_counts; i++) // for loop
    {
        std::cout << "Input a integer (" << i << '/' << type_counts << "): ";
        std::cin >> input;

        if (input < 0)
        {
            std::cout << "The input is negative" << std::endl;
        }
        else if (input == 0)
        {
            std::cout << "The input is zero" << std::endl;
        }
        else // input > 0
        {
            std::cout << "The input is positive" << std::endl;
        }
    }
}
```

### 分析 for loop 架構

``` c++
for (int i = 0; i < type_counts; i++) // for loop
{
}
```

`int i = 0;`：宣告並初始化在 loop 內會用到的變數，一個 for loop 只會執行一次。一般會宣告只會在 for loop 內更動的變數，例如第幾次迴圈或是 array 現在使用的 index。

`i < type_counts;`：for loop 的執行條件，如果條件滿足就會執行 `{}` 所包圍著的程式碼一次。

`i++`：執行 `{}` 所包圍著的程式碼完後會執行的部分。一般會變動 `int i = 0;` 內所宣告的變數，例如下一次迴圈是第幾次回圈的變數或是 array 下一個使用的 index。

NOTE: 以上三個部分都是只能一個 statement，也就是一行以 `;` 結束的程式碼。`i < type_counts;` 部分一定要回傳 `true` or `false` or `0` or 非 `0` 的數字。

## `while () {}`

``` c++
#include <iostream>

int main()
{
    int input = 0;
    int type_counts = 3; // check input three times

    int i = 0; // define index variable

    while (i < type_counts) // while loop, check before execute the follows
    {
        std::cout << "Input a integer (" << i << '/' << type_counts << "): ";
        std::cin >> input;

        if (input < 0)
        {
            std::cout << "The input is negative" << std::endl;
        }
        else if (input == 0)
        {
            std::cout << "The input is zero" << std::endl;
        }
        else // input > 0
        {
            std::cout << "The input is positive" << std::endl;
        }
        i++; // increase index variable
    }
}
```

NOTE: 如果需要宣告在 while loop 內會調整到的變數，需要在 while loop 外宣告。

## variable scope

NOTE: demo with gdb, 觀察 `i` 跟 `today_date`。

``` c++
#include <iostream>

int main()
{
    int input = 0;
    int type_counts = 3; // check input three times

    int i = 0; // define index variable

    while (i < type_counts) // while loop, check before execute the follows
    {
        int i = 0; // wrong example
        long today_date = 20211021;

        std::cout << "Today is (yyyymmdd): " << today_date << std::endl;
        std::cout << "Input a integer (" << i << '/' << type_counts << "): ";
        std::cin >> input;

        if (input < 0)
        {
            std::cout << "The input is negative" << std::endl;
        }
        else if (input == 0)
        {
            std::cout << "The input is zero" << std::endl;
        }
        else // input > 0
        {
            std::cout << "The input is positive" << std::endl;
        }
        i++; // increase index variable
    }
    //std::cout << "Today is (yyyymmdd): " << today_date << std::endl; // compile error
}
```

## `do {} while ();`

``` c++
#include <iostream>

int main()
{
    int input = 0;
    int type_counts = 3; // check input three times

    int i = 0; // define index variable

    do
    {
        std::cout << "Input a integer (" << i << '/' << type_counts << "): ";
        std::cin >> input;

        if (input < 0)
        {
            std::cout << "The input is negative" << std::endl;
        }
        else if (input == 0)
        {
            std::cout << "The input is zero" << std::endl;
        }
        else // input > 0
        {
            std::cout << "The input is positive" << std::endl;
        }
        i++; // increase index variable
    } while (i < type_counts); // do while loop, check after execute the aboves
}
```

## infinite loop & not executed loop

### infinite loop

``` c++
#include <iostream>

int main() 
{
    int input = 0;
    int type_counts = 3; // check input three times

    int i = 0; // define index variable

    while (i < type_counts) // while loop, check before execute the follows
    {
        std::cout << "Input a integer (" << i << '/' << type_counts << "): ";
        std::cin >> input;

        if(input < 0)
        {
            std::cout << "The input is negative" << std::endl;
        }
        else if(input == 0)
        {
            std::cout << "The input is zero" << std::endl;
        }
        else // input > 0
        {
            std::cout << "The input is positive" << std::endl;
        }
        // i++; // infinite loop, condition is always satisfied
    }
}
```

### not executed loop

``` c++
#include <iostream>

int main()
{
    int input = 0;
    int type_counts = 0; // check input zero time

    int i = 0; // define index variable

    while (i < type_counts) // not excute, condition cannot satisify
    {
        std::cout << "Input a integer (" << i << '/' << type_counts << "): ";
        std::cin >> input;

        if (input < 0)
        {
            std::cout << "The input is negative" << std::endl;
        }
        else if (input == 0)
        {
            std::cout << "The input is zero" << std::endl;
        }
        else // input > 0
        {
            std::cout << "The input is positive" << std::endl;
        }
        i++;
    }
}
```

## `break` & `continue`

``` c++
#include <iostream>

int main() 
{
    int input = 0;
    int type_counts = 3; // check input three times

    int i = 0; // define index variable

    while (i < type_counts) // while loop, check before execute the follows
    {
        std::cout << "Input a integer (" << i << '/' << type_counts << "): ";
        std::cin >> input;

        if(input < 0)
        {
            std::cout << "The input is negative, continue" << std::endl;
            continue;
        }
        else if(input == 0)
        {
            std::cout << "The input is zero, exit." << std::endl;
            break;
        }
        else // input > 0
        {
            std::cout << "The input is positive" << std::endl;
        }
        i++; // increase index variable, check after break & continue
    }
}
```

## nested loop

``` c++
#include <iostream>

int main()
{
    while (true)
    {
        int height = 0;
        int width = 0;

        std::cout << "Input height: ";
        std::cin >> height;
        if (height < 0)
        {
            std::cout << "Invalid height: " << height << std::endl;
            continue;
        }
        else if (height == 0)
        {
            std::cout << "Input 0, exit." << std::endl;
            break;
        }

        std::cout << "Input width: ";
        std::cin >> width;
        if (width < 0)
        {
            std::cout << "Invalid width: " << width << std::endl;
            continue;
        }
        else if (width == 0)
        {
            std::cout << "Input 0, exit." << std::endl;
            break;
        }

        for (int i = 0; i < height; i++)
        {
            for (int j = 0; j < width; j++)
            {
                std::cout << '*' << std::flush;
            }
            std::cout << std::endl;
        }
    }
    return 0;
}
```

## examples

### pyramid

``` c++
#include <iostream>

int main()
{
    while (true)
    {
        int height = 0;

        std::cout << "Input height: ";
        std::cin >> height;
        if (height < 0)
        {
            std::cout << "Invalid height: " << height << std::endl;
            continue;
        }
        else if (height == 0)
        {
            std::cout << "Input 0, exit." << std::endl;
            break;
        }

        for (int i = 1; i < (height + 1); i++)
        {
            for (int j = 0; j < i; j++)
            {
                std::cout << '*' << std::flush;
            }
            std::cout << std::endl;
        }
    }
    return 0;
}
```

### 9x9 multiplication table

[Multiplication table - Wikipedia](https://en.wikipedia.org/wiki/Multiplication_table)

``` c++
#include <iostream>
#include <iomanip>

int main()
{
    for (int i = 1; i < (9 + 1); i++) // index start from 1
    {
        for (int j = 1; j < (9 + 1); j++) // index start from 1
        {
            std::cout << i << '*' << j << " = "
                      << std::setw(2) << i * j << ' '
                      << std::flush;
        }
        std::cout << std::endl;
    }
    return 0;
}
```

Reference:
* [htchen/i2p-nthu by 陳煥宗老師](https://github.com/htchen/i2p-nthu/tree/master/%E7%A8%8B%E5%BC%8F%E8%A8%AD%E8%A8%88%E4%B8%80/Introduction%20to%20programming)
* [CNOCycle/cpp_tutorial by E. Chen](https://github.com/CNOCycle/cpp_tutorial)