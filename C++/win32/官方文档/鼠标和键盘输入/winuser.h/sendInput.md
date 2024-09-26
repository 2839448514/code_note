# sendInput 函数 (winuser.h)
**合成键击、鼠标动作和按钮单击。**
## 语法
```C++
UINT SendInput(
  [in] UINT    cInputs,
  [in] LPINPUT pInputs,
  [in] int     cbSize
);
```
## 参数
- **`[in] cInputs`**：_pInputs_ 数组中的结构数。
- **`[in] pInputs`**：[[INPUT]] 结构的数组。 每个结构都表示要插入键盘或鼠标输入流的事件。
- **`[in] cbSize`**：[[INPUT]] 结构的大小（以字节为单位）。 如果 _cbSize_ 不是 **INPUT** 结构的大小，则函数将失败。
## 返回值
类型： **UINT**
函数返回成功插入键盘或鼠标输入流的事件数。 如果函数返回零，则表示输入已被另一个线程阻止。 要获得更多的错误信息，请调用 GetLastError。
此函数在 UIPI 阻止时失败。 请注意， [GetLastError](https://learn.microsoft.com/zh-cn/windows/desktop/api/errhandlingapi/nf-errhandlingapi-getlasterror) 和返回值都不会指示失败是由 UIPI 阻止引起的。
## 注解
此函数受 UIPI 约束。 仅允许应用程序将输入注入到完整性级别相等或更低级别的应用程序。
**SendInput** 函数将 [[INPUT]]结构中的事件串行插入键盘或鼠标输入流。 这些事件不会与用户 (键盘或鼠标) 插入的其他键盘或鼠标输入事件，或者通过调用 [keybd_event](https://learn.microsoft.com/zh-cn/windows/desktop/api/winuser/nf-winuser-keybd_event)、 [mouse_event](https://learn.microsoft.com/zh-cn/windows/desktop/api/winuser/nf-winuser-mouse_event) 或 **对 SendInput** 的其他调用插入。
此函数不会重置键盘的当前状态。 调用函数时已按下的任何键都可能会干扰此函数生成的事件。 若要避免此问题，请使用 [[GetAsyncKeyState]] 函数检查键盘的状态，并根据需要进行更正。
由于触摸键盘使用 winnls.h 中定义的代理宏将输入发送到系统，因此键盘事件挂钩上的侦听器必须解码源自触摸键盘的输入。 有关详细信息，请参阅 [代理项和补充字符](https://learn.microsoft.com/zh-cn/windows/desktop/Intl/surrogates-and-supplementary-characters)。
辅助功能应用程序可以使用 **SendInput** 注入与 shell 处理的应用程序启动快捷键对应的击键。 此功能不保证适用于其他类型的应用程序。
## 示例代码
```C++
//**********************************************************************
//
// Sends Win + D to toggle to the desktop
//
//**********************************************************************
void ShowDesktop()
{
    OutputString(L"Sending 'Win-D'\r\n");
    INPUT inputs[4] = {};
    ZeroMemory(inputs, sizeof(inputs));

    inputs[0].type = INPUT_KEYBOARD;
    inputs[0].ki.wVk = VK_LWIN;
   
    inputs[1].type = INPUT_KEYBOARD;
    inputs[1].ki.wVk = 'D';

    inputs[2].type = INPUT_KEYBOARD;
    inputs[2].ki.wVk = 'D';
    inputs[2].ki.dwFlags = KEYEVENTF_KEYUP;

    inputs[3].type = INPUT_KEYBOARD;
    inputs[3].ki.wVk = VK_LWIN;
    inputs[3].ki.dwFlags = KEYEVENTF_KEYUP;

    UINT uSent = SendInput(ARRAYSIZE(inputs), inputs, sizeof(INPUT));
    if (uSent != ARRAYSIZE(inputs))
    {
        OutputString(L"SendInput failed: 0x%x\n", HRESULT_FROM_WIN32(GetLastError()));
    } 
}
```