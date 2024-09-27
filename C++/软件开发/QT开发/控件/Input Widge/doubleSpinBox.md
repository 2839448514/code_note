`QDoubleSpinBox` 是 Qt 中一个用于输入浮点数的控件，支持设置范围、步长、精度等。以下是 `QDoubleSpinBox` 的详细函数方法及其作用：

### 1. **基本设置**

#### `setValue(double value)`

- **作用**：设置当前的浮点数值。
- **参数**：
  - `value`：要设置的浮点数值，类型为 `double`。

```cpp
doubleSpinBox->setValue(3.14);
```

#### `value()`

- **作用**：获取当前的浮点数值。
- **返回值**：`double`，当前的浮点数值。

```cpp
double currentValue = doubleSpinBox->value();
```

### 2. **范围设置**

#### `setRange(double min, double max)`

- **作用**：设置允许的最小和最大浮点数值范围。
- **参数**：
  - `min`：最小值，类型为 `double`。
  - `max`：最大值，类型为 `double`。

```cpp
doubleSpinBox->setRange(0.0, 100.0);
```

#### `minimum()`

- **作用**：获取允许的最小浮点数值。
- **返回值**：`double`，最小值。

```cpp
double minValue = doubleSpinBox->minimum();
```

#### `maximum()`

- **作用**：获取允许的最大浮点数值。
- **返回值**：`double`，最大值。

```cpp
double maxValue = doubleSpinBox->maximum();
```

### 3. **步长设置**

#### `setSingleStep(double step)`

- **作用**：设置单次增减操作的步长。
- **参数**：
  - `step`：步长值，类型为 `double`。

```cpp
doubleSpinBox->setSingleStep(0.1);
```

#### `singleStep()`

- **作用**：获取当前的步长值。
- **返回值**：`double`，当前的步长值。

```cpp
double step = doubleSpinBox->singleStep();
```

### 4. **精度设置**

#### `setDecimals(int decimals)`

- **作用**：设置浮点数的精度，即小数点后的位数。
- **参数**：
  - `decimals`：精度位数，类型为 `int`。

```cpp
doubleSpinBox->setDecimals(2);
```

#### `decimals()`

- **作用**：获取当前的精度位数。
- **返回值**：`int`，当前的精度位数。

```cpp
int precision = doubleSpinBox->decimals();
```

### 5. **显示格式**

#### `setPrefix(const QString &prefix)`

- **作用**：设置数值前的前缀。
- **参数**：
  - `prefix`：前缀字符串，类型为 `QString`。

```cpp
doubleSpinBox->setPrefix("$");
```

#### `prefix()`

- **作用**：获取当前的前缀。
- **返回值**：`QString`，当前的前缀。

```cpp
QString prefix = doubleSpinBox->prefix();
```

#### `setSuffix(const QString &suffix)`

- **作用**：设置数值后的后缀。
- **参数**：
  - `suffix`：后缀字符串，类型为 `QString`。

```cpp
doubleSpinBox->setSuffix(" units");
```

#### `suffix()`

- **作用**：获取当前的后缀。
- **返回值**：`QString`，当前的后缀。

```cpp
QString suffix = doubleSpinBox->suffix();
```

### 6. **显示模式**

#### `setDisplayIntegerBase(int base)`

- **作用**：设置数值的显示进制（通常用于 `QSpinBox`，`QDoubleSpinBox` 通常用于十进制显示）。
- **参数**：
  - `base`：显示进制，类型为 `int`（例如 `10` 表示十进制）。

```cpp
// 通常 `QDoubleSpinBox` 使用十进制显示，因此此方法较少用于 `QDoubleSpinBox`。
```

### 7. **特殊值**

#### `setSpecialValueText(const QString &text)`

- **作用**：设置特殊值的显示文本（用于表示无效或特殊状态）。
- **参数**：
  - `text`：特殊值文本，类型为 `QString`。

```cpp
doubleSpinBox->setSpecialValueText("N/A");
```

#### `specialValueText()`

- **作用**：获取特殊值的显示文本。
- **返回值**：`QString`，特殊值文本。

```cpp
QString specialValue = doubleSpinBox->specialValueText();
```

### 8. **自定义格式**

#### `setValueFromText(const QString &text)`

- **作用**：从文本中设置浮点数值（通常用于自定义的文本输入验证）。
- **参数**：
  - `text`：文本内容，类型为 `QString`。

```cpp
doubleSpinBox->setValueFromText("12.34");
```

#### `textFromValue(double value)`

- **作用**：将浮点数值转换为文本（用于自定义显示格式）。
- **参数**：
  - `value`：浮点数值，类型为 `double`。
- **返回值**：`QString`，转换后的文本。

```cpp
QString text = doubleSpinBox->textFromValue(12.34);
```

### 9. **信号和槽**

#### `valueChanged(double value)`

- **作用**：当浮点数值发生变化时发射的信号。
- **返回值**：`double`，新数值。

```cpp
connect(doubleSpinBox, QOverload<double>::of(&QDoubleSpinBox::valueChanged), [](double value){
    qDebug() << "Value changed to" << value;
});
```

### 10. **焦点和光标**

#### `setFocusPolicy(Qt::FocusPolicy policy)`

- **作用**：设置控件的焦点策略。
- **参数**：
  - `policy`：焦点策略，类型为 `Qt::FocusPolicy`（例如 `Qt::StrongFocus`）。

```cpp
doubleSpinBox->setFocusPolicy(Qt::StrongFocus);
```

#### `focusPolicy()`

- **作用**：获取控件的焦点策略。
- **返回值**：`Qt::FocusPolicy`，当前的焦点策略。

```cpp
Qt::FocusPolicy policy = doubleSpinBox->focusPolicy();
```

### 11. **布局与样式**

#### `setStyleSheet(const QString &styleSheet)`

- **作用**：设置控件的样式表，允许自定义控件的外观。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。

```cpp
doubleSpinBox->setStyleSheet("QDoubleSpinBox { color: blue; }");
```

#### `setGeometry(const QRect &rect)`

- **作用**：设置控件的位置和大小。
- **参数**：
  - `rect`：位置和大小的矩形，类型为 `QRect`。

```cpp
doubleSpinBox->setGeometry(QRect(10, 10, 120, 30));
```

### 12. **额外功能**

#### `setAccelerated(bool accelerated)`

- **作用**：设置控件的加速模式（对步进操作的加速）。
- **参数**：
  - `accelerated`：是否加速，类型为 `bool`（`true` 表示加速，`false` 表示不加速）。

```cpp
doubleSpinBox->setAccelerated(true);
```

#### `isAccelerated()`

- **作用**：检查控件是否加速。
- **返回值**：`bool`，如果加速返回 `true`，否则返回 `false`。

```cpp
bool accelerated = doubleSpinBox->isAccelerated();
```