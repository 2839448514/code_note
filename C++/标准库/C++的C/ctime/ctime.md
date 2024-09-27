## 介绍

| `宏常量`                 |                                     |
| --------------------- | ----------------------------------- |
| `CLOCKS_PER_SEC`      | 表示每秒钟的时钟计时周期数。它用于将时钟计时周期数转换为秒。(宏常量) |
| `NULL`                | 实现定义的 null 指针常量  （宏常量）              |
| **`类型`**              |                                     |
| `clock_t`             | 进程运行时间  （typedef）                   |
| `size_t`              | sizeof 运算符  （typedef） 返回的无符号整数类型    |
| `time_t`              | 自纪元以来的时间类型  （typedef）               |
| `tm`                  | 日历时间类型  <br>（类）                     |
| `timespec(C++17)`     | 以秒和纳秒  为单位的时间（struct）               |
| `**功能**`              |                                     |
| `**时间操纵**`            |                                     |
| `clock`               | 返回自程序启动以来的原始处理器时钟时间                 |
| `time`                | 返回系统当前时间，以纪元以来的时间表示                 |
| `difftime`            | 计算时间 之间的差值（函数）                      |
| `timespec_get（C++17）` | 根据给定的时基  （函数）返回日历时间（以秒和纳秒为单位）       |
| `**格式转换**`            |                                     |
| `ctime`               | 将` std：：time_t `对象转换为文本表示  形式（函数）   |
| `asctime`             | 将` std：：tm `对象转换为文本表示  形式（函数）       |
| `strftime`            | 将 `std：：tm  `对象转换为自定义文本表示  形式（函数）   |
| `gmtime`              | 将自纪元以来的时间转换为以世界协调时间  表示的日历时间（函数）    |
| `localtime`           | 将自纪元以来的时间转换为以本地时间  表示的日历时间（函数）      |
| `mktime`              | 将日历时间转换为自纪元 以来的时间（函数）               |

## 个别函数介绍

### 1. `CLOCKS_PER_SEC`

```C++
clock_t start = clock(); // 记录开始时间
cout << CLOCKS_PER_SEC << endl;  //1000
clock_t end = clock(); // 记录结束时间
time_t current_time = time(NULL);
cout << "当前时间: " << ctime(&current_time) << endl;  //当前时间: Tue Jul 16 21:02:42 2024
double elapsed_seconds = difftime(end, start)/ CLOCKS_PER_SEC;
cout << "运行时间: " << elapsed_seconds << " 秒" << endl;  //运行时间: 0.001 秒
```

## 概要

```C++

#define NULL /* see description */
#define CLOCKS_PER_SEC /* see description */
#define TIME_UTC /* see description */
 
namespace std {
  using size_t = /* see description */;
  using clock_t = /* see description */;
  using time_t = /* see description */;
 
  struct timespec;
  struct tm;
 
  clock_t clock();
  double difftime(time_t time1, time_t time0);
  time_t mktime(tm* timeptr);
  time_t time(time_t* timer);
  int timespec_get(timespec* ts, int base);
  char* asctime(const tm* timeptr);
  char* ctime(const time_t* timer);
  tm* gmtime(const time_t* timer);
  tm* localtime(const time_t* timer);
  size_t strftime(char* s, size_t maxsize, const char* format, const tm* timeptr);
}

```

### `Class std::timespec`

```C++
struct timespec {
  [std::time_t](http://127.0.0.1:57856/c__/en.cppreference.com/w/cpp/chrono/c/time_t.html) tv_sec;
  long tv_nsec;
};
```

### `Class std::tm`

```C++
struct tm {
  int tm_sec;
  int tm_min;
  int tm_hour;
  int tm_mday;
  int tm_mon;
  int tm_year;
  int tm_wday;
  int tm_yday;
  int tm_isdst;
};
```