`QColumnView` 是 Qt 框架中的一个控件，通常用于展示具有层次结构的数据，例如文件系统或目录结构。`QColumnView` 提供了一种以列的形式展示数据的方式，每一列代表数据模型中的一个层级。以下是 `QColumnView` 的详细方法及其作用：

### 1. 基本构造与销毁

#### `QColumnView(QWidget *parent = nullptr)`

- **作用**：构造一个 `QColumnView` 对象。
- **参数**：
  - `parent`：父控件，类型为 `QWidget*`。默认为 `nullptr`。
- **返回值**：`QColumnView` 对象。

```cpp
QColumnView *columnView = new QColumnView(parentWidget);
```

### 2. 数据模型

#### `void setModel(QAbstractItemModel *model)`

- **作用**：设置视图使用的数据模型。
- **参数**：
  - `model`：数据模型，类型为 `QAbstractItemModel*`。
- **返回值**：`void`，无返回值。

```cpp
columnView->setModel(model);
```

#### `QAbstractItemModel *model() const`

- **作用**：获取视图使用的数据模型。
- **返回值**：`QAbstractItemModel*`，数据模型。

```cpp
QAbstractItemModel *model = columnView->model();
```

### 3. 选择模型

#### `void setSelectionModel(QItemSelectionModel *selectionModel)`

- **作用**：设置视图使用的选择模型。
- **参数**：
  - `selectionModel`：选择模型，类型为 `QItemSelectionModel*`。
- **返回值**：`void`，无返回值。

```cpp
columnView->setSelectionModel(selectionModel);
```

#### `QItemSelectionModel *selectionModel() const`

- **作用**：获取视图使用的选择模型。
- **返回值**：`QItemSelectionModel*`，选择模型。

```cpp
QItemSelectionModel *selectionModel = columnView->selectionModel();
```

### 4. 选择与高亮

#### `void setCurrentIndex(const QModelIndex &index)`

- **作用**：设置当前选中的索引。
- **参数**：
  - `index`：当前索引，类型为 `QModelIndex`。
- **返回值**：`void`，无返回值。

```cpp
columnView->setCurrentIndex(model->index(0, 0));
```

#### `QModelIndex currentIndex() const`

- **作用**：获取当前选中的索引。
- **返回值**：`QModelIndex`，当前索引。

```cpp
QModelIndex index = columnView->currentIndex();
```

### 5. 列表行为

#### `void setModel(QAbstractItemModel *model)`

- **作用**：设置数据模型。
- **参数**：
  - `model`：数据模型，类型为 `QAbstractItemModel*`。
- **返回值**：`void`，无返回值。

```cpp
columnView->setModel(model);
```

### 6. 排序与筛选

#### `void setRootIndex(const QModelIndex &index)`

- **作用**：设置视图的根索引，用于显示数据模型的子项。
- **参数**：
  - `index`：根索引，类型为 `QModelIndex`。
- **返回值**：`void`，无返回值。

```cpp
columnView->setRootIndex(model->index(0, 0));
```

#### `QModelIndex rootIndex() const`

- **作用**：获取视图的根索引。
- **返回值**：`QModelIndex`，根索引。

```cpp
QModelIndex root = columnView->rootIndex();
```

### 7. 列宽设置

#### `void setColumnWidth(int column, int width)`

- **作用**：设置指定列的宽度。
- **参数**：
  - `column`：列索引，类型为 `int`。
  - `width`：列宽，单位为像素，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
columnView->setColumnWidth(0, 200);
```

#### `int columnWidth(int column) const`

- **作用**：获取指定列的宽度。
- **参数**：
  - `column`：列索引，类型为 `int`。
- **返回值**：`int`，列宽。

```cpp
int width = columnView->columnWidth(0);
```

### 8. 滚动条

#### `void setHorizontalScrollBarPolicy(Qt::ScrollBarPolicy policy)`

- **作用**：设置水平滚动条策略。
- **参数**：
  - `policy`：滚动条策略，类型为 `Qt::ScrollBarPolicy`。
- **返回值**：`void`，无返回值。

```cpp
columnView->setHorizontalScrollBarPolicy(Qt::ScrollBarAlwaysOn);
```

#### `Qt::ScrollBarPolicy horizontalScrollBarPolicy() const`

- **作用**：获取水平滚动条策略。
- **返回值**：`Qt::ScrollBarPolicy`，滚动条策略。

```cpp
Qt::ScrollBarPolicy policy = columnView->horizontalScrollBarPolicy();
```

#### `void setVerticalScrollBarPolicy(Qt::ScrollBarPolicy policy)`

- **作用**：设置垂直滚动条策略。
- **参数**：
  - `policy`：滚动条策略，类型为 `Qt::ScrollBarPolicy`。
- **返回值**：`void`，无返回值。

```cpp
columnView->setVerticalScrollBarPolicy(Qt::ScrollBarAlwaysOn);
```

#### `Qt::ScrollBarPolicy verticalScrollBarPolicy() const`

- **作用**：获取垂直滚动条策略。
- **返回值**：`Qt::ScrollBarPolicy`，滚动条策略。

```cpp
Qt::ScrollBarPolicy policy = columnView->verticalScrollBarPolicy();
```

### 9. 高级功能

#### `void setHeader(QHeaderView *header)`

- **作用**：设置表头视图。
- **参数**：
  - `header`：表头视图，类型为 `QHeaderView*`。
- **返回值**：`void`，无返回值。

```cpp
QHeaderView *header = new QHeaderView(Qt::Horizontal);
columnView->setHeader(header);
```

#### `QHeaderView *header() const`

- **作用**：获取表头视图。
- **返回值**：`QHeaderView*`，表头视图。

```cpp
QHeaderView *header = columnView->header();
```

### 10. 自定义绘制与行为

#### `void setItemDelegate(QAbstractItemDelegate *delegate)`

- **作用**：设置自定义的项委托，用于渲染和编辑项。
- **参数**：
  - `delegate`：项委托，类型为 `QAbstractItemDelegate*`。
- **返回值**：`void`，无返回值。

```cpp
QItemDelegate *delegate = new QItemDelegate();
columnView->setItemDelegate(delegate);
```

#### `QAbstractItemDelegate *itemDelegate() const`

- **作用**：获取当前的项委托。
- **返回值**：`QAbstractItemDelegate*`，项委托。

```cpp
QAbstractItemDelegate *delegate = columnView->itemDelegate();
```

### 11. 事件处理

#### `bool event(QEvent *event) override`

- **作用**：重写事件处理方法以自定义事件处理。
- **参数**：
  - `event`：事件对象，类型为 `QEvent*`。
- **返回值**：`bool`，事件处理状态。

```cpp
bool QColumnView::event(QEvent *event) override {
    if (event->type() == QEvent::MouseButtonPress) {
        // Custom event handling code
    }
    return QColumnView::event(event);
}
```

### 12. 样式与视觉效果

#### `void setStyleSheet(const QString &styleSheet)`

- **作用**：设置控件的样式表。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。
- **返回值**：`void`，无返回值。

```cpp
columnView->setStyleSheet("background-color: lightgray;");
```

`QColumnView` 的常用方法已基本涵盖了其主要功能和操作。不过，以下是一些可能不那么常见但仍然有用的额外方法：

### 13. 数据更新与通知

#### `void updateGeometries()`

- **作用**：更新视图中的几何形状，通常在视图布局发生变化时调用。
- **返回值**：`void`，无返回值。

```cpp
columnView->updateGeometries();
```

#### `void setRootIndex(const QModelIndex &index)`

- **作用**：设置根索引，指定数据模型的显示根项。
- **参数**：
  - `index`：根索引，类型为 `QModelIndex`。
- **返回值**：`void`，无返回值。

```cpp
columnView->setRootIndex(model->index(0, 0));
```

### 14. 自定义滚动条

#### `QScrollBar *horizontalScrollBar() const`

- **作用**：获取水平滚动条。
- **返回值**：`QScrollBar*`，水平滚动条对象。

```cpp
QScrollBar *hScrollBar = columnView->horizontalScrollBar();
```

#### `QScrollBar *verticalScrollBar() const`

- **作用**：获取垂直滚动条。
- **返回值**：`QScrollBar*`，垂直滚动条对象。

```cpp
QScrollBar *vScrollBar = columnView->verticalScrollBar();
```

### 15. 高级样式与自定义绘制

#### `void setStyleSheet(const QString &styleSheet)`

- **作用**：设置控件的样式表。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。
- **返回值**：`void`，无返回值。

```cpp
columnView->setStyleSheet("background-color: lightblue;");
```

### 16. 分辨率与渲染

#### `void setColumnWidth(int column, int width)`

- **作用**：设置指定列的宽度。
- **参数**：
  - `column`：列索引，类型为 `int`。
  - `width`：列宽，单位为像素，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
columnView->setColumnWidth(0, 200);
```

#### `int columnWidth(int column) const`

- **作用**：获取指定列的宽度。
- **参数**：
  - `column`：列索引，类型为 `int`。
- **返回值**：`int`，列宽。

```cpp
int width = columnView->columnWidth(0);
```

### 17. 布局调整

#### `void resizeEvent(QResizeEvent *event) override`

- **作用**：重写以自定义控件大小调整时的行为。
- **参数**：
  - `event`：大小调整事件，类型为 `QResizeEvent*`。
- **返回值**：`void`，无返回值。

```cpp
void QColumnView::resizeEvent(QResizeEvent *event) override {
    // Custom resize handling code
    QColumnView::resizeEvent(event);
}
```

### 18. 高级数据交互

#### `void setItemDelegateForColumn(int column, QAbstractItemDelegate *delegate)`

- **作用**：为指定列设置项委托。
- **参数**：
  - `column`：列索引，类型为 `int`。
  - `delegate`：项委托，类型为 `QAbstractItemDelegate*`。
- **返回值**：`void`，无返回值。

```cpp
QItemDelegate *delegate = new QItemDelegate();
columnView->setItemDelegateForColumn(0, delegate);
```

### 19. 自定义模型视图行为

#### `void setHeader(QHeaderView *header)`

- **作用**：设置视图的头部。
- **参数**：
  - `header`：头部视图，类型为 `QHeaderView*`。
- **返回值**：`void`，无返回值。

```cpp
QHeaderView *header = new QHeaderView(Qt::Horizontal);
columnView->setHeader(header);
```

### 20. 选择与多选

#### `void setSelectionBehavior(QAbstractItemView::SelectionBehavior behavior)`

- **作用**：设置选择行为（例如，按行选择或按项选择）。
- **参数**：
  - `behavior`：选择行为，类型为 `QAbstractItemView::SelectionBehavior`。
- **返回值**：`void`，无返回值。

```cpp
columnView->setSelectionBehavior(QAbstractItemView::SelectRows);
```

### 21. 自定义工具条

#### `void setToolButtonStyle(Qt::ToolButtonStyle style)`

- **作用**：设置工具按钮的样式。
- **参数**：
  - `style`：工具按钮样式，类型为 `Qt::ToolButtonStyle`。
- **返回值**：`void`，无返回值。

```cpp
columnView->setToolButtonStyle(Qt::ToolButtonTextBesideIcon);
```

### 22. 高级交互

#### `void setDragDropMode(QAbstractItemView::DragDropMode mode)`

- **作用**：设置拖放模式。
- **参数**：
  - `mode`：拖放模式，类型为 `QAbstractItemView::DragDropMode`。
- **返回值**：`void`，无返回值。

```cpp
columnView->setDragDropMode(QAbstractItemView::InternalMove);
```
