---
tags:
  - QT开发
---
# treeWidget

`QTreeWidget` 是 Qt 中一个用于显示和操作树形数据的控件，继承自 `QTreeView`。它提供了用于管理和操作树节点的功能。以下是 `QTreeWidget` 的详细函数方法及其作用：

### 1. 基本构造与销毁

#### `QTreeWidget(QWidget *parent = nullptr)`

- **作用**：构造一个 `QTreeWidget` 对象。
- **参数**：
  - `parent`：父控件，类型为 `QWidget*`。默认为 `nullptr`。
- **返回值**：`QTreeWidget` 对象。

```cpp
QTreeWidget *treeWidget = new QTreeWidget(parentWidget);
```

### 2. 设置与获取头部

#### `void setHeaderLabels(const QStringList &labels)`

- **作用**：设置树控件的头部标签。
- **参数**：
  - `labels`：标签列表，类型为 `QStringList`。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->setHeaderLabels(QStringList() << "Column 1" << "Column 2");
```

#### `QStringList headerLabels() const`

- **作用**：获取头部标签。
- **返回值**：`QStringList`，头部标签列表。

```cpp
QStringList labels = treeWidget->headerLabels();
```

### 3. 添加与插入节点

#### `QTreeWidgetItem *addTopLevelItem(QTreeWidgetItem *item)`

- **作用**：在顶层添加一个新项。
- **参数**：
  - `item`：要添加的项，类型为 `QTreeWidgetItem*`。
- **返回值**：`void`，无返回值。

```cpp
QTreeWidgetItem *item = new QTreeWidgetItem(QStringList() << "Item 1" << "Detail 1");
treeWidget->addTopLevelItem(item);
```

#### `QTreeWidgetItem *insertTopLevelItem(int index, QTreeWidgetItem *item)`

- **作用**：在指定位置插入一个新项。
- **参数**：
  - `index`：插入位置的索引，类型为 `int`。
  - `item`：要插入的项，类型为 `QTreeWidgetItem*`。
- **返回值**：`void`，无返回值。

```cpp
QTreeWidgetItem *item = new QTreeWidgetItem(QStringList() << "Item 2" << "Detail 2");
treeWidget->insertTopLevelItem(0, item);
```

#### `QTreeWidgetItem *addItem(QTreeWidgetItem *item)`

- **作用**：添加一个新项到当前选中的项下。
- **参数**：
  - `item`：要添加的项，类型为 `QTreeWidgetItem*`。
- **返回值**：`void`，无返回值。

```cpp
QTreeWidgetItem *parentItem = treeWidget->topLevelItem(0);
QTreeWidgetItem *childItem = new QTreeWidgetItem(QStringList() << "Child Item" << "Detail");
parentItem->addChild(childItem);
```

### 4. 删除节点

#### `void clear()`

- **作用**：删除所有项。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->clear();
```

#### `void removeItemWidget(QTreeWidgetItem *item, int column)`

- **作用**：从项中删除 widget。
- **参数**：
  - `item`：要删除 widget 的项，类型为 `QTreeWidgetItem*`。
  - `column`：列索引，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->removeItemWidget(item, 0);
```

#### `void takeTopLevelItem(int index)`

- **作用**：移除并返回顶层的项。
- **参数**：
  - `index`：项的索引，类型为 `int`。
- **返回值**：`QTreeWidgetItem*`，移除的项。

```cpp
QTreeWidgetItem *item = treeWidget->takeTopLevelItem(0);
```

### 5. 获取与设置节点

#### `QTreeWidgetItem *topLevelItem(int index) const`

- **作用**：获取顶层的项。
- **参数**：
  - `index`：项的索引，类型为 `int`。
- **返回值**：`QTreeWidgetItem*`，顶层的项。

```cpp
QTreeWidgetItem *item = treeWidget->topLevelItem(0);
```

#### `QTreeWidgetItem *currentItem() const`

- **作用**：获取当前选中的项。
- **返回值**：`QTreeWidgetItem*`，当前选中的项。

```cpp
QTreeWidgetItem *currentItem = treeWidget->currentItem();
```

#### `void setCurrentItem(QTreeWidgetItem *item)`

- **作用**：设置当前选中的项。
- **参数**：
  - `item`：要选中的项，类型为 `QTreeWidgetItem*`。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->setCurrentItem(item);
```

### 6. 节点操作

#### `void setItemExpanded(QTreeWidgetItem *item)`

- **作用**：展开项。
- **参数**：
  - `item`：要展开的项，类型为 `QTreeWidgetItem*`。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->setItemExpanded(item);
```

#### `void setItemCollapsed(QTreeWidgetItem *item)`

- **作用**：折叠项。
- **参数**：
  - `item`：要折叠的项，类型为 `QTreeWidgetItem*`。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->setItemCollapsed(item);
```

### 7. 搜索与过滤

#### `QTreeWidgetItem *findItems(const QString &text, Qt::MatchFlags flags) const`

- **作用**：查找与指定文本匹配的项。
- **参数**：
  - `text`：要匹配的文本，类型为 `QString`。
  - `flags`：匹配标志，类型为 `Qt::MatchFlags`。
- **返回值**：`QTreeWidgetItem*`，匹配的项。

```cpp
QList<QTreeWidgetItem*> items = treeWidget->findItems("Item 1", Qt::MatchContains);
```

### 8. 模型与视图

#### `void setModel(QAbstractItemModel *model)`

- **作用**：设置树的模型。
- **参数**：
  - `model`：模型，类型为 `QAbstractItemModel*`。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->setModel(myModel);
```

#### `QAbstractItemModel *model() const`

- **作用**：获取树的模型。
- **返回值**：`QAbstractItemModel*`，树的模型。

```cpp
QAbstractItemModel *model = treeWidget->model();
```

### 9. 事件处理

#### `void keyPressEvent(QKeyEvent *event)`

- **作用**：处理键盘按下事件。
- **参数**：
  - `event`：键盘事件，类型为 `QKeyEvent*`。
- **返回值**：`void`，无返回值。

```cpp
void MyTreeWidget::keyPressEvent(QKeyEvent *event) {
    // 自定义处理代码
    QTreeWidget::keyPressEvent(event);
}
```

#### `void mousePressEvent(QMouseEvent *event)`

- **作用**：处理鼠标按下事件。
- **参数**：
  - `event`：鼠标事件，类型为 `QMouseEvent*`。
- **返回值**：`void`，无返回值。

```cpp
void MyTreeWidget::mousePressEvent(QMouseEvent *event) {
    // 自定义处理代码
    QTreeWidget::mousePressEvent(event);
}
```

### 10. 样式与布局

#### `void setStyleSheet(const QString &styleSheet)`

- **作用**：设置控件的样式表。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->setStyleSheet("QTreeWidget { background: lightgray; }");
```

#### `QString styleSheet() const`

- **作用**：获取控件的样式表。
- **返回值**：`QString`，样式表字符串。

```cpp
QString styleSheet = treeWidget->styleSheet();
```

### 11. 其他功能

#### `void setHorizontalScrollBarPolicy(Qt::ScrollBarPolicy policy)`

- **作用**：设置水平滚动条策略。
- **参数**：
  - `policy`：滚动条策略，类型为 `Qt::ScrollBarPolicy`。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->setHorizontalScrollBarPolicy(Qt::ScrollBarAlwaysOff);
```

#### `

void setVerticalScrollBarPolicy(Qt::ScrollBarPolicy policy)`

- **作用**：设置垂直滚动条策略。
- **参数**：
  - `policy`：滚动条策略，类型为 `Qt::ScrollBarPolicy`。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->setVerticalScrollBarPolicy(Qt::ScrollBarAlwaysOn);
```

### 12. 额外方法

#### `void setColumnCount(int columns)`

- **作用**：设置列数。
- **参数**：
  - `columns`：列数，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->setColumnCount(3);
```

#### `int columnCount() const`

- **作用**：获取列数。
- **返回值**：`int`，列数。

```cpp
int columns = treeWidget->columnCount();
```

在 `QTreeWidget` 类中，大部分常用的函数方法已经涵盖了。如果你还有其他具体的功能需求或使用场景，以下是一些可能不那么常用但仍然有用的方法和属性：

### 1. 树结构操作

#### `void setDragDropMode(DragDropMode mode)`

- **作用**：设置拖放模式。
- **参数**：
  - `mode`：拖放模式，类型为 `QAbstractItemView::DragDropMode`。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->setDragDropMode(QAbstractItemView::InternalMove);
```

#### `void setDropIndicatorShown(bool show)`

- **作用**：设置是否显示拖放指示器。
- **参数**：
  - `show`：是否显示，类型为 `bool`。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->setDropIndicatorShown(true);
```

### 2. 项的样式和状态

#### `void setItemExpanded(QTreeWidgetItem *item, bool expanded)`

- **作用**：展开或折叠项。
- **参数**：
  - `item`：要操作的项，类型为 `QTreeWidgetItem*`。
  - `expanded`：是否展开，类型为 `bool`。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->setItemExpanded(item, true); // 展开
treeWidget->setItemExpanded(item, false); // 折叠
```

#### `void setItemWidget(QTreeWidgetItem *item, int column, QWidget *widget)`

- **作用**：在项的指定列中设置小部件。
- **参数**：
  - `item`：项，类型为 `QTreeWidgetItem*`。
  - `column`：列索引，类型为 `int`。
  - `widget`：要设置的 widget，类型为 `QWidget*`。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->setItemWidget(item, 1, new QPushButton("Button"));
```

### 3. 项的选择和排序

#### `void sortItems(int column, Qt::SortOrder order)`

- **作用**：对指定列进行排序。
- **参数**：
  - `column`：列索引，类型为 `int`。
  - `order`：排序顺序，类型为 `Qt::SortOrder`。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->sortItems(0, Qt::AscendingOrder);
```

#### `void setSortingEnabled(bool enable)`

- **作用**：启用或禁用排序功能。
- **参数**：
  - `enable`：是否启用，类型为 `bool`。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->setSortingEnabled(true);
```

### 4. 节点的插入和移动

#### `void setItemSelected(QTreeWidgetItem *item, bool selected)`

- **作用**：设置项是否被选中。
- **参数**：
  - `item`：要操作的项，类型为 `QTreeWidgetItem*`。
  - `selected`：是否选中，类型为 `bool`。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->setItemSelected(item, true); // 选中
treeWidget->setItemSelected(item, false); // 取消选中
```

### 5. 视图的操作

#### `void scrollToItem(QTreeWidgetItem *item, QAbstractItemView::ScrollHint hint)`

- **作用**：滚动视图以确保指定项可见。
- **参数**：
  - `item`：要滚动到的项，类型为 `QTreeWidgetItem*`。
  - `hint`：滚动提示，类型为 `QAbstractItemView::ScrollHint`。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->scrollToItem(item, QAbstractItemView::EnsureVisible);
```

### 6. 搜索和过滤

#### `void setFilterRegExp(const QRegExp &regexp)`

- **作用**：设置用于过滤项的正则表达式。
- **参数**：
  - `regexp`：正则表达式，类型为 `QRegExp`。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->setFilterRegExp(QRegExp("searchPattern"));
```

### 7. 内部数据管理

#### `QTreeWidgetItemIterator itemIterator() const`

- **作用**：获取用于遍历项的迭代器。
- **返回值**：`QTreeWidgetItemIterator`，用于遍历的迭代器。

```cpp
QTreeWidgetItemIterator it(treeWidget);
while (*it) {
    QTreeWidgetItem *item = *it;
    // 处理项
    ++it;
}
```

### 8. 高级功能

#### `void setHeaderHidden(bool hide)`

- **作用**：隐藏或显示头部。
- **参数**：
  - `hide`：是否隐藏头部，类型为 `bool`。
- **返回值**：`void`，无返回值。

```cpp
treeWidget->setHeaderHidden(true); // 隐藏头部
treeWidget->setHeaderHidden(false); // 显示头部
```
