`QScrollBar` 的 `verticalScrollBar` 类似于 `horizontalScrollBar`，但用于垂直方向上的滚动条。`QScrollBar` 控件在 Qt 中用于实现滚动功能，可以在 `QWidget` 的视图中添加水平或垂直的滚动条。以下是 `QScrollBar` 的详细方法和功能，主要涉及垂直滚动条的使用：

### 1. **基本设置**

#### `setValue(int value)`
- **作用**：设置垂直滚动条的当前值。
- **参数**：
  - `value`：要设置的当前值，类型为 `int`。

```cpp
verticalScrollBar->setValue(50);
```

#### `value()`
- **作用**：获取垂直滚动条的当前值。
- **返回值**：`int`，当前值。

```cpp
int currentValue = verticalScrollBar->value();
```

### 2. **范围设置**

#### `setRange(int minValue, int maxValue)`
- **作用**：设置垂直滚动条的最小值和最大值。
- **参数**：
  - `minValue`：最小值，类型为 `int`。
  - `maxValue`：最大值，类型为 `int`。

```cpp
verticalScrollBar->setRange(0, 100);
```

#### `minimum()`
- **作用**：获取垂直滚动条的最小值。
- **返回值**：`int`，最小值。

```cpp
int minValue = verticalScrollBar->minimum();
```

#### `maximum()`
- **作用**：获取垂直滚动条的最大值。
- **返回值**：`int`，最大值。

```cpp
int maxValue = verticalScrollBar->maximum();
```

### 3. **步进设置**

#### `setSingleStep(int step)`
- **作用**：设置每次步进的数值步长。
- **参数**：
  - `step`：步长值，类型为 `int`。

```cpp
verticalScrollBar->setSingleStep(1);
```

#### `singleStep()`
- **作用**：获取每次步进的数值步长。
- **返回值**：`int`，步长值。

```cpp
int step = verticalScrollBar->singleStep();
```

#### `setPageStep(int step)`
- **作用**：设置页面步长，通常用于翻页的步长。
- **参数**：
  - `step`：页面步长值，类型为 `int`。

```cpp
verticalScrollBar->setPageStep(10);
```

#### `pageStep()`
- **作用**：获取页面步长。
- **返回值**：`int`，页面步长值。

```cpp
int pageStep = verticalScrollBar->pageStep();
```

### 4. **显示和隐藏**

#### `setVisible(bool visible)`
- **作用**：设置垂直滚动条是否可见。
- **参数**：
  - `visible`：是否可见，类型为 `bool`（`true` 表示可见，`false` 表示不可见）。

```cpp
verticalScrollBar->setVisible(true);
```

#### `isVisible()`
- **作用**：检查垂直滚动条的可见性。
- **返回值**：`bool`，如果可见返回 `true`，否则返回 `false`。

```cpp
bool visible = verticalScrollBar->isVisible();
```

### 5. **样式和外观**

#### `setStyleSheet(const QString &styleSheet)`
- **作用**：设置垂直滚动条的样式表，用于定制外观。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。

```cpp
verticalScrollBar->setStyleSheet("QScrollBar:vertical { background: lightgrey; }");
```

#### `setAutoFillBackground(bool autoFill)`
- **作用**：设置控件是否自动填充背景。
- **参数**：
  - `autoFill`：是否自动填充，类型为 `bool`（`true` 表示自动填充，`false` 表示不填充）。

```cpp
verticalScrollBar->setAutoFillBackground(true);
```

### 6. **信号和槽**

#### `valueChanged(int value)`
- **作用**：当垂直滚动条的值发生变化时发射的信号。
- **参数**：
  - `value`：新值，类型为 `int`。

```cpp
connect(verticalScrollBar, &QScrollBar::valueChanged, [](int value) {
    qDebug() << "Vertical scroll bar value changed to" << value;
});
```

#### `rangeChanged(int minValue, int maxValue)`
- **作用**：当垂直滚动条的范围发生变化时发射的信号。
- **参数**：
  - `minValue`：新最小值，类型为 `int`。
  - `maxValue`：新最大值，类型为 `int`。

```cpp
connect(verticalScrollBar, &QScrollBar::rangeChanged, [](int minValue, int maxValue) {
    qDebug() << "Vertical scroll bar range changed to" << minValue << "to" << maxValue;
});
```

### 7. **滑块和刻度**

#### `setSliderPosition(int position)`
- **作用**：设置滑块的位置。
- **参数**：
  - `position`：滑块位置，类型为 `int`。

```cpp
verticalScrollBar->setSliderPosition(30);
```

#### `sliderPosition()`
- **作用**：获取滑块的位置。
- **返回值**：`int`，滑块位置。

```cpp
int sliderPos = verticalScrollBar->sliderPosition();
```

#### `setNotchesVisible(bool visible)`
- **作用**：设置是否显示刻度线。
- **参数**：
  - `visible`：是否显示刻度线，类型为 `bool`（`true` 表示显示，`false` 表示不显示）。

```cpp
verticalScrollBar->setNotchesVisible(true);
```

### 8. **滚动条的几何设置**

#### `setGeometry(const QRect &rect)`
- **作用**：设置垂直滚动条的几何形状。
- **参数**：
  - `rect`：几何形状，类型为 `QRect`。

```cpp
verticalScrollBar->setGeometry(QRect(0, 0, 20, 200));
```

### 9. **焦点和输入**

#### `setFocus()`
- **作用**：将焦点设置到垂直滚动条控件上。
- **无参数**。

```cpp
verticalScrollBar->setFocus();
```

#### `focusPolicy()`
- **作用**：获取垂直滚动条的焦点策略。
- **返回值**：`Qt::FocusPolicy`，当前的焦点策略。

```cpp
Qt::FocusPolicy policy = verticalScrollBar->focusPolicy();
```

### 10. **事件处理**

#### `event(QEvent *event)`
- **作用**：处理事件，重写此方法以自定义事件处理逻辑。
- **参数**：
  - `event`：事件对象，类型为 `QEvent`。

```cpp
bool QScrollBar::event(QEvent *event) override {
    if (event->type() == QEvent::Wheel) {
        // Handle wheel event
        return true;
    }
    return QScrollBar::event(event);
}
```

### 11. **滚动条的属性**

#### `setInvertedControls(bool inverted)`
- **作用**：设置是否反转滚动条的控件。
- **参数**：
  - `inverted`：是否反转，类型为 `bool`（`true` 表示反转，`false` 表示不反转）。

```cpp
verticalScrollBar->setInvertedControls(true);
```

#### `invertedControls()`
- **作用**：获取垂直滚动条是否反转。
- **返回值**：`bool`，如果反转返回 `true`，否则返回 `false`。

```cpp
bool isInverted = verticalScrollBar->invertedControls();
```

在 `QScrollBar` 控件的使用中，除了前面提到的方法，还有一些较少使用但依然重要的方法和功能。以下是一些附加的 `QScrollBar` 方法及其作用：

### 12. **信号的扩展**

#### `sliderMoved(int position)`
- **作用**：当滑块被移动时发射的信号。
- **参数**：
  - `position`：滑块的新位置，类型为 `int`。

```cpp
connect(verticalScrollBar, &QScrollBar::sliderMoved, [](int position) {
    qDebug() << "Slider moved to position" << position;
});
```

#### `rangeChanged(int minValue, int maxValue)`
- **作用**：当滚动条的范围发生变化时发射的信号。
- **参数**：
  - `minValue`：新最小值，类型为 `int`。
  - `maxValue`：新最大值，类型为 `int`。

```cpp
connect(verticalScrollBar, &QScrollBar::rangeChanged, [](int minValue, int maxValue) {
    qDebug() << "Scroll bar range changed to" << minValue << "to" << maxValue;
});
```

### 13. **处理用户输入**

#### `setTracking(bool enable)`
- **作用**：设置是否启用跟踪。启用跟踪时，每次滑块位置发生变化时都会发射信号。
- **参数**：
  - `enable`：是否启用跟踪，类型为 `bool`（`true` 表示启用，`false` 表示禁用）。

```cpp
verticalScrollBar->setTracking(true);
```

#### `tracking()`
- **作用**：获取是否启用了跟踪。
- **返回值**：`bool`，如果启用跟踪返回 `true`，否则返回 `false`。

```cpp
bool isTracking = verticalScrollBar->tracking();
```

### 14. **控制显示**

#### `setNotchesVisible(bool visible)`
- **作用**：设置是否显示刻度线。
- **参数**：
  - `visible`：是否显示刻度线，类型为 `bool`（`true` 表示显示，`false` 表示不显示）。

```cpp
verticalScrollBar->setNotchesVisible(true);
```

### 15. **调整显示区域**

#### `setPageStep(int step)`
- **作用**：设置每次翻页时的步长。
- **参数**：
  - `step`：翻页步长值，类型为 `int`。

```cpp
verticalScrollBar->setPageStep(10);
```

### 16. **滚动条属性**

#### `setMinimumWidth(int width)`
- **作用**：设置垂直滚动条的最小宽度。
- **参数**：
  - `width`：最小宽度，类型为 `int`。

```cpp
verticalScrollBar->setMinimumWidth(20);
```

#### `setMaximumWidth(int width)`
- **作用**：设置垂直滚动条的最大宽度。
- **参数**：
  - `width`：最大宽度，类型为 `int`。

```cpp
verticalScrollBar->setMaximumWidth(30);
```

### 17. **自定义样式**

#### `setStyle(const QStyle *style)`
- **作用**：设置滚动条的样式。
- **参数**：
  - `style`：样式对象，类型为 `QStyle` 指针。

```cpp
verticalScrollBar->setStyle(QStyleFactory::create("Fusion"));
```

### 18. **调整属性**

#### `adjustSize()`
- **作用**：调整滚动条控件的大小，以适应其内容。
- **无参数**。

```cpp
verticalScrollBar->adjustSize();
```

### 19. **获取滚动条位置**

#### `maximumSliderPosition()`
- **作用**：获取滚动条的最大滑块位置。
- **返回值**：`int`，最大滑块位置。

```cpp
int maxSliderPos = verticalScrollBar->maximumSliderPosition();
```

#### `minimumSliderPosition()`
- **作用**：获取滚动条的最小滑块位置。
- **返回值**：`int`，最小滑块位置。

```cpp
int minSliderPos = verticalScrollBar->minimumSliderPosition();
```

### 20. **滚动条的几何设置**

#### `sizeHint()`
- **作用**：提供控件的推荐大小。
- **返回值**：`QSize`，推荐大小。

```cpp
QSize size = verticalScrollBar->sizeHint();
```

#### `minimumSizeHint()`
- **作用**：提供控件的最小推荐大小。
- **返回值**：`QSize`，最小推荐大小。

```cpp
QSize minSize = verticalScrollBar->minimumSizeHint();
```

### 21. **滚动条的样式**

#### `setStyleSheet(const QString &styleSheet)`
- **作用**：设置滚动条的样式表，用于定制外观。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。

```cpp
verticalScrollBar->setStyleSheet("QScrollBar:vertical { border: 2px solid pink; }");
```

