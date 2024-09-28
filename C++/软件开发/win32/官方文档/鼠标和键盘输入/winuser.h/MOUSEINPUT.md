---
tags:
  - win32
---
# MOUSEINPUT结构体

### **语法：**

```C++
typedef struct tagMOUSEINPUT {
    LONG      dx;
    LONG      dy;
    DWORD     mouseData;
    DWORD     dwFlags;
    DWORD     time;
    ULONG_PTR dwExtraInfo;
} [[MOUSEINPUT]], *PMOUSEINPUT, *LPMOUSEINPUT;
```

### **成员：**

- **dx**：鼠标的绝对位置，或自上次生成鼠标事件以来的运动量，具体取决于 **dwFlags** 成员的值。 绝对数据指定为鼠标的 x 坐标;相对数据指定为移动的像素数。
- **dy**：鼠标的绝对位置，或自上次生成鼠标事件以来的运动量，具体取决于 **dwFlags** 成员的值。 绝对数据指定为鼠标的 y 坐标;相对数据指定为移动的像素数。
- **mouseData**：如果 **dwFlags** 包含 **MOUSEEVENTF_WHEEL**，则 **mouseData** 指定滚轮移动量。 正值表示滚轮向前旋转（远离用户）；负值表示滚轮向后旋转（朝向用户）。 一键滚轮定义为 **WHEEL_DELTA**，即 120。
- **Windows Vista**：如果 _dwFlags_ 包含 **MOUSEEVENTF_HWHEEL**，则 _dwData_ 指定滚轮移动量。 正值表示滚轮向右旋转；负值表示滚轮向左旋转。 一键滚轮定义为 **WHEEL_DELTA**，即 120。如果 **dwFlags** 不包含 **MOUSEEVENTF_WHEEL**、 **MOUSEEVENTF_XDOWN**或 **MOUSEEVENTF_XUP**，则 **mouseData** 应为零。如果 **dwFlags** 包含 **MOUSEEVENTF_XDOWN** 或 **MOUSEEVENTF_XUP**，则 **mouseData** 指定按下或释放的 X 按钮。 此值可以是以下标志的任意组合。

| Value                    | 含义                 |
| ------------------------ | ------------------ |
| **XBUTTON1**  <br>0x0001 | 设置是否按下或释放第一个 X 按钮。 |
| **XBUTTON2**  <br>0x0002 | 设置是否按下或释放第二个 X 按钮。 |

- **dwFlags**：一组位标志，用于指定鼠标运动和按钮单击的各个方面。 此成员中的位可以是以下值的任意合理组合。指定鼠标按钮状态的位标志设置为指示状态的更改，而不是正在进行的条件。 例如，如果按下并按住鼠标左键，则会在首次按下左键时设置 **MOUSEEVENTF_LEFTDOWN** ，但不设置为后续动作。 同样， **仅在** 首次释放按钮时设置MOUSEEVENTF_LEFTUP。不能在 **dwFlags** 参数中同时指定 **MOUSEEVENTF_WHEEL** 标志和 **MOUSEEVENTF_XDOWN** 或 **MOUSEEVENTF_XUP** 标志，因为它们都需要使用 **mouseData** 字段。

| Value                                       | 含义                                                                                                                                              |
| ------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| **MOUSEEVENTF_MOVE**  <br>0x0001            | 发生了移动。                                                                                                                                          |
| **MOUSEEVENTF_LEFTDOWN**  <br>0x0002        | 按下了左侧按钮。                                                                                                                                        |
| **MOUSEEVENTF_LEFTUP**  <br>0x0004          | 左按钮已释放。                                                                                                                                         |
| **MOUSEEVENTF_RIGHTDOWN**  <br>0x0008       | 按下了向右按钮。                                                                                                                                        |
| **MOUSEEVENTF_RIGHTUP**  <br>0x0010         | 右侧按钮已松开。                                                                                                                                        |
| **MOUSEEVENTF_MIDDLEDOWN**  <br>0x0020      | 按下中间按钮。                                                                                                                                         |
| **MOUSEEVENTF_MIDDLEUP**  <br>0x0040        | 中间按钮已释放。                                                                                                                                        |
| **MOUSEEVENTF_XDOWN**  <br>0x0080           | 按下了 X 按钮。                                                                                                                                       |
| **MOUSEEVENTF_XUP**  <br>0x0100             | 已释放 X 按钮。                                                                                                                                       |
| **MOUSEEVENTF_WHEEL**  <br>0x0800           | 如果鼠标有滚轮，则滚轮已移动。 移动量在 **mouseData** 中指定。                                                                                                         |
| **MOUSEEVENTF_HWHEEL**  <br>0x1000          | 如果鼠标有滚轮，则方向盘是水平移动的。 移动量在 **mouseData** 中指定。  <br>**Windows XP/2000**：不支持此值。                                                                     |
| **MOUSEEVENTF_MOVE_NOCOALESCE**  <br>0x2000 | 不会合并WM_MOUSEMOVE消息。 默认行为是合并 **WM_MOUSEMOVE** 消息。  <br>**Windows XP/2000**：不支持此值。                                                                |
| **MOUSEEVENTF_VIRTUALDESK**  <br>0x4000     | 将坐标映射到整个桌面。 必须与 **MOUSEEVENTF_ABSOLUTE** 一起使用。                                                                                                  |
| **MOUSEEVENTF_ABSOLUTE**  <br>0x8000        | **dx** 和 **dy** 成员包含规范化的绝对坐标。 如果未设置标志， **dx**和 **dy** 包含相对数据 (自上次报告的位置) 更改。 无论哪种类型的鼠标或其他指针设备（如果有）连接到系统，都可以设置或不设置此标志。 有关相对鼠标运动的详细信息，请参阅以下“备注”部分。 |

- **time**：事件的时间戳（以毫秒为单位）。 如果此参数为 0，则系统将提供自己的时间戳。
- **dwExtraInfo**:与鼠标事件关联的附加值。 应用程序调用 GetMessageExtraInfo 以获取此额外信息。

### 示例代码

```C++
#include <Windows.h>
#include <iostream>
int main() {
    // 初始化输入结构体
    INPUT input = {0};
    // 设置输入事件类型为鼠标事件
    input.type = INPUT_MOUSE;
    // 模拟鼠标左键按下
    input.mi.dx = 0; // 相对于屏幕坐标的水平位置
    input.mi.dy = 0; // 相对于屏幕坐标的垂直位置
    input.mi.dwFlags = MOUSEEVENTF_LEFTDOWN; // 鼠标左键按下
    SendInput(1, &input, sizeof(INPUT));
    // 模拟鼠标左键释放
    input.mi.dwFlags = MOUSEEVENTF_LEFTUP; // 鼠标左键释放
    SendInput(1, &input, sizeof(INPUT));
    std::cout << "Mouse left click simulated." << std::endl;
    return 0;
}
```
