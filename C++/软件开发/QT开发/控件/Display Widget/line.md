`QLine` 是 Qt 中用于表示二维空间中一条直线的类，通常用于绘制和处理直线。它提供了多种方法用于设置、操作和查询线段的属性。以下是 `QLine` 类的详细函数方法及其作用：

### 1. **构造函数**

#### `QLine()`

- **作用**：默认构造函数，创建一个无效的 `QLine` 对象（坐标点默认为 (0,0)）。
- **返回值**：`QLine` 对象。

```cpp
QLine line;
```

#### `QLine(int x1, int y1, int x2, int y2)`

- **作用**：使用两个点的坐标构造一个 `QLine` 对象。
- **参数**：
  - `x1`, `y1`：起点坐标。
  - `x2`, `y2`：终点坐标。
- **返回值**：`QLine` 对象。

```cpp
QLine line(10, 20, 30, 40);
```

#### `QLine(const QPoint &p1, const QPoint &p2)`

- **作用**：使用两个 `QPoint` 对象构造一个 `QLine` 对象。
- **参数**：
  - `p1`：起点。
  - `p2`：终点。
- **返回值**：`QLine` 对象。

```cpp
QPoint p1(10, 20);
QPoint p2(30, 40);
QLine line(p1, p2);
```

### 2. **获取和设置点**

#### `QPoint p1() const`

- **作用**：获取线段的起点。
- **返回值**：`QPoint`，起点坐标。

```cpp
QPoint startPoint = line.p1();
```

#### `QPoint p2() const`

- **作用**：获取线段的终点。
- **返回值**：`QPoint`，终点坐标。

```cpp
QPoint endPoint = line.p2();
```

#### `void setP1(const QPoint &point)`

- **作用**：设置线段的起点。
- **参数**：
  - `point`：起点坐标。

```cpp
line.setP1(QPoint(50, 60));
```

#### `void setP2(const QPoint &point)`

- **作用**：设置线段的终点。
- **参数**：
  - `point`：终点坐标。

```cpp
line.setP2(QPoint(70, 80));
```

### 3. **获取和设置坐标**

#### `int x1() const`

- **作用**：获取线段起点的 x 坐标。
- **返回值**：`int`，起点 x 坐标。

```cpp
int x1 = line.x1();
```

#### `int y1() const`

- **作用**：获取线段起点的 y 坐标。
- **返回值**：`int`，起点 y 坐标。

```cpp
int y1 = line.y1();
```

#### `int x2() const`

- **作用**：获取线段终点的 x 坐标。
- **返回值**：`int`，终点 x 坐标。

```cpp
int x2 = line.x2();
```

#### `int y2() const`

- **作用**：获取线段终点的 y 坐标。
- **返回值**：`int`，终点 y 坐标。

```cpp
int y2 = line.y2();
```

#### `void setPoints(int x1, int y1, int x2, int y2)`

- **作用**：设置线段的起点和终点坐标。
- **参数**：
  - `x1`, `y1`：起点坐标。
  - `x2`, `y2`：终点坐标。

```cpp
line.setPoints(10, 20, 30, 40);
```

### 4. **线段属性**

#### `int length() const`

- **作用**：计算线段的长度（不包括宽度）。
- **返回值**：`int`，线段长度。

```cpp
int len = line.length();
```

#### `int dx() const`

- **作用**：计算线段在 x 方向上的长度。
- **返回值**：`int`，x 方向长度。

```cpp
int deltaX = line.dx();
```

#### `int dy() const`

- **作用**：计算线段在 y 方向上的长度。
- **返回值**：`int`，y 方向长度。

```cpp
int deltaY = line.dy();
```

### 5. **计算和转换**

#### `QLine translated(int dx, int dy) const`

- **作用**：返回平移后的 `QLine` 对象。
- **参数**：
  - `dx`：x 方向的平移量。
  - `dy`：y 方向的平移量。
- **返回值**：`QLine`，平移后的线段。

```cpp
QLine translatedLine = line.translated(10, 20);
```

#### `QLine translated(const QPoint &offset) const`

- **作用**：返回平移后的 `QLine` 对象。
- **参数**：
  - `offset`：平移量，类型为 `QPoint`。
- **返回值**：`QLine`，平移后的线段。

```cpp
QPoint offset(10, 20);
QLine translatedLine = line.translated(offset);
```

#### `QLine normal() const`

- **作用**：返回线段的法线线段。
- **返回值**：`QLine`，法线线段。

```cpp
QLine normalLine = line.normal();
```

### 6. **线段比较**

#### `bool operator==(const QLine &other) const`

- **作用**：比较两个线段是否相等。
- **参数**：
  - `other`：另一个 `QLine` 对象。
- **返回值**：`bool`，如果两个线段相等则返回 `true`，否则返回 `false`。

```cpp
bool isEqual = (line == anotherLine);
```

#### `bool operator!=(const QLine &other) const`

- **作用**：比较两个线段是否不相等。
- **参数**：
  - `other`：另一个 `QLine` 对象。
- **返回值**：`bool`，如果两个线段不相等则返回 `true`，否则返回 `false`。

```cpp
bool isNotEqual = (line != anotherLine);
```

### 7. **绘制**

#### `void draw(QPainter *painter) const`

- **作用**：使用 `QPainter` 绘制线段。
- **参数**：
  - `painter`：`QPainter` 对象，用于绘制。

```cpp
QPainter painter(this);
painter.drawLine(line);
```

### 8. **获取线段角度**

#### `qreal angle() const`

- **作用**：获取线段与 x 轴的夹角（单位为度）。
- **返回值**：`qreal`，夹角。

```cpp
qreal angle = line.angle();
```
