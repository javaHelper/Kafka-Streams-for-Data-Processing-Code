#

````sh
kafka-console-producer --bootstrap-server localhost:9092 --topic word-count-input
>hello java
>java spring
>spring unix
>john unix
>
````

````sh
kafka-console-consumer --bootstrap-server localhost:9092 \
--topic word-count-output \
--from-beginning \
--formatter kafka.tools.DefaultMessageFormatter \
--property print.key=true \
--property print.value=true \
--property key.deserializer=org.apache.kafka.common.serialization.StringDeserializer \
--property value.deserializer=org.apache.kafka.common.serialization.LongDeserializer
unix	2
hello	1
java	2
spring	2
john	1
````