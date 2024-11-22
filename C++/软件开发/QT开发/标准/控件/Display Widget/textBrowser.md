---
tags:
  - QT开发
---
# textBrowser

`QTextBrowser` 是 Qt 中用于显示富文本（HTML 格式）的控件。它不仅支持文本显示，还支持超链接、图片、富文本格式等。以下是 `QTextBrowser` 控件的详细函数方法及其作用：

### 1. **文本设置**

#### `setText(const QString &text)`

- **作用**：设置浏览器显示的文本（支持 HTML 格式）。
- **参数**：
  - `text`：要显示的文本，类型为 `QString`。

```cpp
textBrowser->setText("<h1>Hello, world!</h1>");
```

#### `setHtml(const QString &html)`

- **作用**：设置浏览器显示的 HTML 格式文本。
- **参数**：
  - `html`：要显示的 HTML 文本，类型为 `QString`。

```cpp
textBrowser->setHtml("<p>This is a <b>bold</b> paragraph.</p>");
```

#### `toPlainText()`

- **作用**：获取当前显示的纯文本（不包含 HTML 标签）。
- **返回值**：`QString`，当前显示的纯文本。

```cpp
QString plainText = textBrowser->toPlainText();
```

#### `toHtml()`

- **作用**：获取当前显示的 HTML 文本。
- **返回值**：`QString`，当前显示的 HTML 文本。

```cpp
QString htmlText = textBrowser->toHtml();
```

### 2. **超链接**

#### `setOpenExternalLinks(bool open)`

- **作用**：设置是否在外部浏览器中打开超链接。
- **参数**：
  - `open`：是否在外部浏览器中打开，类型为 `bool`（`true` 表示打开，`false` 表示不打开）。

```cpp
textBrowser->setOpenExternalLinks(true);
```

#### `openExternalLinks()`

- **作用**：检查是否设置为在外部浏览器中打开超链接。
- **返回值**：`bool`，如果设置为在外部浏览器中打开则返回 `true`，否则返回 `false`。

```cpp
bool openLinks = textBrowser->openExternalLinks();
```

#### `setSource(const QUrl &url)`

- **作用**：设置要加载的 URL。
- **参数**：
  - `url`：要加载的 URL，类型为 `QUrl`。

```cpp
textBrowser->setSource(QUrl("https://www.example.com"));
```

#### `source()`

- **作用**：获取当前加载的 URL。
- **返回值**：`QUrl`，当前的 URL。

```cpp
QUrl currentUrl = textBrowser->source();
```

### 3. **文本格式**

#### `setTextInteractionFlags(Qt::TextInteractionFlags flags)`

- **作用**：设置文本的交互标志，控制用户对文本的交互行为。
- **参数**：
  - `flags`：交互标志，类型为 `Qt::TextInteractionFlags`（例如 `Qt::TextSelectableByMouse`, `Qt::TextEditable`）。

```cpp
textBrowser->setTextInteractionFlags(Qt::TextSelectableByMouse);
```

#### `textInteractionFlags()`

- **作用**：获取文本的交互标志。
- **返回值**：`Qt::TextInteractionFlags`，当前的交互标志。

```cpp
Qt::TextInteractionFlags flags = textBrowser->textInteractionFlags();
```

### 4. **滚动条**

#### `setVerticalScrollBarPolicy(Qt::ScrollBarPolicy policy)`

- **作用**：设置垂直滚动条的策略。
- **参数**：
  - `policy`：滚动条策略，类型为 `Qt::ScrollBarPolicy`（例如 `Qt::ScrollBarAlwaysOn`, `Qt::ScrollBarAlwaysOff`）。

```cpp
textBrowser->setVerticalScrollBarPolicy(Qt::ScrollBarAlwaysOn);
```

#### `setHorizontalScrollBarPolicy(Qt::ScrollBarPolicy policy)`

- **作用**：设置水平滚动条的策略。
- **参数**：
  - `policy`：滚动条策略，类型为 `Qt::ScrollBarPolicy`（例如 `Qt::ScrollBarAlwaysOn`, `Qt::ScrollBarAlwaysOff`）。

```cpp
textBrowser->setHorizontalScrollBarPolicy(Qt::ScrollBarAlwaysOff);
```

### 5. **字体设置**

#### `setFont(const QFont &font)`

- **作用**：设置浏览器的字体。
- **参数**：
  - `font`：要设置的字体，类型为 `QFont`。

```cpp
textBrowser->setFont(QFont("Arial", 12));
```

#### `font()`

- **作用**：获取浏览器的字体。
- **返回值**：`QFont`，当前的字体。

```cpp
QFont currentFont = textBrowser->font();
```

### 6. **边距与填充**

#### `setMargin(int margin)`

- **作用**：设置文本与边框之间的边距。
- **参数**：
  - `margin`：边距，类型为 `int`。

```cpp
textBrowser->setMargin(10);
```

#### `margin()`

- **作用**：获取文本与边框之间的边距。
- **返回值**：`int`，当前的边距。

```cpp
int margin = textBrowser->margin();
```

### 7. **文本颜色与背景**

#### `setTextColor(const QColor &color)`

- **作用**：设置文本的颜色。
- **参数**：
  - `color`：要设置的颜色，类型为 `QColor`。

```cpp
textBrowser->setTextColor(Qt::blue);
```

#### `setTextBackgroundColor(const QColor &color)`

- **作用**：设置文本背景的颜色。
- **参数**：
  - `color`：要设置的背景颜色，类型为 `QColor`。

```cpp
textBrowser->setTextBackgroundColor(Qt::yellow);
```

### 8. **调整大小**

#### `adjustSize()`

- **作用**：调整浏览器的大小以适应其内容。
- **无参数**。

```cpp
textBrowser->adjustSize();
```

### 9. **事件处理**

#### `installEventFilter(QObject *filterObj)`

- **作用**：安装事件过滤器，用于拦截和处理事件。
- **参数**：
  - `filterObj`：事件过滤器对象，类型为 `QObject` 指针。

```cpp
textBrowser->installEventFilter(myEventFilter);
```

#### `removeEventFilter(QObject *filterObj)`

- **作用**：移除事件过滤器。
- **参数**：
  - `filterObj`：事件过滤器对象，类型为 `QObject` 指针。

```cpp
textBrowser->removeEventFilter(myEventFilter);
```

### 10. **链接操作**

#### `setOpenExternalLinks(bool open)`

- **作用**：设置是否在外部浏览器中打开超链接。
- **参数**：
  - `open`：是否在外部浏览器中打开，类型为 `bool`（`true` 表示打开，`false` 表示不打开）。

```cpp
textBrowser->setOpenExternalLinks(true);
```

#### `setOpenLinksInCurrentPage(bool open)`

- **作用**：设置是否在当前页内打开超链接。
- **参数**：
  - `open`：是否在当前页内打开，类型为 `bool`（`true` 表示打开，`false` 表示不打开）。

```cpp
textBrowser->setOpenLinksInCurrentPage(true);
```

### 11. **回退与前进**

#### `back()`

- **作用**：回退到上一个加载的内容。
- **无参数**。

```cpp
textBrowser->back();
```

#### `forward()`

- **作用**：前进到下一个加载的内容。
- **无参数**。

```cpp
textBrowser->forward();
```

#### `canGoBack()`

- **作用**：检查是否可以回退到上一个内容。
- **返回值**：`bool`，如果可以回退则返回 `true`，否则返回 `false`。

```cpp
bool canBack = textBrowser->canGoBack();
```

#### `canGoForward()`

- **作用**：检查是否可以前进到下一个内容。
- **返回值**：`bool`，如果可以前进则返回 `true`，否则返回 `false`。

```cpp
bool canForward = textBrowser->canGoForward();
```

### 12. **搜索功能**

#### `find(const QString &subString, QTextDocument::FindFlags options = QTextDocument::FindFlags())`

- **作用**：在文本中查找指定的子字符串。
- **参数**：
  - `subString`：要查找的子字符串，类型为 `QString`。
  - `options`：查找选项，类型为 `QTextDocument::FindFlags`（可选）。

```cpp
textBrowser->find("search term");
```

### 13. **设置和获取样式**

#### `setStyleSheet(const QString &styleSheet)`

- **作用**：设置控件的样式表。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。

```cpp
textBrowser->setStyleSheet("QTextBrowser { color: green

; }");
```

#### `styleSheet()`

- **作用**：获取控件的样式表。
- **返回值**：`QString`，当前的样式表。

```cpp
QString style = textBrowser->styleSheet();
```

除了之前提到的方法，`QTextBrowser` 还有一些其他函数方法，可以用于更细致地控制文本显示和用户交互：

### 14. **拖放操作**

#### `setDragEnabled(bool enable)`

- **作用**：启用或禁用拖放操作。
- **参数**：
  - `enable`：是否启用拖放操作，类型为 `bool`（`true` 表示启用，`false` 表示禁用）。

```cpp
textBrowser->setDragEnabled(true);
```

#### `dragEnterEvent(QDragEnterEvent *event)`

- **作用**：处理拖放进入事件。需要重写此方法以自定义行为。
- **参数**：
  - `event`：拖放进入事件对象，类型为 `QDragEnterEvent` 指针。

```cpp
void MyTextBrowser::dragEnterEvent(QDragEnterEvent *event) {
    // 自定义行为
}
```

#### `dragMoveEvent(QDragMoveEvent *event)`

- **作用**：处理拖放移动事件。需要重写此方法以自定义行为。
- **参数**：
  - `event`：拖放移动事件对象，类型为 `QDragMoveEvent` 指针。

```cpp
void MyTextBrowser::dragMoveEvent(QDragMoveEvent *event) {
    // 自定义行为
}
```

#### `dropEvent(QDropEvent *event)`

- **作用**：处理拖放释放事件。需要重写此方法以自定义行为。
- **参数**：
  - `event`：拖放释放事件对象，类型为 `QDropEvent` 指针。

```cpp
void MyTextBrowser::dropEvent(QDropEvent *event) {
    // 自定义行为
}
```

### 15. **事件过滤**

#### `installEventFilter(QObject *filterObj)`

- **作用**：安装事件过滤器，以拦截和处理事件。
- **参数**：
  - `filterObj`：事件过滤器对象，类型为 `QObject` 指针。

```cpp
textBrowser->installEventFilter(myEventFilter);
```

#### `removeEventFilter(QObject *filterObj)`

- **作用**：移除事件过滤器。
- **参数**：
  - `filterObj`：事件过滤器对象，类型为 `QObject` 指针。

```cpp
textBrowser->removeEventFilter(myEventFilter);
```

### 16. **锚点操作**

#### `setAnchorHovered(bool enable)`

- **作用**：设置是否显示超链接的悬停效果。
- **参数**：
  - `enable`：是否启用悬停效果，类型为 `bool`（`true` 表示启用，`false` 表示禁用）。

```cpp
textBrowser->setAnchorHovered(true);
```

#### `anchorClicked(const QUrl &url)`

- **作用**：处理用户点击超链接时的事件。
- **参数**：
  - `url`：被点击的链接的 URL，类型为 `QUrl`。

```cpp
connect(textBrowser, &QTextBrowser::anchorClicked, [](const QUrl &url) {
    qDebug() << "Anchor clicked:" << url.toString();
});
```

### 17. **图片显示**

#### `setTextInteractionFlags(Qt::TextInteractionFlags flags)`

- **作用**：设置文本的交互标志，例如是否允许用户选择文本。
- **参数**：
  - `flags`：交互标志，类型为 `Qt::TextInteractionFlags`（例如 `Qt::TextSelectableByMouse`, `Qt::TextEditable`）。

```cpp
textBrowser->setTextInteractionFlags(Qt::TextSelectableByMouse);
```

#### `setOpenExternalLinks(bool open)`

- **作用**：设置是否在外部浏览器中打开超链接。
- **参数**：
  - `open`：是否在外部浏览器中打开，类型为 `bool`（`true` 表示打开，`false` 表示不打开）。

```cpp
textBrowser->setOpenExternalLinks(true);
```

### 18. **高亮显示**

#### `highlightCurrentBlock()`

- **作用**：高亮显示当前块（例如在编辑模式下）。
- **无参数**。

```cpp
textBrowser->highlightCurrentBlock();
```

### 19. **窗口标题**

#### `setWindowTitle(const QString &title)`

- **作用**：设置窗口的标题。
- **参数**：
  - `title`：要设置的标题，类型为 `QString`。

```cpp
textBrowser->setWindowTitle("My Text Browser");
```

### 20. **保存和加载**

#### `save(const QString &fileName)`

- **作用**：将当前显示的内容保存到文件。
- **参数**：
  - `fileName`：保存的文件名，类型为 `QString`。

```cpp
textBrowser->save("saved_content.html");
```

#### `load(const QString &fileName)`

- **作用**：从文件加载内容。
- **参数**：
  - `fileName`：要加载的文件名，类型为 `QString`。

```cpp
textBrowser->load("saved_content.html");
```
