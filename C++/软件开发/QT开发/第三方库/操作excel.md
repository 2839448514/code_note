---
tags:
  - QT开发
---
# 操作excel

QXlsx 库提供了丰富的功能来处理 Excel 文件。以下是一些主要类及其常用函数的介绍：

### QXlsx::Document 类

`QXlsx::Document` 类是处理 Excel 文件的主要接口，提供了创建、打开、读写和保存 Excel 文件的功能。

#### 构造函数

```cpp
QXlsx::Document();
QXlsx::Document(const QString &name);
```

- **QXlsx::Document()**：创建一个新的空 Excel 文档。
- **QXlsx::Document(const QString &name)**：打开一个已有的 Excel 文件。

### 添加新工作表

#### `addSheet` 函数

```C++
`bool addSheet(const QString &name);`

```

- **addSheet(const QString &name)**：添加一个新的工作表，并命名为 `name`。返回一个布尔值，表示是否成功添加。

### 切换工作表

#### `selectSheet` 函数

```C++
`bool selectSheet(const QString &name);`
```

- **selectSheet(const QString &name)**：切换到名为 `name` 的工作表。返回一个布尔值，表示是否成功切换。

#### 写入函数

```cpp
bool write(const QString &cell, const QVariant &value, const Format &format = Format());
bool write(int row, int col, const QVariant &value, const Format &format = Format());
```

- **write(const QString &cell, const QVariant &value, const Format &format = Format())**：在指定单元格写入数据，可以使用单元格地址（如 "A1"）。
- **write(int row, int col, const QVariant &value, const Format &format = Format())**：在指定行列位置写入数据，行列从 1 开始计数。

#### 读取函数

```cpp
QVariant read(const QString &cell) const;
QVariant read(int row, int col) const;
```

- **read(const QString &cell) const**：读取指定单元格的数据。
- **read(int row, int col) const**：读取指定行列位置的数据。

#### 保存函数

```cpp
bool save() const;
bool saveAs(const QString &name) const;
```

- **save() const**：保存当前文档。
- **saveAs(const QString &name) const**：将当前文档另存为指定文件名。

#### 插入图表

```cpp
QXlsx::Chart *insertChart(int row, int col, const QSize &size);
```

- **insertChart(int row, int col, const QSize &size)**：在指定行列位置插入图表，返回 `QXlsx::Chart` 对象。

#### 插入图片

```cpp
bool insertImage(int row, int col, const QImage &image);
```

- **insertImage(int row, int col, const QImage &image)**：在指定行列位置插入图片。

### QXlsx::Format 类

`QXlsx::Format` 类用于定义单元格的格式，例如字体、颜色、对齐方式等。

#### 构造函数

```cpp
QXlsx::Format();
```

- **QXlsx::Format()**：创建一个默认格式对象。

#### 设置字体

```cpp
void setFontColor(const QColor &color);
void setFontBold(bool bold);
void setFontItalic(bool italic);
void setFontUnderline(QXlsx::Format::FontUnderline underline);
void setFontStrikeOut(bool strikeOut);
```

- **setFontColor(const QColor &color)**：设置字体颜色。
- **setFontBold(bool bold)**：设置字体加粗。
- **setFontItalic(bool italic)**：设置字体斜体。
- **setFontUnderline(QXlsx::Format::FontUnderline underline)**：设置字体下划线。
- **setFontStrikeOut(bool strikeOut)**：设置字体删除线。

#### 设置对齐方式

```cpp
void setHorizontalAlignment(QXlsx::Format::HorizontalAlignment align);
void setVerticalAlignment(QXlsx::Format::VerticalAlignment align);
```

- **setHorizontalAlignment(QXlsx::Format::HorizontalAlignment align)**：设置水平对齐方式。
- **setVerticalAlignment(QXlsx::Format::VerticalAlignment align)**：设置垂直对齐方式。

#### 设置单元格背景颜色

```cpp
void setPatternBackgroundColor(const QColor &color);
```

- **setPatternBackgroundColor(const QColor &color)**：设置单元格背景颜色。

### QXlsx::Chart 类

`QXlsx::Chart` 类用于创建和管理 Excel 图表。

#### 添加数据系列

```cpp
bool addSeries(const QXlsx::CellRange &range, QXlsx::Chart::AxisType axisType = QXlsx::Chart::AXIS_BOTTOM);
```

- **addSeries(const QXlsx::CellRange &range, QXlsx::Chart::AxisType axisType = QXlsx::Chart::AXIS_BOTTOM)**：添加一个数据系列到图表中，数据范围由 `QXlsx::CellRange` 指定。

#### 设置图表标题

```cpp
void setTitle(const QString &title);
```

- **setTitle(const QString &title)**：设置图表标题。

### QXlsx::CellRange 类

`QXlsx::CellRange` 类用于定义单元格范围。

#### 构造函数

```cpp
QXlsx::CellRange();
QXlsx::CellRange(int firstRow, int firstColumn, int lastRow, int lastColumn);
QXlsx::CellRange(const QString &range);
```

- **QXlsx::CellRange()**：创建一个空的单元格范围。
- **QXlsx::CellRange(int firstRow, int firstColumn, int lastRow, int lastColumn)**：创建一个由起始行列和结束行列定义的单元格范围。
- **QXlsx::CellRange(const QString &range)**：使用字符串（如 "A1:C3"）定义单元格范围。

### 代码示例

结合以上函数，可以使用 QXlsx 创建一个简单的 Excel 文件，写入数据，并设置单元格格式：

```cpp
#include <QCoreApplication>
#include <xlsxdocument.h>
#include <xlsxformat.h>
#include <xlsxchart.h>

int main(int argc, char *argv[]) {
    QCoreApplication a(argc, argv);

    // 创建一个新的 Excel 文档
    QXlsx::Document xlsx;

    // 设置格式
    QXlsx::Format headerFormat;
    headerFormat.setFontBold(true);
    headerFormat.setFontColor(Qt::white);
    headerFormat.setPatternBackgroundColor(Qt::blue);

    // 写入标题行
    xlsx.write("A1", "Name", headerFormat);
    xlsx.write("B1", "Score", headerFormat);

    // 写入数据
    xlsx.write("A2", "Alice");
    xlsx.write("B2", 85);

    xlsx.write("A3", "Bob");
    xlsx.write("B3", 90);

    // 插入图表
    QXlsx::Chart *chart = xlsx.insertChart(5, 1, QSize(400, 300));
    chart->addSeries(QXlsx::CellRange("A1:B3"));
    chart->setTitle("Scores");

    // 保存文档
    xlsx.saveAs("example.xlsx");

    return a.exec();
}
```
