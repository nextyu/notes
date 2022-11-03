# jvm堆外内存泄露排查

## NativeMemoryTracking


```
-XX:NativeMemoryTracking=detail # 加入启动参数

java -Xms2g -Xmx2g -Xss512k -jar -XX:NativeMemoryTracking=detail xxx.jar


jcmd PID VM.native_memory baseline // 创建baseline


jcmd PID VM.native_memory detail.diff scale=MB // 运行一段时间之后，对比内存分配情况

```


`jcmd PID VM.native_memory summary scale=MB`

```
Native Memory Tracking:

Total: reserved=3653MB, committed=2448MB
-                 Java Heap (reserved=1800MB, committed=1800MB)
                            (mmap: reserved=1800MB, committed=1800MB) 
 
-                     Class (reserved=1111MB, committed=98MB)
                            (classes #15755)
                            (malloc=5MB #31515) 
                            (mmap: reserved=1106MB, committed=93MB) 
 
-                    Thread (reserved=365MB, committed=365MB)
                            (thread #712)
                            (stack: reserved=361MB, committed=361MB)
                            (malloc=2MB #3559) 
                            (arena=1MB #1422)
 
-                      Code (reserved=255MB, committed=63MB)
                            (malloc=11MB #15911) 
                            (mmap: reserved=244MB, committed=52MB) 
 
-                        GC (reserved=69MB, committed=69MB)
                            (malloc=3MB #493) 
                            (mmap: reserved=66MB, committed=66MB) 
 
-                  Compiler (reserved=2MB, committed=2MB)
                            (malloc=2MB #2079) 
 
-                  Internal (reserved=26MB, committed=26MB)
                            (malloc=26MB #29800) 
 
-                    Symbol (reserved=20MB, committed=20MB)
                            (malloc=17MB #173136) 
                            (arena=4MB #1)
 
-    Native Memory Tracking (reserved=4MB, committed=4MB)
                            (tracking overhead=4MB)
```


```
reserved    是jvm期望使用的内存
committed   是jvm实际使用的内存

```


除了`Java Heap`使用的是堆内存，其他比如`Class`、`Thread`等都是使用的本地内存（native memory），所以一个java程序占用的内存不只有堆内存，还得加上各种`Class`、`Thread`等使用的本地内存。



## 参考资料
- [官方文档](https://docs.oracle.com/javase/8/docs/technotes/guides/vm/nmt-8.html)
- [JVM 堆外内存泄漏分析（一）](https://coderbee.net/index.php/jvm/20190913/1929)
- [一个JDK的Bug与NMT](http://fengbo.cool/java-nmt.html)
- [聊聊HotSpot VM的Native Memory Tracking](https://cloud.tencent.com/developer/article/1406522)
- [统计进程中的线程数](https://www.cnblogs.com/duanxz/archive/2012/10/25/2738897.html)
- [Stack Memory and Heap Space in Java](https://www.baeldung.com/java-stack-heap)
- [JVM option -Xss - What does it do exactly?](https://stackoverflow.com/questions/4967885/jvm-option-xss-what-does-it-do-exactly)
- [一个 jvm 线程占用多少操作系统内存](https://my.oschina.net/xiaominmin/blog/3136486)
- [linux下找到JVM占用资源最高的线程](https://blog.51cto.com/u_15127675/3744316)
- [Understanding Metaspace and Class Space GC Log Entries](https://poonamparhar.github.io/understanding-metaspace-gc-logs/)
- [JVM Tuning Using jcmd](https://dzone.com/articles/jvm-tuning-using-jcmd)