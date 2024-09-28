---
tags:
  - QT开发
---
# tableWidget

`QTableWidget` 是 Qt 中用于显示和操作表格数据的控件，继承自 `QTableView`。它提供了用于管理和操作表格的丰富功能。以下是 `QTableWidget` 的详细函数方法及其作用：

### 1. 基本构造与销毁

#### `QTableWidget(int rows, int columns, QWidget *parent = nullptr)`

- **作用**：构造一个 `QTableWidget` 对象，并指定初始行数和列数。
- **参数**：
  - `rows`：初始行数，类型为 `int`。
  - `columns`：初始列数，类型为 `int`。
  - `parent`：父控件，类型为 `QWidget*`。默认为 `nullptr`。
- **返回值**：`QTableWidget` 对象。

```cpp
QTableWidget *tableWidget = new QTableWidget(5, 3, parentWidget);
```

### 2. 设置与获取列和行

#### `void setRowCount(int rows)`

- **作用**：设置表格的行数。
- **参数**：
  - `rows`：行数，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->setRowCount(10);
```

#### `void setColumnCount(int columns)`

- **作用**：设置表格的列数。
- **参数**：
  - `columns`：列数，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->setColumnCount(5);
```

#### `int rowCount() const`

- **作用**：获取表格的行数。
- **返回值**：`int`，行数。

```cpp
int rows = tableWidget->rowCount();
```

#### `int columnCount() const`

- **作用**：获取表格的列数。
- **返回值**：`int`，列数。

```cpp
int columns = tableWidget->columnCount();
```

### 3. 设置与获取单元格内容

#### `void setItem(int row, int column, QTableWidgetItem *item)`

- **作用**：设置指定位置的单元格项。
- **参数**：
  - `row`：行索引，类型为 `int`。
  - `column`：列索引，类型为 `int`。
  - `item`：要设置的项，类型为 `QTableWidgetItem*`。
- **返回值**：`void`，无返回值。

```cpp
QTableWidgetItem *item = new QTableWidgetItem("Cell Content");
tableWidget->setItem(0, 0, item);
```

#### `QTableWidgetItem *item(int row, int column) const`

- **作用**：获取指定位置的单元格项。
- **参数**：
  - `row`：行索引，类型为 `int`。
  - `column`：列索引，类型为 `int`。
- **返回值**：`QTableWidgetItem*`，指定位置的单元格项。

```cpp
QTableWidgetItem *item = tableWidget->item(0, 0);
```

### 4. 单元格内容的设置与获取

#### `void setHorizontalHeaderLabels(const QStringList &labels)`

- **作用**：设置表格的水平头部标签。
- **参数**：
  - `labels`：标签列表，类型为 `QStringList`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->setHorizontalHeaderLabels(QStringList() << "Column 1" << "Column 2" << "Column 3");
```

#### `QStringList horizontalHeaderLabels() const`

- **作用**：获取表格的水平头部标签。
- **返回值**：`QStringList`，水平头部标签列表。

```cpp
QStringList labels = tableWidget->horizontalHeaderLabels();
```

#### `void setVerticalHeaderLabels(const QStringList &labels)`

- **作用**：设置表格的垂直头部标签。
- **参数**：
  - `labels`：标签列表，类型为 `QStringList`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->setVerticalHeaderLabels(QStringList() << "Row 1" << "Row 2" << "Row 3");
```

#### `QStringList verticalHeaderLabels() const`

- **作用**：获取表格的垂直头部标签。
- **返回值**：`QStringList`，垂直头部标签列表。

```cpp
QStringList labels = tableWidget->verticalHeaderLabels();
```

### 5. 插入与删除行/列

#### `void insertRow(int row)`

- **作用**：在指定位置插入一行。
- **参数**：
  - `row`：插入位置的索引，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->insertRow(2);
```

#### `void insertColumn(int column)`

- **作用**：在指定位置插入一列。
- **参数**：
  - `column`：插入位置的索引，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->insertColumn(2);
```

#### `void removeRow(int row)`

- **作用**：删除指定位置的行。
- **参数**：
  - `row`：要删除的行索引，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->removeRow(2);
```

#### `void removeColumn(int column)`

- **作用**：删除指定位置的列。
- **参数**：
  - `column`：要删除的列索引，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->removeColumn(2);
```

### 6. 表格的视图设置

#### `void setCellWidget(int row, int column, QWidget *widget)`

- **作用**：在指定单元格中设置小部件。
- **参数**：
  - `row`：行索引，类型为 `int`。
  - `column`：列索引，类型为 `int`。
  - `widget`：要设置的 widget，类型为 `QWidget*`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->setCellWidget(0, 1, new QPushButton("Button"));
```

#### `QWidget *cellWidget(int row, int column) const`

- **作用**：获取指定单元格中的小部件。
- **参数**：
  - `row`：行索引，类型为 `int`。
  - `column`：列索引，类型为 `int`。
- **返回值**：`QWidget*`，指定单元格中的小部件。

```cpp
QWidget *widget = tableWidget->cellWidget(0, 1);
```

### 7. 表格的选择与排序

#### `void setSortingEnabled(bool enable)`

- **作用**：启用或禁用排序功能。
- **参数**：
  - `enable`：是否启用排序，类型为 `bool`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->setSortingEnabled(true);
```

#### `void sortItems(int column, Qt::SortOrder order)`

- **作用**：对指定列进行排序。
- **参数**：
  - `column`：列索引，类型为 `int`。
  - `order`：排序顺序，类型为 `Qt::SortOrder`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->sortItems(0, Qt::AscendingOrder);
```

### 8. 表格的选择模式

#### `void setSelectionMode(QAbstractItemView::SelectionMode mode)`

- **作用**：设置选择模式。
- **参数**：
  - `mode`：选择模式，类型为 `QAbstractItemView::SelectionMode`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->setSelectionMode(QAbstractItemView::SingleSelection);
```

#### `QAbstractItemView::SelectionMode selectionMode() const`

- **作用**：获取选择模式。
- **返回值**：`QAbstractItemView::SelectionMode`，选择模式。

```cpp
QAbstractItemView::SelectionMode mode = tableWidget->selectionMode();
```

### 9. 数据操作

#### `void setCurrentCell(int row, int column, QItemSelectionModel::SelectionFlags command)`

- **作用**：设置当前单元格。
- **参数**：
  - `row`：行索引，类型为 `int`。
  - `column`：列索引，类型为 `int`。
  - `command`：选择标志，类型为 `QItemSelectionModel::SelectionFlags`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->setCurrentCell(0, 0);
```

#### `void set

CurrentItem(QTableWidgetItem *item, QItemSelectionModel::SelectionFlags command)`

- **作用**：设置当前项。
- **参数**：
  - `item`：项，类型为 `QTableWidgetItem*`。
  - `command`：选择标志，类型为 `QItemSelectionModel::SelectionFlags`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->setCurrentItem(item);
```

### 10. 表格的视图设置

#### `void setEditTriggers(QAbstractItemView::EditTriggers triggers)`

- **作用**：设置编辑触发器。
- **参数**：
  - `triggers`：编辑触发器，类型为 `QAbstractItemView::EditTriggers`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->setEditTriggers(QAbstractItemView::DoubleClicked);
```

#### `QAbstractItemView::EditTriggers editTriggers() const`

- **作用**：获取编辑触发器。
- **返回值**：`QAbstractItemView::EditTriggers`，编辑触发器。

```cpp
QAbstractItemView::EditTriggers triggers = tableWidget->editTriggers();
```

### 11. 表格的样式设置

#### `void setStyleSheet(const QString &styleSheet)`

- **作用**：设置表格的样式表。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->setStyleSheet("QTableWidget { background-color: #f0f0f0; }");
```

### 12. 额外方法

#### `void clear()`

- **作用**：清空表格中的所有内容。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->clear();
```

#### `void setRowHeight(int row, int height)`

- **作用**：设置指定行的高度。
- **参数**：
  - `row`：行索引，类型为 `int`。
  - `height`：高度，类型为 `int`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->setRowHeight(1, 40);
```

#### `int rowHeight(int row) const`

- **作用**：获取指定行的高度。
- **参数**：
  - `row`：行索引，类型为 `int`。
- **返回值**：`int`，高度。

```cpp
int height = tableWidget->rowHeight(1);
在 `QTableWidget` 的功能中，已经涵盖了绝大多数常用的方法和属性。以下是一些可能较少用但仍然有用的高级功能和方法：

### 13. 高级功能

#### `void resizeColumnsToContents()`
- **作用**：根据内容调整所有列的宽度。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->resizeColumnsToContents();
```

#### `void resizeRowsToContents()`

- **作用**：根据内容调整所有行的高度。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->resizeRowsToContents();
```

#### `void setHorizontalHeader(QHeaderView *header)`

- **作用**：设置表格的水平头部视图。
- **参数**：
  - `header`：头部视图，类型为 `QHeaderView*`。
- **返回值**：`void`，无返回值。

```cpp
QHeaderView *header = new QHeaderView(Qt::Horizontal);
tableWidget->setHorizontalHeader(header);
```

#### `QHeaderView *horizontalHeader() const`

- **作用**：获取表格的水平头部视图。
- **返回值**：`QHeaderView*`，水平头部视图。

```cpp
QHeaderView *header = tableWidget->horizontalHeader();
```

#### `void setVerticalHeader(QHeaderView *header)`

- **作用**：设置表格的垂直头部视图。
- **参数**：
  - `header`：头部视图，类型为 `QHeaderView*`。
- **返回值**：`void`，无返回值。

```cpp
QHeaderView *header = new QHeaderView(Qt::Vertical);
tableWidget->setVerticalHeader(header);
```

#### `QHeaderView *verticalHeader() const`

- **作用**：获取表格的垂直头部视图。
- **返回值**：`QHeaderView*`，垂直头部视图。

```cpp
QHeaderView *header = tableWidget->verticalHeader();
```

#### `void setEditTriggers(QAbstractItemView::EditTriggers triggers)`

- **作用**：设置编辑触发器。
- **参数**：
  - `triggers`：编辑触发器，类型为 `QAbstractItemView::EditTriggers`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->setEditTriggers(QAbstractItemView::AllEditTriggers);
```

#### `QAbstractItemView::EditTriggers editTriggers() const`

- **作用**：获取编辑触发器。
- **返回值**：`QAbstractItemView::EditTriggers`，编辑触发器。

```cpp
QAbstractItemView::EditTriggers triggers = tableWidget->editTriggers();
```

### 14. 数据操作

#### `void setItemPrototype(QTableWidgetItem *prototype)`

- **作用**：设置用于创建新项的原型。
- **参数**：
  - `prototype`：项原型，类型为 `QTableWidgetItem*`。
- **返回值**：`void`，无返回值。

```cpp
QTableWidgetItem *prototype = new QTableWidgetItem();
tableWidget->setItemPrototype(prototype);
```

### 15. 编辑与选择

#### `QItemSelectionModel *selectionModel() const`

- **作用**：获取与表格关联的选择模型。
- **返回值**：`QItemSelectionModel*`，选择模型。

```cpp
QItemSelectionModel *selectionModel = tableWidget->selectionModel();
```

#### `void setSelectionModel(QItemSelectionModel *selectionModel)`

- **作用**：设置表格的选择模型。
- **参数**：
  - `selectionModel`：选择模型，类型为 `QItemSelectionModel*`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->setSelectionModel(selectionModel);
```

### 16. 表格视图的滚动

#### `void scrollToItem(QTableWidgetItem *item, QAbstractItemView::ScrollHint hint)`

- **作用**：滚动视图以确保指定项可见。
- **参数**：
  - `item`：要滚动到的项，类型为 `QTableWidgetItem*`。
  - `hint`：滚动提示，类型为 `QAbstractItemView::ScrollHint`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->scrollToItem(item, QAbstractItemView::EnsureVisible);
```

### 17. 交互模式

#### `void setSelectionBehavior(QAbstractItemView::SelectionBehavior behavior)`

- **作用**：设置选择行为。
- **参数**：
  - `behavior`：选择行为，类型为 `QAbstractItemView::SelectionBehavior`。
- **返回值**：`void`，无返回值。

```cpp
tableWidget->setSelectionBehavior(QAbstractItemView::SelectItems);
```

### 18. 数据过滤与排序

#### `void setModel(QAbstractItemModel *model)`

- **作用**：设置表格的数据模型。
- **参数**：
  - `model`：数据模型，类型为 `QAbstractItemModel*`。
- **返回值**：`void`，无返回值。

```cpp
QAbstractItemModel *model = new QStandardItemModel();
tableWidget->setModel(model);
```

这些方法覆盖了 `QTableWidget` 大多数功能的高级应用。如果有特定的需求或者希望深入了解某些方法，欢迎继续询问！
