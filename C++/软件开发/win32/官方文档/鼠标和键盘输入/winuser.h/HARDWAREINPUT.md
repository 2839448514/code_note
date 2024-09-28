---
tags:
  - win32
---
# HARDWAREINPUT 结构 (winuser.h)

## 语法

```C++
typedef struct tagHARDWAREINPUT {
  DWORD uMsg;
  WORD  wParamL;
  WORD  wParamH;
} HARDWAREINPUT, *PHARDWAREINPUT, *LPHARDWAREINPUT;
```

## 成员

- **uMsg**：输入硬件生成的消息。
- **wParamL**：**uMsg** 的 _lParam_ 参数的低序字。
- **wParamH**：**uMsg** 的 _lParam_ 参数的高序字。
