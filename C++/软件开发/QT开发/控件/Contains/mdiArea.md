`QMDIArea` 是 Qt 中用于管理多个子窗口的控件，通常用于实现 MDI（多文档界面）应用程序。它允许在一个主窗口中创建、排列和管理多个子窗口。以下是 `QMDIArea` 的详细函数方法及其作用：

### 基本构造与销毁

#### `QMDIArea(QWidget *parent = nullptr)`

- **作用**：构造一个 `QMDIArea` 对象。
- **参数**：
  - `parent`：父控件，类型为 `QWidget*`。默认为 `nullptr`。
- **返回值**：`QMDIArea` 对象。

```cpp
QMDIArea *mdiArea = new QMDIArea(parentWidget);
```

### 子窗口管理

#### `QMdiSubWindow *addSubWindow(QWidget *widget, Qt::WindowFlags windowFlags = Qt::WindowFlags())`

- **作用**：将一个子控件添加为子窗口。
- **参数**：
  - `widget`：要添加的子控件，类型为 `QWidget*`。
  - `windowFlags`：窗口标志，类型为 `Qt::WindowFlags`，默认为 `Qt::WindowFlags()`。
- **返回值**：`QMdiSubWindow*`，表示新添加的子窗口。

```cpp
QMdiSubWindow *subWindow = mdiArea->addSubWindow(myWidget);
```

#### `void removeSubWindow(QWidget *widget)`

- **作用**：从 MDI 区域中移除一个子窗口。
- **参数**：
  - `widget`：要移除的子控件，类型为 `QWidget*`。
- **返回值**：`void`，无返回值。

```cpp
mdiArea->removeSubWindow(myWidget);
```

#### `void setActiveSubWindow(QMdiSubWindow *window)`

- **作用**：设置当前活动的子窗口。
- **参数**：
  - `window`：要设置为活动窗口的子窗口，类型为 `QMdiSubWindow*`。
- **返回值**：`void`，无返回值。

```cpp
mdiArea->setActiveSubWindow(subWindow);
```

#### `QMdiSubWindow *activeSubWindow() const`

- **作用**：获取当前活动的子窗口。
- **返回值**：`QMdiSubWindow*`，当前活动的子窗口。

```cpp
QMdiSubWindow *activeWindow = mdiArea->activeSubWindow();
```

### 子窗口的排列与布局

#### `void tileSubWindows()`

- **作用**：将所有子窗口平铺显示。
- **参数**：无。
- **返回值**：`void`，无返回值。

```cpp
mdiArea->tileSubWindows();
```

#### `void cascadeSubWindows()`

- **作用**：将所有子窗口以层叠方式显示。
- **参数**：无。
- **返回值**：`void`，无返回值。

```cpp
mdiArea->cascadeSubWindows();
```

#### `void setLayoutMode(QMdiArea::LayoutMode mode)`

- **作用**：设置子窗口的布局模式。
- **参数**：
  - `mode`：布局模式，类型为 `QMdiArea::LayoutMode`。
- **返回值**：`void`，无返回值。

```cpp
mdiArea->setLayoutMode(QMdiArea::CascadeView);
```

#### `QMdiArea::LayoutMode layoutMode() const`

- **作用**：获取子窗口的布局模式。
- **返回值**：`QMdiArea::LayoutMode`，当前布局模式。

```cpp
QMdiArea::LayoutMode mode = mdiArea->layoutMode();
```

### 窗口的浮动与停靠

#### `void setSubWindowList(const QList<QMdiSubWindow*> &list)`

- **作用**：设置子窗口的列表。
- **参数**：
  - `list`：子窗口列表，类型为 `QList<QMdiSubWindow*>`。
- **返回值**：`void`，无返回值。

```cpp
mdiArea->setSubWindowList(subWindowList);
```

#### `QList<QMdiSubWindow*> subWindowList() const`

- **作用**：获取当前的子窗口列表。
- **返回值**：`QList<QMdiSubWindow*>`，子窗口列表。

```cpp
QList<QMdiSubWindow*> list = mdiArea->subWindowList();
```

### 控件的状态与属性

#### `void setViewMode(QMdiArea::ViewMode mode)`

- **作用**：设置视图模式，例如是否显示窗格。
- **参数**：
  - `mode`：视图模式，类型为 `QMdiArea::ViewMode`。
- **返回值**：`void`，无返回值。

```cpp
mdiArea->setViewMode(QMdiArea::TabbedView);
```

#### `QMdiArea::ViewMode viewMode() const`

- **作用**：获取视图模式。
- **返回值**：`QMdiArea::ViewMode`，当前视图模式。

```cpp
QMdiArea::ViewMode mode = mdiArea->viewMode();
```

#### `void setOption(QMdiArea::AreaOption option, bool on = true)`

- **作用**：设置 MDI 区域的选项。
- **参数**：
  - `option`：选项，类型为 `QMdiArea::AreaOption`。
  - `on`：布尔值，表示是否启用该选项，默认为 `true`。
- **返回值**：`void`，无返回值。

```cpp
mdiArea->setOption(QMdiArea::DontMaximizeSubWindowOnActivation, true);
```

#### `bool testOption(QMdiArea::AreaOption option) const`

- **作用**：测试 MDI 区域是否具有指定选项。
- **参数**：
  - `option`：选项，类型为 `QMdiArea::AreaOption`。
- **返回值**：`bool`，如果具有指定选项则返回 `true`，否则返回 `false`。

```cpp
bool hasOption = mdiArea->testOption(QMdiArea::DontMaximizeSubWindowOnActivation);
```

### 事件处理

#### `void closeEvent(QCloseEvent *event)`

- **作用**：处理窗口关闭事件。
- **参数**：
  - `event`：关闭事件，类型为 `QCloseEvent*`。
- **返回值**：`void`，无返回值。

```cpp
void MyMdiArea::closeEvent(QCloseEvent *event) {
    // 自定义处理代码
    event->accept();
}
```

#### `void resizeEvent(QResizeEvent *event)`

- **作用**：处理控件的调整大小事件。
- **参数**：
  - `event`：调整大小事件，类型为 `QResizeEvent*`。
- **返回值**：`void`，无返回值。

```cpp
void MyMdiArea::resizeEvent(QResizeEvent *event) {
    // 自定义处理代码
    event->accept();
}
```

### 子窗口的状态

#### `bool isMaximized() const`

- **作用**：检查 MDI 区域是否已最大化。
- **返回值**：`bool`，如果已最大化则返回 `true`，否则返回 `false`。

```cpp
bool maximized = mdiArea->isMaximized();
```

### 常用操作

#### `void activateNextSubWindow()`

- **作用**：激活下一个子窗口。
- **参数**：无。
- **返回值**：`void`，无返回值。

```cpp
mdiArea->activateNextSubWindow();
```

#### `void activatePreviousSubWindow()`

- **作用**：激活上一个子窗口。
- **参数**：无。
- **返回值**：`void`，无返回值。

```cpp
mdiArea->activatePreviousSubWindow();
```
