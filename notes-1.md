
### Kafka Basics and Core concepts
![image](https://github.com/vinosubi/Kafka-Notes-1/assets/133937082/23b21eee-e768-4bf3-9a13-a05ff528f092)

### Introduction
Let’s start by answering the question **“What is Kafka?”.**

Kafka is a Distributed Streaming Platform or a Distributed Commit Log

### Distributed
Kafka works as a cluster of one or more nodes that can live in different Datacenters, we can distribute data/ load across different nodes in the Kafka Cluster, and it is inherently scalable, available, and fault-tolerant.

### Streaming Platform
Kafka stores data as a stream of continuous records which can be processed in different methods.

### Commit Log
This one is my favorite. When you push data to Kafka it takes and appends them to a stream of records, like appending logs in a log file or if you’re from a Database background like the WAL. This stream of data can be “Replayed” or read from any point in time.
