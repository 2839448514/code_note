| `包括`                         |                                                       |
| ---------------------------- | ----------------------------------------------------- |
| `<ios>(C++11)`               | std::ios_base 类、std::basic_ios 类模板和几个 typedef         |
| `<streambuf>(C++11)<br><br>` | std::basic_streambuf 类模板                              |
| `<istream>C++11`             | `std::basic_istream 类模板和几个 typedef<ostream>`          |
| `<ostream>(C++11)`           | std::basic_ostream、std::basic_iostream 类模板和几个 typedef |
| `对象`                         |                                                       |
| `cin`<br>`wcin`              | 从标准 C 输入流 stdin 读取（全局对象）                              |
| `cout`<br>`wcout`            | 写入标准 C 输出流 stdout（全局对象）                               |
| `cerr`<br>`wcerr`            | 写入标准 C 错误流 stderr，无缓冲（全局对象）                           |
| `clogw`<br>`clog`            | 写入标准 C 错误流 stderr（全局对象）                               |

### 概要

```C++
#include <ios>
#include <streambuf>
#include <istream>
#include <ostream>
 
namespace std {
  extern istream cin;
  extern ostream cout;
  extern ostream cerr;
  extern ostream clog;
 
  extern wistream wcin;
  extern wostream wcout;
  extern wostream wcerr;
  extern wostream wclog;
}
```