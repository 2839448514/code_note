## 基础案例

```C++
#include "OpenXLSX.hpp"
 
int main() {
    // 创建一个新的Excel文件
    OpenXLSX::XLDocument doc;
    doc.create("example.xlsx");
 
    // 获取工作表
    auto wks = doc.workbook().worksheet("Sheet1");
 
    // 写入数据
    wks.cell("A1").value() = "Hello, OpenXLSX!";
    wks.cell("B1").value() = 42;
 
    // 保存文件
    doc.save();
 
    return 0;
}
```

## 操作

1. **添加多个工作表**:
    
    ```cpp
    OpenXLSX::Workbook wb;
    wb.create("test.xlsx");
    
    auto ws1 = wb.addWorksheet("Sheet1");
    auto ws2 = wb.addWorksheet("Sheet2");
    ```
    
2. **写入不同类型的数据**:
    
    - 写入数字:
        
        ```cpp
        ws.cell("B2").value(123);
        ```
        
    - 写入字符串:
        
        ```cpp
        ws.cell("C3").value("Hello, World!");
        ```
        
    - 写入公式:
        
        ```cpp
        ws.cell("D4").formula("=SUM(1, 1, 1, 10)");
        ```
        
    - 写入布尔值:
        
        ```cpp
        ws.cell("E5").value(true);  // 或 false
        ```
        
    - 写入错误值（如果需要手动设置）:
        
        ```cpp
        ws.cell("F6").value("ERROR");  // 例如可以标记为错误
        ```
        
3. **设置单元格格式**:
    
    ```cpp
    ws.cell("A1").style().setFontBold(true).setFontColor(OpenXLSX::Color(255, 0, 0)); // 红色
    ```
    
4. **合并单元格**:
    
    ```cpp
    ws.mergeCells("A1:B2");
    ws.cell("A1").value("Merged Cells");
    ```
    
5. **设置列宽**:
    
    ```cpp
    ws.column("A").width(20);
    ```
    
6. **设置行高**:
    
    ```cpp
    ws.row(1).height(25);
    ```
    
7. **添加图表**:
    
    `OpenXLSX` 本身不支持图表操作，但你可以使用其他 C++ 库或通过 Excel 的 COM API来添加图表。
    
8. **设置单元格边框**:
    
    ```cpp
    ws.cell("A1").style().setBorder(OpenXLSX::Style::Border::Thin, OpenXLSX::Style::BorderSide::All);
    ```
    
9. **设置单元格背景色**:
    
    ```cpp
    ws.cell("A1").style().setFill(OpenXLSX::Style::Fill::Solid, OpenXLSX::Color(255, 199, 206)); // 红色背景
    ```
    
10. **保存并关闭工作簿**:
    
    ```cpp
    wb.save();
    ```
    

