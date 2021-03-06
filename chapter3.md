#  Kafka 工具

Kafka在“org.apache.kafka.tools。"下打包的工具。工具分为系统工具和复制工具。

## 系统工具

可以使用运行类脚本从命令行运行系统工具。语法如下 -

```
bin/kafka-run-class.sh package.class - - options

```

下面提到一些系统工具 -

* **Kafka迁移工具**- 此工具用于将代理从一个版本迁移到另一个版本。

* **Mirror Maker**- 此工具用于向另一个Kafka集群提供镜像。

* **消费者偏移检查器**- 此工具显示指定的主题和使用者组的消费者组，主题，分区，偏移量，日志大小，所有者。

## 复制工具“

Kafka复制是一个高级设计工具。添加复制工具的目的是为了更强的耐用性和更高的可用性。下面提到一些复制工具 -

* **创建主题工具**- 这将创建一个带有默认分区数，复制因子的主题，并使用Kafka的默认方案进行副本分配。

* **列表主题工具**- 此工具列出了指定主题列表的信息。如果命令行中没有提供主题，该工具将查询Zookeeper以获取所有主题并列出它们的信息。工具显示的字段是主题名称，分区，leader，replicas，isr。

* **添加分区工具**- 创建主题，必须指定主题的分区数。稍后，当主题的卷将增加时，可能需要用于主题的更多分区。此工具有助于为特定主题添加更多分区，还允许手动复制分配已添加的分区。

  




