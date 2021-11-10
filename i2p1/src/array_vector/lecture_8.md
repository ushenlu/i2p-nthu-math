# Lecture 8: Array & String (3)

## `std::string`

`std::string` 是 C++ 提供的標準樣板函式庫 (Standard Template Library, STL)。
可以把這個想成更為方便使用的 **charactor array**。
支援動態調整大小及內建字串內 (in-place) 的調整。

Ref: [std::string class in C++ - GeeksforGeeks](https://www.geeksforgeeks.org/stdstring-class-in-c/)

``` c++
// C++ code to demonstrate the working of
// getline(), push_back() and pop_back()
#include<iostream>
#include<string> // for string class
using namespace std;
int main()
{
	// Declaring string
	string str;

	// Taking string input using getline()
	// "geeksforgeek" in giving output
	getline(cin,str);

	// Displaying string
	cout << "The initial string is : ";
	cout << str << endl;

	// Using push_back() to insert a character
	// at end
	// pushes 's' in this case
	str.push_back('s');

	// Displaying string
	cout << "The string after push_back operation is : ";
	cout << str << endl;

	// Using pop_back() to delete a character
	// from end
	// pops 's' in this case
	str.pop_back();

	// Displaying string
	cout << "The string after pop_back operation is : ";
	cout << str << endl;

	return 0;

}
```

### `std::getline` & `std::cin`

Ref: [std::getline - cppreference.com](https://en.cppreference.com/w/cpp/string/basic_string/getline)

> `getline` reads characters from an input stream and places them into a string:
> 
> 2. Same as `getline(input, str, input.widen('\n'))`, that is, the default delimiter is the endline character.

## `std::string` manipulations

Ref: [std::string class in C++ - GeeksforGeeks](https://www.geeksforgeeks.org/stdstring-class-in-c/)

``` c++
// C++ code to demonstrate the working of
// copy() and swap()
#include<iostream>
#include<string> // for string class
using namespace std;
int main()
{
	// Initializing 1st string
	string str1 = "geeksforgeeks is for geeks";

	// Declaring 2nd string
	string str2 = "geeksforgeeks rocks";

	// Declaring character array
	char ch[80];

	// using copy() to copy elements into char array
	// copies "geeksforgeeks"
	str1.copy(ch,13,0);

	// Displaying char array
	cout << "The new copied character array is : ";
	cout << ch << endl << endl;

	// Displaying strings before swapping
	cout << "The 1st string before swapping is : ";
	cout << str1 << endl;
	cout << "The 2nd string before swapping is : ";
	cout << str2 << endl;

	// using swap() to swap string content
	str1.swap(str2);

	// Displaying strings after swapping
	cout << "The 1st string after swapping is : ";
	cout << str1 << endl;
	cout << "The 2nd string after swapping is : ";
	cout << str2 << endl;

	return 0;

}
```

## `std::stringstream`

Ref: [Converting Strings to Numbers in C/C++ - GeeksforGeeks](https://www.geeksforgeeks.org/converting-strings-numbers-cc/)

``` c++
// A program to demonstrate the use of stringstream
#include <iostream>
#include <sstream>
using namespace std;

int main()
{
	string s = "12345";

	// object from the class stringstream
	stringstream geek(s);

	// The object has the value 12345 and stream
	// it to the integer x
	int x = 0;
	geek >> x;

	// Now the variable x holds the value 12345
	cout << "Value of x : " << x;

	return 0;
}
```

## example: a simple command line integer calculator

``` c++
#include <iostream>
#include <sstream>
#include <string>
#include <vector>

using namespace std;

int main()
{
    string input_buffer;
    vector<long> operands;
    vector<string> operators;

    cout << "Input a forumla: ";
    std::getline(cin, input_buffer);

    stringstream terms_extractor(input_buffer);

    for (string term; (terms_extractor >> term);)
    {
        if (term == "+" || term == "-" || term == "*" || term == "/")
        {
            operators.push_back(term);
        }
        else
        {
            long operand = stol(term);
            operands.push_back(operand);
        }
    }

    cout << "Operands: ";
    for (int i = 0; i < operands.size(); i++)
    {
        cout << operands[i] << " ";
    }
    cout << endl;

    cout << "Operators: ";
    for (int i = 0; i < operators.size(); i++)
    {
        cout << operators[i] << " ";
    }
    cout << endl;

    cout << "Result: ";
    for (int i = 0; i < operators.size(); i++)
    {
        if (operators[i] == "+")
        {
            cout << operands[i] + operands[i + 1] << " ";
            operands[i + 1] = operands[i] + operands[i + 1];
        }
        else if (operators[i] == "-")
        {
            cout << operands[i] - operands[i + 1] << " ";
            operands[i + 1] = operands[i] - operands[i + 1];
        }
        else if (operators[i] == "*")
        {
            cout << operands[i] * operands[i + 1] << " ";
            operands[i + 1] = operands[i] * operands[i + 1];
        }
        else if (operators[i] == "/")
        {
            cout << operands[i] / operands[i + 1] << " ";
            operands[i + 1] = operands[i] / operands[i + 1];
        }
    }
    cout << endl;

    return 0;
}
```

example:

``` console
$ ./a.out⏎
Input a forumla: 1+2*3⏎
Operands: 1 2 3
Operators: + *
Result: 3 9
```