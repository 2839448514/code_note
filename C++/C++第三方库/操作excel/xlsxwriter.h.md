---
tags:
  - 库文件
---
# xlsxwriter.h

## 基本操作

```C++
lxw_workbook* workbook = workbook_new("test.xlsx");
if (!workbook) {
	cerr << "无法创建Excel文件" << endl;
	return -1;
}
lxw_worksheet* worksheet = workbook_add_worksheet(workbook, "Frame Times");
worksheet_write_string(worksheet, 0, 0, "Frame Count", NULL);
worksheet_write_number(worksheet, frame_count + 1, 0, frame_count + 1, NULL);
workbook_close(workbook);
```

## 操作

1. **添加多个工作表**:

   ```cpp
   lxw_worksheet *worksheet1 = workbook_add_worksheet(workbook, "Sheet1");
   lxw_worksheet *worksheet2 = workbook_add_worksheet(workbook, "Sheet2");
   ```

2. **写入不同类型的数据**:
   - 写入数字:

     ```cpp
     worksheet_write_number(worksheet, row, col, number, NULL);
     ```

   - 写入字符串:

     ```cpp
     worksheet_write_string(worksheet, row, col, "Text", NULL);
     ```

   - 写入公式:

     ```cpp
     worksheet_write_formula(worksheet, row, col, "=SUM(1, 1, 1, 10)", NULL);
     ```

   - 写入布尔值:

     ```cpp
     worksheet_write_boolean(worksheet, row, col, 1, NULL); // 1 for TRUE, 0 for FALSE
     ```

   - 写入错误:

     ```cpp
     worksheet_write_error(worksheet, row, col, LXW_ERROR_VALUE, NULL);
     ```

3. **设置单元格格式**:

   ```cpp
   lxw_format *format = workbook_add_format(workbook);
   format_set_bold(format);
   format_set_font_color(format, 0xFF0000); // Red color
   worksheet_write_string(worksheet, row, col, "Bold Red Text", format);
   ```

4. **合并单元格**:

   ```cpp
   worksheet_merge_range(worksheet, start_row, start_col, end_row, end_col, "Merged Cell", NULL);
   ```

5. **设置列宽**:

   ```cpp
   worksheet_set_column(worksheet, col_start, col_end, width, NULL, NULL);
   ```

6. **设置行高**:

   ```cpp
   worksheet_set_row(worksheet, row, height, NULL, 0);
   ```

7. **添加图表**:

   ```cpp
   lxw_chart *chart = workbook_add_chart(workbook, LXW_CHART_LINE);
   chart_add_series(chart, worksheet, "=Sheet1!B2:B9");
   worksheet_insert_chart(worksheet, 4, 0, chart);
   ```

8. **设置单元格边框**:

   ```cpp
   lxw_format *border_format = workbook_add_format(workbook);
   format_set_border(border_format, LXW_BORDER_THIN, "#000000");
   worksheet_set_row_opt(worksheet, row, NULL, border_format);
   ```

9. **设置单元格背景 color**:

   ```cpp
   lxw_format *cell_format = workbook_add_format(workbook);
   format_set_bg_color(cell_format, 0xFFC7CE);
   worksheet_write_string(worksheet, row, col, "Cell with background", cell_format);
   ```

10. **保存并关闭工作簿**:

    ```cpp
    workbook_close(workbook);
    ```
