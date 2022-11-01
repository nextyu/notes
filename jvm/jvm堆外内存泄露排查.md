# jvm堆外内存泄露排查


## NativeMemoryTracking


```
-XX:NativeMemoryTracking=detail # 加入启动参数

java -Xms2g -Xmx2g -Xss512k -jar -XX:NativeMemoryTracking=detail xxx.jar


jcmd PID VM.native_memory baseline // 创建baseline


jcmd PID VM.native_memory detail.diff scale=MB // 运行一段时间之后，对比内存分配情况

```






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