---
tags:
  - win32
---
# INPUT 结构体

```cpp
typedef struct tagINPUT {
    DWORD type;
    union {
        MOUSEINPUT mi;
        KEYBDINPUT ki;
        HARDWAREINPUT hi;
    } DUMMYUNIONNAME;
} INPUT, *PINPUT;
```

### **成员：**

- **type**：指定输入事件的类型。可以是以下之一：
  - `INPUT_MOUSE`：表示鼠标事件。
  - `INPUT_KEYBOARD`：表示键盘事件。
  - `INPUT_HARDWARE`：表示硬件事件。
- **DUMMYUNIONNAME**：联合体，包含以下三个结构体之一：
  - **[[MOUSEINPUT]] mi**：表示鼠标事件。
  - **[[KEYBDINPUT]] ki**：表示键盘事件。
  - **[[HARDWAREINPUT]] hi**：表示硬件事件。

### 示例代码：

```C++
#include <windows.h>
#include <iostream>
void simulateMouseClick(int x, int y) {
    INPUT input = {0};
    input.type = INPUT_MOUSE;
    input.mi.dx = x * (65536 / GetSystemMetrics(SM_CXSCREEN)); // 转换为绝对坐标
    input.mi.dy = y * (65536 / GetSystemMetrics(SM_CYSCREEN)); // 转换为绝对坐标
    input.mi.dwFlags = MOUSEEVENTF_MOVE | MOUSEEVENTF_ABSOLUTE | MOUSEEVENTF_LEFTDOWN | MOUSEEVENTF_LEFTUP;
    SendInput(1, &input, sizeof(INPUT));
}
int main() {
    // 模拟点击屏幕坐标 (100, 100)
    simulateMouseClick(100, 100);
    return 0;
}
