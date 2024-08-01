# c语言的一些关键字



---

## static

static关键字有几个不同的用途，取决于它在代码中的使用位置。



a. 在函数内部：

当在函数内部声明变量时，static会使该变量保持其值在函数调用之间不会丢失。换句话说，静态局部变量在函数调用结束后仍然保留其值，而不是在每次函数调用时重新初始化。

```c
#include <stdio.h>

void myFunction() {
    static int count = 0; // static 局部变量
    count++;
    printf("count = %d\n", count);
}

int main() {
    myFunction(); // count = 1
    myFunction(); // count = 2
    myFunction(); // count = 3
    return 0;
}
```



b. 在函数外部或全局声明：

当在函数外部声明变量或函数时，static会限制其作用域仅在当前文件中。这对于实现文件内的封装非常有用。

```c
static int count = 0; // 仅在当前文件中可见

static void myFunction() {
    printf("This is a static function\n");
}

int main() {
    myFunction();
    return 0;
}
```



---

## const

const关键字用于声明常量，即变量的值一旦初始化后就不能再修改。它可以用于定义常量值、常量指针等。



a. 常量变量：

```c
const int max = 100;
max = 200; // 错误，max是常量
```



b. 常量指针：

```c
int value = 10;
int *const ptr = &value; // ptr 是常量指针，指向的地址不能改变，但值可以改变
*ptr = 20; // 正确
int anotherValue = 30;
ptr = &anotherValue; // 错误，ptr是常量指针
```



c. 指向常量的指针

```c
const int value = 10;
const int *ptr = &value; // ptr 指向常量，值不能改变，但指针可以改变
*ptr = 20; // 错误，不能改变常量的值
int anotherValue = 30;
ptr = &anotherValue; // 正确
```



---

## volatile

volatile关键字告诉编译器，不要对标记为volatile的变量进行优化。这通常用于访问硬件寄存器或在多线程编程中访问变量，保证每次读取或写入都真正访问该变量的内存地址，而不是使用寄存器中的缓存值。



a. 硬件寄存器：

```c
volatile int *hardwareRegister = (int *)0x1234; // 假设这是一个硬件寄存器地址
*hardwareRegister = 0xFF; // 每次访问都从硬件寄存器读取或写入
```



b. 多线程编程：

```c
volatile int flag = 0;

void threadFunction() {
    while (!flag) {
        // 等待flag改变
    }
    // 继续执行
}
```



---

## extern

用于声明变量或函数是定义在另一个文件中的，或者在当前文件中但稍后才会定义。它通常用于在多个文件之间共享全局变量或函数。



a. 声明全局变量

假设有两个文件：file1.c和file2.c。我们希望在file2.c中修改file1.c中的全局变量。

```c
// file1.c

#include <stdio.h>

// 函数声明
void printGlobalVariable();
void modifyGlobalVariable();

// 定义全局变量
int globalVariable = 42;

void printGlobalVariable() {
    printf("Global variable: %d\n", globalVariable);
}

int main() {
    printGlobalVariable();
    modifyGlobalVariable();
    printGlobalVariable();
    return 0;
}
```

```c
// file2.c

#include <stdio.h>

// 声明外部全局变量
extern int globalVariable;

void modifyGlobalVariable() {
    globalVariable = 100;
}
```



b. 声明函数

假设我们有一个文件file1.c定义了一个函数，而我们希望在另一个文件file2.c中调用该函数。

```c
// file1.c

#include <stdio.h>

// 声明外部函数
extern void sayHello();

int main() {
    sayHello(); // 调用 file2.c 中的函数
    return 0;
}
```

```c
// file2.c

#include <stdio.h>

void sayHello() {
    printf("Hello from file2.c!\n");
}
```



---

## register

建议编译器将变量存储在寄存器中，以提高访问速度。现代编译器通常会自动优化，因此这个关键字使用较少。

```c
void exampleFunction() {
    register int counter;
    for (counter = 0; counter < 10; counter++) {
        printf("%d\n", counter);
    }
}
```



---

## typedef

为现有数据类型定义新的类型名。

```c
typedef unsigned long ulong;
ulong largeNumber = 123456789;
```



---

## inline

提示编译器将函数体插入到每个函数调用中，以减少函数调用的开销。

```c
inline int add(int a, int b) {
    return a + b;
}
```



---

## restrict (C99引入)

用于指针，告诉编译器该指针是唯一访问目标对象的方式，有助于优化。

```c
void updateValues(int *restrict ptr1, int *restrict ptr2) {
    *ptr1 += 5;
    *ptr2 += 10;
}
```



---

## _Atomic (C11引入)

用于声明原子类型变量，保证对变量的读写操作是原子的，通常用于多线程编程。

```c
_Atomic int atomicCounter = 0;
```



---
