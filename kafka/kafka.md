# Kafka

Kafka is changing the standard for data platforms. It is leading the way to move from Batch and ETL workflows tothe near real-time data feeds.

Kafka is starting to make a push into microservice design. Kafka is touching a lot of the newest and most practical trends in today's IT fields.

## Introduction

Kafka provides the ability to publish/subscribe to records like a message queue, store records with fault-tolerance, and process streams as they occur.

Kafka has the concept of sending data from various sources of information this is called a Producer. In addtion, Kafka allows multiple output channels that are enabled by Consumers. Receivers can be thought of as message brokers themselves that can handle real-time stream of messages.

Kafka acts as a middle ma to data coming into the system from producers and out of the system by consumers. The producer can send whatever messages it wants and have no idea about if anyone is subscribed.


### Messaging options

Kafka has various ways it can deliever messages. Kafka message delivery can take at lest the following three delivery methods.

* At least once semantics
* At most once semantics
* Exactly once semantics

#### At least once

Kafka default guarantee is at least once semantics. This means that Kafka can be configured to allow for a producer of messages to send the same message more than once and have it written to the brokers.

When a message has not received a guarantee that is was written to the broker, the producer can send the message again in order to try again. This is useful for those cases where you can't miss a message.

The guarantee might require filtering on the consumer end, but is one of the safest methods for delivery.


[Kafka in Action By Dylan Scott](https://www.manning.com/books/kafka-in-action)
