python程序加速
====
#### IO密集型任务 VS 计算密集型任务</br>

* 所谓IO密集型任务:</br>
 是指磁盘IO、网络IO占主要的任务，计算量很小。比如请求网页、读写文件等。
当然我们在Python中可以利用sleep达到IO密集型任务的目的。</br>
* 所谓计算密集型任务: </br>
是指CPU计算占主要的任务，CPU一直处于满负荷状态. </br>

####计算密集型任务</br>
* numpy
* numexpr
* numba
* pypy
* cython
* pycuda

####IO密集型任务</br>
Python中比较常见的并发方式主要有两种：多线程和多进程. </br>
多线程即在一个进程中启动多个线程执行任务。一般来说使用多
线程可以达到并行的目的，但由于Python中使用了全局解释锁
GIL的概念，导致Python中的多线程并不是并行执行，而是“交替
执行”。</br>

Python中解决IO密集型任务（打开多个网站）的方式有很多种，比如多进程、多线程。
但理论上一台电脑中的线程数、进程数是有限的，而且进程、线程之间的切换也比较浪费时间
。所以就出现了“协程”的概念。协程允许一个执行过程A中断，然后转到执行过程B，
在适当的时候再一次转回来，有点类似于多线程。但协程有以下2个优势：
* 协程的数量理论上可以是无限个，而且没有线程之间的切换动作，执行效率比线程高。
* 协程不需要“锁”机制，即不需要lock和release过程，因为所有的协程都在一个线程中。
* 相对于线程，协程更容易调试debug，因为所有的代码是顺序执行的。

一般来说，解决并行事件的传统思路可能是使用多线程。但是多线程有几个劣势,
第一是资源的开销;第二是由于Python GIL（全局解释锁）的存在;
多线程并非并行执行，而是交替执行，造成多线程在计算密集型任务的效率并不高


