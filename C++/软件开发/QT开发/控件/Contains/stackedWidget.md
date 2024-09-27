`QStackedWidget` 是一个可以管理多个页面的控件，它通过堆叠的方式只显示一个页面。以下是 `QStackedWidget` 的详细函数方法及其作用：

### 1. **页面管理**

#### `void addWidget(QWidget *widget)`

- **作用**：向堆叠控件中添加一个页面。
- **参数**：
  - `widget`：要添加的页面控件，类型为 `QWidget*`。
- **返回值**：`void`，无返回值。

```cpp
QWidget *page1 = new QWidget();
stackedWidget->addWidget(page1);
```

#### `int indexOf(QWidget *widget) const`

- **作用**：获取指定页面控件的索引。
- **参数**：
  - `widget`：页面控件，类型为 `QWidget*`。
- **返回值**：`int`，指定页面控件的索引，如果找不到则返回 `-1`。

```cpp
int index = stackedWidget->indexOf(page1);
```

#### `QWidget *widget(int index) const`

- **作用**：获取指定索引处的页面控件。
- **参数**：
  - `index`：页面的索引，类型为 `int`。
- **返回值**：`QWidget*`，指定索引处的页面控件。

```cpp
QWidget *page = stackedWidget->widget(0);
```

#### `void removeWidget(QWidget *widget)`

- **作用**：从堆叠控件中移除指定页面控件。
- **参数**：
  - `widget`：要移除的页面控件，类型为 `QWidget*`。
- **返回值**：`void`，无返回值。

```cpp
stackedWidget->removeWidget(page1);
```

#### `void setCurrentIndex(int index)`

- **作用**：设置当前显示的页面。
- **参数**：
  - `index`：要显示的页面索引，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
stackedWidget->setCurrentIndex(1); // 显示索引为1的页面
```

#### `int currentIndex() const`

- **作用**：获取当前显示的页面的索引。
- **返回值**：`int`，当前显示的页面的索引。

```cpp
int currentIndex = stackedWidget->currentIndex();
```

#### `QWidget *currentWidget() const`

- **作用**：获取当前显示的页面控件。
- **返回值**：`QWidget*`，当前显示的页面控件。

```cpp
QWidget *currentPage = stackedWidget->currentWidget();
```

### 2. **布局和大小策略**

#### `void setLayoutDirection(Qt::LayoutDirection direction)`

- **作用**：设置控件的布局方向（如从左到右或从右到左）。
- **参数**：
  - `direction`：布局方向，类型为 `Qt::LayoutDirection`。
- **返回值**：`void`，无返回值。

```cpp
stackedWidget->setLayoutDirection(Qt::LeftToRight);
```

#### `Qt::LayoutDirection layoutDirection() const`

- **作用**：获取控件的布局方向。
- **返回值**：`Qt::LayoutDirection`，控件的布局方向。

```cpp
Qt::LayoutDirection direction = stackedWidget->layoutDirection();
```

#### `void setSizePolicy(const QSizePolicy &policy)`

- **作用**：设置控件的大小策略。
- **参数**：
  - `policy`：大小策略，类型为 `QSizePolicy`。
- **返回值**：`void`，无返回值。

```cpp
QSizePolicy policy(QSizePolicy::Expanding, QSizePolicy::Expanding);
stackedWidget->setSizePolicy(policy);
```

#### `QSizePolicy sizePolicy() const`

- **作用**：获取控件的大小策略。
- **返回值**：`QSizePolicy`，控件的大小策略。

```cpp
QSizePolicy policy = stackedWidget->sizePolicy();
```

### 3. **信号和槽**

#### `void currentChanged(int index)`

- **作用**：当当前页面发生变化时发出的信号。
- **参数**：
  - `index`：当前显示页面的索引，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
connect(stackedWidget, &QStackedWidget::currentChanged, [](int index) {
    qDebug() << "Current page index changed to:" << index;
});
```

### 4. **其他功能**

#### `int count() const`

- **作用**：获取堆叠控件中的页面数量。
- **返回值**：`int`，页面的数量。

```cpp
int pageCount = stackedWidget->count();
```

#### `void setStyleSheet(const QString &styleSheet)`

- **作用**：设置堆叠控件的样式表。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。
- **返回值**：`void`，无返回值。

```cpp
stackedWidget->setStyleSheet("QStackedWidget { border: 1px solid gray; }");
```

#### `QString styleSheet() const`

- **作用**：获取堆叠控件的样式表字符串。
- **返回值**：`QString`，当前的样式表字符串。

```cpp
QString styleSheet = stackedWidget->styleSheet();
```

### 5. **自定义行为和外观**

#### `void setWindowTitle(const QString &title)`

- **作用**：设置窗口的标题。
- **参数**：
  - `title`：窗口标题，类型为 `QString`。
- **返回值**：`void`，无返回值。

```cpp
stackedWidget->setWindowTitle("My Stacked Widget");
```

#### `QString windowTitle() const`

- **作用**：获取窗口的标题。
- **返回值**：`QString`，窗口的标题。

```cpp
QString title = stackedWidget->windowTitle();
```

在 `QStackedWidget` 的常用方法和功能之外，还有一些更深入的功能和细节可以探索：

### 6. **样式和布局**

#### `void setSpacing(int spacing)`

- **作用**：设置控件之间的间距。
- **参数**：
  - `spacing`：间距值，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
stackedWidget->setSpacing(10); // 设置控件之间的间距为10像素
```

#### `int spacing() const`

- **作用**：获取控件之间的间距。
- **返回值**：`int`，控件之间的间距值。

```cpp
int currentSpacing = stackedWidget->spacing();
```

### 7. **页面的尺寸和可见性**

#### `void setMinimumSize(const QSize &size)`

- **作用**：设置控件的最小尺寸。
- **参数**：
  - `size`：最小尺寸，类型为 `QSize`。
- **返回值**：`void`，无返回值。

```cpp
stackedWidget->setMinimumSize(QSize(300, 200));
```

#### `QSize minimumSize() const`

- **作用**：获取控件的最小尺寸。
- **返回值**：`QSize`，控件的最小尺寸。

```cpp
QSize minSize = stackedWidget->minimumSize();
```

### 8. **对齐和布局**

#### `void setAlignment(Qt::Alignment alignment)`

- **作用**：设置控件的对齐方式。
- **参数**：
  - `alignment`：对齐方式，类型为 `Qt::Alignment`。
- **返回值**：`void`，无返回值。

```cpp
stackedWidget->setAlignment(Qt::AlignCenter);
```

#### `Qt::Alignment alignment() const`

- **作用**：获取控件的对齐方式。
- **返回值**：`Qt::Alignment`，控件的对齐方式。

```cpp
Qt::Alignment currentAlignment = stackedWidget->alignment();
```

### 9. **事件处理**

#### `void resizeEvent(QResizeEvent *event)`

- **作用**：处理控件的调整大小事件。
- **参数**：
  - `event`：调整大小事件，类型为 `QResizeEvent*`。
- **返回值**：`void`，无返回值。

```cpp
void MyStackedWidget::resizeEvent(QResizeEvent *event) {
    QStackedWidget::resizeEvent(event);
    // 自定义处理代码
}
```

#### `void paintEvent(QPaintEvent *event)`

- **作用**：处理控件的绘制事件。
- **参数**：
  - `event`：绘制事件，类型为 `QPaintEvent*`。
- **返回值**：`void`，无返回值。

```cpp
void MyStackedWidget::paintEvent(QPaintEvent *event) {
    QStackedWidget::paintEvent(event);
    // 自定义绘制代码
}
```

### 10. **对话框和窗口管理**

#### `void setModal(bool modal)`

- **作用**：设置控件是否为模态窗口。
- **参数**：
  - `modal`：布尔值，`true` 表示模态，`false` 表示非模态。
- **返回值**：`void`，无返回值。

```cpp
stackedWidget->setModal(true);
```

#### `bool isModal() const`

- **作用**：检查控件是否为模态窗口。
- **返回值**：`bool`，如果是模态窗口则返回 `true`，否则返回 `false`。

```cpp
bool modal = stackedWidget->isModal();
```

### 11. **布局和调整**

#### `void setSizePolicy(QSizePolicy::Policy horizontal, QSizePolicy::Policy vertical)`

- **作用**：设置控件的水平和垂直大小策略。
- **参数**：
  - `horizontal`：水平大小策略，类型为 `QSizePolicy::Policy`。
  - `vertical`：垂直大小策略，类型为 `QSizePolicy::Policy`。
- **返回值**：`void`，无返回值。

```cpp
stackedWidget->setSizePolicy(QSizePolicy::Expanding, QSizePolicy::Expanding);
```

#### `QSizePolicy::Policy horizontalSizePolicy() const`

- **作用**：获取控件的水平大小策略。
- **返回值**：`QSizePolicy::Policy`，水平大小策略。

```cpp
QSizePolicy::Policy horizontalPolicy = stackedWidget->horizontalSizePolicy();
```

#### `QSizePolicy::Policy verticalSizePolicy() const`

- **作用**：获取控件的垂直大小策略。
- **返回值**：`QSizePolicy::Policy`，垂直大小策略。

```cpp
QSizePolicy::Policy verticalPolicy = stackedWidget->verticalSizePolicy();
```

### 12. **动画效果**

#### `void setCurrentWidget(QWidget *widget)`

- **作用**：设置当前显示的页面控件。
- **参数**：
  - `widget`：要显示的页面控件，类型为 `QWidget*`。
- **返回值**：`void`，无返回值。

```cpp
stackedWidget->setCurrentWidget(page1);
```

#### `QWidget *currentWidget() const`

- **作用**：获取当前显示的页面控件。
- **返回值**：`QWidget*`，当前显示的页面控件。

```cpp
QWidget *currentPage = stackedWidget->currentWidget();
```
