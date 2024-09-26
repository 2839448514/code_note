# KEYBDINPUT 结构 
## 语法
```C++
typedef struct tagKEYBDINPUT {
  WORD      wVk;
  WORD      wScan;
  DWORD     dwFlags;
  DWORD     time;
  ULONG_PTR dwExtraInfo;
} KEYBDINPUT, *PKEYBDINPUT, *LPKEYBDINPUT;
```
## 成员
- **wVk**：[[虚拟密钥代码]]。 代码必须是 1 到 254 范围内的值。 如果 **dwFlags** 成员指定 **KEYEVENTF_UNICODE**， **则 wVk** 必须为 0。
- **wScan**：密钥的硬件扫描代码。 如果 **dwFlags** 指定 **KEYEVENTF_UNICODE**， **则 wScan** 将指定一个 Unicode 字符，该字符将发送到前台应用程序。
- **dwFlags**：指定击键的各个方面。 此成员可以是以下值的某些组合。

| 值                                       | 含义                                                                                                                                                                        |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **KEYEVENTF_EXTENDEDKEY**<br><br>0x0001 | 如果指定， **则 wScan** 扫描代码由两个字节组成的序列组成，其中第一个字节的值为 0xE0。 有关详细信息 [，请参阅扩展键标志](https://learn.microsoft.com/zh-cn/windows/win32/inputdev/about-keyboard-input#extended-key-flag) 。 |
| **KEYEVENTF_KEYUP**<br><br>0x0002       | 如果指定，则释放密钥。 如果未指定，则按键。                                                                                                                                                    |
| **KEYEVENTF_SCANCODE**<br><br>0x0008    | 如果指定， **wScan** 将标识密钥，并忽略 **wVk** 。                                                                                                                                       |
| **KEYEVENTF_UNICODE**<br><br>0x0004     | 如果指定，系统会合成 **VK_PACKET** 击键。 **wVk** 参数必须为零。 此标志只能与 **KEYEVENTF_KEYUP** 标志组合使用。 有关详细信息，请参见“备注”部分。                                                                         |

- **time**：事件的时间戳（以毫秒为单位）。 如果此参数为零，则系统将提供自己的时间戳。
- **dwExtraInfo**：与击键关联的附加值。 使用 [GetMessageExtraInfo](https://learn.microsoft.com/zh-cn/windows/desktop/api/winuser/nf-winuser-getmessageextrainfo) 函数获取此信息。
## 注解

**INPUT_KEYBOARD** 支持非键板输入方法（如手写识别或语音识别），就像它是使用 **KEYEVENTF_UNICODE** 标志输入文本一样。 如果指定[](https://learn.microsoft.com/zh-cn/windows/desktop/inputdev/wm-keyup)**了**[KEYEVENTF_UNICODE，SendInput](https://learn.microsoft.com/zh-cn/windows/desktop/api/winuser/nf-winuser-sendinput) 会将[WM_KEYDOWN](https://learn.microsoft.com/zh-cn/windows/desktop/inputdev/wm-keydown)或WM_KEYUP消息发送到 _wParam_ 等于**VK_PACKET**的前景线程的消息队列。 [GetMessage](https://learn.microsoft.com/zh-cn/windows/desktop/api/winuser/nf-winuser-getmessage) 或 [PeekMessage](https://learn.microsoft.com/zh-cn/windows/desktop/api/winuser/nf-winuser-peekmessagea) 获取此消息后，将消息传递给 [TranslateMessage](https://learn.microsoft.com/zh-cn/windows/desktop/api/winuser/nf-winuser-translatemessage) 会发布[WM_CHAR](https://learn.microsoft.com/zh-cn/windows/desktop/inputdev/wm-char)消息，其中包含 **wScan** 最初指定的 Unicode 字符。 如果此 Unicode 字符被发布到 ANSI 窗口，则会自动转换为相应的 ANSI 值。

设置 **KEYEVENTF_SCANCODE** 标志以根据扫描代码定义键盘输入。 无论当前使用的是哪种键盘，这都可用于模拟物理击键。 如果扫描代码是扩展密钥，还可以传递 **KEYEVENTF_EXTENDEDKEY** 标志。 键的虚拟键值可能会根据当前键盘布局或按下的其他键而更改，但扫描代码将始终相同。