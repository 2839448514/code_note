# SetMessageExtraInfo 函数 (winuser.h)

## 语法

```c++
LPARAM SetMessageExtraInfo(
  [in] LPARAM lParam
);
```

## 参数

`[in] lParam`

类型：LPARAM：要与当前线程关联的值。

## 返回值

类型：LPARAM

返回值是与当前线程关联的上一个值。

## 示例代码

```C++
#include <Windows.h>
#include <iostream>
// 定义一个窗口过程函数
LRESULT CALLBACK WindowProc(HWND hwnd, UINT uMsg, WPARAM wParam, LPARAM lParam) {
    switch (uMsg) {
    case WM_LBUTTONDOWN: {
        // 当鼠标左键按下时，获取额外信息
        LPARAM extraInfo = GetMessageExtraInfo();
        std::cout << "Mouse left button down extra info: " << extraInfo << std::endl;
        return 0;
    }
    case WM_DESTROY:
        PostQuitMessage(0);
        return 0;
    }
    return DefWindowProc(hwnd, uMsg, wParam, lParam);
}
int main() {
    // 注册窗口类
    const char CLASS_NAME[] = "Sample Window Class";
    WNDCLASS wc = {0};
    wc.lpfnWndProc = WindowProc;
    wc.hInstance = GetModuleHandle(NULL);
    wc.lpszClassName = CLASS_NAME;
    RegisterClass(&wc);
    // 创建窗口
    HWND hwnd = CreateWindowEx(
        0,
        CLASS_NAME,
        "Learn to Program Windows",
        WS_OVERLAPPEDWINDOW,
        CW_USEDEFAULT, CW_USEDEFAULT, CW_USEDEFAULT, CW_USEDEFAULT,
        NULL,
        NULL,
        GetModuleHandle(NULL),
        NULL
    );
    if (hwnd == NULL) {
        return 0;
    }
    ShowWindow(hwnd, SW_SHOW);
    // 设置额外信息
    LPARAM customInfo = 12345; // 自定义的额外信息
    SetMessageExtraInfo(customInfo);
    // 模拟鼠标左键按下事件
    INPUT input = {0};
    input.type = INPUT_MOUSE;
    input.mi.dwFlags = MOUSEEVENTF_LEFTDOWN;
    SendInput(1, &input, sizeof(INPUT));
    // 消息循环
    MSG msg = {0};
    while (GetMessage(&msg, NULL, 0, 0)) {
        TranslateMessage(&msg);
        DispatchMessage(&msg);
    }
    return 0;
}

```