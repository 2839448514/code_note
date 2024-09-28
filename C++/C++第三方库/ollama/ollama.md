---
tags:
  - 库文件
---
# ollama

只需几行代码即可访问 C++ 中本地语言模型的全部功能：

```c++
#include "ollama.hpp"

std::cout << ollama::generate("llama3.1", "Why is the sky blue?") << std::endl;
```
