`QSlider` 控件的水平版本 (`horizontalSlider`) 和垂直版本 (`verticalSlider`) 在功能上是类似的，只是方向不同。下面是 `QSlider` 的垂直版本（`verticalSlider`）的详细方法和函数，以及它们的作用：

### 1. **基本设置**

#### `setValue(int value)`

- **作用**：设置滑块的当前值。
- **参数**：
  - `value`：滑块的新值，类型为 `int`。

```cpp
verticalSlider->setValue(50);
```

#### `value()`

- **作用**：获取滑块的当前值。
- **返回值**：`int`，当前值。

```cpp
int currentValue = verticalSlider->value();
```

### 2. **范围设置**

#### `setRange(int minValue, int maxValue)`

- **作用**：设置滑块的最小值和最大值。
- **参数**：
  - `minValue`：最小值，类型为 `int`。
  - `maxValue`：最大值，类型为 `int`。

```cpp
verticalSlider->setRange(0, 100);
```

#### `minimum()`

- **作用**：获取滑块的最小值。
- **返回值**：`int`，最小值。

```cpp
int minValue = verticalSlider->minimum();
```

#### `maximum()`

- **作用**：获取滑块的最大值。
- **返回值**：`int`，最大值。

```cpp
int maxValue = verticalSlider->maximum();
```

### 3. **步进设置**

#### `setSingleStep(int step)`

- **作用**：设置每次步进的数值步长。
- **参数**：
  - `step`：步长值，类型为 `int`。

```cpp
verticalSlider->setSingleStep(1);
```

#### `singleStep()`

- **作用**：获取每次步进的数值步长。
- **返回值**：`int`，步长值。

```cpp
int step = verticalSlider->singleStep();
```

#### `setPageStep(int step)`

- **作用**：设置页面步长，通常用于翻页的步长。
- **参数**：
  - `step`：页面步长值，类型为 `int`。

```cpp
verticalSlider->setPageStep(10);
```

#### `pageStep()`

- **作用**：获取页面步长。
- **返回值**：`int`，页面步长值。

```cpp
int pageStep = verticalSlider->pageStep();
```

### 4. **显示和隐藏**

#### `setVisible(bool visible)`

- **作用**：设置滑块是否可见。
- **参数**：
  - `visible`：是否可见，类型为 `bool`（`true` 表示可见，`false` 表示不可见）。

```cpp
verticalSlider->setVisible(true);
```

#### `isVisible()`

- **作用**：检查滑块的可见性。
- **返回值**：`bool`，如果可见返回 `true`，否则返回 `false`。

```cpp
bool visible = verticalSlider->isVisible();
```

### 5. **样式和外观**

#### `setStyleSheet(const QString &styleSheet)`

- **作用**：设置滑块的样式表，用于定制外观。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。

```cpp
verticalSlider->setStyleSheet("QSlider::handle:vertical { background: lightgrey; }");
```

#### `setAutoFillBackground(bool autoFill)`

- **作用**：设置控件是否自动填充背景。
- **参数**：
  - `autoFill`：是否自动填充，类型为 `bool`（`true` 表示自动填充，`false` 表示不填充）。

```cpp
verticalSlider->setAutoFillBackground(true);
```

### 6. **信号和槽**

#### `valueChanged(int value)`

- **作用**：当滑块的值发生变化时发射的信号。
- **参数**：
  - `value`：新值，类型为 `int`。

```cpp
connect(verticalSlider, &QSlider::valueChanged, [](int value) {
    qDebug() << "Slider value changed to" << value;
});
```

#### `sliderMoved(int position)`

- **作用**：当滑块被移动时发射的信号。
- **参数**：
  - `position`：滑块的新位置，类型为 `int`。

```cpp
connect(verticalSlider, &QSlider::sliderMoved, [](int position) {
    qDebug() << "Slider moved to position" << position;
});
```

### 7. **滑块位置**

#### `setSliderPosition(int position)`

- **作用**：设置滑块的位置。
- **参数**：
  - `position`：滑块位置，类型为 `int`。

```cpp
verticalSlider->setSliderPosition(30);
```

#### `sliderPosition()`

- **作用**：获取滑块的位置。
- **返回值**：`int`，滑块位置。

```cpp
int sliderPos = verticalSlider->sliderPosition();
```

### 8. **步长和刻度**

#### `setTickInterval(int interval)`

- **作用**：设置刻度线之间的间隔。
- **参数**：
  - `interval`：刻度线间隔，类型为 `int`。

```cpp
verticalSlider->setTickInterval(10);
```

#### `tickInterval()`

- **作用**：获取刻度线之间的间隔。
- **返回值**：`int`，刻度线间隔。

```cpp
int tickInterval = verticalSlider->tickInterval();
```

#### `setTickPosition(QSlider::TickPosition position)`

- **作用**：设置刻度线的位置。
- **参数**：
  - `position`：刻度线位置，类型为 `QSlider::TickPosition`（`QSlider::NoTicks`, `QSlider::Below`, `QSlider::Above`, `QSlider::BothSides`）。

```cpp
verticalSlider->setTickPosition(QSlider::BothSides);
```

### 9. **设置方向**

#### `setOrientation(Qt::Orientation orientation)`

- **作用**：设置滑块的方向（水平或垂直）。
- **参数**：
  - `orientation`：滑块的方向，类型为 `Qt::Orientation`（`Qt::Horizontal` 或 `Qt::Vertical`）。

```cpp
verticalSlider->setOrientation(Qt::Vertical);
```

#### `orientation()`

- **作用**：获取滑块的方向。
- **返回值**：`Qt::Orientation`，滑块的方向（`Qt::Horizontal` 或 `Qt::Vertical`）。

```cpp
Qt::Orientation orientation = verticalSlider->orientation();
```

### 10. **滑块的几何设置**

#### `setGeometry(const QRect &rect)`

- **作用**：设置滑块控件的几何位置和大小。
- **参数**：
  - `rect`：几何位置，类型为 `QRect`。

```cpp
verticalSlider->setGeometry(QRect(10, 10, 30, 200));
```

### 11. **焦点和输入**

#### `setFocus()`

- **作用**：将焦点设置到滑块控件上。
- **无参数**。

```cpp
verticalSlider->setFocus();
```

#### `focusPolicy()`

- **作用**：获取滑块的焦点策略。
- **返回值**：`Qt::FocusPolicy`，当前的焦点策略。

```cpp
Qt::FocusPolicy policy = verticalSlider->focusPolicy();
```

### 12. **事件过滤器**

#### `installEventFilter(QObject *filterObj)`

- **作用**：安装事件过滤器，用于拦截和处理事件。
- **参数**：
  - `filterObj`：事件过滤器对象，类型为 `QObject` 指针。

```cpp
verticalSlider->installEventFilter(myEventFilter);
```

#### `removeEventFilter(QObject *filterObj)`

- **作用**：移除事件过滤器。
- **参数**：
  - `filterObj`：事件过滤器对象，类型为 `QObject` 指针。

```cpp
verticalSlider->removeEventFilter(myEventFilter);
```

### 13. **设置用户界面**

#### `setEnabled(bool enable)`

- **作用**：设置滑块是否启用。
- **参数**：
  - `enable`：是否启用，类型为 `bool`（`true` 表示启用，`false` 表示禁用）。

```cpp
verticalSlider->setEnabled(true);
```

#### `setFocusProxy(QWidget *proxy)`

- **作用**：设置滑块的焦点代理。
- **参数**：
  - `proxy`：焦点代理控件，类型为 `QWidget` 指针。

```cpp
verticalSlider->setFocusProxy(otherWidget);
```

### 14. **时间设置**

#### `setTracking(bool enable)`

- **作用**：设置是否启用跟踪。启用跟踪时，滑块值变化时会发射 `valueChanged` 信号。
- **参数**：
  - `enable`：是否启用跟踪，类型

为 `bool`（`true` 表示启用，`false` 表示禁用）。

```cpp
verticalSlider->setTracking(true);
```

#### `tracking()`

- **作用**：检查是否启用了跟踪。
- **返回值**：`bool`，如果启用了跟踪返回 `true`，否则返回 `false`。

```cpp
bool isTracking = verticalSlider->tracking();
```

### 15. **尺寸设置**

#### `setMinimumSize(int minWidth, int minHeight)`

- **作用**：设置滑块的最小尺寸。
- **参数**：
  - `minWidth`：最小宽度，类型为 `int`。
  - `minHeight`：最小高度，类型为 `int`。

```cpp
verticalSlider->setMinimumSize(30, 100);
```

#### `setMaximumSize(int maxWidth, int maxHeight)`

- **作用**：设置滑块的最大尺寸。
- **参数**：
  - `maxWidth`：最大宽度，类型为 `int`。
  - `maxHeight`：最大高度，类型为 `int`。

```cpp
verticalSlider->setMaximumSize(30, 300);
```