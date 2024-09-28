---
tags:
  - QT开发
---
# pushButton

### 常用函数方法

### 1. `setText(const QString &text)`

- **作用**：设置按钮上的文本。
- **参数**：
  - `text`：要设置的文本内容，类型为 `QString`。

```cpp
pushButton->setText("Click Me");
```

### 2. `text()`

- **作用**：获取按钮上的文本。
- **返回值**：`QString`，按钮上的文本内容。

```cpp
QString buttonText = pushButton->text();
```

### 3. `setIcon(const QIcon &icon)`

- **作用**：设置按钮上的图标。
- **参数**：
  - `icon`：要设置的图标，类型为 `QIcon`。

```cpp
QIcon icon(":/resources/icon.png");
pushButton->setIcon(icon);
```

### 4. `icon()`

- **作用**：获取按钮上的图标。
- **返回值**：`QIcon`，按钮上的图标。

```cpp
QIcon buttonIcon = pushButton->icon();
```

### 5. `setEnabled(bool enabled)`

- **作用**：设置按钮是否可用。
- **参数**：
  - `enabled`：布尔值，`true` 表示按钮可用，`false` 表示按钮不可用。

```cpp
pushButton->setEnabled(true);
```

### 6. `isEnabled()`

- **作用**：检查按钮是否可用。
- **返回值**：`bool`，如果按钮可用则返回 `true`，否则返回 `false`。

```cpp
bool isEnabled = pushButton->isEnabled();
```

### 7. `setCheckable(bool checkable)`

- **作用**：设置按钮是否可被选中（开关按钮）。
- **参数**：
  - `checkable`：布尔值，`true` 表示按钮可被选中，`false` 表示按钮不可被选中。

```cpp
pushButton->setCheckable(true);
```

### 8. `isCheckable()`

- **作用**：检查按钮是否可被选中。
- **返回值**：`bool`，如果按钮可被选中则返回 `true`，否则返回 `false`。

```cpp
bool isCheckable = pushButton->isCheckable();
```

### 9. `setChecked(bool checked)`

- **作用**：设置按钮的选中状态。
- **参数**：
  - `checked`：布尔值，`true` 表示按钮被选中，`false` 表示按钮未被选中。

```cpp
pushButton->setChecked(true);
```

### 10. `isChecked()`

- **作用**：检查按钮是否被选中。
- **返回值**：`bool`，如果按钮被选中则返回 `true`，否则返回 `false`。

```cpp
bool isChecked = pushButton->isChecked();
```

### 11. `setAutoRepeat(bool repeat)`

- **作用**：设置按钮是否自动重复触发。
- **参数**：
  - `repeat`：布尔值，`true` 表示按钮自动重复触发，`false` 表示按钮不自动重复触发。

```cpp
pushButton->setAutoRepeat(true);
```

### 12. `isAutoRepeat()`

- **作用**：检查按钮是否自动重复触发。
- **返回值**：`bool`，如果按钮自动重复触发则返回 `true`，否则返回 `false`。

```cpp
bool isAutoRepeat = pushButton->isAutoRepeat();
```

### 13. `setDefault(bool isDefault)`

- **作用**：设置按钮为默认按钮。
- **参数**：
  - `isDefault`：布尔值，`true` 表示设置为默认按钮，`false` 表示取消默认按钮设置。

```cpp
pushButton->setDefault(true);
```

### 14. `isDefault()`

- **作用**：检查按钮是否为默认按钮。
- **返回值**：`bool`，如果按钮为默认按钮则返回 `true`，否则返回 `false`。

```cpp
bool isDefault = pushButton->isDefault();
```

### 15. `setFlat(bool flat)`

- **作用**：设置按钮是否为扁平化样式。
- **参数**：
  - `flat`：布尔值，`true` 表示按钮为扁平化样式，`false` 表示按钮为普通样式。

```cpp
pushButton->setFlat(true);
```

### 16. `isFlat()`

- **作用**：检查按钮是否为扁平化样式。
- **返回值**：`bool`，如果按钮为扁平化样式则返回 `true`，否则返回 `false`。

```cpp
bool isFlat = pushButton->isFlat();
```

### 常用信号

### 17. `clicked(bool checked = false)`

- **作用**：当按钮被点击时发出信号。
- **参数**：
  - `checked`：布尔值，指示按钮的选中状态（仅在按钮为可选中时有效）。

```cpp
connect(pushButton, &QPushButton::clicked, this, &YourClass::onButtonClicked);

void YourClass::onButtonClicked(bool checked) {
    // 处理按钮点击事件
}
```

### 18. `pressed()`

- **作用**：当按钮被按下时发出信号。
- **无参数**。

```cpp
connect(pushButton, &QPushButton::pressed, this, &YourClass::onButtonPressed);

void YourClass::onButtonPressed() {
    // 处理按钮按下事件
}
```

### 19. `released()`

- **作用**：当按钮被释放时发出信号。
- **无参数**。

```cpp
connect(pushButton, &QPushButton::released, this, &YourClass::onButtonReleased);

void YourClass::onButtonReleased() {
    // 处理按钮释放事件
}
```

### 20. `toggled(bool checked)`

- **作用**：当按钮的选中状态改变时发出信号（仅在按钮为可选中时有效）。
- **参数**：
  - `checked`：布尔值，指示按钮的新选中状态。

```cpp
connect(pushButton, &QPushButton::toggled, this, &YourClass::onButtonToggled);

void YourClass::onButtonToggled(bool checked) {
    // 处理按钮选中状态改变事件
}
```

### 21. `setShortcut(const QKeySequence &key)`

- **作用**：设置按钮的快捷键。
- **参数**：
  - `key`：快捷键，类型为 `QKeySequence`。

```cpp
pushButton->setShortcut(QKeySequence(Qt::CTRL + Qt::Key_S));
```

### 22. `shortcut()`

- **作用**：获取按钮的快捷键。
- **返回值**：`QKeySequence`，按钮的快捷键。

```cpp
QKeySequence shortcutKey = pushButton->shortcut();
```

### 23. `animateClick(int msec = 100)`

- **作用**：模拟按钮被点击的动画效果。
- **参数**：
  - `msec`：动画持续时间，默认值为 100 毫秒。

```cpp
pushButton->animateClick(200); // 200 毫秒的点击动画
```

### 24. `showMenu()`

- **作用**：显示按钮关联的菜单（如果有）。
- **无参数**。

```cpp
pushButton->showMenu();
```

### 25. `setMenu(QMenu *menu)`

- **作用**：设置按钮关联的菜单。
- **参数**：
  - `menu`：指向 `QMenu` 对象的指针。

```cpp
QMenu *menu = new QMenu(this);
menu->addAction("Option 1");
menu->addAction("Option 2");
pushButton->setMenu(menu);
```

### 26. `menu()`

- **作用**：获取按钮关联的菜单。
- **返回值**：`QMenu*`，指向关联菜单的指针。

```cpp
QMenu *associatedMenu = pushButton->menu();
```

### 27. `setIconSize(const QSize &size)`

- **作用**：设置按钮图标的大小。
- **参数**：
  - `size`：图标的大小，类型为 `QSize`。

```cpp
pushButton->setIconSize(QSize(32, 32));
```

### 28. `iconSize()`

- **作用**：获取按钮图标的大小。
- **返回值**：`QSize`，按钮图标的大小。

```cpp
QSize iconSize = pushButton->iconSize();
```

### 29. `setAutoExclusive(bool autoExclusive)`

- **作用**：设置按钮在同一父级下是否自动互斥（仅对可选按钮有效）。
- **参数**：
  - `autoExclusive`：布尔值，`true` 表示自动互斥，`false` 表示不互斥。

```cpp
pushButton->setAutoExclusive(true);
```

### 30. `autoExclusive()`

- **作用**：检查按钮是否在同一父级下自动互斥（仅对可选按钮有效）。
- **返回值**：`bool`，如果按钮自动互斥则返回 `true`，否则返回 `false`。

```cpp
bool isAutoExclusive = pushButton->autoExclusive();
```

### 31. `setDown(bool down)`

- **作用**：设置按钮的按下状态。
- **参数**：
  - `down`：布尔值，`true` 表示按钮处于按下状态，`false` 表示按钮未按下。

```cpp
pushButton->setDown(true);
```

### 32. `isDown()`

- **作用**：检查按钮是否处于按下状态。
- **返回值**：`bool`，如果按钮处于按下状态则返回 `true`，否则返回 `false`。

```cpp
bool isButtonDown = pushButton->isDown();
```

### 33. `setStyleSheet(const QString &styleSheet)`

- **作用**：设置按钮的样式表，用于自定义按钮的外观。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。

```cpp
pushButton->setStyleSheet("background-color: blue; color: white;");
```

这些额外的方法和属性可以让你更灵活地控制 `QPushButton` 的行为和外观，帮助你实现更多的功能和更好的用户体验。
