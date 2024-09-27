`QRadioButton` 是 Qt 中用于创建单选按钮的控件。以下是一些 `QRadioButton` 常用的函数方法及其作用：

### 常用函数方法

### 1. `setText(const QString &text)`

- **作用**：设置单选按钮上的文本。
- **参数**：
  - `text`：要设置的文本内容，类型为 `QString`。

```cpp
radioButton->setText("Option 1");
```

### 2. `text()`

- **作用**：获取单选按钮上的文本。
- **返回值**：`QString`，单选按钮上的文本内容。

```cpp
QString buttonText = radioButton->text();
```

### 3. `setChecked(bool checked)`

- **作用**：设置单选按钮的选中状态。
- **参数**：
  - `checked`：布尔值，`true` 表示按钮被选中，`false` 表示按钮未被选中。

```cpp
radioButton->setChecked(true);
```

### 4. `isChecked()`

- **作用**：检查单选按钮是否被选中。
- **返回值**：`bool`，如果按钮被选中则返回 `true`，否则返回 `false`。

```cpp
bool isChecked = radioButton->isChecked();
```

### 5. `setAutoExclusive(bool autoExclusive)`

- **作用**：设置单选按钮在同一父级下是否自动互斥。
- **参数**：
  - `autoExclusive`：布尔值，`true` 表示自动互斥，`false` 表示不互斥。

```cpp
radioButton->setAutoExclusive(true);
```

### 6. `autoExclusive()`

- **作用**：检查单选按钮是否在同一父级下自动互斥。
- **返回值**：`bool`，如果按钮自动互斥则返回 `true`，否则返回 `false`。

```cpp
bool isAutoExclusive = radioButton->autoExclusive();
```

### 7. `setEnabled(bool enabled)`

- **作用**：设置单选按钮是否可用。
- **参数**：
  - `enabled`：布尔值，`true` 表示按钮可用，`false` 表示按钮不可用。

```cpp
radioButton->setEnabled(true);
```

### 8. `isEnabled()`

- **作用**：检查单选按钮是否可用。
- **返回值**：`bool`，如果按钮可用则返回 `true`，否则返回 `false`。

```cpp
bool isEnabled = radioButton->isEnabled();
```

### 9. `setIcon(const QIcon &icon)`

- **作用**：设置单选按钮上的图标。
- **参数**：
  - `icon`：要设置的图标，类型为 `QIcon`。

```cpp
QIcon icon(":/resources/icon.png");
radioButton->setIcon(icon);
```

### 10. `icon()`

- **作用**：获取单选按钮上的图标。
- **返回值**：`QIcon`，单选按钮上的图标。

```cpp
QIcon buttonIcon = radioButton->icon();
```

### 11. `setIconSize(const QSize &size)`

- **作用**：设置单选按钮图标的大小。
- **参数**：
  - `size`：图标的大小，类型为 `QSize`。

```cpp
radioButton->setIconSize(QSize(32, 32));
```

### 12. `iconSize()`

- **作用**：获取单选按钮图标的大小。
- **返回值**：`QSize`，单选按钮图标的大小。

```cpp
QSize iconSize = radioButton->iconSize();
```

### 13. `setShortcut(const QKeySequence &key)`

- **作用**：设置单选按钮的快捷键。
- **参数**：
  - `key`：快捷键，类型为 `QKeySequence`。

```cpp
radioButton->setShortcut(QKeySequence(Qt::CTRL + Qt::Key_1));
```

### 14. `shortcut()`

- **作用**：获取单选按钮的快捷键。
- **返回值**：`QKeySequence`，单选按钮的快捷键。

```cpp
QKeySequence shortcutKey = radioButton->shortcut();
```

### 15. `setStyleSheet(const QString &styleSheet)`

- **作用**：设置单选按钮的样式表，用于自定义按钮的外观。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。

```cpp
radioButton->setStyleSheet("background-color: lightgray; color: black;");
```

### 常用信号

### 16. `clicked(bool checked = false)`

- **作用**：当单选按钮被点击时发出信号。
- **参数**：
  - `checked`：布尔值，指示按钮的选中状态。

```cpp
connect(radioButton, &QRadioButton::clicked, this, &YourClass::onRadioButtonClicked);

void YourClass::onRadioButtonClicked(bool checked) {
    // 处理按钮点击事件
}
```

### 17. `toggled(bool checked)`

- **作用**：当单选按钮的选中状态改变时发出信号。
- **参数**：
  - `checked`：布尔值，指示按钮的新选中状态。

```cpp
connect(radioButton, &QRadioButton::toggled, this, &YourClass::onRadioButtonToggled);

void YourClass::onRadioButtonToggled(bool checked) {
    // 处理按钮选中状态改变事件
}
```

### 18. `pressed()`

- **作用**：当单选按钮被按下时发出信号。
- **无参数**。

```cpp
connect(radioButton, &QRadioButton::pressed, this, &YourClass::onRadioButtonPressed);

void YourClass::onRadioButtonPressed() {
    // 处理按钮按下事件
}
```

### 19. `released()`

- **作用**：当单选按钮被释放时发出信号。
- **无参数**。

```cpp
connect(radioButton, &QRadioButton::released, this, &YourClass::onRadioButtonReleased);

void YourClass::onRadioButtonReleased() {
    // 处理按钮释放事件
}
```

### 20. `enterEvent(QEvent *event)`

- **作用**：当鼠标指针进入按钮区域时触发。
- **参数**：
  - `event`：事件对象，类型为 `QEvent*`。

```cpp
void YourClass::enterEvent(QEvent *event) {
    // 处理鼠标进入事件
    radioButton->setStyleSheet("background-color: yellow;");
}
```

### 21. `leaveEvent(QEvent *event)`

- **作用**：当鼠标指针离开按钮区域时触发。
- **参数**：
  - `event`：事件对象，类型为 `QEvent*`。

```cpp
void YourClass::leaveEvent(QEvent *event) {
    // 处理鼠标离开事件
    radioButton->setStyleSheet("");
}
```