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

## std::async

### 第一个参数

#### std::launch::deferred

函数将延迟到`future`对象调用`get()`或者`wait()`的时候

#### std::launch::async

强制这个异步任务在新线程上执行

## std::atomic<T>

## lambda