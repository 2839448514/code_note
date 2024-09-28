---
tags:
  - QT开发
---
# commandLinkButton

`QCommandLinkButton` 是 Qt 中用于创建具有链接风格外观的按钮控件，通常用于提供一种类似于超链接的界面元素。以下是 `QCommandLinkButton` 常用的方法和函数及其作用：

### 常用函数方法

### 1. `setText(const QString &text)`

- **作用**：设置命令链接按钮的主文本。
- **参数**：
  - `text`：要设置的主文本，类型为 `QString`。

```cpp
commandLinkButton->setText("Main Action");
```

### 2. `text()`

- **作用**：获取命令链接按钮的主文本。
- **返回值**：`QString`，按钮的主文本内容。

```cpp
QString buttonText = commandLinkButton->text();
```

### 3. `setDescription(const QString &description)`

- **作用**：设置命令链接按钮的描述文本，通常用于显示在主文本下方。
- **参数**：
  - `description`：要设置的描述文本，类型为 `QString`。

```cpp
commandLinkButton->setDescription("Click to perform the main action.");
```

### 4. `description()`

- **作用**：获取命令链接按钮的描述文本。
- **返回值**：`QString`，按钮的描述文本内容。

```cpp
QString buttonDescription = commandLinkButton->description();
```

### 5. `setIcon(const QIcon &icon)`

- **作用**：设置命令链接按钮的图标。
- **参数**：
  - `icon`：要设置的图标，类型为 `QIcon`。

```cpp
QIcon icon(":/resources/icon.png");
commandLinkButton->setIcon(icon);
```

### 6. `icon()`

- **作用**：获取命令链接按钮的图标。
- **返回值**：`QIcon`，按钮的图标。

```cpp
QIcon buttonIcon = commandLinkButton->icon();
```

### 7. `setIconSize(const QSize &size)`

- **作用**：设置命令链接按钮图标的大小。
- **参数**：
  - `size`：图标的大小，类型为 `QSize`。

```cpp
commandLinkButton->setIconSize(QSize(32, 32));
```

### 8. `iconSize()`

- **作用**：获取命令链接按钮图标的大小。
- **返回值**：`QSize`，按钮图标的大小。

```cpp
QSize iconSize = commandLinkButton->iconSize();
```

### 9. `setAutoDefault(bool autoDefault)`

- **作用**：设置按钮是否自动成为默认按钮。
- **参数**：
  - `autoDefault`：布尔值，`true` 表示按钮是默认按钮，`false` 表示不是。

```cpp
commandLinkButton->setAutoDefault(true);
```

### 10. `isAutoDefault()`

- **作用**：检查按钮是否自动成为默认按钮。
- **返回值**：`bool`，如果按钮是默认按钮则返回 `true`，否则返回 `false`。

```cpp
bool isAutoDefault = commandLinkButton->isAutoDefault();
```

### 11. `setEnabled(bool enabled)`

- **作用**：设置按钮是否可用。
- **参数**：
  - `enabled`：布尔值，`true` 表示按钮可用，`false` 表示按钮不可用。

```cpp
commandLinkButton->setEnabled(true);
```

### 12. `isEnabled()`

- **作用**：检查按钮是否可用。
- **返回值**：`bool`，如果按钮可用则返回 `true`，否则返回 `false`。

```cpp
bool isEnabled = commandLinkButton->isEnabled();
```

### 13. `setVisible(bool visible)`

- **作用**：设置按钮是否可见。
- **参数**：
  - `visible`：布尔值，`true` 表示按钮可见，`false` 表示按钮不可见。

```cpp
commandLinkButton->setVisible(true);
```

### 14. `isVisible()`

- **作用**：检查按钮是否可见。
- **返回值**：`bool`，如果按钮可见则返回 `true`，否则返回 `false`。

```cpp
bool isVisible = commandLinkButton->isVisible();
```

### 15. `setStyleSheet(const QString &styleSheet)`

- **作用**：设置按钮的样式表，用于自定义按钮的外观。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。

```cpp
commandLinkButton->setStyleSheet("background-color: lightblue; color: black;");
```

### 16. `setFocus()`

- **作用**：将焦点设置到按钮上。
- **无参数**。

```cpp
commandLinkButton->setFocus();
```

### 17. `hasFocus()`

- **作用**：检查按钮是否有焦点。
- **返回值**：`bool`，如果按钮有焦点则返回 `true`，否则返回 `false`。

```cpp
bool hasFocus = commandLinkButton->hasFocus();
```

### 常用信号

### 18. `clicked()`

- **作用**：当按钮被点击时发出信号。
- **无参数**。

```cpp
connect(commandLinkButton, &QCommandLinkButton::clicked, this, &YourClass::onCommandLinkButtonClicked);

void YourClass::onCommandLinkButtonClicked() {
    // 处理按钮点击事件
}
```

`QCommandLinkButton` 的功能和方法相对较简单，大部分常用功能已经涵盖了。不过，这里有一些额外的功能和方法，尽管它们不如上述方法常用，但仍然有助于进一步自定义按钮的行为和外观。

### 额外方法

### 19. `setDefault(bool defaultButton)`

- **作用**：设置按钮是否为默认按钮。通常，默认按钮在用户按下 `Enter` 键时会被触发。
- **参数**：
  - `defaultButton`：布尔值，`true` 表示按钮是默认按钮，`false` 表示不是。

```cpp
commandLinkButton->setDefault(true);
```

### 20. `setToolTip(const QString &toolTip)`

- **作用**：设置按钮的工具提示文本。当用户将鼠标悬停在按钮上时显示。
- **参数**：
  - `toolTip`：工具提示文本，类型为 `QString`。

```cpp
commandLinkButton->setToolTip("This is a command link button.");
```

### 21. `toolTip()`

- **作用**：获取按钮的工具提示文本。
- **返回值**：`QString`，按钮的工具提示文本。

```cpp
QString toolTipText = commandLinkButton->toolTip();
```

### 22. `setWhatsThis(const QString &whatsThis)`

- **作用**：设置按钮的“这是什么”文本，用于帮助系统中，提供额外的信息。
- **参数**：
  - `whatsThis`：文本，类型为 `QString`。

```cpp
commandLinkButton->setWhatsThis("This button is used to perform a specific command.");
```

### 23. `whatsThis()`

- **作用**：获取按钮的“这是什么”文本。
- **返回值**：`QString`，按钮的“这是什么”文本。

```cpp
QString whatsThisText = commandLinkButton->whatsThis();
```

### 24. `setFont(const QFont &font)`

- **作用**：设置按钮的字体。
- **参数**：
  - `font`：字体对象，类型为 `QFont`。

```cpp
QFont font("Arial", 12);
commandLinkButton->setFont(font);
```

### 25. `font()`

- **作用**：获取按钮的字体。
- **返回值**：`QFont`，按钮的字体。

```cpp
QFont buttonFont = commandLinkButton->font();
```

### 26. `setGeometry(const QRect &rect)`

- **作用**：设置按钮的位置和大小。
- **参数**：
  - `rect`：矩形区域，类型为 `QRect`，指定按钮的位置和大小。

```cpp
commandLinkButton->setGeometry(QRect(10, 10, 150, 50));
```

### 27. `setStyle(const QString &style)`

- **作用**：设置按钮的样式。虽然这个方法更常用于旧版本的 Qt，但在一些定制化场景中可能仍然有用。
- **参数**：
  - `style`：样式字符串，类型为 `QString`。

```cpp
commandLinkButton->setStyle("background-color: yellow; color: black;");
```

### 28. `update()`

- **作用**：请求重绘按钮。这在需要手动刷新按钮显示时可能会用到。
- **无参数**。

```cpp
commandLinkButton->update();
```

### 29. `setLayoutDirection(Qt::LayoutDirection direction)`

- **作用**：设置按钮的布局方向，用于支持从右到左的布局。
- **参数**：
  - `direction`：布局方向，类型为 `Qt::LayoutDirection`，例如 `Qt::LeftToRight` 或 `Qt::RightToLeft`。

```cpp
commandLinkButton->setLayoutDirection(Qt::RightToLeft);
```

### 30. `layoutDirection()`

- **作用**：获取按钮的布局方向。
- **返回值**：`Qt::LayoutDirection`，按钮的布局方向。

```cpp
Qt::LayoutDirection layoutDir = commandLinkButton->layoutDirection();
```
