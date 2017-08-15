# Kafka 集群架构



看看下面的插图。它显示Kafka的集群图。

![](https://www.w3cschool.cn/attachments/tuploads/apache_kafka/cluster_architecture.jpg "Cluster Architecture")

下表描述了上图中显示的每个组件。

| S.No | 组件和说明 |
| :--- | :--- |
| 1 | **Broker（代理）** Kafka集群通常由多个代理组成以保持负载平衡。Kafka代理是无状态的，所以他们使用ZooKeeper来维护它们的集群状态。一个Kafka代理实例可以每秒处理数十万次读取和写入，每个Broker可以处理TB的消息，而没有性能影响。Kafka经纪人领导选举可以由ZooKeeper完成。 |
| 2 | **ZooKeeper**ZooKeeper用于管理和协调Kafka代理。ZooKeeper服务主要用于通知生产者和消费者Kafka系统中存在任何新代理或Kafka系统中代理失败。根据Zookeeper接收到关于代理的存在或失败的通知，然后产品和消费者采取决定并开始与某些其他代理协调他们的任务。 |
| 3 | **Producers（生产者**）生产者将数据推送给经纪人。当新代理启动时，所有生产者搜索它并自动向该新代理发送消息。Kafka生产者不等待来自代理的确认，并且发送消息的速度与代理可以处理的一样快。 |
| 4 | **Consumers（消费者**）因为Kafka代理是无状态的，这意味着消费者必须通过使用分区偏移来维护已经消耗了多少消息。如果消费者确认特定的消息偏移，则意味着消费者已经消费了所有先前的消息。消费者向代理发出异步拉取请求，以具有准备好消耗的字节缓冲区。消费者可以简单地通过提供偏移值来快退或跳到分区中的任何点。消费者偏移值由ZooKeeper通知。 |

  


