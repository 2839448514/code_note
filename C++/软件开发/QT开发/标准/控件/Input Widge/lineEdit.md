---
tags:
  - QT开发
---
# lineEdit

### 1. `text()`

- **作用**：获取当前文本内容。
- **返回值**：`QString`，当前文本内容。

```cpp
QString currentText = lineEdit->text();
```

### 2. `setText(const QString &text)`

- **作用**：设置文本内容。
- **参数**：
  - `text`：要设置的文本内容，类型为 `QString`。

```cpp
lineEdit->setText("Hello, World!");
```

### 3. `clear()`

- **作用**：清除文本内容。
- **无参数**。

```cpp
lineEdit->clear();
```

### 4. `setPlaceholderText(const QString &text)`

- **作用**：设置占位符文本，当输入框为空时显示。
- **参数**：
  - `text`：占位符文本内容，类型为 `QString`。

```cpp
lineEdit->setPlaceholderText("Enter your text here...");
```

### 5. `setReadOnly(bool readOnly)`

- **作用**：设置输入框是否为只读模式。
- **参数**：
  - `readOnly`：布尔值，`true` 表示只读，`false` 表示可编辑。

```cpp
lineEdit->setReadOnly(true);
```

### 6. `setMaxLength(int length)`

- **作用**：设置文本的最大长度。
- **参数**：
  - `length`：整数，表示文本的最大长度。

```cpp
lineEdit->setMaxLength(100);
```

### 7. `setEchoMode(QLineEdit::EchoMode mode)`

- **作用**：设置回显模式，用于密码输入等场景。
- **参数**：
  - `mode`：回显模式，类型为 `QLineEdit::EchoMode`，可选值有：
    - `QLineEdit::Normal`：普通文本。
    - `QLineEdit::NoEcho`：不显示任何内容。
    - `QLineEdit::Password`：显示密码模式，用星号或点代替字符。
    - `QLineEdit::PasswordEchoOnEdit`：编辑时显示实际字符，其他时间显示密码模式。

```cpp
lineEdit->setEchoMode(QLineEdit::Password);
```

### 8. `textChanged(const QString &text)` 信号

- **作用**：当文本内容改变时发出信号。
- **参数**：
  - `text`：当前文本内容，类型为 `QString`。

```cpp
connect(lineEdit, &QLineEdit::textChanged, this, &YourClass::onTextChanged);

void YourClass::onTextChanged(const QString &text) {
    // 处理文本改变
}
```

### 9. `returnPressed()` 信号

- **作用**：当用户按下回车键时发出信号。
- **无参数**。

```cpp
connect(lineEdit, &QLineEdit::returnPressed, this, &YourClass::onReturnPressed);

void YourClass::onReturnPressed() {
    // 处理回车键按下
}
```

### 10. `setValidator(const QValidator *validator)`

- **作用**：设置输入验证器。
- **参数**：
  - `validator`：指向 `QValidator` 对象的指针，用于验证输入内容。

```cpp
QIntValidator *validator = new QIntValidator(0, 100, this);
lineEdit->setValidator(validator);
```

当然，`QLineEdit` 还有许多其他有用的函数方法和信号。以下是一些常用的补充函数方法：

### 11. `selectAll()`

- **作用**：选择文本框中的所有文本。
- **无参数**。

```cpp
lineEdit->selectAll();
```

### 12. `setSelection(int start, int length)`

- **作用**：设置选中文本的起始位置和长度。
- **参数**：
  - `start`：选中文本的起始位置，类型为 `int`。
  - `length`：选中文本的长度，类型为 `int`。

```cpp
lineEdit->setSelection(0, 5); // 选中前 5 个字符
```

### 13. `selectedText()`

- **作用**：获取选中的文本。
- **返回值**：`QString`，选中的文本内容。

```cpp
QString selected = lineEdit->selectedText();
```

### 14. `cursorPosition()`

- **作用**：获取光标的当前位置。
- **返回值**：`int`，光标的当前位置。

```cpp
int cursorPos = lineEdit->cursorPosition();
```

### 15. `setCursorPosition(int position)`

- **作用**：设置光标的位置。
- **参数**：
  - `position`：光标的位置，类型为 `int`。

```cpp
lineEdit->setCursorPosition(3); // 将光标设置在第 3 个字符后
```

### 16. `hasSelectedText()`

- **作用**：检查是否有选中的文本。
- **返回值**：`bool`，如果有选中的文本则返回 `true`，否则返回 `false`。

```cpp
bool hasSelection = lineEdit->hasSelectedText();
```

### 17. `setInputMask(const QString &inputMask)`

- **作用**：设置输入掩码，以控制输入格式。
- **参数**：
  - `inputMask`：输入掩码，类型为 `QString`。

```cpp
lineEdit->setInputMask("0000-0000;_"); // 设置输入掩码为 4 位数字-4 位数字
```

### 18. `setAlignment(Qt::Alignment alignment)`

- **作用**：设置文本对齐方式。
- **参数**：
  - `alignment`：对齐方式，类型为 `Qt::Alignment`，如 `Qt::AlignLeft`、`Qt::AlignRight`、`Qt::AlignCenter` 等。

```cpp
lineEdit->setAlignment(Qt::AlignCenter);
```

### 19. `isModified()`

- **作用**：检查文本是否被修改过。
- **返回值**：`bool`，如果文本被修改过则返回 `true`，否则返回 `false`。

```cpp
bool modified = lineEdit->isModified();
```

### 20. `setModified(bool modified)`

- **作用**：设置文本是否被修改过。
- **参数**：
  - `modified`：布尔值，`true` 表示文本被修改过，`false` 表示未修改。

```cpp
lineEdit->setModified(true);
```

### 21. `undo()`

- **作用**：撤销最后的操作。
- **无参数**。

```cpp
lineEdit->undo();
```

### 22. `redo()`

- **作用**：重做最后的撤销操作。
- **无参数**。

```cpp
lineEdit->redo();
```

### 23. `cut()`

- **作用**：剪切选中文本。
- **无参数**。

```cpp
lineEdit->cut();
```

### 24. `copy()`

- **作用**：复制选中文本。
- **无参数**。

```cpp
lineEdit->copy();
```

### 25. `paste()`

- **作用**：粘贴剪贴板中的文本。
- **无参数**。

```cpp
lineEdit->paste();
```

### 26. `setDragEnabled(bool b)`

- **作用**：设置是否允许拖动文本。
- **参数**：
  - `b`：布尔值，`true` 表示允许拖动，`false` 表示不允许。

```cpp
lineEdit->setDragEnabled(true);
```

### 27. `dragEnabled()`

- **作用**：检查是否允许拖动文本。
- **返回值**：`bool`，如果允许拖动则返回 `true`，否则返回 `false`。

```cpp
bool dragEnabled = lineEdit->dragEnabled();
```

### 28. `inputMethodQuery(Qt::InputMethodQuery query)`

- **作用**：查询输入法的特定属性。
- **参数**：
  - `query`：查询类型，类型为 `Qt::InputMethodQuery`。
- **返回值**：`QVariant`，查询结果。

```cpp
QVariant queryResult = lineEdit->inputMethodQuery(Qt::ImCursorRectangle);
```
