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

./kafka-console-producer.sh --broker-list 192.168.7.100:19092 --topic shuaige



'''在一台服务器上创建一个订阅者'''

./kafka-console-consumer.sh --zookeeper localhost:12181 --topic shuaige --from-beginning

