### Why is Apache Kafka fast?
* sequential I/O instead of random access I/O.  Append only operation.  This reduces the number of arm movement in HDD. 
* zero copy. see https://en.wikipedia.org/wiki/Zero-copy
credit from bytebytego video

### distributed streaming platform
distributed event requires a different way of thinking to captures messages.  The current way of thinking is we start all the data in the database.  With streaming platform, the process is changed to event driven architecture.  All the incoming messages are stored in topics, ready for further processing.  This means the processing can be done in real time.

* event streaming platform for massive volumes of big data analytics and small volumes of transactional data processing.
* a data integration framework for streaming ETL.

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

### When not to use Apache Kafka
* https://pandio.com/top-10-problems-when-using-apache-kafka/
* https://www.kai-waehner.de/blog/2022/01/04/when-not-to-use-apache-kafka/


### tutorial
* https://blog.csdn.net/ddonking/article/details/81912250?ops_request_misc=&request_id=&biz_id=102&utm_term=apache%2520kafka&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduweb~default-0-81912250.nonecase
