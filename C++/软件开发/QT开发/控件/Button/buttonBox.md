---
tags:
  - QT开发
---
# buttonBox

`QDialogButtonBox` 是 Qt 中用于在对话框中显示标准按钮（如“确定”、“取消”、“应用”等）的控件。它可以自动排列按钮，并提供简便的方式来处理常见的对话框按钮。以下是 `QDialogButtonBox` 的详细函数方法及其作用：

### 常用函数方法

### 1. `setStandardButtons(QDialogButtonBox::StandardButtons buttons)`

- **作用**：设置标准按钮。这些按钮是预定义的，具有常用的功能。
- **参数**：
  - `buttons`：标准按钮集合，类型为 `QDialogButtonBox::StandardButtons`。可以使用按位或运算符 (`|`) 组合多个标准按钮。

```cpp
QDialogButtonBox *buttonBox = new QDialogButtonBox;
buttonBox->setStandardButtons(QDialogButtonBox::Ok | QDialogButtonBox::Cancel);
```

### 2. `standardButtons()`

- **作用**：获取当前设置的标准按钮集合。
- **返回值**：`QDialogButtonBox::StandardButtons`，当前设置的标准按钮。

```cpp
QDialogButtonBox::StandardButtons buttons = buttonBox->standardButtons();
```

### 3. `addButton(QAbstractButton *button, QDialogButtonBox::ButtonRole role)`

- **作用**：添加自定义按钮到按钮盒子中，并指定其角色。
- **参数**：
  - `button`：要添加的按钮，类型为 `QAbstractButton`。
  - `role`：按钮角色，类型为 `QDialogButtonBox::ButtonRole`，如 `QDialogButtonBox::AcceptRole`、`QDialogButtonBox::RejectRole`。

```cpp
QPushButton *customButton = new QPushButton("Custom");
buttonBox->addButton(customButton, QDialogButtonBox::ActionRole);
```

### 4. `button(QDialogButtonBox::StandardButton button)`

- **作用**：获取按钮盒子中指定标准按钮的指针。
- **参数**：
  - `button`：标准按钮，类型为 `QDialogButtonBox::StandardButton`。
- **返回值**：`QAbstractButton*`，指定标准按钮的指针。

```cpp
QPushButton *okButton = qobject_cast<QPushButton*>(buttonBox->button(QDialogButtonBox::Ok));
```

### 5. `removeButton(QAbstractButton *button)`

- **作用**：从按钮盒子中移除指定的按钮。
- **参数**：
  - `button`：要移除的按钮，类型为 `QAbstractButton`。

```cpp
buttonBox->removeButton(okButton);
```

### 6. `setCenterButtons(const QList<QAbstractButton *> &buttons)`

- **作用**：设置中心区域显示的按钮。按钮将被居中显示。
- **参数**：
  - `buttons`：按钮列表，类型为 `QList<QAbstractButton*>`。

```cpp
QPushButton *button1 = new QPushButton("Button 1");
QPushButton *button2 = new QPushButton("Button 2");
buttonBox->setCenterButtons({button1, button2});
```

### 7. `centerButtons()`

- **作用**：获取当前在中心区域显示的按钮列表。
- **返回值**：`QList<QAbstractButton*>`，中心区域显示的按钮列表。

```cpp
QList<QAbstractButton*> centerButtons = buttonBox->centerButtons();
```

### 8. `setOrientation(Qt::Orientation orientation)`

- **作用**：设置按钮盒子的方向，水平或垂直。
- **参数**：
  - `orientation`：方向，类型为 `Qt::Orientation`，可以是 `Qt::Horizontal` 或 `Qt::Vertical`。

```cpp
buttonBox->setOrientation(Qt::Vertical);
```

### 9. `orientation()`

- **作用**：获取按钮盒子的当前方向。
- **返回值**：`Qt::Orientation`，按钮盒子的当前方向。

```cpp
Qt::Orientation orientation = buttonBox->orientation();
```

### 10. `setLayoutDirection(Qt::LayoutDirection direction)`

- **作用**：设置按钮盒子的布局方向，用于支持从右到左的布局。
- **参数**：
  - `direction`：布局方向，类型为 `Qt::LayoutDirection`，例如 `Qt::LeftToRight` 或 `Qt::RightToLeft`。

```cpp
buttonBox->setLayoutDirection(Qt::RightToLeft);
```

### 11. `layoutDirection()`

- **作用**：获取按钮盒子的布局方向。
- **返回值**：`Qt::LayoutDirection`，按钮盒子的布局方向。

```cpp
Qt::LayoutDirection layoutDirection = buttonBox->layoutDirection();
```

### 12. `setStyleSheet(const QString &styleSheet)`

- **作用**：设置按钮盒子的样式表，用于自定义其外观。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。

```cpp
buttonBox->setStyleSheet("background-color: lightgray; border: 1px solid black;");
```

### 13. `setEnabled(bool enabled)`

- **作用**：设置按钮盒子是否可用。
- **参数**：
  - `enabled`：布尔值，`true` 表示按钮盒子可用，`false` 表示不可用。

```cpp
buttonBox->setEnabled(true);
```

### 14. `isEnabled()`

- **作用**：检查按钮盒子是否可用。
- **返回值**：`bool`，如果按钮盒子可用则返回 `true`，否则返回 `false`。

```cpp
bool isEnabled = buttonBox->isEnabled();
```

### 15. `setVisible(bool visible)`

- **作用**：设置按钮盒子是否可见。
- **参数**：
  - `visible`：布尔值，`true` 表示按钮盒子可见，`false` 表示不可见。

```cpp
buttonBox->setVisible(true);
```

### 16. `isVisible()`

- **作用**：检查按钮盒子是否可见。
- **返回值**：`bool`，如果按钮盒子可见则返回 `true`，否则返回 `false`。

```cpp
bool isVisible = buttonBox->isVisible();
```

### 17. `setFocus()`

- **作用**：将焦点设置到按钮盒子上。
- **无参数**。

```cpp
buttonBox->setFocus();
```

### 18. `hasFocus()`

- **作用**：检查按钮盒子是否有焦点。
- **返回值**：`bool`，如果按钮盒子有焦点则返回 `true`，否则返回 `false`。

```cpp
bool hasFocus = buttonBox->hasFocus();
```

### 19. `addButton(QAbstractButton *button, QDialogButtonBox::ButtonRole role)`

- **作用**：将按钮添加到按钮盒子中，并指定其角色（例如接受、拒绝、应用等）。
- **参数**：
  - `button`：要添加的按钮，类型为 `QAbstractButton`。
  - `role`：按钮的角色，类型为 `QDialogButtonBox::ButtonRole`，例如 `QDialogButtonBox::AcceptRole`、`QDialogButtonBox::RejectRole`。

```cpp
QPushButton *applyButton = new QPushButton("Apply");
buttonBox->addButton(applyButton, QDialogButtonBox::ApplyRole);
```

### 20. `removeButton(QAbstractButton *button)`

- **作用**：从按钮盒子中移除指定的按钮。
- **参数**：
  - `button`：要移除的按钮，类型为 `QAbstractButton`。

```cpp
buttonBox->removeButton(applyButton);
```

`QDialogButtonBox` 的核心功能和方法已经在之前的回答中涵盖，但以下是一些额外的、较少使用但仍可能有用的函数和方法：

### 额外方法

### 21. `setFocusProxy(QWidget *proxy)`

- **作用**：设置焦点代理，使得按钮盒子能够将焦点转移到另一个指定的控件上。
- **参数**：
  - `proxy`：要设置为焦点代理的控件，类型为 `QWidget*`。

```cpp
buttonBox->setFocusProxy(anotherWidget);
```

### 22. `focusProxy()`

- **作用**：获取焦点代理控件。
- **返回值**：`QWidget*`，当前的焦点代理控件。

```cpp
QWidget* focusProxy = buttonBox->focusProxy();
```

### 23. `setSizePolicy(const QSizePolicy &policy)`

- **作用**：设置按钮盒子的尺寸策略，用于控制其在布局中的扩展行为。
- **参数**：
  - `policy`：尺寸策略，类型为 `QSizePolicy`。

```cpp
QSizePolicy policy(QSizePolicy::Expanding, QSizePolicy::Fixed);
buttonBox->setSizePolicy(policy);
```

### 24. `sizePolicy()`

- **作用**：获取按钮盒子的尺寸策略。
- **返回值**：`QSizePolicy`，按钮盒子的尺寸策略。

```cpp
QSizePolicy policy = buttonBox->sizePolicy();
```

### 25. `setLayout(QLayout *layout)`

- **作用**：设置按钮盒子的布局。通常使用标准布局，但可以自定义布局。
- **参数**：
  - `layout`：布局对象，类型为 `QLayout*`。

```cpp
QVBoxLayout *layout = new QVBoxLayout;
buttonBox->setLayout(layout);
```

### 26. `layout()`

- **作用**：获取按钮盒子的布局。
- **返回值**：`QLayout*`，按钮盒子的布局对象。

```cpp
QLayout *layout = buttonBox->layout();
```

### 27. `setStyle(const QString &style)`

- **作用**：设置按钮盒子的样式。虽然 `setStyle` 方法在 Qt 中不再推荐使用，但在某些情况下可能仍然适用。
- **参数**：
  - `style`：样式字符串，类型为 `QString`。

```cpp
buttonBox->setStyle("background-color: white;");
```

### 28. `updateGeometry()`

- **作用**：请求按钮盒子重新计算其几何属性。通常在更改大小策略或布局后需要调用此方法。
- **无参数**。

```cpp
buttonBox->updateGeometry();
```

### 29. `setMinimumSize(const QSize &size)`

- **作用**：设置按钮盒子的最小尺寸。
- **参数**：
  - `size`：最小尺寸，类型为 `QSize`。

```cpp
buttonBox->setMinimumSize(QSize(200, 50));
```

### 30. `minimumSize()`

- **作用**：获取按钮盒子的最小尺寸。
- **返回值**：`QSize`，按钮盒子的最小尺寸。

```cpp
QSize minSize = buttonBox->minimumSize();
```

### 31. `setMaximumSize(const QSize &size)`

- **作用**：设置按钮盒子的最大尺寸。
- **参数**：
  - `size`：最大尺寸，类型为 `QSize`。

```cpp
buttonBox->setMaximumSize(QSize(400, 100));
```

### 32. `maximumSize()`

- **作用**：获取按钮盒子的最大尺寸。
- **返回值**：`QSize`，按钮盒子的最大尺寸。

```cpp
QSize maxSize = buttonBox->maximumSize();
```

### 33. `setSizeHint(const QSize &sizeHint)`

- **作用**：设置按钮盒子的大小提示。
- **参数**：
  - `sizeHint`：大小提示，类型为 `QSize`。

```cpp
buttonBox->setSizeHint(QSize(300, 70));
```

### 34. `sizeHint()`

- **作用**：获取按钮盒子的大小提示。
- **返回值**：`QSize`，按钮盒子的大小提示。

```cpp
QSize sizeHint = buttonBox->sizeHint();
```
