# kafka配置

/Users/didi/kafka/server1/kafka\_2.10-0.8.2.1/config

vi server.properties

\# root directory for all kafka znodes.

zookeeper.connect=localhost:2181,localhost:2182,localhost:2183

1、启动服务

\#从后台启动Kafka集群（3台都需要启动）

cd /Users/didi/kafka/server1/kafka\_2.10-0.8.2.1/bin \#进入到kafka的bin目录

./kafka-server-start.sh -daemon ../config/server.properties



