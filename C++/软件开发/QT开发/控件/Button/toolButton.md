### 常用函数方法

### 1. `setText(const QString &text)`
- **作用**：设置工具按钮上的文本。
- **参数**：
  - `text`：要设置的文本内容，类型为 `QString`。

```cpp
toolButton->setText("Tool");
```

### 2. `text()`
- **作用**：获取工具按钮上的文本。
- **返回值**：`QString`，工具按钮上的文本内容。

```cpp
QString buttonText = toolButton->text();
```

### 3. `setIcon(const QIcon &icon)`
- **作用**：设置工具按钮上的图标。
- **参数**：
  - `icon`：要设置的图标，类型为 `QIcon`。

```cpp
QIcon icon(":/resources/icon.png");
toolButton->setIcon(icon);
```

### 4. `icon()`
- **作用**：获取工具按钮上的图标。
- **返回值**：`QIcon`，工具按钮上的图标。

```cpp
QIcon buttonIcon = toolButton->icon();
```

### 5. `setIconSize(const QSize &size)`
- **作用**：设置工具按钮图标的大小。
- **参数**：
  - `size`：图标的大小，类型为 `QSize`。

```cpp
toolButton->setIconSize(QSize(32, 32));
```

### 6. `iconSize()`
- **作用**：获取工具按钮图标的大小。
- **返回值**：`QSize`，工具按钮图标的大小。

```cpp
QSize iconSize = toolButton->iconSize();
```

### 7. `setToolButtonStyle(Qt::ToolButtonStyle style)`
- **作用**：设置工具按钮的样式。
- **参数**：
  - `style`：工具按钮的样式，类型为 `Qt::ToolButtonStyle`。可选值包括 `Qt::ToolButtonIconOnly`、`Qt::ToolButtonTextOnly`、`Qt::ToolButtonTextBesideIcon`、`Qt::ToolButtonTextUnderIcon`。

```cpp
toolButton->setToolButtonStyle(Qt::ToolButtonTextUnderIcon);
```

### 8. `toolButtonStyle()`
- **作用**：获取工具按钮的样式。
- **返回值**：`Qt::ToolButtonStyle`，工具按钮的样式。

```cpp
Qt::ToolButtonStyle style = toolButton->toolButtonStyle();
```

### 9. `setAutoRaise(bool enable)`
- **作用**：设置工具按钮是否在工具栏中自动升起。
- **参数**：
  - `enable`：布尔值，`true` 表示自动升起，`false` 表示不自动升起。

```cpp
toolButton->setAutoRaise(true);
```

### 10. `autoRaise()`
- **作用**：检查工具按钮是否在工具栏中自动升起。
- **返回值**：`bool`，如果工具按钮自动升起则返回 `true`，否则返回 `false`。

```cpp
bool isAutoRaise = toolButton->autoRaise();
```

### 11. `setMenu(QMenu *menu)`
- **作用**：设置工具按钮关联的菜单。
- **参数**：
  - `menu`：指向 `QMenu` 对象的指针。

```cpp
QMenu *menu = new QMenu(this);
menu->addAction("Option 1");
menu->addAction("Option 2");
toolButton->setMenu(menu);
```

### 12. `menu()`
- **作用**：获取工具按钮关联的菜单。
- **返回值**：`QMenu*`，指向关联菜单的指针。

```cpp
QMenu *associatedMenu = toolButton->menu();
```

### 13. `setPopupMode(QToolButton::ToolButtonPopupMode mode)`
- **作用**：设置工具按钮的弹出模式。
- **参数**：
  - `mode`：弹出模式，类型为 `QToolButton::ToolButtonPopupMode`。可选值包括 `QToolButton::DelayedPopup`、`QToolButton::MenuButtonPopup`、`QToolButton::InstantPopup`。

```cpp
toolButton->setPopupMode(QToolButton::MenuButtonPopup);
```

### 14. `popupMode()`
- **作用**：获取工具按钮的弹出模式。
- **返回值**：`QToolButton::ToolButtonPopupMode`，工具按钮的弹出模式。

```cpp
QToolButton::ToolButtonPopupMode mode = toolButton->popupMode();
```

### 15. `setCheckable(bool checkable)`
- **作用**：设置工具按钮是否可被选中（开关按钮）。
- **参数**：
  - `checkable`：布尔值，`true` 表示按钮可被选中，`false` 表示按钮不可被选中。

```cpp
toolButton->setCheckable(true);
```

### 16. `isCheckable()`
- **作用**：检查工具按钮是否可被选中。
- **返回值**：`bool`，如果按钮可被选中则返回 `true`，否则返回 `false`。

```cpp
bool isCheckable = toolButton->isCheckable();
```

### 17. `setChecked(bool checked)`
- **作用**：设置工具按钮的选中状态。
- **参数**：
  - `checked`：布尔值，`true` 表示按钮被选中，`false` 表示按钮未被选中。

```cpp
toolButton->setChecked(true);
```

### 18. `isChecked()`
- **作用**：检查工具按钮是否被选中。
- **返回值**：`bool`，如果按钮被选中则返回 `true`，否则返回 `false`。

```cpp
bool isChecked = toolButton->isChecked();
```

### 19. `setAutoRepeat(bool repeat)`
- **作用**：设置工具按钮是否自动重复触发。
- **参数**：
  - `repeat`：布尔值，`true` 表示按钮自动重复触发，`false` 表示按钮不自动重复触发。

```cpp
toolButton->setAutoRepeat(true);
```

### 20. `isAutoRepeat()`
- **作用**：检查工具按钮是否自动重复触发。
- **返回值**：`bool`，如果按钮自动重复触发则返回 `true`，否则返回 `false`。

```cpp
bool isAutoRepeat = toolButton->isAutoRepeat();
```

### 21. `setAutoExclusive(bool autoExclusive)`
- **作用**：设置工具按钮在同一父级下是否自动互斥（仅对可选按钮有效）。
- **参数**：
  - `autoExclusive`：布尔值，`true` 表示自动互斥，`false` 表示不互斥。

```cpp
toolButton->setAutoExclusive(true);
```

### 22. `autoExclusive()`
- **作用**：检查工具按钮是否在同一父级下自动互斥（仅对可选按钮有效）。
- **返回值**：`bool`，如果按钮自动互斥则返回 `true`，否则返回 `false`。

```cpp
bool isAutoExclusive = toolButton->autoExclusive();
```

### 常用信号

### 23. `clicked(bool checked = false)`
- **作用**：当工具按钮被点击时发出信号。
- **参数**：
  - `checked`：布尔值，指示按钮的选中状态（仅在按钮为可选中时有效）。

```cpp
connect(toolButton, &QToolButton::clicked, this, &YourClass::onToolButtonClicked);

void YourClass::onToolButtonClicked(bool checked) {
    // 处理按钮点击事件
}
```

### 24. `pressed()`
- **作用**：当工具按钮被按下时发出信号。
- **无参数**。

```cpp
connect(toolButton, &QToolButton::pressed, this, &YourClass::onToolButtonPressed);

void YourClass::onToolButtonPressed() {
    // 处理按钮按下事件
}
```

### 25. `released()`
- **作用**：当工具按钮被释放时发出信号。
- **无参数**。

```cpp
connect(toolButton, &QToolButton::released, this, &YourClass::onToolButtonReleased);

void YourClass::onToolButtonReleased() {
    // 处理按钮释放事件
}
```

### 26. `toggled(bool checked)`
- **作用**：当工具按钮的选中状态改变时发出信号（仅在按钮为可选中时有效）。
- **参数**：
  - `checked`：布尔值，指示按钮的新选中状态。

```cpp
connect(toolButton, &QToolButton::toggled, this, &YourClass::onToolButtonToggled);

void YourClass::onToolButtonToggled(bool checked) {
    // 处理按钮选中状态改变事件
}
```
