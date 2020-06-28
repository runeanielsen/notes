# Kafka

## Introduction

Kafka is changing the standard for data platforms. It is leading the way to move from Batch and ETL workflows tothe near real-time data feeds.

Kafka is starting to make a push into microservice design. Kafka is touching a lot of the newest and most practical trends in today's IT fields.

Kafka provides the ability to publish/subscribe to records like a message queue, store records with fault-tolerance, and process streams as they occur.

Kafka has the concept of sending data from various sources of information this is called a Producer. In addtion, Kafka allows multiple output channels that are enabled by Consumers. Receivers can be thought of as message brokers themselves that can handle real-time stream of messages.

Kafka acts as a middle ma to data coming into the system from producers and out of the system by consumers. The producer can send whatever messages it wants and have no idea about if anyone is subscribed.


## Messaging options

Kafka has various ways it can deliever messages. Kafka message delivery can take at lest the following three delivery methods.

* At least once semantics
* At most once semantics
* Exactly once semantics

### At least once

Kafka default guarantee is at least once semantics. This means that Kafka can be configured to allow for a producer of messages to send the same message more than once and have it written to the brokers.

When a message has not received a guarantee that is was written to the broker, the producer can send the message again in order to try again. This is useful for those cases where you can't miss a message.

The guarantee might require filtering on the consumer end, but is one of the safest methods for delivery.

### At most once

Most once semantics are when a producer of messages might send a message once and never retries. In the event of a failure, the producer moves on and never attemps to send again. This can be useful for performance focused systems where it is okay to loss a few events if it means gaining performance by not having to wait for acknowledgements. 

### Extactly once 

Exactly once is a new addition to the Kafka feature set. In the context of a Kafka system, if a producer sends a message more than once, it would be delivered once to the end consumer. Exactly once semantics has touch points at all layers of Kafka, from producers, topics, brokers, and consumers. 



## Thanks to

[Kafka in Action By Dylan Scott](https://www.manning.com/books/kafka-in-action)
