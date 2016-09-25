# idfs_JNI
概述：
1.最近项目上需要提供C接口，因为客户那边使用的是高并发大流量【1.2GB/S】
2.hbase提供的Thrift API在流量要求上达不到要求
3.因此选择了C_JNI_JAVA此技术方案

本次技术开发中遇到的问题：
1.内存释放的问题【对象的内存该由谁负责释放】，最初的现象是程序运行爆掉
2.JVM运行机制【起初代码出现重复加载问题，影响效率】，解决办法：使用结构体，避免重复加载的问题
3.在多线程中javaVM线程可以共享，但是JNIEnv线程间不可以共享，否则运行会报错



参考链接：
JNI使用示例：
https://newcircle.com/s/post/1292/jni_reference_example
http://hildstrom.com/projects/jni/index.html
http://www.cnblogs.com/icejoywoo/archive/2012/02/24/2367116.html

hbase性能优化：
http://aperise.iteye.com/blog/2282670  
https://www.cloudera.com/documentation/enterprise/latest/topics/admin_hbase_rest_api.html     【RestFulAPI】

JVM-GC链接：
http://www.cnblogs.com/zhguang/p/3257367.html
http://www.importnew.com/3146.html
http://blog.csdn.net/ning109314/article/details/10411495/

GC观测插件使用：
https://www.ibm.com/developerworks/cn/java/j-lo-visualvm/

问题解决：
http://www.codeweblog.com/getbytearrayelements%E5%92%8Creleasebytearrayelements/
http://stackoverflow.com/questions/8574241/jni-newbytearray-memory-leak
http://stackoverflow.com/questions/18668135/jni-memory-leak-from-byte-array
http://stackoverflow.com/questions/31907157/where-to-free-allocated-memory-by-jni-newbytearray
http://stackoverflow.com/questions/1533378/jni-freeing-memory-to-avoid-memory-leak
http://stackoverflow.com/questions/17343832/glibc-detected-double-free-or-corruption
http://stackoverflow.com/questions/14063791/double-free-or-corruption-but-why
http://stackoverflow.com/questions/22573292/glibc-detected-a-out-double-free-or-corruption-out-0xbfe69600





