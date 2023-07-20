

## What is Kafka?

Kafka is a distributed streaming platform that is used to publish and subscribe to streams of records/events. It stores streams of records in categories called topics. 

## What are some key features of Kafka?

- Distributed and fault tolerant
- High throughput for publishing and subscribing 
- Storage of streams of records in categories called topics
- Messages are persisted on disk and replicated
- Horizontally scalable

## What are Kafka topics, partitions, and offsets?

- Topics: Categories or feed names to which records are published 
- Partitions: Topics are split into partitions for scalability. Each partition is an ordered and immutable sequence of records.
- Offsets: Each record in a partition is assigned a unique offset.

## What is a Kafka broker? 

A Kafka cluster is composed of multiple brokers or servers. Kafka brokers are stateless, so they use Zookeeper for coordinating. The brokers are responsible for maintaining the published data.

## What is a Kafka producer?

Producers publish data to Kafka topics. Producers send data to Kafka brokers which eventually store it as partitions.

## What is a Kafka consumer?

Consumers subscribe to Kafka topics and consume published messages. Consumer pull data using a poll loop and track the offsets of records consumed.

## How does Kafka provide high availability and fault tolerance?

Kafka replicates data and distributes it across brokers. A topic should have a replication factor > 1 (usually between 2-3). This way if a broker is down, another broker can serve the data ensuring high availability.

Kafka can sustain node failures and rebalance partitions across brokers. Consumers use group ids and keep track of offsets to enable fault tolerance.

## What is Kafka Zookeeper and its role?

Zookeeper serves as the coordination interface between the Kafka brokers and consumers. It provides distributed synchronization and maintains broker metadata information like which partitions exist, which broker is the leader for a partition etc.

## What are some use cases for Kafka?

- Messaging
- Activity Tracking
- Gathering Metrics 
- Log Aggregation
- Stream Processing
- Decoupling of systems