`QFontComboBox` 是 Qt 中一个用于显示和选择字体的控件，它结合了 `QComboBox` 和字体选择的功能。以下是 `QFontComboBox` 的详细函数方法及其作用：

### 常用函数方法

### 1. `setFontFilters(QFontComboBox::FontFilter filter)`

- **作用**：设置字体过滤器，用于指定要显示的字体类别。
- **参数**：
  - `filter`：字体过滤器，类型为 `QFontComboBox::FontFilter`，可以是以下任意组合：
    - `QFontComboBox::AllFonts`：显示所有字体
    - `QFontComboBox::ScalableFonts`：显示可缩放字体
    - `QFontComboBox::MonospacedFonts`：显示等宽字体
    - `QFontComboBox::ProportionalFonts`：显示比例字体

```cpp
fontComboBox->setFontFilters(QFontComboBox::AllFonts);
```

### 2. `fontFilters()`

- **作用**：获取当前的字体过滤器。
- **返回值**：`QFontComboBox::FontFilter`，当前的字体过滤器。

```cpp
QFontComboBox::FontFilter filters = fontComboBox->fontFilters();
```

### 3. `setCurrentFont(const QFont &font)`

- **作用**：设置当前选中的字体。
- **参数**：
  - `font`：要设置的字体，类型为 `QFont`。

```cpp
QFont font("Arial", 12);
fontComboBox->setCurrentFont(font);
```

### 4. `currentFont()`

- **作用**：获取当前选中的字体。
- **返回值**：`QFont`，当前选中的字体。

```cpp
QFont currentFont = fontComboBox->currentFont();
```

### 5. `setCurrentIndex(int index)`

- **作用**：设置当前选中的项的索引。
- **参数**：
  - `index`：要设置的项的索引，类型为 `int`。

```cpp
fontComboBox->setCurrentIndex(2);
```

### 6. `currentIndex()`

- **作用**：获取当前选中的项的索引。
- **返回值**：`int`，当前选中的项的索引。

```cpp
int index = fontComboBox->currentIndex();
```

### 7. `setEditable(bool editable)`

- **作用**：设置下拉列表是否可编辑。如果为 `true`，用户可以在下拉列表中输入自定义字体名称。
- **参数**：
  - `editable`：布尔值，`true` 表示可编辑，`false` 表示不可编辑。

```cpp
fontComboBox->setEditable(true);
```

### 8. `isEditable()`

- **作用**：检查下拉列表是否可编辑。
- **返回值**：`bool`，如果可编辑则返回 `true`，否则返回 `false`。

```cpp
bool editable = fontComboBox->isEditable();
```

### 9. `setFont(const QFont &font)`

- **作用**：设置字体组合框的字体，这会影响到字体组合框的显示。
- **参数**：
  - `font`：要设置的字体，类型为 `QFont`。

```cpp
fontComboBox->setFont(QFont("Times New Roman", 10));
```

### 10. `font()`

- **作用**：获取字体组合框的字体。
- **返回值**：`QFont`，当前字体组合框的字体。

```cpp
QFont font = fontComboBox->font();
```

### 11. `setFontFilter(QFontComboBox::FontFilter filter)`

- **作用**：设置字体过滤器，用于指定要显示的字体类别。
- **参数**：
  - `filter`：字体过滤器，类型为 `QFontComboBox::FontFilter`，可以是以下任意组合：
    - `QFontComboBox::AllFonts`：显示所有字体
    - `QFontComboBox::ScalableFonts`：显示可缩放字体
    - `QFontComboBox::MonospacedFonts`：显示等宽字体
    - `QFontComboBox::ProportionalFonts`：显示比例字体

```cpp
fontComboBox->setFontFilter(QFontComboBox::ScalableFonts);
```

### 12. `setStyleSheet(const QString &styleSheet)`

- **作用**：设置字体组合框的样式表，用于自定义外观。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。

```cpp
fontComboBox->setStyleSheet("background-color: lightgray;");
```

### 13. `setSizePolicy(const QSizePolicy &policy)`

- **作用**：设置字体组合框的尺寸策略，用于控制其在布局中的扩展行为。
- **参数**：
  - `policy`：尺寸策略，类型为 `QSizePolicy`。

```cpp
fontComboBox->setSizePolicy(QSizePolicy::Expanding, QSizePolicy::Fixed);
```

### 14. `sizePolicy()`

- **作用**：获取字体组合框的尺寸策略。
- **返回值**：`QSizePolicy`，当前的尺寸策略。

```cpp
QSizePolicy policy = fontComboBox->sizePolicy();
```

### 15. `setMinimumSize(const QSize &size)`

- **作用**：设置字体组合框的最小尺寸。
- **参数**：
  - `size`：最小尺寸，类型为 `QSize`。

```cpp
fontComboBox->setMinimumSize(QSize(200, 30));
```

### 16. `minimumSize()`

- **作用**：获取字体组合框的最小尺寸。
- **返回值**：`QSize`，当前的最小尺寸。

```cpp
QSize minSize = fontComboBox->minimumSize();
```

### 17. `setMaximumSize(const QSize &size)`

- **作用**：设置字体组合框的最大尺寸。
- **参数**：
  - `size`：最大尺寸，类型为 `QSize`。

```cpp
fontComboBox->setMaximumSize(QSize(300, 40));
```

### 18. `maximumSize()`

- **作用**：获取字体组合框的最大尺寸。
- **返回值**：`QSize`，当前的最大尺寸。

```cpp
QSize maxSize = fontComboBox->maximumSize();
```

### 19. `setSizeHint(const QSize &sizeHint)`

- **作用**：设置字体组合框的大小提示，用于布局计算。
- **参数**：
  - `sizeHint`：大小提示，类型为 `QSize`。

```cpp
fontComboBox->setSizeHint(QSize(250, 30));
```

### 20. `sizeHint()`

- **作用**：获取字体组合框的大小提示。
- **返回值**：`QSize`，当前的大小提示。

```cpp
QSize sizeHint = fontComboBox->sizeHint();
```

### 21. `setToolTip(const QString &toolTip)`

- **作用**：设置字体组合框的工具提示。
- **参数**：
  - `toolTip`：工具提示文本，类型为 `QString`。

```cpp
fontComboBox->setToolTip("Select a font");
```

### 22. `toolTip()`

- **作用**：获取字体组合框的工具提示文本。
- **返回值**：`QString`，当前的工具提示文本。

```cpp
QString toolTip = fontComboBox->toolTip();
```

### 23. `setStatusTip(const QString &statusTip)`

- **作用**：设置字体组合框的状态提示文本。
- **参数**：
  - `statusTip`：状态提示文本，类型为 `QString`。

```cpp
fontComboBox->setStatusTip("Choose a font from the list");
```

### 24. `statusTip()`

- **作用**：获取字体组合框的状态提示文本。
- **返回值**：`QString`，当前的状态提示文本。

```cpp
QString statusTip = fontComboBox->statusTip();
```

### 25. `setWhatsThis(const QString &whatsThis)`

- **作用**：设置字体组合框的帮助文本，通常用于提供详细的帮助信息。
- **参数**：
  - `whatsThis`：帮助文本，类型为 `QString`。

```cpp
fontComboBox->setWhatsThis("Select a font from the list to use in your document.");
```

### 26. `whatsThis()`

- **作用**：获取字体组合框的帮助文本。
- **返回值**：`QString`，当前的帮助文本。

```cpp
QString whatsThis = fontComboBox->whatsThis();
```

### 27. `setFocusPolicy(Qt::FocusPolicy policy)`

- **作用**：设置字体组合框的焦点策略，用于控制如何接受焦点。
- **参数**：
  - `policy`：焦点策略，类型为 `Qt::FocusPolicy`。

```cpp
fontComboBox->setFocusPolicy(Qt::StrongFocus);
```

### 28. `focusPolicy()`

- **作用**：获取字体组合框的焦点策略。
- **返回值**：`Qt::

FocusPolicy`，当前的焦点策略。

```cpp
Qt::FocusPolicy policy = fontComboBox->focusPolicy();
```