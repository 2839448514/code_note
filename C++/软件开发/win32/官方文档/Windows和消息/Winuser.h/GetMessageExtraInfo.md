# GetMessageExtraInfo 函数 (winuser.h)

## 本文内容

## 语法

```C++
LPARAM GetMessageExtraInfo();
```

## 返回值

类型：LPARAM

返回值指定额外信息。 额外信息的含义特定于设备。

## 注解

若要设置线程的额外消息信息，请使用 [[SetMessageExtraInfo]] 函数。

## 示例代码

```C++
#include <Windows.h>
#include <iostream>
// 定义一个窗口过程函数
LRESULT CALLBACK WindowProc(HWND hwnd, UINT uMsg, WPARAM wParam, LPARAM lParam) {
    switch (uMsg) {
    case WM_MOUSEMOVE: {
        // 当鼠标移动时，获取额外信息
        LPARAM extraInfo = GetMessageExtraInfo();
        std::cout << "Mouse move extra info: " << extraInfo << std::endl;
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
    // 消息循环
    MSG msg = {0};
    while (GetMessage(&msg, NULL, 0, 0)) {
        TranslateMessage(&msg);
        DispatchMessage(&msg);
    }
    return 0;
}
```