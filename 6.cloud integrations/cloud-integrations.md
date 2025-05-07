# cloud integrations
When we have multiple applications deployed, at some other point they need to communicate with each other

There are 2 types of communications

1.**Synchronous communication** (application to application)
2.**aSynchronous communication** (application to queue to application)

## SQS (simple queue service) (FIFO)

* fully managed service(**serverless**) used to **decouple** applications

* Default retention of messages: 4 days, max of 14 days

* no limit how many messages can be in queue

* Messages are deleted after they are read by consumers

* low latency

  ## Amazon kinesis data streams
  * Kinesis is a managed service to collect, process and analyze realtime bigdata streaming

## SNS (Simple notification service)
* only "event publishers" send messages to one SNS topic
  
* many "event subscribers" as we want to listen to SNS topic notifications

  * SNS  can have many subscribers that might be SQS,Lambda, emails, SMS & mobile notifications,http/s endpoints

