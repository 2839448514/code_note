# getAsyncKeyState 函数 (winuser.h)
确定调用函数时键是向上还是向下，以及上次调用 GetAsyncKeyState 后是否按下了该键。
## 语法
```C++
SHORT GetAsyncKeyState(
  [in] int vKey
);
```
## 参数
- **`[in] vKey`**：虚拟密钥代码。 有关详细信息，请参阅 [[虚拟密钥代码]]。可以使用左右区分常量来指定某些键。 有关详细信息，请参阅备注部分。
## 返回值
类型： **SHORT**

如果函数成功，则返回值指定自上次调用 **GetAsyncKeyState** 以来是否按下了键，以及键当前是打开还是关闭。 如果设置了最有效位，则键关闭，如果设置了最小有效位，则上一次调用 **GetAsyncKeyState** 后按下了键。 但是，不应依赖于此最后一种行为;有关详细信息，请参阅备注。

对于以下情况，返回值为零：
- 当前桌面不是活动桌面
- 前台线程属于另一个进程，桌面不允许挂钩或日志记录。
## 注解

**GetAsyncKeyState** 函数适用于鼠标按钮。 但是，它会检查物理鼠标按钮的状态，而不是物理按钮映射到的逻辑鼠标按钮。 例如，调用 **GetAsyncKeyState** (VK_LBUTTON) 始终返回左物理鼠标按钮的状态，无论它是映射到左逻辑鼠标按钮还是右逻辑鼠标按钮。 可以通过调用 `GetSystemMetrics(SM_SWAPBUTTON)`来确定系统的物理鼠标按钮到逻辑鼠标按钮的当前映射。如果已交换鼠标按钮，则返回 TRUE。

尽管返回值的最小有效位指示自上次查询以来是否已按下键，但由于 Windows 的抢占性多任务性质，另一个应用程序可以调用 **GetAsyncKeyState** 并接收“最近按下的”位，而不是应用程序。 严格保留返回值中最小有效位的行为，以便与 16 位 Windows 应用程序兼容， (这些应用程序是非抢占) 且不应依赖的。

可以使用虚拟键代码常量 **VK_SHIFT**、 **VK_CONTROL**和 **VK_MENU** 作为 _vKey_ 参数的值。 这会提供 SHIFT、Ctrl 或 ALT 键的状态，而不区分左键和右键。

可以使用以下虚拟键代码常量作为 _vKey_ 的值来区分这些键的左实例和右实例。

|代码|含义|
|---|---|
|**VK_LSHIFT**|左移键。|
|**VK_RSHIFT**|右移键。|
|**VK_LCONTROL**|左控制键。|
|**VK_RCONTROL**|右侧控制键。|
|**VK_LMENU**|左侧菜单键。|
|**VK_RMENU**|右侧菜单键。|

这些左右区分常量仅在调用 [GetKeyboardState、SetKeyboardState](https://learn.microsoft.com/zh-cn/windows/desktop/api/winuser/nf-winuser-getkeyboardstate)、**GetAsyncKeyState**、[GetKeyState](https://learn.microsoft.com/zh-cn/windows/desktop/api/winuser/nf-winuser-getkeystate) 和 [MapVirtualKey](https://learn.microsoft.com/zh-cn/windows/desktop/api/winuser/nf-winuser-mapvirtualkeya) 函数时可用。[](https://learn.microsoft.com/zh-cn/windows/desktop/api/winuser/nf-winuser-setkeyboardstate)

## 示例代码

```C++
while (GetMessage(&msg, nullptr, 0, 0))
{
    if (!TranslateAccelerator(msg.hwnd, hAccelTable, &msg))
    {
        TranslateMessage(&msg);
        DispatchMessage(&msg);
    }

    switch (msg.message)
    {
    case WM_KEYDOWN:
        if ((GetAsyncKeyState(VK_ESCAPE) & 0x01) && bRunning)
        {
            Stop();
        }
        break;
    }
}
```
