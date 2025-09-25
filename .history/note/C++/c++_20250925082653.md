# C++

## C++基本语法

```c++
#include <iostream>
using namespace std;

int main() {
    cout << "Hello World!" << endl;
    return 0;
}
```

## 基本数据类型

- 整型：`int`、`short`、`long`、`long long`
- 浮点型：`float`、`double`
- 字符串型：`string`
- 宽字符型：`wchar_t`  (`typedef short int wchar_t`)
- 字符型：`char`
- 布尔型：`bool`
- 空类型：`void`

## 类型修饰符

- `signed`：有符号
- `unsigned`：无符号
- `short`：短整型
- `long`：长整型
- `const`：常量
- `volatile`：易失性
- `extern`：外部变量
- `auto`：自动
- `register`：寄存器
- `static`：静态

## c++ 11新增类型和示例

- `nullptr`：空指针`nullptr_t`
- `auto`：自动类型推导`auto x = 10;`
- `decltype`：类型推导`decltype(x) y = 10;`
- `constexpr`：常量表达式`constexpr int x = 10;`
- `noexcept`：异常说明`noexcept(f())`
- `alignof`：对齐方式`alignof(int)`
- `sizeof`：类型大小`sizeof(int)`
- `typeid`：类型信息`typeid(int)`
- `static_assert`：静态断言`static_assert(sizeof(int) == 4, "int is not 4 bytes");`
- `thread_local`：线程局部存储`thread_local int x = 10;`
- `nullptr_t`：空指针类型`nullptr_t x = nullptr;`

## 派送数据类型
```c++
- 数组：int arr[10];
- 结构体：struct Person { int age; string name; };
- 枚举：enum Color { RED, GREEN, BLUE };
- 联合体：union Data { int i; float f; char str[20]; };
- 类：`class Person { public: int age; string name; };`
- 指针：`int *p;`
- 引用：`int &r = x;`
- 函数指针：`int (*p)(int, int);`
- 函数对象：`class Add { public: int operator()(int x, int y) { return x + y; } };`
- lambda表达式：`auto add = [](int x, int y) { return x + y; };`
- 模板：`template <typename T> class Vector { ... };`
- 右值引用：`int &&r = 10;`
- 右值引用折叠：`int &&r = std::move(x);`
- 右值引用绑定：`int &&r = std::forward<int &&>(x);`
- 完美转发：`template <typename T> void f(T &&t) { ... }`
- 类型萃取：`std::is_same<int, int>::value`
```