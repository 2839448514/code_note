ollama-hpp
==========

适用于 [Ollama](https://ollama.ai) API 的现代、仅限标头的 C++11/14/20 绑定。

只需几行代码即可访问 C++ 中本地语言模型的全部功能：

```c++
#include "ollama.hpp"
std::cout << ollama::generate("llama3:8b", "Why is the sky blue?") << std::endl;
```

 快速开始
-----

在 singleheader/ollama.hpp 中下载头文件，并将其包含在您的项目中以开始使用。不需要额外的文件或链接。C++11 是所需的最低语言规范，还支持 C++14/20。

 例如： `g++ your_source_file.cpp -Iollama-hpp/singleheader -std=c++11`

确保您拥有 ollama 服务器的活动实例和您计划运行的任何模型。有关更多详细信息，请参阅 [https://ollama.com](https://ollama.com)。您可以使用以下方法检查您的 ollama 服务器是否正在运行： `sudo systemctl status ollama`

 建筑示例
-----

要构建 ollama-hpp 示例和测试用例，请使用：`make -j8`

要运行示例和测试用例，请使用：

 `构建/测试`

 `构建/示例`

 完整的 API
--------

### Ollama 类和单例

`Ollama` 类定义了与 ollama 服务器接口所需的逻辑。

```C++
Ollama my_server("http://localhost:11434");
std::cout << my_server.generate("llama3:8b", "Why is the sky blue?") << std::endl;
```

为方便起见，Ollama 类的静态单例包含在 `ollama` 命名空间中，默认为 [http://localhost:11434](http://localhost:11434)。使用静态单例是首选，并且对大多数人来说是最简单的。这样，您只需包含 Headers 即可立即调用默认服务器。对 Ollama 类的所有调用也对单例有效：

```C++
// 无需创建对象；文件一经包含，静态单例即可使用
// http://localhost:11434 是默认服务器位置
ollama::generate("llama3:8b", "Why is the sky blue?") << std::endl;
```

###  Ollama 响应

`ollama：：response` 类包含来自服务器的响应。这是大多数代返回的默认类。根据上下文，它可以灵活地表示为 `nlohmann：：json` 或 `std：：string`。

```c++
ollama::response response = ollama::generate("llama3:8b", "Why is the sky blue?");
// A JSON object created from the server response
nlohmann::json data = response.as_json();
// 表示收到的 JSON 数据的字符串
std::string json_string = response.as_json_string();
//通常仅包含来自一代人的可读响应/chat
std::string simple_string = response.as_simple_string();
```

当与流或字符串交互时，`ollama：：response` 将默认使用 `as_simple_string` 表示。这通常包含响应的人类可读部分。

```c++
// 将打印生成的响应的人类可读部分，而不是 JSON
std::cout << response << std::endl;
```

###  设置服务器参数

`Ollama` 对象包含一系列用于与 ollama 服务器通信的智能默认值。您通常不必更改这些内容，但可以在需要时进行更改：

```c++
// 可选。默认情况下，服务器 URL 设置为 http://localhost:11434。
// 如果您的服务器位于其他 URL，请使用此功能。
ollama::setServerURL("http://localhost:11434");    
// 可选。设置服务器交互的读写超时时间（以秒为单位）。
// 如果您的模型较大且响应时间较长，则可能需要增加这些值。
ollama::setReadTimeout(120);
ollama::setWriteTimeout(120);
```

###  获取服务器状态

验证 Ollama 服务器是否正在使用 `ollama：：is_running（）` 运行

```c++
bool running = ollama::is_running();
```

###  获取服务器版本

使用 `ollama：：get_version（）` 返回一个包含 ollama 服务器版本的`std：：string`

```c++
std::string version = ollama::get_version();
```

### 将模型加载到内存中

这可以选择用于在使用之前有意识地将模型加载到内存中。当对已卸载的模型发出请求时，这会自动发生，但对于提前加载模型可能很有用。

```c++
bool model_loaded = ollama::load_model("llama3:8b");
```

### 拉取、复制和删除模型

您可以轻松提取、复制和删除 ollama 服务器中本地可用的模型。有关 Ollama 库中可用模型的完整列表，请参阅 [https://ollama.com/library](https://ollama.com/library)。

```c++
// 通过指定模型名称来拉取模型。
bool model_pulled = ollama::pull_model("llama3:8b");
// Copy a model by specifying a source model and destination model name.
bool model_copied = ollama::copy_model("llama3:8b", "llama3_copy");
// Delete a model by specifying a model name.
bool model_deleted = ollama::delete_model("llama3_copy");
```

###  检索模型信息

可以提取指定模型名称的模型信息。这将作为 `nlohmann：：json` 对象返回。

```c++
// 从 Ollama 服务器请求模型信息。
nlohmann::json model_info = ollama::show_model_info("llama3:8b");
std::cout << "Model family is " << model_info["details"]["family"] << std::endl;
```

### 列出本地可用和正在运行的模型

您可以使用以下内容查询 ollama 服务器上本地可用的模型列表。这以 `std：：string` 的 `std：：vector` 形式返回。

```c++
// 列出 ollama 服务器本地可用的模型
std::vector<std::string> models = ollama::list_models();
```

同样，您可以使用以下方法查询 ollama 服务器上当前正在运行的模型列表：

```c++
// 列出 ollama 服务器本地可用的模型
std::vector<std::string> models = ollama::list_running_models();
```

有关这些模型的详细参数，您可以使用 `ollama：：list_model_json（）` 和 `ollama：：running_model_json（）` 获取详细的 JSON 模型描述。

###  异常处理

大多数调用会在发生错误时抛出 `ollama：：exception`，并提供有关已发生异常的详细信息。默认情况下，异常处于启用状态。

```c++
try { 
  ollama::generate("Non-existent-model", "Requesting this model will throw an error"); 
 } 
catch(ollama::exception e) { std::cout << e.what() << std::endl; }
```

您还可以动态启用和禁用异常。如果禁用了异常，函数将在适当的时候返回空的 `ollama：：response` 或 false，而不是抛出 `ollama：：exception`。

```c++
ollama::allow_exceptions(false);
```

###  基本生成

可以通过指定模型名称和提示符来进行生成调用。这将返回一个 `ollama：：response`。

```c++
ollama::response response = ollama::generate("llama3:8b", "Why is the sky blue?");
std::cout << response << std::endl;
```

如前所述，你可以根据自己的喜好将 `ollama：：response` 作为 `nlohmann：：json` 对象或 `std：：string` 进行访问。

默认调用不使用来自 Ollama 服务器的流式处理，因此回复将阻止并作为一个响应接收。

###  使用选项

所有生成调用都可以包含通过 `ollama：：options` 对象指定的选项。此类扩展了 `nlohmann：：json`，并且可以支持[此处](https://github.com/ollama/ollama/blob/main/docs/api.md#generate-request-with-options)指定的选项。

```c++
ollama::options options;

// 像任何其他 json 类型一样访问和设置这些选项。
options["seed"] = 1;
options["temperature"] = 0;
options["num_predict"] = 18;

// 选项可以包含在任何生成函数中
ollama::response response = ollama::generate("llama3:8b", "Why is the sky blue?",options);

```

###  流式生成

您可以使用流式生成来绑定每次收到令牌时调用的回调函数。当您有较大的响应并希望在令牌到达时显示令牌时，这非常有用。

```c++

void on_receive_response(const ollama::response& response)
{   
//打印收到的令牌
  std::cout << response << std::flush;

// 服务器将把最后一个响应的“done”设置为 true
 if (response.as_json()["done"]==true) std::cout << std::endl;
}
 
// 此函数将在每个标记中调用
  std::function<void(const ollama::response&)> response_callback = on_receive_response;   
// 将回调绑定到生成
 ollama::generate("llama3:8b", "Why is the sky blue?", response_callback);
 
```

此函数使用阻塞套接字调用，因此它仍会阻塞主线程，直到收到所有令牌。

### 异步流生成

如果您不希望线程阻塞主线程，则可以在线程中启动流式处理调用。这将允许异步执行。

```c++

 std::atomic<bool> done{false};
 
 void on_receive_response(const ollama::response& response)
{   
 std::cout << response << std::flush;

if (response.as_json()["done"]==true) { done=true;  std::cout << std::endl;}
}
 
// 使用 std::function 从现有函数定义回调
// 您还可以使用具有等效签名的 lambda
 std::function<void(const ollama::response&)> response_callback = on_receive_response;  

// 您可以在带有回调的线程中启动生成以异步使用它。
std::thread new_thread( [response_callback]{ 
 ollama::generate("llama3:8b", "Why is the sky blue?", response_callback); } );

// 在等待异步响应时防止主线程退出。
 while (!done) { std::this_thread::sleep_for(std::chrono::microseconds(100) ); }
new_thread.join();

```

###  使用图像

代可以包含支持视觉的模型（如 `llava`）的图像。`ollama：：image` 类可以从文件中加载图像并将其编码为 [base64](https://en.wikipedia.org/wiki/Base64) 字符串。

```c++
ollama::image image = ollama::image::from_file("llama.jpg");
```

图像也可以表示为 base64 字符串文本。

```c++
ollama::image base64_image =ollama::image::from_base64_string("iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAAFUlQVR42mNkYPhfz0AEYBxVSF+FAP5FDvcfRYWgAAAAAElFTkSuQmCC");
```

###  使用映像生成

生成式调用还可以包含图像。

```c++
ollama::image image = ollama::image::from_file("llama.jpg");
ollama::response response = ollama::generate("llava", "What do you see in this image?", options, image);
```

可以使用 `ollama：：images` 容器包含多个图像。

```c++
ollama::image image = ollama::image::from_file("llama.jpg");
ollama::image image2 = ollama::image::from_file("another_llama.jpg");
// 在此处包含图像列表
ollama::images images={image, image2};
ollama::response response = ollama::generate("llava", "What do you see in these images?", options, images);
```

###  基本聊天生成

Ollama 聊天 API 可以用作基本生成的替代方案。这允许用户向服务器发送一系列消息并获取对话中的下一个响应。

`ollama：：message` 表示对话中的单个聊天消息。它由角色、内容和一系列可选的图像组成。

```c++
ollama::message message("user", "Why is the sky blue?");
```

向服务器发送消息将返回对话中的下一条消息。

```c++
ollama::message message("user", "Why is the sky blue?");
ollama::response response = ollama::chat("llama3:8b", message);

```

与任何生成式通话一样，聊天通话也可以包含选项。

```c++
ollama::options options;
options["seed"] = 1;

ollama::message message("user", "Why is the sky blue?");

ollama::response response = ollama::chat("llama3:8b", message, options);
```

### 使用多条消息聊天

您可以在聊天中使用消息集合。这允许 chain of-thought 提示，并且对于设置对话很有用。

```c++
ollama::message message1("user", "What are nimbus clouds?");
ollama::message message2("assistant", "Nimbus clouds are dark rain clouds.");
ollama::message message3("user", "What are some other kinds of clouds?");

ollama::messages messages = {message1, message2, message3};

ollama::response response = ollama::chat("llama3:8b", messages);

```

### 流式聊天生成

默认聊天生成不会流式传输令牌，而是将整个回复作为一个响应返回。您可以绑定回调函数来处理每个令牌的流式响应，就像标准代一样。

```c++
  
   void on_receive_response(const ollama::response& response)
  {   
  std::cout << response << std::flush;
  
  if (response.as_json()["done"]==true) std::cout << std::endl;
  }
  
  std::function<void(const ollama::response&)> response_callback = on_receive_response; 
  
  ollama::message message("user", "Why is the sky blue?");       
 
  ollama::chat("llama3:8b", message, response_callback, options); 
```

###  与图片聊天

`ollama：：message` 类可以包含任意数量的要发送到服务器的 `ollama：：image` 对象。这允许在支持视觉的模型的聊天的每条消息中发送图像。

```c++
ollama::image image = ollama::image::from_file("llama.jpg");
// 我们可以选择在每条消息中包含图像。 
//支持视觉的模型将能够利用这些图像。
ollama::message message_with_image("user", "What do you see in this image?", image);
ollama::response response = ollama::chat("llava", message_with_image);
```

###  嵌入生成

可以从指定的模型名称和提示符生成嵌入。

```c++
ollama::response response = ollama::generate_embeddings("llama3:8b", "Why is the sky blue?");
```

与任何其他生成函数一样，选项可以在生成过程中包含在内。

```c++

ollama::options options;
options["num_predict"] = 20;

ollama::response response = ollama::generate_embeddings("llama3:8b", "Why is the sky blue?", options);
```

###  调试信息

可以轻松打开和关闭请求和回复服务器的调试日志记录。如果您想查看从服务器发送和接收的实际 JSON，这非常有用。

```c++
ollama::show_requests(true);
ollama::show_replies(true);
```

###  手动请求

对于那些希望更好地控制发送到 ollama 服务器的请求的人来说，可以通过 `ollama：：request` 类创建手动请求。此类扩展了 `nlohmann：：json`，可以被视为标准 JSON 对象。

```c++
ollama::request request(ollama::message_type::generation);
request["model"]="mistral";
request["prompt"]="Why is the sky blue?";
request["system"] = "Talk like a pirate for the next reply."
std::cout << ollama::generate(request) << std::endl;

```

这提供了对请求的大多数自定义。用户应注意确保提供有效字段，否则可能会在响应时引发异常。可以对生成、聊天和嵌入终端节点发出手动请求。

###  处理上下文

可以通过将过去的 `ollama：：response` 与 `generate` 一起包含来自先前生成请求的上下文来使用：

```c++
std::string model = "llama3.1:8b";
ollama::response context = ollama::generate(model, "Why is the sky blue?");
ollama::response response = ollama::generate(model, "Tell me more about this.",context);
```

这将在生成新一代时提供过去的用户提示和对模型的响应。Context 可以链接在多个消息上，并将包含从第一个提示开始的整个对话历史记录：

```c++
ollama::response first_response = ollama::generate(model, "Why is the sky blue?");
ollama::response second_response = ollama::generate(model, "Tell me more about this.", first_response);
ollama::response third_response = ollama::generate(model, "What was the first question that I asked you?", second_response);

```

在创建手动请求时，也可以将 Context 添加为 JSON：

```c++
ollama::response response = ollama::generate("llama3.1:8b", "Why is the sky blue?");

ollama::request request(ollama::message_type::generation);
request["model"]="llama3.1:8b";
request["prompt"]="Why is the sky blue?";
request["context"] = response.as_json()["context"];
std::cout << ollama::generate(request) << std::endl;

//请注意，`聊天`端点没有专用的 context 参数;context 只是通过对话的消息历史记录提供：
ollama::message message1("user", "What are nimbus clouds?");
ollama::message message2("assistant", "Nimbus clouds are dense, moisture-filled clouds that produce rain.");
ollama::message message3("user", "What was the first question I asked you?");
ollama::messages messages = {message1, message2, message3};
std::cout << ollama::chat("llama3.1:8b", messages) << std::endl;
```

###  上下文长度

大多数语言模型都有它们可以接受的最大输入上下文长度。此长度确定在信息丢失之前，可以与提示一起作为输入提供给模型的先前标记的数量。例如，Llama 3.1 的最大上下文长度为 128k 个令牌;默认情况下，Ollama 通常启用数量少得多的 **2048** 个令牌，以减少内存使用。你可以使用 `ollama：：options` 中的 `num_ctx` 参数来增加上下文窗口的大小，用于需要保留较长对话历史记录的任务：

```c++
// 将上下文窗口的大小设置为 8192 个标记。
 ollama::options options;
 options["num_ctx"] = 8192; 
 
// 执行包含模型选项的简单生成。
std::cout << ollama::generate("llama3.1:8b", "Why is the sky blue?", options) << std::endl;
```

请记住，在加载到 GPU 时，增加上下文长度会增加内存中的模型大小。在配置长上下文任务时，应确保硬件具有足够的内存来容纳较大的模型。

单标题 vs 独立标题
-----------

为方便起见，ollama-hpp 在 `singleheader/ollama.hpp` 中包含了该库的单头版本，该版本将核心 ollama.hpp 代码与 nlohmann json、httplib 和 base64.h 的单头版本捆绑在一起。这些库中的每一个都可以在 MIT 许可证下使用，并且它们各自的许可证也包含在内。可以通过运行 `./make_single_header.sh` 从这些独立文件重新生成单头 include

如果您希望单独包含这些库的标头，则可以通过包含位于 `include/ollama.hpp` 中的标准标头来实现此目的。

 关于这个软件
-------

Ollama 是一个高质量的 REST 服务器和 API，提供了一个通过 llama.cpp 在本地运行语言模型的接口。

Ollama 由 Jeffrey Morgan （@jmorganca） 和 Ollama 团队制作，可在 MIT 许可证下使用。要支持此项目或了解更多详情，请访问 [https://github.com/ollama](https://github.com/ollama) 或 [https://ollama.ai](https://ollama.ai)

该库是 Ollama API 的仅头文件 C++ 集成，提供对大多数 API 功能的访问，同时将它们与 std 库类或社区中流行的仅头文件库集成。使用以下外部库：

*   **nlohmnann JSON** 是一种功能丰富的仅标头 C++ JSON 实现。该库由 Niels Lohmann 创建，可在 MIT 许可证下使用。有关更多详细信息，请访问：[https://github.com/nlohmann/json](https://github.com/nlohmann/json)

*   **httplib** 是一个仅限头文件的 C++ http/https 库。该库由 Yuji Hirose 创建，可在 MIT 许可证下使用。有关更多详细信息，请访问：[https://github.com/yhirose/cpp-httplib](https://github.com/yhirose/cpp-httplib)

*   **Base64.h** 是一个仅限头文件的 C++ 库，用于对 Base64 值进行编码和解码。该库由 tomykaira 创建，可在 MIT 许可证下使用。有关更多详细信息，请访问：[https://gist.github.com/tomykaira/f0fd86b6c73063283afe550bc5d77594](https://gist.github.com/tomykaira/f0fd86b6c73063283afe550bc5d77594)