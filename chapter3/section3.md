# 问题

Exception in thread "main" org.apache.kafka.common.config.ConfigException: Missing required configuration "partition.assignment.strategy" which has no default value.

解决

props.put\("partition.assignment.strategy", "range"\);



