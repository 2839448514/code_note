`QToolBox` 是 Qt 中用于显示一组工具页的控件。每个工具页都可以包含不同的控件，用户可以通过点击工具栏中的标签来切换显示的内容。以下是 `QToolBox` 的详细函数方法及其作用：

### 1. **构造函数**

#### `QToolBox(QWidget *parent = nullptr)`

- **作用**：创建一个 `QToolBox` 对象。
- **参数**：
  - `parent`：父窗口部件，类型为 `QWidget*`（可选）。
- **返回值**：`QToolBox` 对象。

```cpp
QToolBox *toolBox = new QToolBox(parentWidget);
```

### 2. **添加和移除工具页**

#### `int addItem(QWidget *widget, const QString &text)`

- **作用**：向工具箱中添加一个工具页。
- **参数**：
  - `widget`：要添加的工具页内容，类型为 `QWidget*`。
  - `text`：工具页的标题文本，类型为 `QString`。
- **返回值**：`int`，工具页的索引。

```cpp
int index = toolBox->addItem(new QLabel("Page Content"), "Page Title");
```

#### `int addItem(QWidget *widget, const QIcon &icon, const QString &text)`

- **作用**：向工具箱中添加一个带有图标的工具页。
- **参数**：
  - `widget`：要添加的工具页内容，类型为 `QWidget*`。
  - `icon`：工具页的图标，类型为 `QIcon`。
  - `text`：工具页的标题文本，类型为 `QString`。
- **返回值**：`int`，工具页的索引。

```cpp
int index = toolBox->addItem(new QLabel("Page Content"), QIcon("icon.png"), "Page Title");
```

#### `void removeItem(int index)`

- **作用**：从工具箱中移除指定的工具页。
- **参数**：
  - `index`：要移除的工具页的索引，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
toolBox->removeItem(index);
```

#### `void clear()`

- **作用**：移除所有工具页。
- **返回值**：`void`，无返回值。

```cpp
toolBox->clear();
```

### 3. **获取和设置当前工具页**

#### `int currentIndex() const`

- **作用**：获取当前显示的工具页的索引。
- **返回值**：`int`，当前工具页的索引。

```cpp
int index = toolBox->currentIndex();
```

#### `void setCurrentIndex(int index)`

- **作用**：设置当前显示的工具页。
- **参数**：
  - `index`：要显示的工具页的索引，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
toolBox->setCurrentIndex(1); // 切换到索引为1的工具页
```

#### `QWidget *widget(int index) const`

- **作用**：获取指定工具页的内容控件。
- **参数**：
  - `index`：工具页的索引，类型为 `int`。
- **返回值**：`QWidget*`，指定工具页的内容控件。

```cpp
QWidget *pageWidget = toolBox->widget(0); // 获取索引为0的工具页的内容控件
```

### 4. **工具页的标题和图标**

#### `QString itemText(int index) const`

- **作用**：获取指定工具页的标题文本。
- **参数**：
  - `index`：工具页的索引，类型为 `int`。
- **返回值**：`QString`，指定工具页的标题文本。

```cpp
QString title = toolBox->itemText(0); // 获取索引为0的工具页的标题文本
```

#### `void setItemText(int index, const QString &text)`

- **作用**：设置指定工具页的标题文本。
- **参数**：
  - `index`：工具页的索引，类型为 `int`。
  - `text`：新的标题文本，类型为 `QString`。
- **返回值**：`void`，无返回值。

```cpp
toolBox->setItemText(0, "New Title"); // 设置索引为0的工具页的标题文本
```

#### `QIcon itemIcon(int index) const`

- **作用**：获取指定工具页的图标。
- **参数**：
  - `index`：工具页的索引，类型为 `int`。
- **返回值**：`QIcon`，指定工具页的图标。

```cpp
QIcon icon = toolBox->itemIcon(0); // 获取索引为0的工具页的图标
```

#### `void setItemIcon(int index, const QIcon &icon)`

- **作用**：设置指定工具页的图标。
- **参数**：
  - `index`：工具页的索引，类型为 `int`。
  - `icon`：新的图标，类型为 `QIcon`。
- **返回值**：`void`，无返回值。

```cpp
toolBox->setItemIcon(0, QIcon("newIcon.png")); // 设置索引为0的工具页的图标
```

### 5. **工具页的可见性和启用状态**

#### `bool isItemEnabled(int index) const`

- **作用**：检查指定工具页是否启用。
- **参数**：
  - `index`：工具页的索引，类型为 `int`。
- **返回值**：`bool`，如果启用则返回 `true`，否则返回 `false`。

```cpp
bool isEnabled = toolBox->isItemEnabled(0);
```

#### `void setItemEnabled(int index, bool enabled)`

- **作用**：设置指定工具页的启用状态。
- **参数**：
  - `index`：工具页的索引，类型为 `int`。
  - `enabled`：布尔值，`true` 表示启用，`false` 表示禁用。
- **返回值**：`void`，无返回值。

```cpp
toolBox->setItemEnabled(0, false); // 禁用索引为0的工具页
```

### 6. **工具页的内容控件**

#### `QWidget *currentWidget() const`

- **作用**：获取当前显示的工具页的内容控件。
- **返回值**：`QWidget*`，当前显示工具页的内容控件。

```cpp
QWidget *currentWidget = toolBox->currentWidget();
```

#### `void setCurrentWidget(QWidget *widget)`

- **作用**：设置当前显示的工具页的内容控件。
- **参数**：
  - `widget`：要显示的工具页的内容控件，类型为 `QWidget*`。
- **返回值**：`void`，无返回值。

```cpp
toolBox->setCurrentWidget(myWidget); // 设置当前显示的工具页的内容控件
```

### 7. **事件处理**

#### `void resizeEvent(QResizeEvent *event) override`

- **作用**：处理工具箱的尺寸变化事件。
- **参数**：
  - `event`：尺寸变化事件对象，类型为 `QResizeEvent*`。
- **返回值**：`void`，无返回值。

```cpp
void MyToolBox::resizeEvent(QResizeEvent *event) {
    QToolBox::resizeEvent(event);
    // 处理尺寸变化的额外代码
}
```

#### `void paintEvent(QPaintEvent *event) override`

- **作用**：处理工具箱的绘制事件。
- **参数**：
  - `event`：绘制事件对象，类型为 `QPaintEvent*`。
- **返回值**：`void`，无返回值。

```cpp
void MyToolBox::paintEvent(QPaintEvent *event) {
    QToolBox::paintEvent(event);
    // 处理绘制的额外代码
}
```

### 8. **布局和大小**

#### `void setLayout(QLayout *layout)`

- **作用**：设置工具箱的布局。
- **参数**：
  - `layout`：布局对象，类型为 `QLayout*`。
- **返回值**：`void`，无返回值。

```cpp
QVBoxLayout *layout = new QVBoxLayout();
toolBox->setLayout(layout);
```

#### `QLayout *layout() const`

- **作用**：获取工具箱的布局。
- **返回值**：`QLayout*`，当前的布局对象。

```cpp
QLayout *currentLayout = toolBox->layout();
```

在 `QToolBox` 的基本功能和方法之外，还有一些高级用法和细节，你可以探索：

### 9. **自定义工具页样式**

#### `void setItemToolTip(int index, const QString &toolTip)`

- **作用**：设置指定工具页的提示信息。
- **参数**：
  - `index`：工具页的索引，类型为 `int`。
  - `toolTip`：提示信息，类型为 `QString`。
- **返回值**：`void`，无返回值。

```cpp
toolBox->setItemToolTip(0, "This is a tooltip for the first page.");
```

#### `QString itemToolTip(int index) const`

- **作用**：获取指定工具页的提示信息。
- **参数**：
  - `index`：工具页的索引，类型为 `int`。
- **返回值**：`QString`，工具页的提示信息。

```cpp
QString toolTip = toolBox->itemToolTip(0);
```

### 10. **图标和标题的布局**

#### `void setItemIconSize(const QSize &size)`

- **作用**：设置工具页图标的大小。
- **参数**：
  - `size`：图标的大小，类型为 `QSize`。
- **返回值**：`void`，无返回值。

```cpp
toolBox->setItemIconSize(QSize(24, 24));
```

#### `QSize itemIconSize() const`

- **作用**：获取工具页图标的大小。
- **返回值**：`QSize`，当前图标的大小。

```cpp
QSize iconSize = toolBox->itemIconSize();
```

### 11. **动画和过渡效果**

#### `void setStyleSheet(const QString &styleSheet)`

- **作用**：设置工具箱的样式表，以自定义其外观。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。
- **返回值**：`void`，无返回值。

```cpp
toolBox->setStyleSheet("QToolBox::tab { font: bold; }");
```

#### `QString styleSheet() const`

- **作用**：获取工具箱的样式表字符串。
- **返回值**：`QString`，当前样式表字符串。

```cpp
QString currentStyleSheet = toolBox->styleSheet();
```

### 12. **工具箱的布局和外观**

#### `void setTabPosition(QTabWidget::TabPosition position)`

- **作用**：设置工具页标签的位置。
- **参数**：
  - `position`：标签的位置，类型为 `QTabWidget::TabPosition`（如 `QTabWidget::North`、`QTabWidget::South`）。
- **返回值**：`void`，无返回值。

```cpp
toolBox->setTabPosition(QTabWidget::North);
```

#### `QTabWidget::TabPosition tabPosition() const`

- **作用**：获取工具页标签的位置。
- **返回值**：`QTabWidget::TabPosition`，当前标签的位置。

```cpp
QTabWidget::TabPosition position = toolBox->tabPosition();
```

### 13. **工具箱的大小策略**

#### `void setSizePolicy(const QSizePolicy &policy)`

- **作用**：设置工具箱的大小策略。
- **参数**：
  - `policy`：大小策略，类型为 `QSizePolicy`。
- **返回值**：`void`，无返回值。

```cpp
toolBox->setSizePolicy(QSizePolicy::Expanding, QSizePolicy::Expanding);
```

#### `QSizePolicy sizePolicy() const`

- **作用**：获取工具箱的大小策略。
- **返回值**：`QSizePolicy`，当前的大小策略。

```cpp
QSizePolicy policy = toolBox->sizePolicy();
```

### 14. **工具页的索引和顺序**

#### `int indexOf(QWidget *widget) const`

- **作用**：获取指定工具页内容控件的索引。
- **参数**：
  - `widget`：工具页的内容控件，类型为 `QWidget*`。
- **返回值**：`int`，工具页的索引，如果未找到则返回 `-1`。

```cpp
int index = toolBox->indexOf(myWidget);
```

#### `void setItemEnabled(int index, bool enabled)`

- **作用**：设置指定工具页的启用状态。
- **参数**：
  - `index`：工具页的索引，类型为 `int`。
  - `enabled`：布尔值，`true` 表示启用，`false` 表示禁用。
- **返回值**：`void`，无返回值。

```cpp
toolBox->setItemEnabled(0, false); // 禁用索引为0的工具页
```

### 15. **工具页的排序**

#### `void moveItem(int from, int to)`

- **作用**：移动工具页的位置。
- **参数**：
  - `from`：原始位置的索引，类型为 `int`。
  - `to`：目标位置的索引，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
toolBox->moveItem(1, 0); // 将索引为1的工具页移动到索引为0的位置
```

### 16. **工具页的显示方式**

#### `void setLayoutDirection(Qt::LayoutDirection direction)`

- **作用**：设置工具箱的布局方向。
- **参数**：
  - `direction`：布局方向，类型为 `Qt::LayoutDirection`（如 `Qt::LeftToRight`、`Qt::RightToLeft`）。
- **返回值**：`void`，无返回值。

```cpp
toolBox->setLayoutDirection(Qt::RightToLeft);
```

#### `Qt::LayoutDirection layoutDirection() const`

- **作用**：获取工具箱的布局方向。
- **返回值**：`Qt::LayoutDirection`，当前的布局方向。

```cpp
Qt::LayoutDirection direction = toolBox->layoutDirection();
```