LocalStack is a nice way to test AWS functionality locally.

### Caveat

Localstack does not work in Microsoft Windows, and it needs to be run in Unix system.  Furthermore, it had Python, Maven, and Java as requirement. Latest version expect the user to run it in docker.

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



