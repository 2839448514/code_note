---
tags:
  - QT开发
---
# checkBox

### 常用函数方法

### 1. `setText(const QString &text)`

- **作用**：设置复选框上的文本。
- **参数**：
  - `text`：要设置的文本内容，类型为 `QString`。

```cpp
checkBox->setText("Option 1");
```

### 2. `text()`

- **作用**：获取复选框上的文本。
- **返回值**：`QString`，复选框上的文本内容。

```cpp
QString boxText = checkBox->text();
```

### 3. `setChecked(bool checked)`

- **作用**：设置复选框的选中状态。
- **参数**：
  - `checked`：布尔值，`true` 表示复选框被选中，`false` 表示复选框未被选中。

```cpp
checkBox->setChecked(true);
```

### 4. `isChecked()`

- **作用**：检查复选框是否被选中。
- **返回值**：`bool`，如果复选框被选中则返回 `true`，否则返回 `false`。

```cpp
bool isChecked = checkBox->isChecked();
```

### 5. `setTristate(bool y = true)`

- **作用**：设置复选框是否支持三态模式。
- **参数**：
  - `y`：布尔值，`true` 表示支持三态模式，`false` 表示不支持三态模式。默认为 `true`。

```cpp
checkBox->setTristate(true);
```

### 6. `isTristate()`

- **作用**：检查复选框是否支持三态模式。
- **返回值**：`bool`，如果复选框支持三态模式则返回 `true`，否则返回 `false`。

```cpp
bool isTristate = checkBox->isTristate();
```

### 7. `setCheckState(Qt::CheckState state)`

- **作用**：设置复选框的选中状态（支持三态）。
- **参数**：
  - `state`：复选框的状态，类型为 `Qt::CheckState`。可选值包括 `Qt::Unchecked`、`Qt::PartiallyChecked`、`Qt::Checked`。

```cpp
checkBox->setCheckState(Qt::PartiallyChecked);
```

### 8. `checkState()`

- **作用**：获取复选框的选中状态。
- **返回值**：`Qt::CheckState`，复选框的状态。

```cpp
Qt::CheckState state = checkBox->checkState();
```

### 9. `setIcon(const QIcon &icon)`

- **作用**：设置复选框的图标。
- **参数**：
  - `icon`：要设置的图标，类型为 `QIcon`。

```cpp
QIcon icon(":/resources/icon.png");
checkBox->setIcon(icon);
```

### 10. `icon()`

- **作用**：获取复选框的图标。
- **返回值**：`QIcon`，复选框的图标。

```cpp
QIcon boxIcon = checkBox->icon();
```

### 11. `setIconSize(const QSize &size)`

- **作用**：设置复选框图标的大小。
- **参数**：
  - `size`：图标的大小，类型为 `QSize`。

```cpp
checkBox->setIconSize(QSize(32, 32));
```

### 12. `iconSize()`

- **作用**：获取复选框图标的大小。
- **返回值**：`QSize`，复选框图标的大小。

```cpp
QSize iconSize = checkBox->iconSize();
```

### 13. `setEnabled(bool enabled)`

- **作用**：设置复选框是否可用。
- **参数**：
  - `enabled`：布尔值，`true` 表示复选框可用，`false` 表示复选框不可用。

```cpp
checkBox->setEnabled(true);
```

### 14. `isEnabled()`

- **作用**：检查复选框是否可用。
- **返回值**：`bool`，如果复选框可用则返回 `true`，否则返回 `false`。

```cpp
bool isEnabled = checkBox->isEnabled();
```

### 15. `setVisible(bool visible)`

- **作用**：设置复选框是否可见。
- **参数**：
  - `visible`：布尔值，`true` 表示复选框可见，`false` 表示复选框不可见。

```cpp
checkBox->setVisible(true);
```

### 16. `isVisible()`

- **作用**：检查复选框是否可见。
- **返回值**：`bool`，如果复选框可见则返回 `true`，否则返回 `false`。

```cpp
bool isVisible = checkBox->isVisible();
```

### 17. `setStyleSheet(const QString &styleSheet)`

- **作用**：设置复选框的样式表，用于自定义复选框的外观。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。

```cpp
checkBox->setStyleSheet("background-color: lightgray; color: black;");
```

### 常用信号

### 18. `clicked(bool checked = false)`

- **作用**：当复选框被点击时发出信号。
- **参数**：
  - `checked`：布尔值，指示复选框的选中状态。

```cpp
connect(checkBox, &QCheckBox::clicked, this, &YourClass::onCheckBoxClicked);

void YourClass::onCheckBoxClicked(bool checked) {
    // 处理复选框点击事件
}
```

### 19. `toggled(bool checked)`

- **作用**：当复选框的选中状态改变时发出信号。
- **参数**：
  - `checked`：布尔值，指示复选框的新选中状态。

```cpp
connect(checkBox, &QCheckBox::toggled, this, &YourClass::onCheckBoxToggled);

void YourClass::onCheckBoxToggled(bool checked) {
    // 处理复选框选中状态改变事件
}
```

### 20. `stateChanged(int state)`

- **作用**：当复选框的状态改变时发出信号。
- **参数**：
  - `state`：整数值，指示复选框的新状态，取值为 `Qt::Unchecked`、`Qt::PartiallyChecked` 或 `Qt::Checked`。

```cpp
connect(checkBox, &QCheckBox::stateChanged, this, &YourClass::onCheckBoxStateChanged);

void YourClass::onCheckBoxStateChanged(int state) {
    // 处理复选框状态改变事件
}
```

`QCheckBox` 还有一些其他方法和函数，虽然不如上面列出的那些常用，但也有助于更细致的控制和使用 `QCheckBox` 控件。以下是一些额外的方法：

### 其他方法函数

### 21. `setTristate(bool y)`

- **作用**：设置复选框是否启用三态模式。
- **参数**：
  - `y`：布尔值，`true` 启用三态模式，`false` 禁用三态模式。三态模式允许复选框有一个额外的中间状态。

```cpp
checkBox->setTristate(true);
```

### 22. `setCheckState(Qt::CheckState state)`

- **作用**：设置复选框的选中状态。此方法仅在三态模式下有效。
- **参数**：
  - `state`：状态，类型为 `Qt::CheckState`，可取 `Qt::Unchecked`、`Qt::PartiallyChecked`、`Qt::Checked`。

```cpp
checkBox->setCheckState(Qt::PartiallyChecked);
```

### 23. `setCheckable(bool checkable)`

- **作用**：设置复选框是否可被选中。若设为 `false`，复选框将只显示文本而不具备选中功能。
- **参数**：
  - `checkable`：布尔值，`true` 表示复选框可以被选中，`false` 表示不可选中。

```cpp
checkBox->setCheckable(true);
```

### 24. `isCheckable()`

- **作用**：检查复选框是否可以被选中。
- **返回值**：`bool`，如果复选框可以被选中则返回 `true`，否则返回 `false`。

```cpp
bool isCheckable = checkBox->isCheckable();
```

### 25. `setTristate(bool tristate)`

- **作用**：设置复选框是否启用三态模式。
- **参数**：
  - `tristate`：布尔值，`true` 启用三态模式，`false` 禁用三态模式。

```cpp
checkBox->setTristate(true);
```

### 26. `setStyleSheet(const QString &styleSheet)`

- **作用**：设置复选框的样式表，用于自定义复选框的外观。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。

```cpp
checkBox->setStyleSheet("background-color: lightgray; color: black;");
```

### 27. `setGeometry(const QRect &rect)`

- **作用**：设置复选框的位置和大小。
- **参数**：
  - `rect`：矩形区域，类型为 `QRect`，指定复选框的位置和大小。

```cpp
checkBox->setGeometry(QRect(10, 10, 100, 30));
```

### 28. `setFont(const QFont &font)`

- **作用**：设置复选框的字体。
- **参数**：
  - `font`：字体对象，类型为 `QFont`。

```cpp
QFont font("Arial", 12);
checkBox->setFont(font);
```

### 29. `font()`

- **作用**：获取复选框的字体。
- **返回值**：`QFont`，复选框的字体。

```cpp
QFont boxFont = checkBox->font();
```

### 30. `setToolTip(const QString &toolTip)`

- **作用**：设置复选框的工具提示文本，当用户将鼠标悬停在复选框上时显示。
- **参数**：
  - `toolTip`：工具提示文本，类型为 `QString`。

```cpp
checkBox->setToolTip("Select this option for more settings.");
```

### 31. `toolTip()`

- **作用**：获取复选框的工具提示文本。
- **返回值**：`QString`，复选框的工具提示文本。

```cpp
QString toolTipText = checkBox->toolTip();
```

### 32. `setWhatsThis(const QString &whatsThis)`

- **作用**：设置复选框的“这是什么”文本，用于帮助系统中。
- **参数**：
  - `whatsThis`：文本，类型为 `QString`。

```cpp
checkBox->setWhatsThis("This checkbox allows you to select this option.");
```

### 33. `whatsThis()`

- **作用**：获取复选框的“这是什么”文本。
- **返回值**：`QString`，复选框的“这是什么”文本。

```cpp
QString whatsThisText = checkBox->whatsThis();
```

### 34. `setFocus()`

- **作用**：设置复选框为焦点项。
- **无参数**。

```cpp
checkBox->setFocus();
```

### 35. `hasFocus()`

- **作用**：检查复选框是否有焦点。
- **返回值**：`bool`，如果复选框有焦点则返回 `true`，否则返回 `false`。

```cpp
bool hasFocus = checkBox->hasFocus();
```
