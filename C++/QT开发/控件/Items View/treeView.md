`QTreeView` 是 Qt 框架中的一个控件，用于显示和操作树形数据。它适用于展示具有层级结构的数据，例如文件系统目录、组织结构图等。以下是 `QTreeView` 的详细函数方法及其作用：

### 1. 基本构造与销毁

#### `QTreeView(QWidget *parent = nullptr)`
- **作用**：构造一个 `QTreeView` 对象。
- **参数**：
  - `parent`：父控件，类型为 `QWidget*`。默认为 `nullptr`。
- **返回值**：`QTreeView` 对象。

```cpp
QTreeView *treeView = new QTreeView(parentWidget);
```

### 2. 数据模型

#### `void setModel(QAbstractItemModel *model)`
- **作用**：设置视图使用的数据模型。
- **参数**：
  - `model`：数据模型，类型为 `QAbstractItemModel*`。
- **返回值**：`void`，无返回值。

```cpp
treeView->setModel(model);
```

#### `QAbstractItemModel *model() const`
- **作用**：获取视图使用的数据模型。
- **返回值**：`QAbstractItemModel*`，数据模型。

```cpp
QAbstractItemModel *model = treeView->model();
```

### 3. 选择模型

#### `void setSelectionModel(QItemSelectionModel *selectionModel)`
- **作用**：设置视图使用的选择模型。
- **参数**：
  - `selectionModel`：选择模型，类型为 `QItemSelectionModel*`。
- **返回值**：`void`，无返回值。

```cpp
treeView->setSelectionModel(selectionModel);
```

#### `QItemSelectionModel *selectionModel() const`
- **作用**：获取视图使用的选择模型。
- **返回值**：`QItemSelectionModel*`，选择模型。

```cpp
QItemSelectionModel *selectionModel = treeView->selectionModel();
```

### 4. 显示模式与排序

#### `void setRootIndex(const QModelIndex &index)`
- **作用**：设置视图的根索引。
- **参数**：
  - `index`：根索引，类型为 `QModelIndex`。
- **返回值**：`void`，无返回值。

```cpp
treeView->setRootIndex(model->index(0, 0));
```

#### `QModelIndex rootIndex() const`
- **作用**：获取视图的根索引。
- **返回值**：`QModelIndex`，根索引。

```cpp
QModelIndex rootIndex = treeView->rootIndex();
```

#### `void setHeaderHidden(bool hide)`
- **作用**：设置是否隐藏列头。
- **参数**：
  - `hide`：是否隐藏，类型为 `bool`。
- **返回值**：`void`，无返回值。

```cpp
treeView->setHeaderHidden(true);
```

#### `bool isHeaderHidden() const`
- **作用**：检查列头是否隐藏。
- **返回值**：`bool`，是否隐藏。

```cpp
bool headerHidden = treeView->isHeaderHidden();
```

### 5. 树形视图操作

#### `void expand(const QModelIndex &index)`
- **作用**：展开指定的索引。
- **参数**：
  - `index`：要展开的索引，类型为 `QModelIndex`。
- **返回值**：`void`，无返回值。

```cpp
treeView->expand(model->index(0, 0));
```

#### `void collapse(const QModelIndex &index)`
- **作用**：折叠指定的索引。
- **参数**：
  - `index`：要折叠的索引，类型为 `QModelIndex`。
- **返回值**：`void`，无返回值。

```cpp
treeView->collapse(model->index(0, 0));
```

#### `void expandAll()`
- **作用**：展开视图中的所有项。
- **返回值**：`void`，无返回值。

```cpp
treeView->expandAll();
```

#### `void collapseAll()`
- **作用**：折叠视图中的所有项。
- **返回值**：`void`，无返回值。

```cpp
treeView->collapseAll();
```

### 6. 选择与高亮

#### `void setCurrentIndex(const QModelIndex &index)`
- **作用**：设置当前选中的索引。
- **参数**：
  - `index`：要设置为当前的索引，类型为 `QModelIndex`。
- **返回值**：`void`，无返回值。

```cpp
treeView->setCurrentIndex(model->index(0, 0));
```

#### `QModelIndex currentIndex() const`
- **作用**：获取当前选中的索引。
- **返回值**：`QModelIndex`，当前索引。

```cpp
QModelIndex currentIndex = treeView->currentIndex();
```

### 7. 树形视图行为

#### `void setIndentation(int indentation)`
- **作用**：设置树形项的缩进量。
- **参数**：
  - `indentation`：缩进量，单位为像素，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
treeView->setIndentation(20);
```

#### `int indentation() const`
- **作用**：获取树形项的缩进量。
- **返回值**：`int`，缩进量。

```cpp
int indentation = treeView->indentation();
```

### 8. 树形视图渲染

#### `void setItemDelegate(QAbstractItemDelegate *delegate)`
- **作用**：设置自定义的项委托，用于渲染和编辑项。
- **参数**：
  - `delegate`：项委托，类型为 `QAbstractItemDelegate*`。
- **返回值**：`void`，无返回值。

```cpp
QItemDelegate *delegate = new QItemDelegate();
treeView->setItemDelegate(delegate);
```

#### `QAbstractItemDelegate *itemDelegate() const`
- **作用**：获取当前的项委托。
- **返回值**：`QAbstractItemDelegate*`，项委托。

```cpp
QAbstractItemDelegate *delegate = treeView->itemDelegate();
```

### 9. 自定义行为

#### `void setDragEnabled(bool enable)`
- **作用**：设置是否启用拖放操作。
- **参数**：
  - `enable`：是否启用，类型为 `bool`。
- **返回值**：`void`，无返回值。

```cpp
treeView->setDragEnabled(true);
```

#### `bool isDragEnabled() const`
- **作用**：检查拖放操作是否启用。
- **返回值**：`bool`，是否启用。

```cpp
bool dragEnabled = treeView->isDragEnabled();
```

#### `void setDropIndicatorShown(bool shown)`
- **作用**：设置是否显示拖放指示器。
- **参数**：
  - `shown`：是否显示，类型为 `bool`。
- **返回值**：`void`，无返回值。

```cpp
treeView->setDropIndicatorShown(true);
```

#### `bool isDropIndicatorShown() const`
- **作用**：检查拖放指示器是否显示。
- **返回值**：`bool`，是否显示。

```cpp
bool dropIndicatorShown = treeView->isDropIndicatorShown();
```

### 10. 显示与隐藏

#### `void setHorizontalScrollBarPolicy(Qt::ScrollBarPolicy policy)`
- **作用**：设置水平滚动条策略。
- **参数**：
  - `policy`：滚动条策略，类型为 `Qt::ScrollBarPolicy`。
- **返回值**：`void`，无返回值。

```cpp
treeView->setHorizontalScrollBarPolicy(Qt::ScrollBarAlwaysOff);
```

#### `Qt::ScrollBarPolicy horizontalScrollBarPolicy() const`
- **作用**：获取水平滚动条策略。
- **返回值**：`Qt::ScrollBarPolicy`，滚动条策略。

```cpp
Qt::ScrollBarPolicy policy = treeView->horizontalScrollBarPolicy();
```

#### `void setVerticalScrollBarPolicy(Qt::ScrollBarPolicy policy)`
- **作用**：设置垂直滚动条策略。
- **参数**：
  - `policy`：滚动条策略，类型为 `Qt::ScrollBarPolicy`。
- **返回值**：`void`，无返回值。

```cpp
treeView->setVerticalScrollBarPolicy(Qt::ScrollBarAlwaysOn);
```

#### `Qt::ScrollBarPolicy verticalScrollBarPolicy() const`
- **作用**：获取垂直滚动条策略。
- **返回值**：`Qt::ScrollBarPolicy`，滚动条策略。

```cpp
Qt::ScrollBarPolicy policy = treeView->verticalScrollBarPolicy();
```

### 11. 自定义绘制与样式

#### `void setStyleSheet(const QString &styleSheet)`
- **作用**：设置自定义的样式表，以改变视图的外观

。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。
- **返回值**：`void`，无返回值。

```cpp
treeView->setStyleSheet("QTreeView { background-color: lightgray; }");
```

#### `void setEditTriggers(QAbstractItemView::EditTriggers triggers)`
- **作用**：设置视图的编辑触发条件。
- **参数**：
  - `triggers`：编辑触发条件，类型为 `QAbstractItemView::EditTriggers`。
- **返回值**：`void`，无返回值。

```cpp
treeView->setEditTriggers(QAbstractItemView::AllEditTriggers);
```

### 12. 布局与尺寸

#### `void setFixedSize(const QSize &size)`
- **作用**：设置视图的固定尺寸。
- **参数**：
  - `size`：尺寸，类型为 `QSize`。
- **返回值**：`void`，无返回值。

```cpp
treeView->setFixedSize(QSize(400, 300));
```

#### `QSize sizeHint() const`
- **作用**：获取视图的推荐尺寸。
- **返回值**：`QSize`，推荐尺寸。

```cpp
QSize sizeHint = treeView->sizeHint();
```

### 13. 事件处理

#### `bool event(QEvent *event) override`
- **作用**：重写事件处理方法以自定义事件处理。
- **参数**：
  - `event`：事件对象，类型为 `QEvent*`。
- **返回值**：`bool`，事件处理状态。

```cpp
bool QTreeView::event(QEvent *event) override {
    if (event->type() == QEvent::MouseButtonPress) {
        // Custom event handling code
    }
    return QTreeView::event(event);
}
```
以下是一些更高级和较少使用的 `QTreeView` 方法及其作用，涵盖了不同方面的功能：

### 14. 列宽与排序

#### `void setColumnWidth(int column, int width)`
- **作用**：设置指定列的宽度。
- **参数**：
  - `column`：列索引，类型为 `int`。
  - `width`：列宽，单位为像素，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
treeView->setColumnWidth(0, 200);
```

#### `int columnWidth(int column) const`
- **作用**：获取指定列的宽度。
- **参数**：
  - `column`：列索引，类型为 `int`。
- **返回值**：`int`，列宽。

```cpp
int width = treeView->columnWidth(0);
```

#### `void resizeColumnToContents(int column)`
- **作用**：根据内容调整列宽。
- **参数**：
  - `column`：列索引，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
treeView->resizeColumnToContents(0);
```

### 15. 自定义视图行为

#### `void setAlternatingRowColors(bool enable)`
- **作用**：设置是否交替行颜色。
- **参数**：
  - `enable`：是否启用交替颜色，类型为 `bool`。
- **返回值**：`void`，无返回值。

```cpp
treeView->setAlternatingRowColors(true);
```

#### `bool alternatingRowColors() const`
- **作用**：检查是否启用交替行颜色。
- **返回值**：`bool`，是否启用交替颜色。

```cpp
bool alternatingColors = treeView->alternatingRowColors();
```

### 16. 自定义项

#### `void setItemDelegateForColumn(int column, QAbstractItemDelegate *delegate)`
- **作用**：为指定列设置自定义项委托。
- **参数**：
  - `column`：列索引，类型为 `int`。
  - `delegate`：项委托，类型为 `QAbstractItemDelegate*`。
- **返回值**：`void`，无返回值。

```cpp
QItemDelegate *delegate = new QItemDelegate();
treeView->setItemDelegateForColumn(0, delegate);
```

#### `void setItemDelegateForRow(int row, QAbstractItemDelegate *delegate)`
- **作用**：为指定行设置自定义项委托。
- **参数**：
  - `row`：行索引，类型为 `int`。
  - `delegate`：项委托，类型为 `QAbstractItemDelegate*`。
- **返回值**：`void`，无返回值。

```cpp
QItemDelegate *delegate = new QItemDelegate();
treeView->setItemDelegateForRow(0, delegate);
```

#### `void setItemDelegateForIndex(QAbstractItemDelegate *delegate, const QModelIndex &index)`
- **作用**：为指定的索引设置自定义项委托。
- **参数**：
  - `delegate`：项委托，类型为 `QAbstractItemDelegate*`。
  - `index`：索引，类型为 `QModelIndex`。
- **返回值**：`void`，无返回值。

```cpp
QItemDelegate *delegate = new QItemDelegate();
treeView->setItemDelegateForIndex(delegate, model->index(0, 0));
```

### 17. 数据处理与编辑

#### `void setEditTriggers(QAbstractItemView::EditTriggers triggers)`
- **作用**：设置视图的编辑触发条件。
- **参数**：
  - `triggers`：编辑触发条件，类型为 `QAbstractItemView::EditTriggers`。
- **返回值**：`void`，无返回值。

```cpp
treeView->setEditTriggers(QAbstractItemView::DoubleClicked);
```

#### `QAbstractItemView::EditTriggers editTriggers() const`
- **作用**：获取视图的编辑触发条件。
- **返回值**：`QAbstractItemView::EditTriggers`，编辑触发条件。

```cpp
QAbstractItemView::EditTriggers triggers = treeView->editTriggers();
```

### 18. 过滤与排序

#### `void setSortingEnabled(bool enable)`
- **作用**：设置是否启用排序功能。
- **参数**：
  - `enable`：是否启用，类型为 `bool`。
- **返回值**：`void`，无返回值。

```cpp
treeView->setSortingEnabled(true);
```

#### `bool isSortingEnabled() const`
- **作用**：检查排序功能是否启用。
- **返回值**：`bool`，是否启用排序。

```cpp
bool sortingEnabled = treeView->isSortingEnabled();
```

### 19. 拖放支持

#### `void setDropIndicatorShown(bool shown)`
- **作用**：设置是否显示拖放指示器。
- **参数**：
  - `shown`：是否显示，类型为 `bool`。
- **返回值**：`void`，无返回值。

```cpp
treeView->setDropIndicatorShown(true);
```

#### `bool isDropIndicatorShown() const`
- **作用**：检查拖放指示器是否显示。
- **返回值**：`bool`，是否显示。

```cpp
bool dropIndicatorShown = treeView->isDropIndicatorShown();
```

### 20. 事件处理

#### `void setHeader(QHeaderView *header)`
- **作用**：设置视图的列头。
- **参数**：
  - `header`：列头，类型为 `QHeaderView*`。
- **返回值**：`void`，无返回值。

```cpp
QHeaderView *header = new QHeaderView(Qt::Horizontal);
treeView->setHeader(header);
```

#### `QHeaderView *header() const`
- **作用**：获取视图的列头。
- **返回值**：`QHeaderView*`，列头。

```cpp
QHeaderView *header = treeView->header();
```

这些方法涵盖了 `QTreeView` 控件的更高级和专业功能。如果你有具体的用例或遇到问题，可以提供更多细节以便获得更精准的帮助。