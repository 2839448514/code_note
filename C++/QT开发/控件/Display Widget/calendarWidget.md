`QCalendarWidget` 是 Qt 框架中的一个控件，用于显示和操作日历。它提供了丰富的功能来管理日期选择和显示。以下是 `QCalendarWidget` 的详细函数方法及其作用：

### 1. **基本设置和初始化**

#### `setSelectedDate(const QDate &date)`
- **作用**：设置选定的日期。
- **参数**：
  - `date`：要设置的日期，类型为 `QDate`。

```cpp
calendarWidget->setSelectedDate(QDate(2024, 7, 23));
```

#### `selectedDate()`
- **作用**：获取当前选定的日期。
- **返回值**：`QDate`，当前选定的日期。

```cpp
QDate date = calendarWidget->selectedDate();
```

### 2. **日期范围**

#### `setMinimumDate(const QDate &date)`
- **作用**：设置最小可选择日期。
- **参数**：
  - `date`：最小日期，类型为 `QDate`。

```cpp
calendarWidget->setMinimumDate(QDate(2024, 1, 1));
```

#### `minimumDate()`
- **作用**：获取最小可选择日期。
- **返回值**：`QDate`，最小日期。

```cpp
QDate minDate = calendarWidget->minimumDate();
```

#### `setMaximumDate(const QDate &date)`
- **作用**：设置最大可选择日期。
- **参数**：
  - `date`：最大日期，类型为 `QDate`。

```cpp
calendarWidget->setMaximumDate(QDate(2024, 12, 31));
```

#### `maximumDate()`
- **作用**：获取最大可选择日期。
- **返回值**：`QDate`，最大日期。

```cpp
QDate maxDate = calendarWidget->maximumDate();
```

#### `setDateRange(const QDate &minDate, const QDate &maxDate)`
- **作用**：设置日期选择范围。
- **参数**：
  - `minDate`：最小日期，类型为 `QDate`。
  - `maxDate`：最大日期，类型为 `QDate`。

```cpp
calendarWidget->setDateRange(QDate(2024, 1, 1), QDate(2024, 12, 31));
```

### 3. **日期选择**

#### `setGridVisible(bool visible)`
- **作用**：设置是否显示日期网格。
- **参数**：
  - `visible`：是否显示网格，类型为 `bool`（`true` 表示显示，`false` 表示不显示）。

```cpp
calendarWidget->setGridVisible(true);
```

#### `isGridVisible()`
- **作用**：检查网格是否可见。
- **返回值**：`bool`，网格是否可见。

```cpp
bool gridVisible = calendarWidget->isGridVisible();
```

### 4. **显示设置**

#### `setFirstDayOfWeek(Qt::DayOfWeek day)`
- **作用**：设置一周的第一天。
- **参数**：
  - `day`：一周的第一天，类型为 `Qt::DayOfWeek`（例如 `Qt::Monday`）。

```cpp
calendarWidget->setFirstDayOfWeek(Qt::Monday);
```

#### `firstDayOfWeek()`
- **作用**：获取一周的第一天。
- **返回值**：`Qt::DayOfWeek`，一周的第一天。

```cpp
Qt::DayOfWeek firstDay = calendarWidget->firstDayOfWeek();
```

### 5. **日期格式**

#### `setHeaderTextFormat(const QDate &date, const QString &format)`
- **作用**：设置日期头部文本格式。
- **参数**：
  - `date`：需要设置格式的日期，类型为 `QDate`。
  - `format`：日期格式，类型为 `QString`（例如 `"yyyy-MM-dd"`）。

```cpp
calendarWidget->setHeaderTextFormat(QDate(2024, 7, 23), "MMMM yyyy");
```

#### `headerTextFormat()`
- **作用**：获取日期头部文本格式。
- **返回值**：`QString`，日期头部的文本格式。

```cpp
QString format = calendarWidget->headerTextFormat();
```

### 6. **信号与槽**

#### `clicked(const QDate &date)`
- **作用**：当用户点击一个日期时发出信号。
- **参数**：
  - `date`：被点击的日期，类型为 `QDate`。

```cpp
connect(calendarWidget, &QCalendarWidget::clicked, [](const QDate &date) {
    qDebug() << "Clicked date:" << date.toString();
});
```

#### `selectionChanged()`
- **作用**：当选定日期改变时发出信号。

```cpp
connect(calendarWidget, &QCalendarWidget::selectionChanged, []() {
    qDebug() << "Selection changed!";
});
```

### 7. **自定义显示**

#### `setHeaderTextFormat(const QDate &date, const QString &format)`
- **作用**：自定义日期头部的显示格式。
- **参数**：
  - `date`：要设置的日期，类型为 `QDate`。
  - `format`：自定义格式，类型为 `QString`。

```cpp
calendarWidget->setHeaderTextFormat(QDate(2024, 7, 23), "MMMM yyyy");
```

### 8. **样式和外观**

#### `setStyleSheet(const QString &styleSheet)`
- **作用**：设置控件的样式表。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。

```cpp
calendarWidget->setStyleSheet("QCalendarWidget { background-color: lightblue; }");
```

### 9. **日期事件**

#### `paintCell(QPainter *painter, const QRect &rect, const QDate &date)`
- **作用**：自定义绘制单元格。
- **参数**：
  - `painter`：绘图工具，类型为 `QPainter` 指针。
  - `rect`：单元格区域，类型为 `QRect`。
  - `date`：日期，类型为 `QDate`。

```cpp
void MyCalendarWidget::paintCell(QPainter *painter, const QRect &rect, const QDate &date) {
    // 自定义绘制逻辑
}
```

### 10. **日历事件**

#### `paintHeader(QPainter *painter, const QRect &rect)`
- **作用**：自定义绘制头部。
- **参数**：
  - `painter`：绘图工具，类型为 `QPainter` 指针。
  - `rect`：头部区域，类型为 `QRect`。

```cpp
void MyCalendarWidget::paintHeader(QPainter *painter, const QRect &rect) {
    // 自定义绘制逻辑
}
```

`QCalendarWidget` 的功能非常全面，但以下是一些额外的方法和功能，以确保覆盖所有主要的使用场景：

### 11. **选择区域**

#### `setSelectedDate(const QDate &date)`
- **作用**：设置选定的日期。
- **参数**：
  - `date`：要设置的日期，类型为 `QDate`。

```cpp
calendarWidget->setSelectedDate(QDate(2024, 7, 23));
```

#### `selectedDate()`
- **作用**：获取当前选定的日期。
- **返回值**：`QDate`，当前选定的日期。

```cpp
QDate date = calendarWidget->selectedDate();
```

### 12. **日期格式**

#### `setDateTextFormat(const QDate &date, const QTextCharFormat &format)`
- **作用**：设置特定日期的文本格式。
- **参数**：
  - `date`：需要设置格式的日期，类型为 `QDate`。
  - `format`：文本格式，类型为 `QTextCharFormat`。

```cpp
QTextCharFormat format;
format.setForeground(Qt::red);
calendarWidget->setDateTextFormat(QDate(2024, 7, 23), format);
```

#### `dateTextFormat(const QDate &date)`
- **作用**：获取特定日期的文本格式。
- **参数**：
  - `date`：需要获取格式的日期，类型为 `QDate`。
- **返回值**：`QTextCharFormat`，指定日期的文本格式。

```cpp
QTextCharFormat format = calendarWidget->dateTextFormat(QDate(2024, 7, 23));
```

### 13. **背景颜色**

#### `setDateBackgroundColor(const QDate &date, const QColor &color)`
- **作用**：设置特定日期的背景颜色。
- **参数**：
  - `date`：需要设置颜色的日期，类型为 `QDate`。
  - `color`：背景颜色，类型为 `QColor`。

```cpp
calendarWidget->setDateBackgroundColor(QDate(2024, 7, 23), Qt::yellow);
```

#### `dateBackgroundColor(const QDate &date)`
- **作用**：获取特定日期的背景颜色。
- **参数**：
  - `date`：需要获取颜色的日期，类型为 `QDate`。
- **返回值**：`QColor`，指定日期的背景颜色。

```cpp
QColor color = calendarWidget->dateBackgroundColor(QDate(2024, 7, 23));
```

### 14. **日期选择器**

#### `setDateEditEnabled(bool enabled)`
- **作用**：设置是否允许编辑日期（即是否显示日期编辑框）。
- **参数**：
  - `enabled`：是否启用日期编辑，类型为 `bool`（`true` 表示启用，`false` 表示禁用）。

```cpp
calendarWidget->setDateEditEnabled(true);
```

#### `isDateEditEnabled()`
- **作用**：检查日期编辑是否启用。
- **返回值**：`bool`，日期编辑是否启用。

```cpp
bool enabled = calendarWidget->isDateEditEnabled();
```

### 15. **日期选择模式**

#### `setNavigationBarVisible(bool visible)`
- **作用**：设置是否显示导航栏。
- **参数**：
  - `visible`：是否显示导航栏，类型为 `bool`（`true` 表示显示，`false` 表示不显示）。

```cpp
calendarWidget->setNavigationBarVisible(true);
```

#### `isNavigationBarVisible()`
- **作用**：检查导航栏是否可见。
- **返回值**：`bool`，导航栏是否可见。

```cpp
bool visible = calendarWidget->isNavigationBarVisible();
```

### 16. **日期范围**

#### `setFirstDayOfWeek(Qt::DayOfWeek day)`
- **作用**：设置一周的第一天。
- **参数**：
  - `day`：一周的第一天，类型为 `Qt::DayOfWeek`（例如 `Qt::Monday`）。

```cpp
calendarWidget->setFirstDayOfWeek(Qt::Monday);
```

#### `firstDayOfWeek()`
- **作用**：获取一周的第一天。
- **返回值**：`Qt::DayOfWeek`，一周的第一天。

```cpp
Qt::DayOfWeek day = calendarWidget->firstDayOfWeek();
```

### 17. **自定义绘制**

#### `paintCell(QPainter *painter, const QRect &rect, const QDate &date)`
- **作用**：自定义绘制单元格。
- **参数**：
  - `painter`：绘图工具，类型为 `QPainter` 指针。
  - `rect`：单元格区域，类型为 `QRect`。
  - `date`：日期，类型为 `QDate`。

```cpp
void MyCalendarWidget::paintCell(QPainter *painter, const QRect &rect, const QDate &date) {
    // 自定义绘制逻辑
}
```

#### `paintHeader(QPainter *painter, const QRect &rect)`
- **作用**：自定义绘制头部。
- **参数**：
  - `painter`：绘图工具，类型为 `QPainter` 指针。
  - `rect`：头部区域，类型为 `QRect`。

```cpp
void MyCalendarWidget::paintHeader(QPainter *painter, const QRect &rect) {
    // 自定义绘制逻辑
}
```

### 18. **日历事件**

#### `calendarWidget->currentPageChanged(int year, int month)`
- **作用**：当日历页面（月份）改变时发出信号。
- **参数**：
  - `year`：当前年，类型为 `int`。
  - `month`：当前月，类型为 `int`。

```cpp
connect(calendarWidget, &QCalendarWidget::currentPageChanged, [](int year, int month) {
    qDebug() << "Current page changed to:" << year << month;
});
```

#### `calendarWidget->selectionChanged()`
- **作用**：当选定日期改变时发出信号。

```cpp
connect(calendarWidget, &QCalendarWidget::selectionChanged, []() {
    qDebug() << "Selection changed!";
});
```

`QCalendarWidget` 提供了丰富的功能，但以下是一些进一步的详细方法和功能，它们在特定情况下可能会用到：

### 19. **日期选择和高亮**

#### `setHighlightedDate(const QDate &date)`
- **作用**：设置高亮显示的日期。
- **参数**：
  - `date`：需要高亮显示的日期，类型为 `QDate`。

```cpp
calendarWidget->setHighlightedDate(QDate(2024, 7, 23));
```

#### `highlightedDate()`
- **作用**：获取当前高亮显示的日期。
- **返回值**：`QDate`，当前高亮显示的日期。

```cpp
QDate highlightedDate = calendarWidget->highlightedDate();
```

### 20. **自定义显示格式**

#### `setHeaderTextFormat(const QDate &date, const QTextCharFormat &format)`
- **作用**：设置头部文本格式。
- **参数**：
  - `date`：需要设置格式的日期，类型为 `QDate`。
  - `format`：文本格式，类型为 `QTextCharFormat`。

```cpp
QTextCharFormat format;
format.setFontWeight(QFont::Bold);
calendarWidget->setHeaderTextFormat(QDate(2024, 7, 23), format);
```

#### `headerTextFormat(const QDate &date)`
- **作用**：获取特定日期的头部文本格式。
- **参数**：
  - `date`：需要获取格式的日期，类型为 `QDate`。
- **返回值**：`QTextCharFormat`，指定日期的头部文本格式。

```cpp
QTextCharFormat format = calendarWidget->headerTextFormat(QDate(2024, 7, 23));
```

### 21. **视图设置**

#### `setVerticalHeaderVisible(bool visible)`
- **作用**：设置是否显示垂直头部。
- **参数**：
  - `visible`：是否显示垂直头部，类型为 `bool`（`true` 表示显示，`false` 表示不显示）。

```cpp
calendarWidget->setVerticalHeaderVisible(true);
```

#### `isVerticalHeaderVisible()`
- **作用**：检查垂直头部是否可见。
- **返回值**：`bool`，垂直头部是否可见。

```cpp
bool visible = calendarWidget->isVerticalHeaderVisible();
```

### 22. **自定义选中状态**

#### `setDateSelectionEnabled(bool enabled)`
- **作用**：设置是否启用日期选择。
- **参数**：
  - `enabled`：是否启用日期选择，类型为 `bool`（`true` 表示启用，`false` 表示禁用）。

```cpp
calendarWidget->setDateSelectionEnabled(true);
```

#### `isDateSelectionEnabled()`
- **作用**：检查日期选择是否启用。
- **返回值**：`bool`，日期选择是否启用。

```cpp
bool enabled = calendarWidget->isDateSelectionEnabled();
```

### 23. **自定义绘制日期**

#### `setDateTextFormat(const QDate &date, const QTextCharFormat &format)`
- **作用**：设置特定日期的文本格式。
- **参数**：
  - `date`：需要设置格式的日期，类型为 `QDate`。
  - `format`：文本格式，类型为 `QTextCharFormat`。

```cpp
QTextCharFormat format;
format.setForeground(Qt::green);
calendarWidget->setDateTextFormat(QDate(2024, 7, 23), format);
```

#### `dateTextFormat(const QDate &date)`
- **作用**：获取特定日期的文本格式。
- **参数**：
  - `date`：需要获取格式的日期，类型为 `QDate`。
- **返回值**：`QTextCharFormat`，指定日期的文本格式。

```cpp
QTextCharFormat format = calendarWidget->dateTextFormat(QDate(2024, 7, 23));
```

### 24. **操作和设置**

#### `setFirstDayOfWeek(Qt::DayOfWeek day)`
- **作用**：设置一周的第一天。
- **参数**：
  - `day`：一周的第一天，类型为 `Qt::DayOfWeek`（例如 `Qt::Monday`）。

```cpp
calendarWidget->setFirstDayOfWeek(Qt::Monday);
```

#### `firstDayOfWeek()`
- **作用**：获取一周的第一天。
- **返回值**：`Qt::DayOfWeek`，一周的第一天。

```cpp
Qt::DayOfWeek firstDay = calendarWidget->firstDayOfWeek();
```

### 25. **自定义绘制**

#### `paintCell(QPainter *painter, const QRect &rect, const QDate &date)`
- **作用**：自定义绘制单元格。
- **参数**：
  - `painter`：绘图工具，类型为 `QPainter` 指针。
  - `rect`：单元格区域，类型为 `QRect`。
  - `date`：日期，类型为 `QDate`。

```cpp
void MyCalendarWidget::paintCell(QPainter *painter, const QRect &rect, const QDate &date) {
    // 自定义绘制逻辑
}
```

#### `paintHeader(QPainter *painter, const QRect &rect)`
- **作用**：自定义绘制头部。
- **参数**：
  - `painter`：绘图工具，类型为 `QPainter` 指针。
  - `rect`：头部区域，类型为 `QRect`。

```cpp
void MyCalendarWidget::paintHeader(QPainter *painter, const QRect &rect) {
    // 自定义绘制逻辑
}
```

### 26. **其他功能**

#### `setNavigationBarVisible(bool visible)`
- **作用**：设置是否显示导航栏。
- **参数**：
  - `visible`：是否显示导航栏，类型为 `bool`（`true` 表示显示，`false` 表示不显示）。

```cpp
calendarWidget->setNavigationBarVisible(true);
```

#### `isNavigationBarVisible()`
- **作用**：检查导航栏是否可见。
- **返回值**：`bool`，导航栏是否可见。

```cpp
bool visible = calendarWidget->isNavigationBarVisible();
```

