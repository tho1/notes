https://blog.csdn.net/ddonking/article/details/81912250?ops_request_misc=&request_id=&biz_id=102&utm_term=apache%2520kafka&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-81912250.nonecase


### distributed streaming platform


### some commands 

* ```zkServer.sh start``` - start zookeeper 
* ```kafka-server-start.sh config/server.properties``` - start kafka
* ```gps | grep Kafka``` check the Kafka process is running

### terminology 
* cluster - contain multiple topics
* topics - contain multiple partition
* batch - collecteion of messages produced for the same partition and topic. Sometimes  compressed together
* message - contain key and body
* producer
* consumer
* brokers - part of a cluster, and one of the broker acts as cluster controller
* stream - a single topic store certain class of data.


### Kafka cheat sheets
* https://github.com/naveen1512/apache-kafka-commands-cheat-sheet
* https://github.com/lensesio/kafka-cheat-sheet
* https://gist.github.com/alexnoz/5aaa7446374a2aca4302968fc69e08fd
* https://gist.github.com/sahilsk/d2a6ec384f5f2333e3fef40a581a97e1
