`QAxWidget` 是 Qt 中用于嵌入和与 ActiveX 控件进行交互的控件。ActiveX 控件是由 Microsoft Windows 提供的一种软件组件，可以在 Windows 平台上用于实现各种功能。`QAxWidget` 允许 Qt 应用程序嵌入和操作这些控件。

以下是 `QAxWidget` 的详细函数方法及其作用：

### 基本构造与销毁

#### `QAxWidget(const QString &clsid, QWidget *parent = nullptr)`

- **作用**：构造一个 `QAxWidget` 对象。
- **参数**：
  - `clsid`：ActiveX 控件的 CLSID（类标识符），类型为 `QString`。
  - `parent`：父控件，类型为 `QWidget*`。默认为 `nullptr`。
- **返回值**：`QAxWidget` 对象。

```cpp
QAxWidget *axWidget = new QAxWidget("CLSID_of_ActiveX_Control", parentWidget);
```

### 属性、方法和事件

#### `void setControl(const QString &clsid)`

- **作用**：设置 ActiveX 控件的 CLSID。
- **参数**：
  - `clsid`：ActiveX 控件的 CLSID，类型为 `QString`。
- **返回值**：`void`，无返回值。

```cpp
axWidget->setControl("CLSID_of_ActiveX_Control");
```

#### `QString control() const`

- **作用**：获取当前设置的 ActiveX 控件的 CLSID。
- **返回值**：`QString`，ActiveX 控件的 CLSID。

```cpp
QString clsid = axWidget->control();
```

### COM 对象操作

#### `QAxObject *querySubObject(const QString &name, const QVariant &value = QVariant())`

- **作用**：查询 ActiveX 控件的子对象。
- **参数**：
  - `name`：子对象的名称，类型为 `QString`。
  - `value`：查询时传递的值，类型为 `QVariant`，默认为 `QVariant()`。
- **返回值**：`QAxObject*`，查询到的子对象。

```cpp
QAxObject *subObject = axWidget->querySubObject("SubObjectName");
```

#### `QAxObject *dynamicCall(const QString &method, const QVariant &arg1 = QVariant(), const QVariant &arg2 = QVariant(), const QVariant &arg3 = QVariant(), const QVariant &arg4 = QVariant())`

- **作用**：调用 ActiveX 控件的方法。
- **参数**：
  - `method`：方法名称，类型为 `QString`。
  - `arg1`, `arg2`, `arg3`, `arg4`：方法参数，类型为 `QVariant`，最多支持四个参数。
- **返回值**：`QAxObject*`，调用结果。

```cpp
QAxObject *result = axWidget->dynamicCall("MethodName", arg1, arg2);
```

#### `QVariant property(const QString &name) const`

- **作用**：获取 ActiveX 控件的属性值。
- **参数**：
  - `name`：属性名称，类型为 `QString`。
- **返回值**：`QVariant`，属性值。

```cpp
QVariant value = axWidget->property("PropertyName");
```

#### `void setProperty(const QString &name, const QVariant &value)`

- **作用**：设置 ActiveX 控件的属性值。
- **参数**：
  - `name`：属性名称，类型为 `QString`。
  - `value`：属性值，类型为 `QVariant`。
- **返回值**：`void`，无返回值。

```cpp
axWidget->setProperty("PropertyName", newValue);
```

### 事件处理

#### `void setProperty(const QString &name, const QVariant &value)`

- **作用**：设置 ActiveX 控件的属性值。
- **参数**：
  - `name`：属性名称，类型为 `QString`。
  - `value`：属性值，类型为 `QVariant`。
- **返回值**：`void`，无返回值。

```cpp
axWidget->setProperty("PropertyName", newValue);
```

### 调试和错误处理

#### `QString errorString() const`

- **作用**：获取最后一次发生的错误信息。
- **返回值**：`QString`，错误信息。

```cpp
QString error = axWidget->errorString();
```

#### `bool isNull() const`

- **作用**：检查 `QAxWidget` 是否为空或无效。
- **返回值**：`bool`，如果无效则返回 `true`，否则返回 `false`。

```cpp
bool isNull = axWidget->isNull();
```

### 控件状态与功能

#### `void setControl(const QString &clsid)`

- **作用**：设置 ActiveX 控件的 CLSID。
- **参数**：
  - `clsid`：ActiveX 控件的 CLSID，类型为 `QString`。
- **返回值**：`void`，无返回值。

```cpp
axWidget->setControl("CLSID_of_ActiveX_Control");
```

#### `QString control() const`

- **作用**：获取当前设置的 ActiveX 控件的 CLSID。
- **返回值**：`QString`，ActiveX 控件的 CLSID。

```cpp
QString clsid = axWidget->control();
```

### COM 对象的事件处理

#### `void setEventFilter(QObject *filter)`

- **作用**：设置事件过滤器，以处理 ActiveX 控件的事件。
- **参数**：
  - `filter`：事件过滤器，类型为 `QObject*`。
- **返回值**：`void`，无返回值。

```cpp
axWidget->setEventFilter(myEventFilter);
```

#### `QObject *eventFilter(QObject *obj, QEvent *event)`

- **作用**：处理 ActiveX 控件的事件。
- **参数**：
  - `obj`：事件源对象，类型为 `QObject*`。
  - `event`：事件对象，类型为 `QEvent*`。
- **返回值**：`QObject*`，返回处理后的结果。

```cpp
QObject *result = axWidget->eventFilter(obj, event);
```

### 控件的样式与外观

#### `void setStyleSheet(const QString &styleSheet)`

- **作用**：设置控件的样式表。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。
- **返回值**：`void`，无返回值。

```cpp
axWidget->setStyleSheet("QAxWidget { background: lightblue; }");
```

#### `QString styleSheet() const`

- **作用**：获取控件的样式表。
- **返回值**：`QString`，样式表字符串。

```cpp
QString styleSheet = axWidget->styleSheet();
```