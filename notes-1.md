
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


# why do we need Kafka?

Imagine you have two applications, let’s call them App1 and App2. When App1 needs to send a message to App2, it can be a problem if App2 is not available at that moment. In such cases, the message might be lost in transit.

However, Kafka comes to the rescue. When App1 sends a message to App2 via Kafka, even if App2 isn’t ready to receive it immediately, Kafka stores the message safely. When App2 becomes available, it can retrieve the message from Kafka. This ensures that no data gets lost in the process.

Kafka is necessary when your application is large or complex, with many servers connected to each other. Communicating in such a scenario can be challenging. There are several challenges to address, such as data formatting complexity, connection types, and the high number of connections.

- **Data Formatting Complexity:-** In big applications, you often deal with various types of data in different formats or schemas. Managing this complexity can be challenging.

- **Connection Types:-** These applications use different types of connections, like HTTP, JDBC, TCP, and more. Coordinating and managing these diverse connections across various services can be quite complex.

- **Number of Connections:**- When you have multiple servers connecting to each other, the number of connections can explode quickly. For example, if one server is connected to five others, and you have four such servers, you’re dealing with 20 connections to manage.
   ![image](https://github.com/vinosubi/Kafka-Notes-1/assets/133937082/d519fbbc-d30f-4b8f-87d3-2abc64243c03)

    Without Kafka complexity


But Kafka simplifies everything. Senders can use any type of data or connection (like HTTP, TCP, JDBC) to Kafka. Kafka securely stores the data. Receivers can then retrieve the data from Kafka. This simplifies communication and reduces the number of connections required.

![image](https://github.com/vinosubi/Kafka-Notes-1/assets/133937082/88ea3b77-31c8-469f-85f5-8d11c540b79a)
                                                Add Kafka between servers for communication



# How does Kafka work?

Kafka operates on a Pub/Sub (Publisher-Subscriber) model. It functions as a communication system that enables different parts of a computer system to exchange data through the publication and subscription to topics. Here’s how it works:-

Imagine Kafka as a central hub for messages and data.
When a sender (the publisher) wants to send a message, it publishes it on a specific topic.
The receiver (the subscriber) is interested in that topic and subscribes to it.
Once subscribed, the receiver can directly receive the messages sent to that topic.
Kafka Architecture and Its Components

Kafka’s architecture consists of nine key components.

**1. Producer:-** The producer’s role is to create and send messages, essentially publishing them to Kafka.

**2. Consumer:-** Consumers are responsible for receiving and processing messages or events.

**3. Broker:-** Brokers act as intermediaries between producers and consumers. They facilitate message exchange, ensuring messages reach their intended recipients.

  ![image](https://github.com/vinosubi/Kafka-Notes-1/assets/133937082/ad7b16b1-484a-422d-9020-6a541dd895b8)
                                   Process of producer, consumer, and broker

**4. Cluster:-** A Kafka cluster is a group of computers or servers working together for a common purpose. Since Kafka is a distributed system, a Kafka cluster includes multiple Kafka servers or brokers. There can be one or more brokers in a Kafka cluster. This clustering ensures scalability and fault tolerance. For instance, if one broker can’t handle all the data produced, another can take over.
                                    ![image](https://github.com/vinosubi/Kafka-Notes-1/assets/133937082/64831ea5-f7a0-43ee-9465-421d11d73149)
                                   Kafka Cluster

**5. Topic:-** A Kafka topic serves as a named channel or category where messages are published by producers and consumed by consumers. Topics are used to organize and categorize data within a Kafka cluster. They are identified by names, which are strings. Producers publish messages to specific topics, and consumers subscribe to one or more topics to consume messages.
                                       ![image](https://github.com/vinosubi/Kafka-Notes-1/assets/133937082/d788331c-26bc-4ef6-9f11-384d18795a7b)
                                       Kafka Topic


**6. Partitions:-** Producers send data to brokers, and brokers store messages on different topics. If a producer generates a massive amount of data in a short time, a single topic may struggle to handle it. Kafka addresses this by dividing topics into partitions and distributing these partitions across multiple machines. This concept is known as topic partitioning, and each part is called a partition. The number of partitions for a topic can be decided when creating it.

  ![image](https://github.com/vinosubi/Kafka-Notes-1/assets/133937082/044934c9-2e73-4d94-a903-947bdc5d411f)
                                        Topic partition


**7. Offset:-** When a producer sends data to a broker, the data goes to a specific partition. The partition assigns a unique sequence number, called an offset, to each message. Offset helps consumers keep track of which messages they have consumed and where to resume consumption. For example, if a consumer reads messages 0 to 3 and then stops, it knows to start reading from the 4th offset when it resumes.

   ![image](https://github.com/vinosubi/Kafka-Notes-1/assets/133937082/0844775d-679e-4cef-8be8-9c35b936b1c6)
                                        Offsets

**8. Consumer Groups:-** Since there can be many partitions, a single consumer may not handle all of them efficiently. That’s why Kafka employs consumer groups. These groups consist of multiple consumer instances that work together. They share the workload and read from different partitions in parallel, improving throughput.
                                   ![image](https://github.com/vinosubi/Kafka-Notes-1/assets/133937082/dadf1f38-e57a-4ccb-a8b8-a731f6cde164)
                                    Consumer groups


                                    
**9. Zookeeper:-** A zookeeper is a crucial component in the Kafka ecosystem. Kafka is a distributed system, and it relies on Zookeeper for coordination and tracking of the status of Kafka cluster nodes. Zookeeper also keeps track of Kafka topics, partitions, offsets, and more. In essence, Zookeeper serves as the manager for your Kafka cluster and brokers.
                                         ![image](https://github.com/vinosubi/Kafka-Notes-1/assets/133937082/e37f690c-be27-4ead-8180-7c792822bb4d)
                                         Zookeeper

Kafka’s architecture and components work in harmony to ensure efficient, reliable, and scalable data streaming and processing.

