# Lecture 11: Function & Reference (2)

## How to create a function from scratch

以下會介紹如何從頭將原本重複的程式碼轉換成函式，並且把原本的程式碼改寫。

### 確認重複使用的程式碼片段

``` c++
#include <iostream>
#include <cctype>    // isdigit()
#include <algorithm> // reverse()
#include <vector>    // vector<int>()

using namespace std;

int main()
{
    char input_buffer[10000 + 1]; // + 1 for the last '\0'
    vector<int> a, b;

    cout << "Input a non-negative integer number (a): ";
    cin >> input_buffer;

    // begin repeated codes, parse the input (a)
    for (int i = 0; input_buffer[i] != '\0'; i++)
    {
        if (!isdigit(input_buffer[i]))
        {
            cout << "Invalid input: " << input_buffer << endl;
            return 0;
        }
        else
        {
            int digit = input_buffer[i] - '0';
            a.push_back(digit);
        }
    }

    reverse(a.begin(), a.end());

    // remove leading zeros
    for (int i = a.size() - 1; i >= 1; i--)
    {
        if (a[i] == 0)
        {
            a.pop_back();
        }
        else
        {
            break;
        }
    }
    // end repeated codes, parse the input (a)

    // begin repeated codes, clean up the input buffer
    for (int i = 0; i < (10000 + 1); i++)
    {
        input_buffer[i] = '\0';
    }
    // end repeated codes, clean up the input buffer

    cout << "(a) = ";
    // begin repeated codes, print the input (a)
    for (int i = a.size() - 1; i >= 0; i--)
    {
        cout << a[i];
    }
    cout << endl;
    // end repeated codes, print the input (a)

    cout << "Input a non-negative integer number (b): ";
    cin >> input_buffer;

    // begin repeated codes, parse the input (b)
    for (int i = 0; input_buffer[i] != '\0'; i++)
    {
        if (!isdigit(input_buffer[i]))
        {
            cout << "Invalid input: " << input_buffer << endl;
            return 0;
        }
        else
        {
            int digit = input_buffer[i] - '0';
            b.push_back(digit);
        }
    }

    reverse(b.begin(), b.end());

    // remove leading zeros
    for (int i = b.size() - 1; i >= 1; i--)
    {
        if (b[i] == 0)
        {
            b.pop_back();
        }
        else
        {
            break;
        }
    }
    // end repeated codes, parse the input (b)

    // begin repeated codes, clean up the input buffer
    for (int i = 0; i < (10000 + 1); i++)
    {
        input_buffer[i] = '\0';
    }
    // end repeated codes, clean up the input buffer

    cout << "(b) = ";
    // begin repeated codes, print the input (b)
    for (int i = b.size() - 1; i >= 0; i--)
    {
        cout << b[i];
    }
    cout << endl;
    // end repeated codes, print the input (b)
}
```

### 建立 function 的輸入參數及輸出

#### parse the input

``` c++
    // begin repeated codes, parse the input (a)
    for (int i = 0; input_buffer[i] != '\0'; i++)
    {
        if (!isdigit(input_buffer[i]))
        {
            cout << "Invalid input: " << input_buffer << endl;
            return 0;
        }
        else
        {
            int digit = input_buffer[i] - '0';
            a.push_back(digit);
        }
    }

    reverse(a.begin(), a.end());

    // remove leading zeros
    for (int i = a.size() - 1; i >= 1; i--)
    {
        if (a[i] == 0)
        {
            a.pop_back();
        }
        else
        {
            break;
        }
    }
    // end repeated codes, parse the input (a)
```

* Input: `input_buffer`
* Output: `a`

#### clean up the input buffer

``` c++
    // begin repeated codes, clean up the input buffer
    for (int i = 0; i < (10000 + 1); i++)
    {
        input_buffer[i] = '\0';
    }
    // end repeated codes, clean up the input buffer
```

* Input: `input_buffer`
* Output: none

#### print the input

``` c++
    // begin repeated codes, print the input (a)
    for (int i = a.size() - 1; i >= 0; i--)
    {
        cout << a[i];
    }
    cout << endl;
    // end repeated codes, print the input (a)
```

* Input: `a`
* Output: none

### 將使用的變數替換成 function 的參數或 function 內的變數

#### parse the input

``` c++
vector<int> parse_big_number(const char input_buffer[])
{
    vector<int> big_number;
    for (int i = 0; input_buffer[i] != '\0'; i++)
    {
        if (!isdigit(input_buffer[i]))
        {
            cout << "Invalid input: " << input_buffer << endl;
            return vector<int>();
        }
        else
        {
            int digit = input_buffer[i] - '0';
            big_number.push_back(digit);
        }
    }

    reverse(big_number.begin(), big_number.end());

    // remove leading zeros
    for (int i = big_number.size() - 1; i >= 1; i--)
    {
        if (big_number[i] == 0)
        {
            big_number.pop_back();
        }
        else
        {
            break;
        }
    }

    return big_number;
}
```

* Input: `input_buffer` -> `const char input_buffer[]`
* Output: `a` -> `vector<int> big_number`
* Return: `big_number`

#### clean up the input buffer

``` c++
void clean_up_input_buffer(char input_buffer[])
{
    for (int i = 0; input_buffer[i] != '\0'; i++)
    {
        input_buffer[i] = '\0';
    }
}
```

* Input: `input_buffer` -> `char input_buffer[]`
* Output: none

#### print the input

``` c++
void print_big_number(const vector<int> &big_number)
{
    for (int i = big_number.size() - 1; i >= 0; i--)
    {
        cout << big_number[i];
    }
    cout << endl;
}
```

* Input: `a` -> `const vector<int> &big_number`
* Output: none

### 將原本的程式碼片段改成使用 function

``` c++
#include <iostream>
#include <cctype>    // isdigit()
#include <algorithm> // reverse()
#include <vector>    // vector<int>()

using namespace std;

int main()
{
    char input_buffer[10000 + 1]; // + 1 for the last '\0'
    vector<int> a, b;

    cout << "Input a non-negative integer number (a): ";
    cin >> input_buffer;

    // begin repeated codes, parse the input (a)
    /*
    for (int i = 0; input_buffer[i] != '\0'; i++)
    {
        if (!isdigit(input_buffer[i]))
        {
            cout << "Invalid input: " << input_buffer << endl;
            return 0;
        }
        else
        {
            int digit = input_buffer[i] - '0';
            a.push_back(digit);
        }
    }

    reverse(a.begin(), a.end());

    // remove leading zeros
    for (int i = a.size() - 1; i >= 1; i--)
    {
        if (a[i] == 0)
        {
            a.pop_back();
        }
        else
        {
            break;
        }
    }
    */
    // end repeated codes, parse the input (a)
    a = parse_big_number(input_buffer);

    // begin repeated codes, clean up the input buffer
    /*
    for (int i = 0; i < (10000 + 1); i++)
    {
        input_buffer[i] = '\0';
    }
    */
    // end repeated codes, clean up the input buffer
    clean_up_input_buffer(input_buffer);

    cout << "(a) = ";
    // begin repeated codes, print the input (a)
    /*
    for (int i = a.size() - 1; i >= 0; i--)
    {
        cout << a[i];
    }
    cout << endl;
    */
    // end repeated codes, print the input (a)
    print_big_number(a);

    cout << "Input a non-negative integer number (b): ";
    cin >> input_buffer;

    // begin repeated codes, parse the input (b)
    /*
    for (int i = 0; input_buffer[i] != '\0'; i++)
    {
        if (!isdigit(input_buffer[i]))
        {
            cout << "Invalid input: " << input_buffer << endl;
            return 0;
        }
        else
        {
            int digit = input_buffer[i] - '0';
            b.push_back(digit);
        }
    }

    reverse(b.begin(), b.end());

    // remove leading zeros
    for (int i = b.size() - 1; i >= 1; i--)
    {
        if (b[i] == 0)
        {
            b.pop_back();
        }
        else
        {
            break;
        }
    }
    */
    // end repeated codes, parse the input (b)
    b = parse_big_number(input_buffer);

    // begin repeated codes, clean up the input buffer
    /*
    for (int i = 0; i < (10000 + 1); i++)
    {
        input_buffer[i] = '\0';
    }
    */
    // end repeated codes, clean up the input buffer
    clean_up_input_buffer(input_buffer);

    cout << "(b) = ";
    // begin repeated codes, print the input (b)
    /*
    for (int i = b.size() - 1; i >= 0; i--)
    {
        cout << b[i];
    }
    cout << endl;
    */
    // end repeated codes, print the input (b)
    print_big_number(b);

    return 0;
}
```

### Result

請參考 [Lecture 10: Function & Reference (1) - Function example](./lecture_10.html#function-example)

## Multiple C++ source files & Prebuilt functions

在 function 較多的情況下，我們可以將 function 分開到不同的 source file 中，這樣可以減少 compile time，並且可以減少程式碼的複雜度。

常見的方法是以功能為單位，並且每個功能都有自己的 source file (or header file)，例如：

`big_number.h`

``` c++
#include <iostream>
#include <cctype>    // isdigit()
#include <algorithm> // reverse()
#include <vector>    // vector<int>()

using namespace std;

vector<int> parse_big_number(const char input_buffer[])
{
    vector<int> big_number;
    for (int i = 0; input_buffer[i] != '\0'; i++)
    {
        if (!isdigit(input_buffer[i]))
        {
            cout << "Invalid input: " << input_buffer << endl;
            return vector<int>();
        }
        else
        {
            int digit = input_buffer[i] - '0';
            big_number.push_back(digit);
        }
    }

    reverse(big_number.begin(), big_number.end());

    // remove leading zeros
    for (int i = big_number.size() - 1; i >= 1; i--)
    {
        if (big_number[i] == 0)
        {
            big_number.pop_back();
        }
        else
        {
            break;
        }
    }

    return big_number;
}

void print_big_number(const vector<int> &big_number)
{
    for (int i = big_number.size() - 1; i >= 0; i--)
    {
        cout << big_number[i];
    }
    cout << endl;
}
```

`input_buffer.h`

``` c++
void clean_up_input_buffer(char input_buffer[])
{
    for (int i = 0; input_buffer[i] != '\0'; i++)
    {
        input_buffer[i] = '\0';
    }
}
```

`main.cpp`

``` c++
#include <iostream>
#include <vector>    // vector<int>()
#include "big_number.h"
#include "input_buffer.h"

using namespace std;

int main()
{
    char input_buffer[10000 + 1]; // + 1 for the last '\0'
    vector<int> a, b;

    cout << "Input a non-negative integer number (a): ";
    cin >> input_buffer;

    a = parse_big_number(input_buffer);

    clean_up_input_buffer(input_buffer);

    cout << "(a) = ";
    print_big_number(a);

    cout << "Input a non-negative integer number (b): ";
    cin >> input_buffer;

    b = parse_big_number(input_buffer);

    clean_up_input_buffer(input_buffer);

    cout << "(b) = ";
    print_big_number(b);

    return 0;
}
```

這個例子中就是將多個 function 分配到不同的 header file 中，並且在 main.cpp 中引用這些 header file 來使用這些 function。
這種方法的可以方便的減少程式碼的複雜度，但是並不能減少 compile time。

### Multiple C++ source files and a header file

若需要減少 compile time，可以將 function 分開到不同的 source file 中，並且依據 source file 建立各自的 header file，並在該 header file 中宣告 function prototype。
最後在 main.cpp 中引用這些 header file 來使用這些 function。

Example:

#### `big_number.h`

``` c++
#ifndef BIG_NUMBER_H
#define BIG_NUMBER_H
#include <vector>    // vector<int>()

using namespace std;

vector<int> parse_big_number(const char input_buffer[]);
void print_big_number(const vector<int> &big_number);

#endif
```

#### `big_number.cpp`

``` c++
#include <iostream>
#include <cctype>    // isdigit()
#include <algorithm> // reverse()
#include <vector>    // vector<int>()

#include "big_number.h"

using namespace std;

vector<int> parse_big_number(const char input_buffer[])
{
    vector<int> big_number;
    for (int i = 0; input_buffer[i] != '\0'; i++)
    {
        if (!isdigit(input_buffer[i]))
        {
            cout << "Invalid input: " << input_buffer << endl;
            return vector<int>();
        }
        else
        {
            int digit = input_buffer[i] - '0';
            big_number.push_back(digit);
        }
    }

    reverse(big_number.begin(), big_number.end());

    // remove leading zeros
    for (int i = big_number.size() - 1; i >= 1; i--)
    {
        if (big_number[i] == 0)
        {
            big_number.pop_back();
        }
        else
        {
            break;
        }
    }

    return big_number;
}

void print_big_number(const vector<int> &big_number)
{
    for (int i = big_number.size() - 1; i >= 0; i--)
    {
        cout << big_number[i];
    }
    cout << endl;
}
```

#### `input_buffer.h`

``` c++
#ifndef INPUT_BUFFER_H
#define INPUT_BUFFER_H

void clean_up_input_buffer(char input_buffer[]);

#endif
```

#### `input_buffer.cpp`

``` c++
#include "input_buffer.h"

void clean_up_input_buffer(char input_buffer[])
{
    for (int i = 0; input_buffer[i] != '\0'; i++)
    {
        input_buffer[i] = '\0';
    }
}
```

#### `main.cpp`

``` c++
#include <iostream>
#include <vector>    // vector<int>()
#include "big_number.h"
#include "input_buffer.h"

using namespace std;

int main()
{
    char input_buffer[10000 + 1]; // + 1 for the last '\0'
    vector<int> a, b;

    cout << "Input a non-negative integer number (a): ";
    cin >> input_buffer;

    a = parse_big_number(input_buffer);

    clean_up_input_buffer(input_buffer);

    cout << "(a) = ";
    print_big_number(a);

    cout << "Input a non-negative integer number (b): ";
    cin >> input_buffer;

    b = parse_big_number(input_buffer);

    clean_up_input_buffer(input_buffer);

    cout << "(b) = ";
    print_big_number(b);

    return 0;
}
```

### Compile Multiple C++ source files and link them together

如何將多個 c++ source 檔案 compile 並且 link 一起，並且可以避免 compile time？

1. 將所有 c++ source 檔案 compile 成 `.o` 檔案

``` console
$ g++ -c big_number.cpp input_buffer.cpp⏎
$ ls⏎
big_number.cpp   big_number.h     big_number.o     input_buffer.cpp 
input_buffer.h   input_buffer.o   main.cpp         test.cpp
```

2. compile `main.cpp` 時，將所有 `.o` 檔案 link 起來

``` console
$ g++ main.cpp big_number.o input_buffer.o⏎
$ ls⏎
a.out            big_number.h     input_buffer.cpp input_buffer.o   test.cpp
big_number.cpp   big_number.o     input_buffer.h   main.cpp
$ ./a.out⏎
Input a non-negative integer number (a): 12345⏎
(a) = 12345
Input a non-negative integer number (b): 54321⏎
(b) = 54321
$ 
```

3. 若僅修改 `main.cpp` 時，只要再 compile `main.cpp` 就可以了

``` console
# modify main.cpp
$ g++ main.cpp big_number.o input_buffer.o⏎
$ ./a.out⏎
Input a non-negative integer number (a): 12345⏎
(a) = 12345
Input a non-negative integer number (b): 54321⏎
(b) = 54321
$ 
```

4. 若僅修改 `big_number.cpp` 或 `input_buffer.cpp` 時，需要再 compile 相對應的 `.cpp`，並且再次 compile `main.cpp` 就可以了 

``` console
# modify big_number.cpp
$ g++ -c big_number.cpp⏎
$ g++ main.cpp big_number.o input_buffer.o⏎
$ ./a.out⏎
Input a non-negative integer number (a): 12345⏎
(a) = 12345
Input a non-negative integer number (b): 54321⏎
(b) = 54321
$ 
```

## Function Overloading

如果有多個 function 名稱相同，但是參數不同，這時候就會有 function overloading。
此時同名的 function 彼此視為不同的 function，而且可以有不同的程式碼。

Example:

``` c++
void print_big_number(const vector<int> &big_number)
{
    for (int i = big_number.size() - 1; i >= 0; i--)
    {
        cout << big_number[i];
    }
    cout << endl;
}
void print_big_number(const vector<int> &big_number, int base)
{
    if(base > 10)
    {
        cout << "Base must be less than or equal to 10." << endl;
        return;
    }
    else if(base < 2)
    {
        cout << "Base must be greater than or equal to 2." << endl;
        return;
    }
    else if(base == 10)
    {
        print_big_number(big_number);
        return;
    }
    else
    {
        vector<int> big_number_in_base(big_number); // copy big_number
        for (int i = 0; i < big_number_in_base.size(); i++)
        {
            if(big_number_in_base[i] >= base)
            {
                if(i == big_number_in_base.size() - 1)
                {
                    big_number_in_base.push_back(big_number_in_base[i] / base);
                }
                else
                {
                    big_number_in_base[i + 1] += big_number_in_base[i] / base;
                }
                big_number_in_base[i] = big_number_in_base[i] % base;
            }
        }
        print_big_number(big_number_in_base);
    }
}
```

## Variable Scope & Lifetime

Reference: [Scope of Variables in C++](https://www.geeksforgeeks.org/scope-of-variables-in-c/)

### Local Variable

Wrong example: use others' local variable

``` c++
// CPP program to illustrate
// usage of local variables
#include <iostream>
using namespace std;

void func()
{
    // this variable is local to the
    // function func() and cannot be
    // accessed outside this function
    int age = 18;
}

int main()
{
    cout << "Age is: " << age;

    return 0;
}
```

Correct example: use owned local variable

``` c++
// CPP program to illustrate
// usage of local variables
#include <iostream>
using namespace std;

void func()
{
    // this variable is local to the
    // function func() and cannot be
    // accessed outside this function
    int age = 18;
    cout << age;
}

int main()
{
    cout << "Age is: ";
    func();

    return 0;
}
```

### Global Variable

``` c++
// CPP program to illustrate
// usage of global variables
#include <iostream>
using namespace std;

// global variable
int global = 5;

// global variable accessed from
// within a function
void display()
{
    cout << global << endl;
}

// main function
int main()
{
    display();

    // changing value of global
    // variable from main function
    global = 10;
    display();
}
```

### Variable Lifetime

``` c++
// CPP program to illustrate
// scope of local variables
// and global variables together
#include <iostream>
using namespace std;

// global variable
int global = 5;

// main function
int main()
{
    // local variable with same
    // name as that of global variable

    int global = 2;
    cout << global << endl;
}
```

To access global variable with same name as that of local variable, you need to use `::` to access global variable.

``` c++
// C++ program to show that we can access a global
// variable using scope resolution operator :: when
// there is a local variable with same name
#include <iostream>
using namespace std;

// Global x
int x = 0;

int main()
{
    // Local x
    int x = 10;
    cout << "Value of global x is " << ::x;
    cout << "\nValue of local x is " << x;
    return 0;
}
```

## Namespace

如果有多個 class 同名，需要使用 namespace 才能避免名稱衝突。

``` c++
#include <iostream>

namespace a
{
    void print_char()
    {
        std::cout << "a" << std::endl;
    }
}

namespace b
{
    void print_char()
    {
        std::cout << "b" << std::endl;
    }
}

int main()
{
    a::print_char();
    b::print_char();
    return 0;
}
```