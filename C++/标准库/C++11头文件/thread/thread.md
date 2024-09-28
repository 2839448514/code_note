---
tags:
  - CPP
---
# thread

## 介绍

| **包括**                                                                                            |                                  |
| ------------------------------------------------------------------------------------------------- | -------------------------------- |
| **`<compare>`(C++20)**                                                                            | **三向比较运算符支持**                    |
| **命名空间**                                                                                          |                                  |
| **`**this_thread**`**                                                                             | **提供访问当前执行线程的函数**                |
| **类**                                                                                             |                                  |
| **thread(C++11)**                                                                                 | **管理单独的线程  （类）**                 |
| **jthread(C++20)<br>**                                                                            | **std：：thread，支持自动加入和取消  （类）**   |
| **std::hash<std::thread::id>**                                                                    | **专门化 std：：hash  <br>（类模板专用化）**  |
| **函数**                                                                                            |                                  |
| **std：：swap(std：：thread)（C++11）**                                                                 | **专门化 std：：swap 算法  （函数）**       |
| **operator==<br>operator!=<br>operator<<br>operator<=<br>operator><br>operator>=<br>operator<=>** | **比较两个对象  <br>（函数）`thread::id`** |
| **operator<<**                                                                                    | **序列化 thread::id 对象**            |
| **在命名空间中定义`std::this_thread`**                                                                    |                                  |
| **yield  (C++11)<br>**                                                                            | **建议实现重新安排线程  的执行（函数）**          |
| **get_id(C++11)**                                                                                 | **返回当前线程  的线程 ID（函数）**           |
| **sleep_for（C++11）**                                                                              | **在指定的持续时间  内停止当前线程的执行（函数）**     |
| **sleep_until（C++11）**                                                                            | **停止当前线程的执行，直到指定的时间点  （函数）**     |

### 概要

```C++
#include <compare>
namespace std {
  class thread;
  void swap(thread& x, thread& y) noexcept;
  // class jthread
  class jthread;
  namespace this_thread {
    thread::id get_id() noexcept;
    void yield() noexcept;
    template<class Clock, class Duration>
      void sleep_until(const chrono::time_point<Clock, Duration>& abs_time);
    template<class Rep, class Period>
      void sleep_for(const chrono::duration<Rep, Period>& rel_time);
  }
}
```

#### Class std::thread

```C++
namespace std {
  class thread {
  public:
    // types
    class id;
    using native_handle_type = /* implementation-defined */;
 
    // construct/copy/destroy
    thread() noexcept;
    template<class F, class... Args> explicit thread(F&& f, Args&&... args);
    ~thread();
    thread(const thread&) = delete;
    thread(thread&&) noexcept;
    thread& operator=(const thread&) = delete;
    thread& operator=(thread&&) noexcept;
 
    // members
    void swap(thread&) noexcept;
    bool joinable() const noexcept;
    void join();
    void detach();
    id get_id() const noexcept;
    native_handle_type native_handle();
 
    // static members
    static unsigned int hardware_concurrency() noexcept;
  };
}

```

#### Class std::jthread

```C++
namespace std {
  class jthread {
  public:
    // types
    using id = thread::id;
    using native_handle_type = thread::native_handle_type;
 
    // constructors, move, and assignment
    jthread() noexcept;
    template<class F, class... Args> explicit jthread(F&& f, Args&&... args);
    ~jthread();
    jthread(const jthread&) = delete;
    jthread(jthread&&) noexcept;
    jthread& operator=(const jthread&) = delete;
    jthread& operator=(jthread&&) noexcept;
 
    // members
    void swap(jthread&) noexcept;
    [[nodiscard]] bool joinable() const noexcept;
    void join();
    void detach();
    [[nodiscard]] id get_id() const noexcept;
    [[nodiscard]] native_handle_type native_handle();
 
    // stop token handling
    [[nodiscard]] stop_source get_stop_source() noexcept;
    [[nodiscard]] stop_token get_stop_token() const noexcept;
    bool request_stop() noexcept;
 
    // specialized algorithms
    friend void swap(jthread& lhs, jthread& rhs) noexcept;
 
    // static members
    [[nodiscard]] static unsigned int hardware_concurrency() noexcept;
 
  private:
    stop_source ssource;        // exposition only
  };
}

```

#### Class std::thread::id

```C++
namespace std {
  class thread::id {
  public:
    id() noexcept;
  };
 
  bool operator==(thread::id x, thread::id y) noexcept;
  strong_ordering operator<=>(thread::id x, thread::id y) noexcept;
 
  template<class CharT, class Traits>
    basic_ostream<CharT, Traits>&
      operator<<(basic_ostream<CharT, Traits>& out, thread::id id);
 
  // hash support
  template<class T> struct hash;
  template<> struct hash<thread::id>;
}
```
