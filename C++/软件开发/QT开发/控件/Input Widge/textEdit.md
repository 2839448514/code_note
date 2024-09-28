---
tags:
  - QT开发
---
# textEdit

`QTextEdit` 是 Qt 中的一个富文本编辑控件，支持多种文本格式、样式和内容操作。以下是 `QTextEdit` 的详细函数方法及其作用：

### 常用函数方法

### 1. **文本操作**

#### `setText(const QString &text)`

- **作用**：设置文本编辑器的内容。
- **参数**：
  - `text`：要设置的文本，类型为 `QString`。

```cpp
textEdit->setText("Hello, World!");
```

#### `toPlainText()`

- **作用**：获取文本编辑器中的纯文本（去除格式）。
- **返回值**：`QString`，文本内容。

```cpp
QString plainText = textEdit->toPlainText();
```

#### `setHtml(const QString &html)`

- **作用**：设置文本编辑器的内容为 HTML 格式。
- **参数**：
  - `html`：要设置的 HTML 文本，类型为 `QString`。

```cpp
textEdit->setHtml("<h1>Hello, World!</h1>");
```

#### `toHtml()`

- **作用**：获取文本编辑器中的 HTML 内容。
- **返回值**：`QString`，HTML 内容。

```cpp
QString htmlContent = textEdit->toHtml();
```

### 2. **文本格式**

#### `setFont(const QFont &font)`

- **作用**：设置文本编辑器的字体。
- **参数**：
  - `font`：要设置的字体，类型为 `QFont`。

```cpp
textEdit->setFont(QFont("Arial", 12));
```

#### `font()`

- **作用**：获取文本编辑器的字体。
- **返回值**：`QFont`，当前的字体。

```cpp
QFont currentFont = textEdit->font();
```

#### `setFontPointSize(qreal pointSize)`

- **作用**：设置文本编辑器的字体大小。
- **参数**：
  - `pointSize`：字体大小，类型为 `qreal`。

```cpp
textEdit->setFontPointSize(14);
```

#### `fontPointSize()`

- **作用**：获取文本编辑器的字体大小。
- **返回值**：`qreal`，当前的字体大小。

```cpp
qreal fontSize = textEdit->fontPointSize();
```

### 3. **文本对齐**

#### `setAlignment(Qt::Alignment alignment)`

- **作用**：设置文本的对齐方式。
- **参数**：
  - `alignment`：对齐方式，类型为 `Qt::Alignment`（例如 `Qt::AlignLeft`、`Qt::AlignCenter`、`Qt::AlignRight`）。

```cpp
textEdit->setAlignment(Qt::AlignCenter);
```

#### `alignment()`

- **作用**：获取文本的对齐方式。
- **返回值**：`Qt::Alignment`，当前的对齐方式。

```cpp
Qt::Alignment alignment = textEdit->alignment();
```

### 4. **撤销与重做**

#### `undo()`

- **作用**：撤销上一步操作。
- **无参数**。

```cpp
textEdit->undo();
```

#### `redo()`

- **作用**：重做上一步被撤销的操作。
- **无参数**。

```cpp
textEdit->redo();
```

### 5. **文本选择**

#### `selectAll()`

- **作用**：选择文本编辑器中的所有文本。
- **无参数**。

```cpp
textEdit->selectAll();
```

#### `setTextCursor(const QTextCursor &cursor)`

- **作用**：设置文本编辑器的光标位置和状态。
- **参数**：
  - `cursor`：要设置的文本光标，类型为 `QTextCursor`。

```cpp
QTextCursor cursor = textEdit->textCursor();
cursor.movePosition(QTextCursor::End);
textEdit->setTextCursor(cursor);
```

#### `textCursor()`

- **作用**：获取文本编辑器中的文本光标。
- **返回值**：`QTextCursor`，当前的文本光标。

```cpp
QTextCursor cursor = textEdit->textCursor();
```

### 6. **文本样式**

#### `setTextColor(const QColor &color)`

- **作用**：设置文本的颜色。
- **参数**：
  - `color`：要设置的颜色，类型为 `QColor`。

```cpp
textEdit->setTextColor(Qt::red);
```

#### `textColor()`

- **作用**：获取文本的颜色。
- **返回值**：`QColor`，当前的文本颜色。

```cpp
QColor color = textEdit->textColor();
```

#### `setTextBackgroundColor(const QColor &color)`

- **作用**：设置文本背景的颜色。
- **参数**：
  - `color`：要设置的背景颜色，类型为 `QColor`。

```cpp
textEdit->setTextBackgroundColor(Qt::yellow);
```

#### `textBackgroundColor()`

- **作用**：获取文本背景的颜色。
- **返回值**：`QColor`，当前的背景颜色。

```cpp
QColor bgColor = textEdit->textBackgroundColor();
```

### 7. **文本段落**

#### `setTextInteractionFlags(Qt::TextInteractionFlags flags)`

- **作用**：设置文本编辑器的交互模式。
- **参数**：
  - `flags`：交互标志，类型为 `Qt::TextInteractionFlags`（例如 `Qt::TextEditorInteraction`、`Qt::TextSelectableByKeyboard`）。

```cpp
textEdit->setTextInteractionFlags(Qt::TextEditorInteraction);
```

#### `textInteractionFlags()`

- **作用**：获取文本编辑器的交互模式。
- **返回值**：`Qt::TextInteractionFlags`，当前的交互模式。

```cpp
Qt::TextInteractionFlags flags = textEdit->textInteractionFlags();
```

### 8. **行与段落**

#### `setLineWrapMode(QTextEdit::LineWrapMode mode)`

- **作用**：设置文本编辑器的自动换行模式。
- **参数**：
  - `mode`：换行模式，类型为 `QTextEdit::LineWrapMode`（例如 `QTextEdit::NoWrap`、`QTextEdit::WidgetWidth`）。

```cpp
textEdit->setLineWrapMode(QTextEdit::WidgetWidth);
```

#### `lineWrapMode()`

- **作用**：获取文本编辑器的自动换行模式。
- **返回值**：`QTextEdit::LineWrapMode`，当前的换行模式。

```cpp
QTextEdit::LineWrapMode mode = textEdit->lineWrapMode();
```

### 9. **插入与删除**

#### `insertPlainText(const QString &text)`

- **作用**：在光标位置插入纯文本。
- **参数**：
  - `text`：要插入的文本，类型为 `QString`。

```cpp
textEdit->insertPlainText("Inserted text.");
```

#### `insertHtml(const QString &html)`

- **作用**：在光标位置插入 HTML 格式的文本。
- **参数**：
  - `html`：要插入的 HTML 文本，类型为 `QString`。

```cpp
textEdit->insertHtml("<b>Inserted HTML text</b>");
```

#### `append(const QString &text)`

- **作用**：将文本追加到文本编辑器的末尾。
- **参数**：
  - `text`：要追加的文本，类型为 `QString`。

```cpp
textEdit->append("Appended text.");
```

### 10. **滚动**

#### `setScrollBarPolicy(Qt::Orientation orientation, Qt::ScrollBarPolicy policy)`

- **作用**：设置指定方向的滚动条策略。
- **参数**：
  - `orientation`：滚动条方向，类型为 `Qt::Orientation`（例如 `Qt::Vertical`、`Qt::Horizontal`）。
  - `policy`：滚动条策略，类型为 `Qt::ScrollBarPolicy`（例如 `Qt::ScrollBarAsNeeded`、`Qt::ScrollBarAlwaysOff`）。

```cpp
textEdit->setScrollBarPolicy(Qt::Vertical, Qt::ScrollBarAlwaysOn);
```

#### `setVerticalScrollBarPolicy(Qt::ScrollBarPolicy policy)`

- **作用**：设置垂直滚动条的策略。
- **参数**：
  - `policy`：滚动条策略，类型为 `Qt::ScrollBarPolicy`。

```cpp
textEdit->setVerticalScrollBarPolicy(Qt::ScrollBarAsNeeded);
```

#### `setHorizontalScrollBarPolicy(Qt::ScrollBarPolicy policy)`

- **作用**：设置水平滚动条的策略。
- **参数**：
  - `policy`：滚动条策略，类型为 `Qt::ScrollBarPolicy`。

```cpp
textEdit->setHorizontalScrollBarPolicy(Qt::ScrollBarAlwaysOff);
```

### 11. **文档与块**

#### `document()`

- **作用**：获取文本编辑器的 `QTextDocument` 对象。
- **返回值**：`QTextDocument*`，当前的 `QTextDocument` 对象。

```cpp
QTextDocument *doc = textEdit->document();
```

#### `setDocument(QTextDocument *document)`

 **作用**：设置文本编辑器的文档对象。
- **参数**：
  - `document`：要设置的文档对象，类型为 `QTextDocument*`。

```cpp
textEdit->setDocument(new QTextDocument);
```

#### `setDocumentTitle(const QString &title)`

- **作用**：设置文本文档的标题。
- **参数**：
  - `title`：要设置的标题，类型为 `QString`。

```cpp
textEdit->setDocumentTitle("Document Title");
```

#### `documentTitle()`

- **作用**：获取文本文档的标题。
- **返回值**：`QString`，当前的文档标题。

```cpp
QString title = textEdit->documentTitle();
```

### 12. **光标位置**

#### `setCursorWidth(int width)`

- **作用**：设置光标的宽度。
- **参数**：
  - `width`：光标宽度，类型为 `int`。

```cpp
textEdit->setCursorWidth(2);
```

#### `cursorWidth()`

- **作用**：获取光标的宽度。
- **返回值**：`int`，当前的光标宽度。

```cpp
int cursorWidth = textEdit->cursorWidth();
```

### 13. **文本块**

#### `blockCount()`

- **作用**：获取文本块的数量。
- **返回值**：`int`，文本块的数量。

```cpp
int blockCount = textEdit->blockCount();
```

#### `firstVisibleBlock()`

- **作用**：获取第一个可见文本块。
- **返回值**：`QTextBlock`，第一个可见的文本块。

```cpp
QTextBlock block = textEdit->firstVisibleBlock();
```

#### `lastVisibleBlock()`

- **作用**：获取最后一个可见文本块。
- **返回值**：`QTextBlock`，最后一个可见的文本块。

```cpp
QTextBlock block = textEdit->lastVisibleBlock();
```

当然，`QTextEdit` 提供了许多其他功能来支持丰富的文本编辑和处理需求。以下是一些额外的函数方法及其作用：

### 14. **光标操作**

#### `moveCursor(QTextCursor::MoveOperation op, QTextCursor::MoveMode mode = QTextCursor::MoveAnchor)`

- **作用**：移动光标到指定位置。
- **参数**：
  - `op`：光标移动操作，类型为 `QTextCursor::MoveOperation`（例如 `QTextCursor::Start`, `QTextCursor::End`）。
  - `mode`：光标移动模式，类型为 `QTextCursor::MoveMode`（例如 `QTextCursor::MoveAnchor`、`QTextCursor::KeepAnchor`）。

```cpp
textEdit->moveCursor(QTextCursor::Start);
```

#### `setTextCursor(const QTextCursor &cursor)`

- **作用**：设置文本编辑器的光标。
- **参数**：
  - `cursor`：要设置的光标，类型为 `QTextCursor`。

```cpp
QTextCursor cursor = textEdit->textCursor();
cursor.movePosition(QTextCursor::End);
textEdit->setTextCursor(cursor);
```

### 15. **自动换行**

#### `setLineWrapMode(QTextEdit::LineWrapMode mode)`

- **作用**：设置文本自动换行模式。
- **参数**：
  - `mode`：换行模式，类型为 `QTextEdit::LineWrapMode`（例如 `QTextEdit::NoWrap`、`QTextEdit::WidgetWidth`）。

```cpp
textEdit->setLineWrapMode(QTextEdit::WidgetWidth);
```

#### `lineWrapMode()`

- **作用**：获取当前的换行模式。
- **返回值**：`QTextEdit::LineWrapMode`，当前的换行模式。

```cpp
QTextEdit::LineWrapMode mode = textEdit->lineWrapMode();
```

### 16. **样式表与背景**

#### `setStyleSheet(const QString &styleSheet)`

- **作用**：设置文本编辑器的样式表，允许自定义外观。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。

```cpp
textEdit->setStyleSheet("background-color: lightgray;");
```

#### `setAutoFormatting(QTextEdit::AutoFormattingFlags format)`

- **作用**：设置自动格式化选项。
- **参数**：
  - `format`：自动格式化标志，类型为 `QTextEdit::AutoFormattingFlags`（例如 `QTextEdit::AutoBulletList`、`QTextEdit::AutoTextItalic`）。

```cpp
textEdit->setAutoFormatting(QTextEdit::AutoBulletList);
```

#### `autoFormatting()`

- **作用**：获取当前的自动格式化选项。
- **返回值**：`QTextEdit::AutoFormattingFlags`，当前的自动格式化选项。

```cpp
QTextEdit::AutoFormattingFlags format = textEdit->autoFormatting();
```

### 17. **清除与重置**

#### `clear()`

- **作用**：清除文本编辑器中的所有内容。
- **无参数**。

```cpp
textEdit->clear();
```

#### `clearUndoRedoStacks()`

- **作用**：清除撤销和重做的历史记录。
- **无参数**。

```cpp
textEdit->clearUndoRedoStacks();
```

### 18. **复制与剪切**

#### `cut()`

- **作用**：剪切选中的文本。
- **无参数**。

```cpp
textEdit->cut();
```

#### `copy()`

- **作用**：复制选中的文本。
- **无参数**。

```cpp
textEdit->copy();
```

### 19. **粘贴**

#### `paste()`

- **作用**：粘贴剪贴板中的内容到当前光标位置。
- **无参数**。

```cpp
textEdit->paste();
```

### 20. **文本操作**

#### `find(const QString &exp, QTextDocument::FindFlags options = QTextDocument::FindFlags())`

- **作用**：在文本中查找指定的文本。
- **参数**：
  - `exp`：要查找的文本，类型为 `QString`。
  - `options`：查找选项，类型为 `QTextDocument::FindFlags`（例如 `QTextDocument::FindBackward`）。

```cpp
textEdit->find("search text");
```

### 21. **文件操作**

#### `load(const QString &fileName)`

- **作用**：从指定的文件加载内容到文本编辑器中。
- **参数**：
  - `fileName`：文件名，类型为 `QString`。

```cpp
textEdit->load("document.txt");
```

#### `save(const QString &fileName)`

- **作用**：将文本编辑器的内容保存到指定的文件。
- **参数**：
  - `fileName`：文件名，类型为 `QString`。

```cpp
textEdit->save("document.txt");
```

### 22. **打印**

#### `print(QPrinter *printer)`

- **作用**：将文本编辑器的内容打印到指定的打印机。
- **参数**：
  - `printer`：打印机对象，类型为 `QPrinter*`。

```cpp
QPrinter printer;
textEdit->print(&printer);
```

### 23. **撤销与重做状态**

#### `canUndo()`

- **作用**：检查是否可以撤销操作。
- **返回值**：`bool`，如果可以撤销则返回 `true`，否则返回 `false`。

```cpp
bool canUndo = textEdit->canUndo();
```

#### `canRedo()`

- **作用**：检查是否可以重做操作。
- **返回值**：`bool`，如果可以重做则返回 `true`，否则返回 `false`。

```cpp
bool canRedo = textEdit->canRedo();
```

### 24. **焦点管理**

#### `setFocus(Qt::FocusReason reason)`

- **作用**：设置焦点到文本编辑器，并指定焦点原因。
- **参数**：
  - `reason`：焦点原因，类型为 `Qt::FocusReason`（例如 `Qt::MouseFocusReason`、`Qt::TabFocusReason`）。

```cpp
textEdit->setFocus(Qt::MouseFocusReason);
```

### 25. **撤销/重做堆栈**

#### `undoStack()`

- **作用**：获取撤销堆栈，用于管理撤销和重做操作。
- **返回值**：`QUndoStack*`，当前的撤销堆栈。

```cpp
QUndoStack *undoStack = textEdit->undoStack();
```

### 26. **格式化**

#### `setCurrentCharFormat(const QTextCharFormat &format)`

- **作用**：设置当前字符格式，影响当前选中的文本。
- **参数**：
  - `format`：字符格式，类型为 `QTextCharFormat`。

```cpp
QTextCharFormat format;
format.setFontWeight(QFont::Bold);
textEdit->setCurrentCharFormat(format);
```

#### `currentCharFormat()`

- **作用**：获取当前字符格式。
- **返回值**：`QTextCharFormat`，当前的字符格式。

```cpp
QTextCharFormat format = textEdit->currentCharFormat();
```

#### `setCurrentBlockFormat(const QTextBlockFormat &format)`

- **作用**：设置当前文本块格式。
- **参数**：
  - `format`：文本块格式，类型为 `QTextBlockFormat`。

```cpp
QTextBlockFormat blockFormat;
blockFormat.setAlignment(Qt::AlignCenter);
textEdit->setCurrentBlockFormat(blockFormat);
```

#### `currentBlockFormat()`

- **作用**：获取当前文本块格式。
- **返回值**：`QTextBlockFormat`，当前的文本块格式。

```cpp
QTextBlockFormat blockFormat = textEdit->currentBlockFormat();
```

这些方法和函数可以帮助你更全面地利用 `QTextEdit` 控件的功能，实现各种文本处理和编辑需求。
