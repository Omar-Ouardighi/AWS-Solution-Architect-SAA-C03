- Unlimited throughput, unlimited number of messages in queue
- Default retention of messages: 4 days, maximum of 14 days
- • Low latency (<10 ms on publish and receive)
- Limitation of 256KB per message sent
- Can have duplicate messages (at least once delivery, occasionally) 
- Can have out of order messages (best effort ordering)

Encryption: • In-flight encryption using HTTPS API • At-rest encryption using KMS keys • Client-side encryption if the client wants to perform encryption/decryption itself

## SQS – Message Visibility Timeout
- After a message is polled by a consumer, it becomes invisible to other consumers 
- By default, the “message visibility timeout” is 30 seconds 
- That means the message has 30 seconds to be processed •
- After the message visibility timeout is over, the message is “visible” in SQS
## Long Polling
- When a consumer requests messages from the queue, it can optionally “wait” for messages to arrive if there are none in the queue 
- This is called Long Polling
- LongPolling decreases the number of API calls made to SQS while increasing the efficiency and reducing latency of your application 
- The wait time can be between 1 sec to 20 sec (20 sec preferable)

## FIFO Queue
- Limited throughput: 300 msg/s without batching, 3000 msg/s with 
- Exactly-once send capability (by removing duplicates) 
- Messages are processed in order by the consumer

![[Screenshot 2025-03-07 171423.png]]![[Screenshot 2025-03-07 174423.png]]![[Screenshot 2025-03-07 174446.png]]