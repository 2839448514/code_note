---
tags:
  - QT开发
---
# label

`QLabel` 是 Qt 中的一个控件，用于显示文本或图像。以下是 `QLabel` 控件的详细函数方法及其作用：

### 1. **文本设置**

#### `setText(const QString &text)`

- **作用**：设置标签显示的文本。
- **参数**：
  - `text`：要显示的文本，类型为 `QString`。

```cpp
label->setText("Hello, world!");
```

#### `text()`

- **作用**：获取标签显示的文本。
- **返回值**：`QString`，当前显示的文本。

```cpp
QString currentText = label->text();
```

### 2. **图像设置**

#### `setPixmap(const QPixmap &pixmap)`

- **作用**：设置标签显示的图像。
- **参数**：
  - `pixmap`：要显示的图像，类型为 `QPixmap`。

```cpp
label->setPixmap(QPixmap("image.png"));
```

#### `pixmap()`

- **作用**：获取标签显示的图像。
- **返回值**：`QPixmap`，当前显示的图像。

```cpp
QPixmap currentPixmap = label->pixmap();
```

### 3. **对齐**

#### `setAlignment(Qt::Alignment alignment)`

- **作用**：设置文本或图像的对齐方式。
- **参数**：
  - `alignment`：对齐方式，类型为 `Qt::Alignment`（例如 `Qt::AlignLeft`, `Qt::AlignCenter`）。

```cpp
label->setAlignment(Qt::AlignCenter);
```

#### `alignment()`

- **作用**：获取文本或图像的对齐方式。
- **返回值**：`Qt::Alignment`，当前的对齐方式。

```cpp
Qt::Alignment currentAlignment = label->alignment();
```

### 4. **文本格式**

#### `setWordWrap(bool wordWrap)`

- **作用**：设置是否启用自动换行。
- **参数**：
  - `wordWrap`：是否启用，类型为 `bool`（`true` 表示启用，`false` 表示不启用）。

```cpp
label->setWordWrap(true);
```

#### `wordWrap()`

- **作用**：检查是否启用了自动换行。
- **返回值**：`bool`，如果启用了自动换行则返回 `true`，否则返回 `false`。

```cpp
bool isWordWrap = label->wordWrap();
```

### 5. **文本设置**

#### `setTextInteractionFlags(Qt::TextInteractionFlags flags)`

- **作用**：设置文本的交互标志，控制用户对文本的交互行为。
- **参数**：
  - `flags`：交互标志，类型为 `Qt::TextInteractionFlags`（例如 `Qt::TextSelectableByMouse`）。

```cpp
label->setTextInteractionFlags(Qt::TextSelectableByMouse);
```

#### `textInteractionFlags()`

- **作用**：获取文本的交互标志。
- **返回值**：`Qt::TextInteractionFlags`，当前的交互标志。

```cpp
Qt::TextInteractionFlags flags = label->textInteractionFlags();
```

### 6. **样式**

#### `setStyleSheet(const QString &styleSheet)`

- **作用**：设置标签的样式表，用于定制外观。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。

```cpp
label->setStyleSheet("QLabel { color: red; font-size: 20px; }");
```

### 7. **背景与边框**

#### `setAutoFillBackground(bool autoFill)`

- **作用**：设置标签是否自动填充背景。
- **参数**：
  - `autoFill`：是否自动填充，类型为 `bool`（`true` 表示自动填充，`false` 表示不填充）。

```cpp
label->setAutoFillBackground(true);
```

#### `setBackgroundRole(QPalette::Role role)`

- **作用**：设置标签的背景角色。
- **参数**：
  - `role`：背景角色，类型为 `QPalette::Role`（例如 `QPalette::Base`）。

```cpp
label->setBackgroundRole(QPalette::Base);
```

### 8. **字体**

#### `setFont(const QFont &font)`

- **作用**：设置标签的字体。
- **参数**：
  - `font`：要设置的字体，类型为 `QFont`。

```cpp
label->setFont(QFont("Arial", 16));
```

#### `font()`

- **作用**：获取标签的字体。
- **返回值**：`QFont`，当前的字体。

```cpp
QFont currentFont = label->font();
```

### 9. **设置几何属性**

#### `setGeometry(const QRect &rect)`

- **作用**：设置标签的几何位置和大小。
- **参数**：
  - `rect`：几何位置，类型为 `QRect`。

```cpp
label->setGeometry(QRect(10, 10, 200, 50));
```

### 10. **焦点与输入**

#### `setFocus()`

- **作用**：将焦点设置到标签上。
- **无参数**。

```cpp
label->setFocus();
```

#### `focusPolicy()`

- **作用**：获取标签的焦点策略。
- **返回值**：`Qt::FocusPolicy`，当前的焦点策略。

```cpp
Qt::FocusPolicy policy = label->focusPolicy();
```

### 11. **事件处理**

#### `installEventFilter(QObject *filterObj)`

- **作用**：安装事件过滤器，用于拦截和处理事件。
- **参数**：
  - `filterObj`：事件过滤器对象，类型为 `QObject` 指针。

```cpp
label->installEventFilter(myEventFilter);
```

#### `removeEventFilter(QObject *filterObj)`

- **作用**：移除事件过滤器。
- **参数**：
  - `filterObj`：事件过滤器对象，类型为 `QObject` 指针。

```cpp
label->removeEventFilter(myEventFilter);
```

### 12. **工具提示**

#### `setToolTip(const QString &toolTip)`

- **作用**：设置标签的工具提示文本，当鼠标悬停时显示。
- **参数**：
  - `toolTip`：工具提示文本，类型为 `QString`。

```cpp
label->setToolTip("This is a label.");
```

#### `toolTip()`

- **作用**：获取标签的工具提示文本。
- **返回值**：`QString`，当前的工具提示文本。

```cpp
QString toolTipText = label->toolTip();
```

### 13. **背景与前景色**

#### `setPalette(const QPalette &palette)`

- **作用**：设置标签的调色板。
- **参数**：
  - `palette`：调色板对象，类型为 `QPalette`。

```cpp
QPalette palette;
palette.setColor(QPalette::WindowText, Qt::blue);
label->setPalette(palette);
```

#### `palette()`

- **作用**：获取标签的调色板。
- **返回值**：`QPalette`，当前的调色板。

```cpp
QPalette palette = label->palette();
```

### 14. **响应大小**

#### `adjustSize()`

- **作用**：调整标签的大小以适应其内容。
- **无参数**。

```cpp
label->adjustSize();
```

除了之前提到的方法，`QLabel` 还有一些其他的函数方法和属性，可以用于更多的自定义和控制：

### 15. **工具提示**

#### `setToolTipDuration(int msec)`

- **作用**：设置工具提示显示的持续时间（毫秒）。
- **参数**：
  - `msec`：持续时间，单位为毫秒，类型为 `int`。

```cpp
label->setToolTipDuration(2000); // 显示2秒
```

#### `toolTipDuration()`

- **作用**：获取工具提示的持续时间。
- **返回值**：`int`，工具提示的持续时间，单位为毫秒。

```cpp
int duration = label->toolTipDuration();
```

### 16. **图像设置**

#### `setScaledContents(bool scaled)`

- **作用**：设置是否自动缩放图像以适应标签的大小。
- **参数**：
  - `scaled`：是否缩放，类型为 `bool`（`true` 表示缩放，`false` 表示不缩放）。

```cpp
label->setScaledContents(true);
```

#### `isScaledContents()`

- **作用**：检查是否启用了图像缩放。
- **返回值**：`bool`，如果启用了缩放则返回 `true`，否则返回 `false`。

```cpp
bool scaled = label->isScaledContents();
```

### 17. **文本交互**

#### `setTextInteractionFlags(Qt::TextInteractionFlags flags)`

- **作用**：设置文本的交互标志，控制用户对文本的交互行为。
- **参数**：
  - `flags`：交互标志，类型为 `Qt::TextInteractionFlags`（例如 `Qt::TextSelectableByMouse`, `Qt::TextEditable`）。

```cpp
label->setTextInteractionFlags(Qt::TextSelectableByMouse);
```

#### `textInteractionFlags()`

- **作用**：获取文本的交互标志。
- **返回值**：`Qt::TextInteractionFlags`，当前的交互标志。

```cpp
Qt::TextInteractionFlags flags = label->textInteractionFlags();
```

### 18. **焦点与交互**

#### `setFocusPolicy(Qt::FocusPolicy policy)`

- **作用**：设置标签的焦点策略。
- **参数**：
  - `policy`：焦点策略，类型为 `Qt::FocusPolicy`（例如 `Qt::NoFocus`, `Qt::StrongFocus`）。

```cpp
label->setFocusPolicy(Qt::NoFocus);
```

#### `focusPolicy()`

- **作用**：获取标签的焦点策略。
- **返回值**：`Qt::FocusPolicy`，当前的焦点策略。

```cpp
Qt::FocusPolicy policy = label->focusPolicy();
```

### 19. **边距与填充**

#### `setMargin(int margin)`

- **作用**：设置标签内容与边框之间的边距。
- **参数**：
  - `margin`：边距，类型为 `int`。

```cpp
label->setMargin(10);
```

#### `margin()`

- **作用**：获取标签内容与边框之间的边距。
- **返回值**：`int`，当前的边距。

```cpp
int margin = label->margin();
```

#### `setIndent(int indent)`

- **作用**：设置标签文本的缩进。
- **参数**：
  - `indent`：缩进量，类型为 `int`。

```cpp
label->setIndent(20);
```

#### `indent()`

- **作用**：获取标签文本的缩进量。
- **返回值**：`int`，当前的缩进量。

```cpp
int indent = label->indent();
```

### 20. **文本渲染**

#### `setTextFormat(Qt::TextFormat format)`

- **作用**：设置标签文本的格式（例如富文本）。
- **参数**：
  - `format`：文本格式，类型为 `Qt::TextFormat`（例如 `Qt::PlainText`, `Qt::RichText`）。

```cpp
label->setTextFormat(Qt::RichText);
```

#### `textFormat()`

- **作用**：获取标签文本的格式。
- **返回值**：`Qt::TextFormat`，当前的文本格式。

```cpp
Qt::TextFormat format = label->textFormat();
```

### 21. **对齐方式**

#### `setAlignment(Qt::Alignment alignment)`

- **作用**：设置标签文本或图像的对齐方式。
- **参数**：
  - `alignment`：对齐方式，类型为 `Qt::Alignment`（例如 `Qt::AlignLeft`, `Qt::AlignCenter`）。

```cpp
label->setAlignment(Qt::AlignCenter);
```

### 22. **最大和最小尺寸**

#### `setMaximumSize(int w, int h)`

- **作用**：设置标签的最大尺寸。
- **参数**：
  - `w`：最大宽度，类型为 `int`。
  - `h`：最大高度，类型为 `int`。

```cpp
label->setMaximumSize(200, 100);
```

#### `setMinimumSize(int w, int h)`

- **作用**：设置标签的最小尺寸。
- **参数**：
  - `w`：最小宽度，类型为 `int`。
  - `h`：最小高度，类型为 `int`。

```cpp
label->setMinimumSize(100, 50);
```

### 23. **尺寸策略**

#### `setSizePolicy(QSizePolicy::Policy horizontalPolicy, QSizePolicy::Policy verticalPolicy)`

- **作用**：设置标签的尺寸策略。
- **参数**：
  - `horizontalPolicy`：水平尺寸策略，类型为 `QSizePolicy::Policy`（例如 `QSizePolicy::Fixed`）。
  - `verticalPolicy`：垂直尺寸策略，类型为 `QSizePolicy::Policy`（例如 `QSizePolicy::Expanding`）。

```cpp
label->setSizePolicy(QSizePolicy::Expanding, QSizePolicy::Fixed);
```

### 24. **转换**

#### `toHtml()`

- **作用**：将标签的文本转换为 HTML 格式。
- **返回值**：`QString`，HTML 格式的文本。

```cpp
QString htmlText = label->toHtml();
```

### 25. **设置焦点**

#### `setFocus()`

- **作用**：将焦点设置到标签上（如果标签支持焦点）。
- **无参数**。

```cpp
label->setFocus();
```
