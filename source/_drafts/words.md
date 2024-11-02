---
title: words
tags:
---

### 随手记

1. for new


2. Gang Scheduling：All or nothing，离线作业具有组合调度的特点，即：要求所有的子任务都能够成功创建后，整个作业才能正常运行，一般采用PodGroup方案，需调整；
3. Binpack/Spreading Scheduling：LeastRequestedPriority，消耗的资源最少的节点会优先被调度，使得整体集群的资源使用在所有节点之间分配地相对均匀，即spreading摊大饼，反之则是binpack装箱，一般采用资源利用率打分方案构建，复用Kubernetes Scheduler score扩展点；
4. MMF：max-min-fairness：最大最小化公平分配算法，用户 1, 2, 3, 4 的需求分别为 2, 2.6, 4, 5，总资源数为 10。首先我们将资源数平分 4 等份，10/4 = 2.5。用户 1 需求是 2，则剩余 2.5 - 2 = 0.5，0.5 再平分给用户 2，3，4，0.5/3 = 0.1666…。然后用户 2 需求 2.6，剩余 2.5 + 0.1666 - 2.6 = 0.066…，再平分，0.066/2 = 0.033…，则用户 3 获得 2.5 + 0.66… + 0.033… = 2.7 ，此时不满足资源需求，结束。最终 4 个用户获得的资源数依次为 2, 2.6, 2.7, 2.7。
5. DRF： dominant resource fairness，类似MMF，那么何谓 Dominant Resource 呢？简而言之，用户被分配的资源中占比总资源比重最大的资源就是 Dominant Resource。举个例子，系统拥有资源 9 CPUs, 18 GB RAM，用户 A 的 task 需要资源为 \<1 CPU，4 GB RAM>，则用户 A 的资源占比分别为 CPU 1/9，RAM 2/9，则用户 A 的 Dominant Resource 就是 RAM。用户 B 的 task 需要资源 \<3 CPUs, 1 GB RAM>，则用户 B 的 Dominant Resource 为 CPU。最后 DRF 最求的结果就是平等权利的用户的 Dominant Resource 占的份额是一样的。求x+3y<=9cpu,4x+y<=18,2x/9=y/3解。
6. konga 
7. greenplum 
8. mxgraph 
9. SCADA
10. superset 
11. prestodb
12. CarbonData
13. agv
14. ServiceComb
15. FreeSwitch
16. PSTN  公共交换电话网,
17. Gini index 和信息熵
18. CANAL
19. SQOOP
20. splunk
21. impala
22. graylog
23. squid
24. Apache Guacamole  VNC 
25. TCC、FMT
26. nebula
27. waterdrop
28. dolphinscheduler
29. Disruptor
30. togaf
31. Seata
32. nifi
33. graphx
34. gremlin、Apache TinkerPop





### Java速记

#### HashMap的扰动函数

思路：保留高低位的数据特性，避免只高位变化带来hash冲撞<br/>

Java7:

```java
h ^=(h >>> 20)^(h >>> 12);
return h ^(h >>> 7)^(h >>> 4);
```

Java8：

将key的哈希code一分为二。其中：【高半区16位】数据不变。【低半区16位】数据与高半区16位数据进行异或操作，以此来加大低位的随机性。


```java
static final int hash(Object key) {
    int h;
    return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);
}
```

#### HashMap的负载因子

#### HashMap的底层数据结构

