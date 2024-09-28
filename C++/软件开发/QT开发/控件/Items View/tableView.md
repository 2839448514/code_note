---
tags:
  - QT开发
---
# tableView

`QTableView` 是 Qt 框架中的一个控件，用于以表格形式展示和操作数据。它适用于展示表格数据，例如数据库表格、数据分析结果等。以下是 `QTableView` 的详细方法及其作用：

### 1. 基本构造与销毁

#### `QTableView(QWidget *parent = nullptr)`

- **作用**：构造一个 `QTableView` 对象。
- **参数**：
  - `parent`：父控件，类型为 `QWidget*`。默认为 `nullptr`。
- **返回值**：`QTableView` 对象。

```cpp
QTableView *tableView = new QTableView(parentWidget);
```

### 2. 数据模型

#### `void setModel(QAbstractItemModel *model)`

- **作用**：设置视图使用的数据模型。
- **参数**：
  - `model`：数据模型，类型为 `QAbstractItemModel*`。
- **返回值**：`void`，无返回值。

```cpp
tableView->setModel(model);
```

#### `QAbstractItemModel *model() const`

- **作用**：获取视图使用的数据模型。
- **返回值**：`QAbstractItemModel*`，数据模型。

```cpp
QAbstractItemModel *model = tableView->model();
```

### 3. 选择模型

#### `void setSelectionModel(QItemSelectionModel *selectionModel)`

- **作用**：设置视图使用的选择模型。
- **参数**：
  - `selectionModel`：选择模型，类型为 `QItemSelectionModel*`。
- **返回值**：`void`，无返回值。

```cpp
tableView->setSelectionModel(selectionModel);
```

#### `QItemSelectionModel *selectionModel() const`

- **作用**：获取视图使用的选择模型。
- **返回值**：`QItemSelectionModel*`，选择模型。

```cpp
QItemSelectionModel *selectionModel = tableView->selectionModel();
```

### 4. 排序与筛选

#### `void setSortingEnabled(bool enable)`

- **作用**：设置是否启用排序功能。
- **参数**：
  - `enable`：是否启用，类型为 `bool`。
- **返回值**：`void`，无返回值。

```cpp
tableView->setSortingEnabled(true);
```

#### `bool isSortingEnabled() const`

- **作用**：检查排序功能是否启用。
- **返回值**：`bool`，是否启用排序。

```cpp
bool sortingEnabled = tableView->isSortingEnabled();
```

### 5. 表格视图操作

#### `void setHorizontalHeader(QHeaderView *header)`

- **作用**：设置水平表头。
- **参数**：
  - `header`：水平表头，类型为 `QHeaderView*`。
- **返回值**：`void`，无返回值。

```cpp
QHeaderView *header = new QHeaderView(Qt::Horizontal);
tableView->setHorizontalHeader(header);
```

#### `QHeaderView *horizontalHeader() const`

- **作用**：获取水平表头。
- **返回值**：`QHeaderView*`，水平表头。

```cpp
QHeaderView *header = tableView->horizontalHeader();
```

#### `void setVerticalHeader(QHeaderView *header)`

- **作用**：设置垂直表头。
- **参数**：
  - `header`：垂直表头，类型为 `QHeaderView*`。
- **返回值**：`void`，无返回值。

```cpp
QHeaderView *header = new QHeaderView(Qt::Vertical);
tableView->setVerticalHeader(header);
```

#### `QHeaderView *verticalHeader() const`

- **作用**：获取垂直表头。
- **返回值**：`QHeaderView*`，垂直表头。

```cpp
QHeaderView *header = tableView->verticalHeader();
```

### 6. 列宽与行高

#### `void setColumnWidth(int column, int width)`

- **作用**：设置指定列的宽度。
- **参数**：
  - `column`：列索引，类型为 `int`。
  - `width`：列宽，单位为像素，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
tableView->setColumnWidth(0, 100);
```

#### `int columnWidth(int column) const`

- **作用**：获取指定列的宽度。
- **参数**：
  - `column`：列索引，类型为 `int`。
- **返回值**：`int`，列宽。

```cpp
int width = tableView->columnWidth(0);
```

#### `void setRowHeight(int row, int height)`

- **作用**：设置指定行的高度。
- **参数**：
  - `row`：行索引，类型为 `int`。
  - `height`：行高，单位为像素，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
tableView->setRowHeight(0, 30);
```

#### `int rowHeight(int row) const`

- **作用**：获取指定行的高度。
- **参数**：
  - `row`：行索引，类型为 `int`。
- **返回值**：`int`，行高。

```cpp
int height = tableView->rowHeight(0);
```

### 7. 视图行为

#### `void setEditTriggers(QAbstractItemView::EditTriggers triggers)`

- **作用**：设置视图的编辑触发条件。
- **参数**：
  - `triggers`：编辑触发条件，类型为 `QAbstractItemView::EditTriggers`。
- **返回值**：`void`，无返回值。

```cpp
tableView->setEditTriggers(QAbstractItemView::AllEditTriggers);
```

#### `QAbstractItemView::EditTriggers editTriggers() const`

- **作用**：获取视图的编辑触发条件。
- **返回值**：`QAbstractItemView::EditTriggers`，编辑触发条件。

```cpp
QAbstractItemView::EditTriggers triggers = tableView->editTriggers();
```

#### `void setAlternatingRowColors(bool enable)`

- **作用**：设置是否交替行颜色。
- **参数**：
  - `enable`：是否启用交替颜色，类型为 `bool`。
- **返回值**：`void`，无返回值。

```cpp
tableView->setAlternatingRowColors(true);
```

#### `bool alternatingRowColors() const`

- **作用**：检查是否启用交替行颜色。
- **返回值**：`bool`，是否启用交替颜色。

```cpp
bool alternatingColors = tableView->alternatingRowColors();
```

### 8. 滚动条

#### `void setHorizontalScrollBarPolicy(Qt::ScrollBarPolicy policy)`

- **作用**：设置水平滚动条策略。
- **参数**：
  - `policy`：滚动条策略，类型为 `Qt::ScrollBarPolicy`。
- **返回值**：`void`，无返回值。

```cpp
tableView->setHorizontalScrollBarPolicy(Qt::ScrollBarAlwaysOn);
```

#### `Qt::ScrollBarPolicy horizontalScrollBarPolicy() const`

- **作用**：获取水平滚动条策略。
- **返回值**：`Qt::ScrollBarPolicy`，滚动条策略。

```cpp
Qt::ScrollBarPolicy policy = tableView->horizontalScrollBarPolicy();
```

#### `void setVerticalScrollBarPolicy(Qt::ScrollBarPolicy policy)`

- **作用**：设置垂直滚动条策略。
- **参数**：
  - `policy`：滚动条策略，类型为 `Qt::ScrollBarPolicy`。
- **返回值**：`void`，无返回值。

```cpp
tableView->setVerticalScrollBarPolicy(Qt::ScrollBarAlwaysOn);
```

#### `Qt::ScrollBarPolicy verticalScrollBarPolicy() const`

- **作用**：获取垂直滚动条策略。
- **返回值**：`Qt::ScrollBarPolicy`，滚动条策略。

```cpp
Qt::ScrollBarPolicy policy = tableView->verticalScrollBarPolicy();
```

### 9. 自定义绘制

#### `void setItemDelegate(QAbstractItemDelegate *delegate)`

- **作用**：设置自定义的项委托，用于渲染和编辑项。
- **参数**：
  - `delegate`：项委托，类型为 `QAbstractItemDelegate*`。
- **返回值**：`void`，无返回值。

```cpp
QItemDelegate *delegate = new QItemDelegate();
tableView->setItemDelegate(delegate);
```

#### `QAbstractItemDelegate *itemDelegate() const`

- **作用**：获取当前的项委托。
- **返回值**：`QAbstractItemDelegate*`，项委托。

```cpp
QAbstractItemDelegate *delegate = tableView->itemDelegate();
```

### 10. 选择与高亮

#### `void setCurrentIndex(const QModelIndex &index)`

- **作用**：设置当前选中的索引。
- **参数**：

  - `index`：当前索引，类型为 `QModelIndex`。
- **返回值**：`void`，无返回值。

```cpp
tableView->setCurrentIndex(model->index(0, 0));
```

#### `QModelIndex currentIndex() const`

- **作用**：获取当前选中的索引。
- **返回值**：`QModelIndex`，当前索引。

```cpp
QModelIndex index = tableView->currentIndex();
```

### 11. 数据刷新

#### `void reset()`

- **作用**：重置视图，刷新视图数据。
- **返回值**：`void`，无返回值。

```cpp
tableView->reset();
```

### 12. 布局与尺寸

#### `void setFixedSize(const QSize &size)`

- **作用**：设置视图的固定尺寸。
- **参数**：
  - `size`：尺寸，类型为 `QSize`。
- **返回值**：`void`，无返回值。

```cpp
tableView->setFixedSize(QSize(800, 600));
```

#### `QSize sizeHint() const`

- **作用**：获取视图的推荐尺寸。
- **返回值**：`QSize`，推荐尺寸。

```cpp
QSize sizeHint = tableView->sizeHint();
```

### 13. 事件处理

#### `bool event(QEvent *event) override`

- **作用**：重写事件处理方法以自定义事件处理。
- **参数**：
  - `event`：事件对象，类型为 `QEvent*`。
- **返回值**：`bool`，事件处理状态。

```cpp
bool QTableView::event(QEvent *event) override {
    if (event->type() == QEvent::MouseButtonPress) {
        // Custom event handling code
    }
    return QTableView::event(event);
}
```

`QTableView` 的常用方法已涵盖了大部分功能，不过还有一些较少使用或高级功能的方法，可能对你有用：

### 14. 高级数据处理

#### `void setRootIndex(const QModelIndex &index)`

- **作用**：设置视图的根索引，用于显示数据模型的子项。
- **参数**：
  - `index`：根索引，类型为 `QModelIndex`。
- **返回值**：`void`，无返回值。

```cpp
tableView->setRootIndex(model->index(0, 0));
```

#### `QModelIndex rootIndex() const`

- **作用**：获取视图的根索引。
- **返回值**：`QModelIndex`，根索引。

```cpp
QModelIndex root = tableView->rootIndex();
```

### 15. 数据导出与持久化

#### `void setPersistentEditor(const QModelIndex &index)`

- **作用**：设置指定索引的编辑器为持久化编辑器。
- **参数**：
  - `index`：指定的索引，类型为 `QModelIndex`。
- **返回值**：`void`，无返回值。

```cpp
tableView->setPersistentEditor(model->index(0, 0));
```

#### `void removePersistentEditor(const QModelIndex &index)`

- **作用**：移除指定索引的持久化编辑器。
- **参数**：
  - `index`：指定的索引，类型为 `QModelIndex`。
- **返回值**：`void`，无返回值。

```cpp
tableView->removePersistentEditor(model->index(0, 0));
```

### 16. 拖放操作

#### `void setDragDropMode(QAbstractItemView::DragDropMode mode)`

- **作用**：设置拖放模式。
- **参数**：
  - `mode`：拖放模式，类型为 `QAbstractItemView::DragDropMode`。
- **返回值**：`void`，无返回值。

```cpp
tableView->setDragDropMode(QAbstractItemView::InternalMove);
```

#### `QAbstractItemView::DragDropMode dragDropMode() const`

- **作用**：获取当前的拖放模式。
- **返回值**：`QAbstractItemView::DragDropMode`，拖放模式。

```cpp
QAbstractItemView::DragDropMode mode = tableView->dragDropMode();
```

### 17. 自定义交互

#### `void setEditTriggers(QAbstractItemView::EditTriggers triggers)`

- **作用**：设置视图的编辑触发条件。
- **参数**：
  - `triggers`：编辑触发条件，类型为 `QAbstractItemView::EditTriggers`。
- **返回值**：`void`，无返回值。

```cpp
tableView->setEditTriggers(QAbstractItemView::AllEditTriggers);
```

### 18. 高亮与选择

#### `void setSelectionBehavior(QAbstractItemView::SelectionBehavior behavior)`

- **作用**：设置选择行为（例如，按行或按列选择）。
- **参数**：
  - `behavior`：选择行为，类型为 `QAbstractItemView::SelectionBehavior`。
- **返回值**：`void`，无返回值。

```cpp
tableView->setSelectionBehavior(QAbstractItemView::SelectRows);
```

#### `QAbstractItemView::SelectionBehavior selectionBehavior() const`

- **作用**：获取选择行为。
- **返回值**：`QAbstractItemView::SelectionBehavior`，选择行为。

```cpp
QAbstractItemView::SelectionBehavior behavior = tableView->selectionBehavior();
```

### 19. 视图的可视化

#### `void setGridStyle(Qt::PenStyle style)`

- **作用**：设置网格线的样式。
- **参数**：
  - `style`：网格线样式，类型为 `Qt::PenStyle`。
- **返回值**：`void`，无返回值。

```cpp
tableView->setGridStyle(Qt::DashLine);
```

#### `Qt::PenStyle gridStyle() const`

- **作用**：获取网格线的样式。
- **返回值**：`Qt::PenStyle`，网格线样式。

```cpp
Qt::PenStyle style = tableView->gridStyle();
```

### 20. 背景与视觉效果

#### `void setStyleSheet(const QString &styleSheet)`

- **作用**：设置控件的样式表。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。
- **返回值**：`void`，无返回值。

```cpp
tableView->setStyleSheet("background-color: lightgray;");
```

### 21. 自定义滚动条

#### `QScrollBar *horizontalScrollBar() const`

- **作用**：获取水平滚动条。
- **返回值**：`QScrollBar*`，水平滚动条。

```cpp
QScrollBar *hScrollBar = tableView->horizontalScrollBar();
```

#### `QScrollBar *verticalScrollBar() const`

- **作用**：获取垂直滚动条。
- **返回值**：`QScrollBar*`，垂直滚动条。

```cpp
QScrollBar *vScrollBar = tableView->verticalScrollBar();
```

这些方法涵盖了 `QTableView` 的一些更高级和专业的功能。如果你有任何具体需求或遇到问题，可以提供更多细节，以便提供更准确的帮助。
