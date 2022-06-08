# Concurrency

## std::thread
``` c++
std::thread normalThread = thread(function, args);
std::thread objThread = thread(&X::function, *obj);
normalThread.join();
normalThread.detach();
normalThread.joinable();
```

## std::mutex std::lock_guard  std::unique_lock

```cpp
std::mutex myMutex;
myMutex.lock();
myMutex.unlock();
```

```cpp
std::mutex myMutex;
std::lock_guard<std::mutex> guard(myMutex);
```

```cpp
std::mutex myMutex1;
std::mutex myMutex2;
std::lock(myMutex1, myMutex2);
```

## std::future

```cpp
// future from a packaged_task
std::packaged_task<int()> task([]{ return 7; }); // wrap the function
std::future<int> f1 = task.get_future();  // get a future
std::thread t(std::move(task)); // launch on a thread

// future from an async()
std::future<int> f2 = std::async(std::launch::async, []{ return 8; });

// future from a promise
std::promise<int> p;
std::future<int> f3 = p.get_future();
std::thread( [&p]{ p.set_value_at_thread_exit(9); }).detach();

std::cout << "Waiting..." << std::flush;
f1.wait();
f2.wait();
f3.wait();
std::cout << "Done!\nResults are: "
          << f1.get() << ' ' << f2.get() << ' ' << f3.get() << '\n';
t.join();
```

## std::async

### 第一个参数

#### std::launch::deferred

函数将延迟到`future`对象调用`get()`或者`wait()`的时候

#### std::launch::async

强制这个异步任务在新线程上执行

## std::atomic<T>

## lambda

## std::function

## std::chrono
```cpp
// cpp11
std::chrono::nanoseconds
std::chrono::microseconds
std::chrono::milliseconds
std::chrono::seconds
std::chrono::minutes
std::chrono::hours
//cpp 20
std::chrono::days
std::chrono::weeks
std::chrono::months
std::chrono::years
```

## std::ratio
```cpp
std::ratio<1, 10000>; // 1/10000
```