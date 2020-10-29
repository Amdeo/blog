---
title: python多进程multiprocessing
date: 2020-04-18 18:11:13
tags:
categories:
toc: true
keywords:
description:
comments: true
---

# multiprocessing

multiprocessing是python中多进程的包，由于python全局解释器锁的存在，导致python多线程无法使用cpu多核。

但是multiprocessing库带来的多进程是真正的多进程，可以让python充分使用 机器上的多个核心 。

```python
from multiprocessing import Pool


def f(x):	#进程函数
    return x * x

if __name__ == '__main__':
    with Pool(5) as p:
        print(p.map(f, [1, 2, 3])) #这里list中有3个参数表示，启动三个进程
```

这是python文档上一个例子，使用Pool来创建线程，Pool(5)`表示一个进程池中最多有5给进行同时运行`。

## `Process` 类

通过Prcocess来创建进程

```python
from multiprocessing import Process
import os

def info(title):
    print(title)
    print('module name:', __name__) # 模块名
    print('parent process:', os.getppid()) # 父进程id
    print('process id:', os.getpid()) # 当前进程id

def f(name):
    info('function f')	#子进程调用下这个函数
    print('hello', name)

if __name__ == '__main__':
    info('main line') # 主进程调用这个函数
    p = Process(target=f, args=('bob',))
    p.start()
    p.join()
```

 [`multiprocessing`](https://docs.python.org/zh-cn/3.7/library/multiprocessing.html#module-multiprocessing) 支持三种启动进程的方法。这些 *启动方法* 有 

*spawn*

父进程启动一个新的Python解释器进程。子进程只会继承那些运行进程对象的 [`run()`](https://docs.python.org/zh-cn/3.7/library/multiprocessing.html#multiprocessing.Process.run) 方法所需的资源。特别是父进程中非必须的文件描述符和句柄不会被继承。相对于使用 *fork* 或者 *forkserver*，使用这个方法启动进程相当慢。

可在Unix和Windows上使用。 Windows上的默认设置。

*fork*

父进程使用 [`os.fork()`](https://docs.python.org/zh-cn/3.7/library/os.html#os.fork) 来产生 Python 解释器分叉。子进程在开始时实际上与父进程相同。父进程的所有资源都由子进程继承。请注意，安全分叉多线程进程是棘手的。

只存在于Unix。Unix中的默认值。

*forkserver*

程序启动并选择* forkserver * 启动方法时，将启动服务器进程。从那时起，每当需要一个新进程时，父进程就会连接到服务器并请求它分叉一个新进程。分叉服务器进程是单线程的，因此使用 [`os.fork()`](https://docs.python.org/zh-cn/3.7/library/os.html#os.fork) 是安全的。没有不必要的资源被继承。

可在Unix平台上使用，支持通过Unix管道传递文件描述符。



## multiprocessing进程间通信

Queue

```python
from multiprocessing import Process, Queue

def f(q):
    q.put([42, None, 'hello'])

if __name__ == '__main__':
    q = Queue() # 主进程创建一个Queue
    p = Process(target=f, args=(q,)) #将Queue当做参数传入子进程
    p.start()
    print(q.get())    # prints "[42, None, 'hello']"
    p.join()
```

Pipe

```python
from multiprocessing import Process, Pipe

def f(conn):
    conn.send([42, None, 'hello'])
    conn.close()

if __name__ == '__main__':
    parent_conn, child_conn = Pipe() # 创建管道，管道的每一端都有读写，当两个进程同事读或者写，管道中数据可能会损坏
    p = Process(target=f, args=(child_conn,))
    p.start()
    print(parent_conn.recv())   # prints "[42, None, 'hello']"
    p.join()
```

### 进程间的同步

Lock 进程锁

```python
from multiprocessing import Process, Lock

def f(l, i):
    l.acquire()
    try:
        print('hello world', i)
    finally:
        l.release()

if __name__ == '__main__':
    lock = Lock()

    for num in range(10):
        Process(target=f, args=(lock, num)).start()
```

###  **共享内存** 

```python
from multiprocessing import Process, Value, Array

def f(n, a):
    n.value = 3.1415927
    for i in range(len(a)):
        a[i] = -a[i]

if __name__ == '__main__':
    num = Value('d', 0.0)
    arr = Array('i', range(10))

    p = Process(target=f, args=(num, arr))
    p.start()
    p.join()

    print(num.value)
    print(arr[:])
```

服务器进程

 由 `Manager()` 返回的管理器对象控制一个服务器进程，该进程保存Python对象并允许其他进程使用代理操作它们。 

 `Manager()` 返回的管理器支持类型： [`list`](https://docs.python.org/zh-cn/3.7/library/stdtypes.html#list) 、 [`dict`](https://docs.python.org/zh-cn/3.7/library/stdtypes.html#dict) 、 [`Namespace`](https://docs.python.org/zh-cn/3.7/library/multiprocessing.html#multiprocessing.managers.Namespace) 、 [`Lock`](https://docs.python.org/zh-cn/3.7/library/multiprocessing.html#multiprocessing.Lock) 、 [`RLock`](https://docs.python.org/zh-cn/3.7/library/multiprocessing.html#multiprocessing.RLock) 、 [`Semaphore`](https://docs.python.org/zh-cn/3.7/library/multiprocessing.html#multiprocessing.Semaphore) 、 [`BoundedSemaphore`](https://docs.python.org/zh-cn/3.7/library/multiprocessing.html#multiprocessing.BoundedSemaphore) 、 [`Condition`](https://docs.python.org/zh-cn/3.7/library/multiprocessing.html#multiprocessing.Condition) 、 [`Event`](https://docs.python.org/zh-cn/3.7/library/multiprocessing.html#multiprocessing.Event) 、 [`Barrier`](https://docs.python.org/zh-cn/3.7/library/multiprocessing.html#multiprocessing.Barrier) 、 [`Queue`](https://docs.python.org/zh-cn/3.7/library/multiprocessing.html#multiprocessing.Queue) 、 [`Value`](https://docs.python.org/zh-cn/3.7/library/multiprocessing.html#multiprocessing.Value) 和 [`Array`](https://docs.python.org/zh-cn/3.7/library/multiprocessing.html#multiprocessing.Array) 。例如 

```python
from multiprocessing import Process, Manager

def f(d, l):
    d[1] = '1'
    d['2'] = 2
    d[0.25] = None
    l.reverse()

if __name__ == '__main__':
    with Manager() as manager: #manger的管理数据的进程
        d = manager.dict()
        l = manager.list(range(10))

        p = Process(target=f, args=(d, l))
        p.start()
        p.join()

        print(d)
        print(l)
```

