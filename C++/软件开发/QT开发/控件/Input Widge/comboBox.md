`QComboBox` 是 Qt 中的一个下拉列表控件，允许用户从下拉菜单中选择一个选项。它结合了 `QPushButton` 和 `QListView` 的功能，可以显示一组可供选择的项。以下是 `QComboBox` 的详细函数方法及其作用：

### 常用函数方法

### 1. `addItem(const QString &text, const QVariant &userData = QVariant())`
- **作用**：在下拉列表中添加一个项。
- **参数**：
  - `text`：要显示的文本，类型为 `QString`。
  - `userData`：与该项相关联的用户数据，类型为 `QVariant`，默认为 `QVariant()`。

```cpp
comboBox->addItem("Item 1", QVariant(1));
```

### 2. `addItems(const QStringList &texts)`
- **作用**：在下拉列表中添加多个项。
- **参数**：
  - `texts`：要添加的文本列表，类型为 `QStringList`。

```cpp
QStringList items;
items << "Item 1" << "Item 2" << "Item 3";
comboBox->addItems(items);
```

### 3. `insertItem(int index, const QString &text, const QVariant &userData = QVariant())`
- **作用**：在指定索引位置插入一个项。
- **参数**：
  - `index`：插入的位置索引，类型为 `int`。
  - `text`：要显示的文本，类型为 `QString`。
  - `userData`：与该项相关联的用户数据，类型为 `QVariant`，默认为 `QVariant()`。

```cpp
comboBox->insertItem(1, "Inserted Item", QVariant(2));
```

### 4. `insertItems(int index, const QStringList &texts)`
- **作用**：在指定索引位置插入多个项。
- **参数**：
  - `index`：插入的位置索引，类型为 `int`。
  - `texts`：要插入的文本列表，类型为 `QStringList`。

```cpp
comboBox->insertItems(2, QStringList() << "Inserted Item 1" << "Inserted Item 2");
```

### 5. `removeItem(int index)`
- **作用**：移除指定索引位置的项。
- **参数**：
  - `index`：要移除的项的索引，类型为 `int`。

```cpp
comboBox->removeItem(0);
```

### 6. `clear()`
- **作用**：清除所有项。
- **无参数**。

```cpp
comboBox->clear();
```

### 7. `count()`
- **作用**：获取下拉列表中项的数量。
- **返回值**：`int`，项的数量。

```cpp
int itemCount = comboBox->count();
```

### 8. `currentIndex()`
- **作用**：获取当前选中项的索引。
- **返回值**：`int`，当前选中项的索引。

```cpp
int index = comboBox->currentIndex();
```

### 9. `setCurrentIndex(int index)`
- **作用**：设置当前选中项的索引。
- **参数**：
  - `index`：要设置的索引，类型为 `int`。

```cpp
comboBox->setCurrentIndex(1);
```

### 10. `currentText()`
- **作用**：获取当前选中项的文本。
- **返回值**：`QString`，当前选中项的文本。

```cpp
QString text = comboBox->currentText();
```

### 11. `setCurrentText(const QString &text)`
- **作用**：设置当前选中项的文本。
- **参数**：
  - `text`：要设置的文本，类型为 `QString`。

```cpp
comboBox->setCurrentText("Item 2");
```

### 12. `itemText(int index)`
- **作用**：获取指定索引位置项的文本。
- **参数**：
  - `index`：要获取文本的项的索引，类型为 `int`。
- **返回值**：`QString`，指定索引位置项的文本。

```cpp
QString text = comboBox->itemText(0);
```

### 13. `itemData(int index, int role = Qt::UserRole)`
- **作用**：获取指定索引位置项的用户数据。
- **参数**：
  - `index`：要获取用户数据的项的索引，类型为 `int`。
  - `role`：数据角色，类型为 `int`，默认为 `Qt::UserRole`。
- **返回值**：`QVariant`，指定索引位置项的用户数据。

```cpp
QVariant data = comboBox->itemData(0);
```

### 14. `setItemData(int index, const QVariant &data, int role = Qt::UserRole)`
- **作用**：设置指定索引位置项的用户数据。
- **参数**：
  - `index`：要设置数据的项的索引，类型为 `int`。
  - `data`：要设置的用户数据，类型为 `QVariant`。
  - `role`：数据角色，类型为 `int`，默认为 `Qt::UserRole`。

```cpp
comboBox->setItemData(0, QVariant(42));
```

### 15. `setEditable(bool editable)`
- **作用**：设置下拉列表是否可编辑。如果为 `true`，用户可以在下拉列表中输入自定义文本。
- **参数**：
  - `editable`：布尔值，`true` 表示可编辑，`false` 表示不可编辑。

```cpp
comboBox->setEditable(true);
```

### 16. `isEditable()`
- **作用**：检查下拉列表是否可编辑。
- **返回值**：`bool`，如果可编辑则返回 `true`，否则返回 `false`。

```cpp
bool editable = comboBox->isEditable();
```

### 17. `setModel(QAbstractItemModel *model)`
- **作用**：设置下拉列表的数据模型。可以使用自定义模型来管理列表中的数据。
- **参数**：
  - `model`：数据模型，类型为 `QAbstractItemModel*`。

```cpp
QStandardItemModel *model = new QStandardItemModel;
comboBox->setModel(model);
```

### 18. `model()`
- **作用**：获取下拉列表的数据模型。
- **返回值**：`QAbstractItemModel*`，当前使用的数据模型。

```cpp
QAbstractItemModel *model = comboBox->model();
```

### 19. `setView(QAbstractItemView *view)`
- **作用**：设置下拉列表的视图。可以使用自定义视图来显示列表中的项。
- **参数**：
  - `view`：视图，类型为 `QAbstractItemView*`。

```cpp
QListView *listView = new QListView;
comboBox->setView(listView);
```

### 20. `view()`
- **作用**：获取下拉列表的视图。
- **返回值**：`QAbstractItemView*`，当前使用的视图。

```cpp
QAbstractItemView *view = comboBox->view();
```

### 21. `setInsertPolicy(QComboBox::InsertPolicy policy)`
- **作用**：设置项的插入策略。可以控制新项是插入到现有项的前面、后面，还是在末尾。
- **参数**：
  - `policy`：插入策略，类型为 `QComboBox::InsertPolicy`。

```cpp
comboBox->setInsertPolicy(QComboBox::InsertAtTop);
```

### 22. `insertPolicy()`
- **作用**：获取项的插入策略。
- **返回值**：`QComboBox::InsertPolicy`，当前的插入策略。

```cpp
QComboBox::InsertPolicy policy = comboBox->insertPolicy();
```

### 23. `setSizeAdjustPolicy(QComboBox::SizeAdjustPolicy policy)`
- **作用**：设置大小调整策略，控制下拉列表的宽度如何自动调整。
- **参数**：
  - `policy`：大小调整策略，类型为 `QComboBox::SizeAdjustPolicy`。

```cpp
comboBox->setSizeAdjustPolicy(QComboBox::AdjustToContents);
```

### 24. `sizeAdjustPolicy()`
- **作用**：获取大小调整策略。
- **返回值**：`QComboBox::SizeAdjustPolicy`，当前的大小调整策略。

```cpp
QComboBox::SizeAdjustPolicy policy = comboBox->sizeAdjustPolicy();
```

### 25. `setDuplicatesEnabled(bool enable)`
- **作用**：设置是否允许重复项。如果为 `false`，则在添加项时会检查是否已存在相同的项。
- **参数**：
  - `enable`：布尔值，`true` 表示允许重复项，`false` 表示不允许。

```cpp
comboBox->setDuplicatesEnabled(false);
```

### 26. `duplicatesEnabled()`
-

 **作用**：检查是否允许重复项。
- **返回值**：`bool`，如果允许重复项则返回 `true`，否则返回 `false`。

```cpp
bool enabled = comboBox->duplicatesEnabled();
```

### 27. `setIconSize(const QSize &iconSize)`
- **作用**：设置下拉列表项图标的大小。
- **参数**：
  - `iconSize`：图标大小，类型为 `QSize`。

```cpp
comboBox->setIconSize(QSize(32, 32));
```

### 28. `iconSize()`
- **作用**：获取下拉列表项图标的大小。
- **返回值**：`QSize`，当前图标的大小。

```cpp
QSize iconSize = comboBox->iconSize();
```

### 29. `clearEditText()`
- **作用**：清除编辑模式下的文本。如果 `QComboBox` 是可编辑的，调用此方法将清除当前输入的文本。
- **无参数**。

```cpp
comboBox->clearEditText();
```

### 30. `setEditable(bool editable)`
- **作用**：设置下拉列表是否允许用户编辑文本。如果为 `true`，用户可以输入自定义文本。
- **参数**：
  - `editable`：布尔值，`true` 表示可编辑，`false` 表示不可编辑。

```cpp
comboBox->setEditable(true);
```

### 31. `lineEdit()`
- **作用**：获取下拉列表的 `QLineEdit` 控件，用于编辑模式下显示用户输入的文本。
- **返回值**：`QLineEdit*`，当前的 `QLineEdit` 控件。

```cpp
QLineEdit *lineEdit = comboBox->lineEdit();
```
