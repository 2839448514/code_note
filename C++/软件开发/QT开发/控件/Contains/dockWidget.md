`QDockWidget` 是 Qt 中用于实现可停靠窗口的控件，通常用于创建可移动、可停靠的面板或工具栏。它可以被停靠在主窗口的边缘，或在主窗口内部作为浮动窗口存在。以下是 `QDockWidget` 的详细函数方法及其作用：

### 基本构造与销毁

#### `QDockWidget(const QString &title, QWidget *parent = nullptr, Qt::WindowFlags flags = Qt::WindowFlags())`
- **作用**：构造一个 `QDockWidget` 对象。
- **参数**：
  - `title`：停靠窗口的标题，类型为 `QString`。
  - `parent`：父控件，类型为 `QWidget*`。默认为 `nullptr`。
  - `flags`：窗口标志，类型为 `Qt::WindowFlags`，默认为 `Qt::WindowFlags()`。
- **返回值**：`QDockWidget` 对象。

```cpp
QDockWidget *dockWidget = new QDockWidget("Dock Widget", parentWidget);
```

### 停靠窗口内容

#### `void setWidget(QWidget *widget)`
- **作用**：设置停靠窗口的内容。
- **参数**：
  - `widget`：要设置的内容控件，类型为 `QWidget*`。
- **返回值**：`void`，无返回值。

```cpp
dockWidget->setWidget(myWidget);
```

#### `QWidget *widget() const`
- **作用**：获取停靠窗口的内容控件。
- **返回值**：`QWidget*`，当前内容控件。

```cpp
QWidget *contentWidget = dockWidget->widget();
```

### 标题与图标

#### `void setWindowTitle(const QString &title)`
- **作用**：设置停靠窗口的标题。
- **参数**：
  - `title`：窗口标题，类型为 `QString`。
- **返回值**：`void`，无返回值。

```cpp
dockWidget->setWindowTitle("New Title");
```

#### `QString windowTitle() const`
- **作用**：获取停靠窗口的标题。
- **返回值**：`QString`，窗口标题。

```cpp
QString title = dockWidget->windowTitle();
```

#### `void setWindowIcon(const QIcon &icon)`
- **作用**：设置停靠窗口的图标。
- **参数**：
  - `icon`：窗口图标，类型为 `QIcon`。
- **返回值**：`void`，无返回值。

```cpp
dockWidget->setWindowIcon(QIcon("icon.png"));
```

#### `QIcon windowIcon() const`
- **作用**：获取停靠窗口的图标。
- **返回值**：`QIcon`，窗口图标。

```cpp
QIcon icon = dockWidget->windowIcon();
```

### 停靠窗口的显示与隐藏

#### `void setVisible(bool visible)`
- **作用**：设置停靠窗口的可见性。
- **参数**：
  - `visible`：布尔值，`true` 表示可见，`false` 表示隐藏。
- **返回值**：`void`，无返回值。

```cpp
dockWidget->setVisible(true);
```

#### `bool isVisible() const`
- **作用**：检查停靠窗口是否可见。
- **返回值**：`bool`，如果可见则返回 `true`，否则返回 `false`。

```cpp
bool visible = dockWidget->isVisible();
```

### 停靠窗口的停靠与浮动

#### `void setAllowedAreas(Qt::DockWidgetAreas areas)`
- **作用**：设置停靠窗口允许停靠的区域。
- **参数**：
  - `areas`：允许停靠的区域，类型为 `Qt::DockWidgetAreas`。
- **返回值**：`void`，无返回值。

```cpp
dockWidget->setAllowedAreas(Qt::LeftDockWidgetArea | Qt::RightDockWidgetArea);
```

#### `Qt::DockWidgetAreas allowedAreas() const`
- **作用**：获取停靠窗口允许停靠的区域。
- **返回值**：`Qt::DockWidgetAreas`，允许停靠的区域。

```cpp
Qt::DockWidgetAreas areas = dockWidget->allowedAreas();
```

#### `void setFeatures(QDockWidget::DockWidgetFeatures features)`
- **作用**：设置停靠窗口的功能特性，例如是否可以浮动、是否可固定等。
- **参数**：
  - `features`：功能特性，类型为 `QDockWidget::DockWidgetFeatures`。
- **返回值**：`void`，无返回值。

```cpp
dockWidget->setFeatures(QDockWidget::DockWidgetMovable | QDockWidget::DockWidgetFloatable);
```

#### `QDockWidget::DockWidgetFeatures features() const`
- **作用**：获取停靠窗口的功能特性。
- **返回值**：`QDockWidget::DockWidgetFeatures`，当前功能特性。

```cpp
QDockWidget::DockWidgetFeatures features = dockWidget->features();
```

### 停靠窗口的浮动与停靠状态

#### `void setFloating(bool floating)`
- **作用**：设置停靠窗口是否浮动。
- **参数**：
  - `floating`：布尔值，`true` 表示浮动，`false` 表示停靠。
- **返回值**：`void`，无返回值。

```cpp
dockWidget->setFloating(true);
```

#### `bool isFloating() const`
- **作用**：检查停靠窗口是否为浮动状态。
- **返回值**：`bool`，如果为浮动状态则返回 `true`，否则返回 `false`。

```cpp
bool floating = dockWidget->isFloating();
```

### 停靠窗口的控制

#### `void setFeatures(QDockWidget::DockWidgetFeatures features)`
- **作用**：设置停靠窗口的功能特性，例如是否可以浮动、是否可以关闭等。
- **参数**：
  - `features`：功能特性，类型为 `QDockWidget::DockWidgetFeatures`。
- **返回值**：`void`，无返回值。

```cpp
dockWidget->setFeatures(QDockWidget::DockWidgetClosable | QDockWidget::DockWidgetMovable);
```

#### `void toggleViewAction()`
- **作用**：切换视图的显示或隐藏。通常用在菜单中，用来控制停靠窗口的可见性。
- **参数**：无。
- **返回值**：`void`，无返回值。

```cpp
dockWidget->toggleViewAction()->trigger();
```

#### `QAction *toggleViewAction() const`
- **作用**：获取用于切换视图的动作。
- **返回值**：`QAction*`，切换视图的动作。

```cpp
QAction *action = dockWidget->toggleViewAction();
```

### 事件处理

#### `void closeEvent(QCloseEvent *event)`
- **作用**：处理窗口关闭事件。
- **参数**：
  - `event`：关闭事件，类型为 `QCloseEvent*`。
- **返回值**：`void`，无返回值。

```cpp
void MyDockWidget::closeEvent(QCloseEvent *event) {
    // 自定义处理代码
    event->accept();
}
```

#### `void resizeEvent(QResizeEvent *event)`
- **作用**：处理窗口调整大小事件。
- **参数**：
  - `event`：调整大小事件，类型为 `QResizeEvent*`。
- **返回值**：`void`，无返回值。

```cpp
void MyDockWidget::resizeEvent(QResizeEvent *event) {
    // 自定义处理代码
    event->accept();
}
```

### 停靠窗口的样式和特性

#### `void setStyleSheet(const QString &styleSheet)`
- **作用**：设置停靠窗口的样式表。
- **参数**：
  - `styleSheet`：样式表字符串，类型为 `QString`。
- **返回值**：`void`，无返回值。

```cpp
dockWidget->setStyleSheet("QDockWidget { background: lightgray; }");
```

#### `QString styleSheet() const`
- **作用**：获取停靠窗口的样式表。
- **返回值**：`QString`，样式表字符串。

```cpp
QString styleSheet = dockWidget->styleSheet();
```

这些方法涵盖了 `QDockWidget` 的基本功能，包括内容设置、标题和图标管理、显示与隐藏、停靠状态、功能特性、事件处理等。如果你有其他问题或需要更多详细信息，请随时告知！