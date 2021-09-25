# Lab 1-1: Hello World (1)

Helloworld 的範例程式碼

```c++
#include <iostream>

int main(void){
    std::cout << "Hello world!" << std::endl;
    return 0;
}
```

## 互動式顯示 `Hello world! <your student id>` (50%)

* 輸入：學生學號
* 輸出：Hello world 文字及學生學號
* 檔名：lab1_1_<學號>.cpp (e.g. lab1_1_106062802.cpp)

程式需提示使用者輸入學號，程式需輸出 `Hello world!` 以及使用者輸入的學號。

```console
$ ./a.out
Your student ID: <your student id>
Hello world! student <your student id>

$ ./a.out
Your student ID: 106062802
Hello world! student 106062802
```
