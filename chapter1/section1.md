# kafka配置

/Users/didi/kafka/server1/kafka\_2.10-0.8.2.1/config

vi server.properties

\# root directory for all kafka znodes.

zookeeper.connect=localhost:2181,localhost:2182,localhost:2183

1、启动服务

\#从后台启动Kafka集群（3台都需要启动）

cd /Users/didi/kafka/server1/kafka\_2.10-0.8.2.1/bin \#进入到kafka的bin目录

./kafka-server-start.sh -daemon ../config/server.properties

2、检查服务是否启动

\#执行命令jps

$ jps

747

11308 QuorumPeerMain

11339 QuorumPeerMain

11497 Kafka

11634 Jps

637 Main

11132 QuorumPeerMain

/Users/didi/kafka/server2/kafka\_2.10-0.8.2.1/config

vi server.properties

broker.id=0  \#当前机器在集群中的唯一标识，和zookeeper的myid性质一样

port=9093 \#当前kafka对外提供服务的端口默认是9093

$ pwd

/Users/didi/kafka/server2/kafka\_2.10-0.8.2.1/bin

$ ./kafka-server-start.sh -daemon ../config/server.properties

localhost:bin didi$ jps

747

11308 QuorumPeerMain

11339 QuorumPeerMain

11710 Kafka

11497 Kafka

11711 Jps

637 Main

11132 QuorumPeerMain

3、创建Topic来验证是否创建成功

cd /Users/didi/kafka/server1/kafka\_2.10-0.8.2.1/bin

$ ./kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 2 --partitions 1 --topic shuaige

Created topic "shuaige".

\#解释

--replication-factor 2   \#复制两份

--partitions 1 \#创建1个分区

--topic \#主题为shuaige

'''在一台服务器上创建一个发布者'''

\#创建一个broker，发布者

.$ ./kafka-console-producer.sh --broker-list localhost:9092 --topic shuaige

\[2017-05-17 21:38:37,347\] WARN Property topic is not valid \(kafka.utils.VerifiableProperties\)

'''在一台服务器上创建一个订阅者'''

$ ./kafka-console-consumer.sh --zookeeper localhost:2181 --topic shuaige --from-beginning

\[2017-05-17 21:37:34,110\] WARN \[console-consumer-78661\_localhost-1495028211868-555ab916-leader-finder-thread\], Failed to add leader for partitions \[shuaige,0\]; will retry \(kafka.consumer.ConsumerFetcherManager$LeaderFinderThread\)

kafka.common.NotLeaderForPartitionException

```
at sun.reflect.GeneratedConstructorAccessor2.newInstance\(Unknown Source\)

at sun.reflect.DelegatingConstructorAccessorImpl.newInstance\(DelegatingConstructorAccessorImpl.java:27\)

at java.lang.reflect.Constructor.newInstance\(Constructor.java:513\)

at java.lang.Class.newInstance0\(Class.java:357\)

at java.lang.Class.newInstance\(Class.java:310\)

at kafka.common.ErrorMapping$.exceptionFor\(ErrorMapping.scala:86\)

at kafka.consumer.SimpleConsumer.earliestOrLatestOffset\(SimpleConsumer.scala:169\)

at kafka.consumer.ConsumerFetcherThread.handleOffsetOutOfRange\(ConsumerFetcherThread.scala:60\)

at kafka.server.AbstractFetcherThread$$anonfun$addPartitions$2.apply\(AbstractFetcherThread.scala:177\)

at kafka.server.AbstractFetcherThread$$anonfun$addPartitions$2.apply\(AbstractFetcherThread.scala:172\)

at scala.collection.TraversableLike$WithFilter$$anonfun$foreach$1.apply\(TraversableLike.scala:772\)

at scala.collection.immutable.Map$Map1.foreach\(Map.scala:109\)

at scala.collection.TraversableLike$WithFilter.foreach\(TraversableLike.scala:771\)

at kafka.server.AbstractFetcherThread.addPartitions\(AbstractFetcherThread.scala:172\)
```

4.1、查看topic



./kafka-topics.sh --list --zookeeper localhost:12181

\#就会显示我们创建的所有topic

4.2、查看topic状态



复制代码

/kafka-topics.sh --describe --zookeeper localhost:12181 --topic shuaige

\#下面是显示信息

Topic:ssports    PartitionCount:1    ReplicationFactor:2    Configs:

    Topic: shuaige    Partition: 0    Leader: 1    Replicas: 0,1    Isr: 1

\#分区为为1  复制因子为2   他的  shuaige的分区为0 

\#Replicas: 0,1   复制的为0，1

