# Java performance

## step 1 找到占用CPU和RAW最高的线程

### jps

jps是jdk提供的一个查看当前java进程的工具

```
# 常用指令
jps -l
# 参数
-l 输出jar的完全路径名
-q 仅显示进程号
-v 输出JVM参数
```

### ps

获取进程下线程信息

```
# 常用指令
ps -mp $PID -o THREAD,tid,time
```

## step 2 详细信息

### jmap

查看jvm堆详细情况

```
jmap -heap $PID
jmap -histo $PID
```

### jstat

```
jstat -gcutil $PID 1000 5
jstat -printcompilation -h3 $PID
```

### jstack

dump出当前JVM进程的堆栈信息

```
# 常用指令
printf "%x\n" $TID
jstack $PID >> dump.log
grep $16进制TID dump.log -C 10
```

http://www.xitongzhijia.net/xtjc/20141203/31828.html
[java性能调优随机](https://yq.aliyun.com/articles/236782?utm_content=m_34647)
[大话java性能优化](http://product.dangdang.com/23949549.html?ref=customer-0-B)
