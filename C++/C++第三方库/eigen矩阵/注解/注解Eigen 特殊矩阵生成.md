# 注解Eigen 特殊矩阵生成

### 特殊矩阵生成

```cpp
MatrixXd::Identity(rows, cols)       // eye(rows, cols)
```

**作用**：生成一个 `rows x cols` 的单位矩阵，对角线元素为 1，其余元素为 0。

```cpp
C.setIdentity(rows, cols)            // C = eye(rows, cols)
```

**作用**：将矩阵 `C` 设置为 `rows x cols` 的单位矩阵，直接修改已有矩阵的内容。

```cpp
MatrixXd::Zero(rows, cols)           // zeros(rows, cols)
```

**作用**：生成一个 `rows x cols` 的零矩阵，所有元素初始化为 0。

```cpp
C.setZero(rows, cols)                // C = zeros(rows, cols)
```

**作用**：将矩阵 `C` 的所有元素设置为 0，便于快速初始化已有矩阵。

```cpp
MatrixXd::Ones(rows, cols)           // ones(rows, cols)
```

**作用**：生成一个 `rows x cols` 的全 1 矩阵，所有元素初始化为 1。

```cpp
C.setOnes(rows, cols)                // C = ones(rows, cols)
```

**作用**：将矩阵 `C` 的所有元素设置为 1，便于快速初始化已有矩阵。

```cpp
MatrixXd::Random(rows, cols)         // rand(rows, cols) * 2 - 1
```

**作用**：生成一个 `rows x cols` 的矩阵，元素为在 (-1, 1) 范围内的随机数，提供随机初始化的方式。

```cpp
C.setRandom(rows, cols)              // C = rand(rows, cols) * 2 - 1
```

**作用**：将矩阵 `C` 的元素设置为在 (-1, 1) 范围内的随机数，直接修改已有矩阵的内容。

```cpp
VectorXd::LinSpaced(size, low, high)  // linspace(low, high, size)'
```

**作用**：生成一个包含 `size` 个等间距点的向量，从 `low` 到 `high`，便于创建线性空间。

```cpp
v.setLinSpaced(size, low, high)       // v = linspace(low, high, size)'
```

**作用**：将向量 `v` 设置为从 `low` 到 `high` 的 `size` 个等间距点，直接修改已有向量的内容。

这些特殊矩阵生成的函数对于快速初始化矩阵和向量非常有用，尤其是在算法开发和数值计算中。如果你还有其他问题，随时告诉我！
