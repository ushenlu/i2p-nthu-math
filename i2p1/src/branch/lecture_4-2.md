# Lecture 4-2: Branch Statement

## `if ... `

``` c++
#include <iostream>

int main() 
{
    bool flag = true;
    if(flag)
    {
        std::cout << "The flag is true" << std::endl;
    }
    std::cout << "The normal statement" << std::endl;
}
```

``` c++
#include <iostream>

int main() 
{
    bool flag = true;
    if(flag)
        std::cout << "The flag is true" << std::endl;
    std::cout << "The normal statement" << std::endl;
}
```

Notice: different from python

``` c++
#include <iostream>

int main() 
{
    bool flag = true;
    if(flag)
        std::cout << "The flag is true" << std::endl;
        std::cout << "The normal statement" << std::endl;
}
```

``` c++
#include <iostream>

int main() 
{
    int input = -100;
    if(input < 0)
    {
        std::cout << "The input is negative" << std::endl;
    }
}
```

## `if ... else`

``` c++
#include <iostream>

int main() 
{
    bool flag = true;
    if(flag)
    {
        std::cout << "The flag is true" << std::endl;
    }
    else // flag == false
    {
        std::cout << "The flag is false" << std::endl;
    }
    std::cout << "The normal statement" << std::endl;
}
```

``` c++
#include <iostream>

int main() 
{
    int input = -100;
    if(input < 0)
    {
        std::cout << "The input is negative" << std::endl;
    }
    else // input >= 0
    {
        std::cout << "The input is positive" << std::endl;
    }
}
```

## `if ... else if ... else`

``` c++
#include <iostream>

int main() 
{
    int input = -100;
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
}
```

## nested `if ... else`

``` c++
#include <iostream>

int main() 
{
    int input = -100;
    if(input < 0)
    {
        std::cout << "The input is negative" << std::endl;
    }
    else 
    {
        if(input == 0)
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

## `switch ... case`

``` c++
#include <iostream>

int main() 
{
    int input = -100;
    switch(input)
    {
        case -1:
            std::cout << "The input is -1" << std::endl;
            //break;
        case 0:
            std::cout << "The input is 0" << std::endl;
            //break;
        case 1:
            std::cout << "The input is 1" << std::endl;
            //break;
        default:
            std::cout << "The input is others" << std::endl;
    }
}
```

## `return 0` to end `main` function

``` c++
#include <iostream>

int main() 
{
    int input = -100;
    if(input < 0)
    {
        std::cout << "The input is negative" << std::endl;
    }
    else 
    {
        // return 0;
        if(input == 0)
        {
            std::cout << "The input is zero" << std::endl;
        }
        else // input > 0
        {
            std::cout << "The input is positive" << std::endl;
        }
    }
    return 0;
}
```

Reference:
* [htchen/i2p-nthu by 陳煥宗老師](https://github.com/htchen/i2p-nthu/tree/master/%E7%A8%8B%E5%BC%8F%E8%A8%AD%E8%A8%88%E4%B8%80/Introduction%20to%20programming)
* [CNOCycle/cpp_tutorial by E. Chen](https://github.com/CNOCycle/cpp_tutorial)