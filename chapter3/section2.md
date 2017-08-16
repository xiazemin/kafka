# kafka使用

a$server1/kafka\_2.10-0.8.2.1/bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 2 -partitions 1 --topic Multibrokerapplication

SLF4J: Class path contains multiple SLF4J bindings.

SLF4J: Found binding in \[jar:file:/Users/didi/hbase/hbase/lib/slf4j-log4j12-1.7.5.jar!/org/slf4j/impl/StaticLoggerBinder.class\]

SLF4J: Found binding in \[jar:file:/Users/didi/kafka/server1/kafka\_2.10-0.8.2.1/libs/slf4j-log4j12-1.6.1.jar!/org/slf4j/impl/StaticLoggerBinder.class\]

SLF4J: See http://www.slf4j.org/codes.html\#multiple\_bindings for an explanation.

SLF4J: Actual binding is of type \[org.slf4j.impl.Log4jLoggerFactory\]

Created topic "Multibrokerapplication".

$server1/kafka\_2.10-0.8.2.1/bin/kafka-topics.sh --describe --zookeeper localhost:2181 --topic Multibrokerapplication

SLF4J: Class path contains multiple SLF4J bindings.

SLF4J: Found binding in \[jar:file:/Users/didi/hbase/hbase/lib/slf4j-log4j12-1.7.5.jar!/org/slf4j/impl/StaticLoggerBinder.class\]

SLF4J: Found binding in \[jar:file:/Users/didi/kafka/server1/kafka\_2.10-0.8.2.1/libs/slf4j-log4j12-1.6.1.jar!/org/slf4j/impl/StaticLoggerBinder.class\]

SLF4J: See http://www.slf4j.org/codes.html\#multiple\_bindings for an explanation.

SLF4J: Actual binding is of type \[org.slf4j.impl.Log4jLoggerFactory\]

Topic:Multibrokerapplication	PartitionCount:1	ReplicationFactor:2	Configs:

	Topic: Multibrokerapplication	Partition: 0	Leader: 0	Replicas: 0,1	Isr: 0,1

$ kafka/server1/kafka\_2.10-0.8.2.1/bin/kafka-console-producer.sh --broker-list localhost:9092 --topic Multibrokerapplication

\[2017-08-16 21:41:44,874\] WARN Property topic is not valid \(kafka.utils.VerifiableProperties\)

SLF4J: Class path contains multiple SLF4J bindings.

SLF4J: Found binding in \[jar:file:/Users/didi/hbase/hbase/lib/slf4j-log4j12-1.7.5.jar!/org/slf4j/impl/StaticLoggerBinder.class\]

SLF4J: Found binding in \[jar:file:/Users/didi/kafka/server1/kafka\_2.10-0.8.2.1/libs/slf4j-log4j12-1.6.1.jar!/org/slf4j/impl/StaticLoggerBinder.class\]

SLF4J: See http://www.slf4j.org/codes.html\#multiple\_bindings for an explanation.

SLF4J: Actual binding is of type \[org.slf4j.impl.Log4jLoggerFactory\]

This is single node-multi broker demo

This is the second message

     test

$server1/kafka\_2.10-0.8.2.1/bin/kafka-console-consumer.sh --zookeeper localhost:2181 --topic Multibrokerapplication --from-beginning

SLF4J: Class path contains multiple SLF4J bindings.

SLF4J: Found binding in \[jar:file:/Users/didi/hbase/hbase/lib/slf4j-log4j12-1.7.5.jar!/org/slf4j/impl/StaticLoggerBinder.class\]

SLF4J: Found binding in \[jar:file:/Users/didi/kafka/server1/kafka\_2.10-0.8.2.1/libs/slf4j-log4j12-1.6.1.jar!/org/slf4j/impl/StaticLoggerBinder.class\]

SLF4J: See http://www.slf4j.org/codes.html\#multiple\_bindings for an explanation.

SLF4J: Actual binding is of type \[org.slf4j.impl.Log4jLoggerFactory\]

This is single node-multi broker demo

This is the second message

     test

