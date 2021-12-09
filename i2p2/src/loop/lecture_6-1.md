# Lecture 6-1: Loop Statement (2)

## guess number

``` c++
#include <iostream>
#include <cstdlib> // for rand() function

int main() 
{
    int input = 0;
    int type_counts = 3; // check input three times
    unsigned int number = rand() % 10; // get a random number from 0 to 9

    int i = 0; // define index variable

    while (i < type_counts) // while loop, check before execute the follows
    {
        std::cout << "Input a integer (" << i << '/' << type_counts << "): ";
        std::cin >> input;

        if(input < number)
        {
            std::cout << "The input is smaller than the number" << std::endl;
        }
        else if(input == number)
        {
            std::cout << "You guessed it!" << std::endl;
            return 0;
        }
        else // input > number
        {
            std::cout << "The input is larger than the number" << std::endl;
        }
        i++; // increase index variable, check after break & continue
    }
    std::cout << "The number is " << number << std::endl;
}
```

## Fibonacci number

$$ \begin{align} F_0 &= 0 \\\\
F_1 &= 1 \\\\
F_n &= F_{n-1} + F_{n-2}, n \ge 2 \end{align}$$

Modified from [Nth-Fibonacci/Approach_3_O(n)_Time_&_O(1)_Space.cpp at main · iamrajiv/Nth-Fibonacci (github.com)](https://github.com/iamrajiv/Nth-Fibonacci/blob/main/C%2B%2B/Approach_3_O(n)_Time_%26_O(1)_Space.cpp)

``` c++
#include <iostream>

int main()
{
    int current = 1, previous = 0;
    int counter = 2, n = 0;
    std::cout << "fib number: ";
    std::cin >> n;
    while (counter <= n)
    {
        int nextFib = previous + current;
        previous = current;
        current = nextFib;
        counter++;
    }
    std::cout << (n > 0 ? current : previous) << std::endl;
    return 0;
}
```

## Long Division

``` c++
#include <iostream>
#include <cmath> // for log10() & pow()

int main()
{
    unsigned int N = 0, D = 0;

    std::cout << "Dividend: ";
    std::cin >> N;
    std::cout << "Divisor: ";
    std::cin >> D;

    unsigned int R = N, Q = 0;
    unsigned int N_digits = (N == 0) ? 1 : (log10(N) + 1);
    unsigned int D_digits = (D == 0) ? 1 : (log10(D) + 1);
    unsigned int D_shifted = D * pow(10, N_digits - D_digits);

    for (int i = N_digits; i >= D_digits; i--)
    {
        Q *= 10;
        while (D_shifted <= R)
        {
            R = R - D_shifted;
            Q++;
        }
        D_shifted /= 10;
    }

    std::cout << N << " / " << D << " = " << Q << " ... " << R << std::endl;
    return 0;
}
```

## check prime

Modified from [A C++ program to check whether given number is prime or not. (github.com)](https://gist.github.com/nalin-adh/a95f629bb5c2cdee5c91)

``` c++
#include <iostream>

int main()
{
    int n;
    bool flag = 0;

    std::cout << "Enter a number to check if prime or not : ";
    std::cin >> n;

    for (int i = 2; i <= n / 2; i++)
    {
        if (n % i == 0)
        {
            flag = 1;
            break;
        }
    }
    if (flag == 0)
    {
        std::cout << "\nThe number " << n << " is a prime number." << std::endl;
    }
    else
    {
        std::cout << "\nThe number " << n << " is not a prime number." << std::endl;
    }
    return (0);
}
```

Reference:
* [htchen/i2p-nthu by 陳煥宗老師](https://github.com/htchen/i2p-nthu/tree/master/%E7%A8%8B%E5%BC%8F%E8%A8%AD%E8%A8%88%E4%B8%80/Introduction%20to%20programming)
* [CNOCycle/cpp_tutorial by E. Chen](https://github.com/CNOCycle/cpp_tutorial)