Authors:
- Lukasz Matyasik
- Eugene Sudakov

### Example of Direct Communication (Client-Server):

1. As a sender:
```bash
   java -cp .:amqp-client-5.16.0.jar:slf4j-api-1.7.36.jar:slf4j-simple-1.7.36.jar sent
```

2. As a receiver:
```bash
java -cp .:amqp-client-5.16.0.jar:slf4j-api-1.7.36.jar:slf4j-simple-1.7.36.jar recv
```

### Example of Ping-Pong Communication:

1. To queue a task:
```bash
   java -cp .:amqp-client-5.16.0.jar:slf4j-api-1.7.36.jar:slf4j-simple-1.7.36.jar NewTask Message.....
```
2. Worker class (open in at least two terminals to observe ping-pong behavior):
```bash
java -cp .:amqp-client-5.16.0.jar:slf4j-api-1.7.36.jar:slf4j-simple-1.7.36.jar Worker
```

In the Worker class, a task has been simulated. Each time a dot is detected, working time will be simulated by Thread.sleep. The communication in this example is acknowledged, which means if the work is disrupted (consumer dead), the work will be transferred to another consumer. After acknowledging the finished task, the message will be deleted from the queue.

### Example of Publish-Subscribe:
1. To simulate log:
```bash
java -cp .:amqp-client-5.16.0.jar:slf4j-api-1.7.36.jar:slf4j-simple-1.7.36.jar EmitLog Someloog
```
2. Receive logs (open as many ReceiveLogs instances as needed; logs will be received by all consumers):
```bash
java -cp .:amqp-client-5.16.0.jar:slf4j-api-1.7.36.jar:slf4j-simple-1.7.36.jar ReceiveLogs
```
