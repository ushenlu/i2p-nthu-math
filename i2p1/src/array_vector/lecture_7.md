# Lecture 7: Array & String (2)

## `std::vector`

`std::vector` 是 C++ 提供的標準樣板函式庫 (Standard Template Library, STL)。
可以把這個想成更為方便使用的 array 。
支援任何型態、動態調整大小及使用變數宣告大小。

Ref: [Vector in C++ STL - GeeksforGeeks](https://www.geeksforgeeks.org/vector-in-cpp-stl/)

``` c++
// C++ program to illustrate the
// iterators in vector
#include <iostream>
#include <vector>
#include <iterator>
  
int main()
{
    std::vector<int> g1;
  
    for (int i = 1; i <= 5; i++)
        g1.push_back(i);
  
    std::cout << "Output of begin and end: ";
    for (auto i = g1.begin(); i != g1.end(); ++i)
        std::cout << *i << " ";
  
    std::cout << "\nOutput of cbegin and cend: ";
    for (auto i = g1.cbegin(); i != g1.cend(); ++i)
        std::cout << *i << " ";
  
    std::cout << "\nOutput of rbegin and rend: ";
    for (auto ir = g1.rbegin(); ir != g1.rend(); ++ir)
        std::cout << *ir << " ";
  
    std::cout << "\nOutput of crbegin and crend : ";
    for (auto ir = g1.crbegin(); ir != g1.crend(); ++ir)
        std::cout << *ir << " ";
  
    return 0;
}
```

### define

``` c++
#include <vector>
  
int main()
{
    std::vector<int> g1;
}
```

`#include <vector>` 是使用 `std::vector` 要 include 的函式庫。
宣告變數時需要使用 `< >` 來指定 `std::vector` array 需要存放的型態，這邊以 `int` 為例，也可以使用其他型態，例如：`double`、`float`、`long` 等。
但是不建議用 `char` ，因為有 `std::string` 支援字串處理，使用起來比 `std::vector<char>` 方便。

### set/get element's value, `push()` & `pop()`

``` c++
// C++ program to illustrate the
// Modifiers in vector
#include <vector>
#include <iostream>
using namespace std; // shortcut of std::

int main()
{
    // Assign vector
    vector<int> v;

    // fill the array with 10 five times
    v.assign(5, 10);

    cout << "The vector elements are: ";
    for (int i = 0; i < v.size(); i++)
        cout << v[i] << " ";

    // inserts 15 to the last position
    v.push_back(15);
    int n = v.size();
    cout << "\nThe last element is: " << v[n - 1];

    // prints the vector
    cout << "\nThe vector elements are: ";
    for (int i = 0; i < v.size(); i++)
        cout << v[i] << " ";

    // removes last element
    v.pop_back();

    // inserts 5 at the beginning
    v.insert(v.begin(), 5);

    cout << "\nThe first element is: " << v[0];

    // prints the vector
    cout << "\nThe vector elements are: ";
    for (int i = 0; i < v.size(); i++)
        cout << v[i] << " ";

    // removes the first element
    v.erase(v.begin());

    cout << "\nThe first element is: " << v[0];

    // prints the vector
    cout << "\nThe vector elements are: ";
    for (int i = 0; i < v.size(); i++)
        cout << v[i] << " ";

    // inserts at the beginning
    v.emplace(v.begin(), 5);
    cout << "\nThe first element is: " << v[0];

    // prints the vector
    cout << "\nThe vector elements are: ";
    for (int i = 0; i < v.size(); i++)
        cout << v[i] << " ";

    // Inserts 20 at the end
    v.emplace_back(20);
    n = v.size();
    cout << "\nThe last element is: " << v[n - 1];

    // prints the vector
    cout << "\nThe vector elements are: ";
    for (int i = 0; i < v.size(); i++)
        cout << v[i] << " ";

    // change v[3] = 30
    v[3] = 30;

    // prints the vector
    cout << "\nThe vector elements are: ";
    for (int i = 0; i < v.size(); i++)
        cout << v[i] << " ";

    // erases the vector
    v.clear();
    cout << "\nVector size after erase(): " << v.size();

    // prints the vector
    cout << "\nThe vector elements are: ";
    for (int i = 0; i < v.size(); i++)
        cout << v[i] << " ";

    // two vector to perform swap
    vector<int> v1, v2;
    v1.push_back(1);
    v1.push_back(2);
    v2.push_back(3);
    v2.push_back(4);

    cout << "\n\nVector 1: ";
    for (int i = 0; i < v1.size(); i++)
        cout << v1[i] << " ";

    cout << "\nVector 2: ";
    for (int i = 0; i < v2.size(); i++)
        cout << v2[i] << " ";

    // Swaps v1 and v2
    v1.swap(v2);

    cout << "\nAfter Swap \nVector 1: ";
    for (int i = 0; i < v1.size(); i++)
        cout << v1[i] << " ";

    cout << "\nVector 2: ";
    for (int i = 0; i < v2.size(); i++)
        cout << v2[i] << " ";
}
```

### 2-d `std::vector`

``` c++
#include <iostream>
#include <iomanip>
#include <vector>

using namespace std;

int main()
{
    // define 2-d vector
    vector< vector<int> > table;

    // setup 2-d vector
    for (int i = 0; i < 9; i++) // index start from 0
    {   
        table.push_back(vector<int>()); // push a vector<int> without varaible name
        for (int j = 0; j < 9; j++) // index start from 0
        {
            table[i].push_back((i + 1) * (j + 1));
        }
    }

    // print 2-d vector
    for (int i = 0; i < table.size(); i++) // index start from 0
    {   
        for (int j = 0; j < table[i].size(); j++) // index start from 0
        {
            std::cout << (i+1) << '*' << (j+1) << " = "
                      << std::setw(2) << table[i][j] << ' '
                      << std::flush;
        }
        std::cout << std::endl;
    }
    return 0;
}
```

## `atoi`, `atol`

Ref: [Converting Strings to Numbers in C/C++ - GeeksforGeeks](https://www.geeksforgeeks.org/converting-strings-numbers-cc/)

``` c++
// For C++11 above
#include <cstdlib>
#include <iostream>
using namespace std;

int main()
{
    const char *str1 = "42";
    const char *str2 = "3.14159";
    const char *str3 = "31337 geek";

    int num1 = atoi(str1);
    int num2 = atoi(str2);
    int num3 = atoi(str3);

    cout << "atoi(\"" << str1 << "\") is " << num1 << '\n';
    cout << "atoi(\"" << str2 << "\") is " << num2 << '\n';
    cout << "atoi(\"" << str3 << "\") is " << num3 << '\n';

    return 0;
}
```

Ref: [Write your own atoi() - GeeksforGeeks](https://www.geeksforgeeks.org/write-your-own-atoi/)

``` c++
// Initialize result
int res = 0;

// Initialize sign as positive
int sign = 1;

// Initialize index of first digit
int i = 0;

// If number is negative,
// then update sign
if (str[0] == '-')
{
    sign = -1;

    // Also update index of first digit
    i++;
}

// Iterate through all digits
// and update the result
for (; str[i] != '\0'; ++i)
    res = res * 10 + str[i] - '0';

// Return result with sign
return sign * res;
```

## use a `std::vector` to save a number

``` c++
#include <iostream>
#include <cctype>    // isdigit()
#include <algorithm> // reverse()
#include <vector>    // vector<int>()

using namespace std;

int main()
{
    char input_buffer[10000 + 1]; // + 1 for the last '\0'
    vector<int> a;

    cout << "Input a non-negative integer number (a): ";
    cin >> input_buffer;

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

    // clean up input buffer
    for (int i = 0; i < (10000 + 1); i++)
    {
        input_buffer[i] = '\0';
    }
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

    cout << "(a) = ";
    for (int i = a.size() - 1; i >= 0; i--)
    {
        cout << a[i];
    }
    cout << endl;
}
```

Output:

``` console
$ ./a.out
Input a non-negative integer number (a): 000001234500000⏎
(a) = 1234500000
```

### check `isdigit`

Ref: [std::isdigit - cpprefrence.com](https://en.cppreference.com/w/cpp/string/byte/isdigit)

``` c++
    for (int i = 0; input_buffer[i] != '\0'; i++)
    {
        if (!isdigit(input_buffer[i]))
        {
            cout << "Invalid input: " << input_buffer << endl;
            return 0;
        }
```

### push digits & reverse

``` c++
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
    // check gdb
    reverse(a.begin(), a.end());
    // check gdb
```

#### `std::reverse`

Reference: [std::reverse - cppreference.com](https://en.cppreference.com/w/cpp/algorithm/reverse)

``` c++
#include <vector>
#include <iostream>
#include <algorithm>

int main()
{
    std::vector<int> v{1, 2, 3};
    std::reverse(v.begin(), v.end());
    for (int i = 0; i < v.size(); i++)
    {
        std::cout << v[i];
    }
    std::cout << '\n';
}
```

### clean up input buffer & remove leading zeros

``` c++
    // clean up input buffer
    for (int i = 0; i < (10000 + 1); i++)
    {
        input_buffer[i] = '\0';
    }
    // remove leading zeros
    for (int i = a.size() - 1; i >= 1; i--) // start from the most significant digit
    {
        if (a[i] == 0)
        {
            a.pop_back(); // remove the last element in vector,
                          // which is the most significant digit
        }
        else
        {
            break; // stop if process the most significant non-zero digit
        }
    }
```

### print the number

``` c++
    cout << "(a) = ";
    for (int i = a.size() - 1; i >= 0; i--)
    {
        cout << a[i];
    }
    cout << endl;
```

