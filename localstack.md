LocalStack is a nice way to test AWS functionality locally.

### Caveat

Localstack does not work in Microsoft Windows, and it needs to be run in Unix system.  Furthermore, it had Python, Maven, nodejs, and Java as requirement. Latest version expect the user to run it in docker.

I had downloaded an old version of the localstack in 2019, and run it on Fatdog Linux.  I preferred to run it in host mode instead of inside docker.  When I install it, the python files are installed in */usr/lib/python2.7/site-packages/localstack*

Here are some of the changes I run into to resolve the issues I to run in Linux host. 

1. update the PATH for java and maven, as dynamo, elasticmq, and a few others depend to you.
... *PATH=$PATH:/opt/java/bin:/opt/maven/bin

2. It complains the DynamoDBLocal.jar is corrupted. *Error: Invalid or corrupt jarfile DynamoDBLocal.jar*
... I solved the issue by downloading the zip file in *https://s3.us-west-2.amazonaws.com/dynamodb-local/dynamodb_local_latest.zip*
... Extract the zip, and copy the DynamoDBLocal.jar to */usr/lib/python2.7/site-packages/localstack/infra/dynamodb*

3. Unable to access Elastic-mq server
... Go to AWS and download the jar file.  I downloaded *elasticmq-server-0.15.7.jar* and copy it to the directory */usr/lib/python2.7/site-packages/localstack/infra/elasticmq*. Be sure to rename it to elasticmq-server.jar

4. Unable to access StepFunctionsLocal.jar
... Go to AWS and download the StepFunctionsLocal.tar.gz and expand the contents in the directory */usr/lib/python2.7/site-packages/localstack/infra/stepfunctions*

5. ElasticSearch failed with a JNI error.
... Complains *Exception in thread "main" java.lang.NoClassDefFoundError: org/eclipse/jetty/server/handler/AbstractHandler*
... Looks like it can't find the AbstractHandler. Found the *jetty-server-8.1.12.v20130726.jar* in the stepfunctions directory and copy it to */usr/lib/python2.7/site-packages/localstack/infra/elasticsearch/lib* Don't know is this the correct way, but the exception disappears.

6. ElasticSearch complains it runs as root, as Puppy Linux and Fatdog Linux is the way it is.  I tried to run it as spot instead. Spot had less priviledge and then it complains it can't write to the temp file. After further digging,
... modify the jvm.options, and change the -Djava.io.tmpdir value. I changed it to */home/spot/localstacktmp*, and create such directory.  
... Another issue is the elasticsearch is owned by root. I used the command chown -R spot:spot for the entire directory, so it is owned by spot from now on.

7. Another elastic search is it complains about the tmp directory.
...[o.e.b.ElasticsearchUncaughtExceptionHandler] [5uBgEsm] uncaught exception in thread [main]
org.elasticsearch.bootstrap.StartupException: ElasticsearchException[Failed to create native process factories for Machine Learning]; nested: FileNotFoundException[/tmp/elasticsearch-2623876071252029113/controller_log_29465 (No such file or directory)];
...After some google digging, I don't think I mean machine learning, and go to elasticsearch.yml and add the line *xpack.ml.enabled: false*


Finally, I got it runnning.

### TODO

1. Turn it into a squashfs file so it can be loaded easily.
2. Spend more time to learn how to boto works.






