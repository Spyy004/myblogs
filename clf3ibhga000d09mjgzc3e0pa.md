---
title: "Message Queues Made Easy: A Beginner's Guide to Application Communication"
seoTitle: "Message Queues Made Easy: A Beginner's Guide to Application"
seoDescription: "Today in the system design series, we will learn about message queues. Message queues are one of the most important parts of a highly scaled-and"
datePublished: Sat Mar 11 2023 05:09:08 GMT+0000 (Coordinated Universal Time)
cuid: clf3ibhga000d09mjgzc3e0pa
slug: message-queues-made-easy-a-beginners-guide-to-application-communication
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1678511277719/f839ba23-d00f-4261-b1f8-c427264bcd54.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1678511311998/6896578f-81ce-482f-b0f9-e1ec2932e2d9.png
tags: tutorial, programming, beginners, system-architecture, system-design

---

# Introduction

Welcome back! Today in the system design series, we will learn about message queues. Message queues are one of the most important parts of a highly scaled-and successful system. So let's explore what is a message queue, how is it implemented, where is it implemented, and one real-life example of the same.

# What is a message queue?

In simple terms, a message queue is used to achieve asynchronous communication between multiple systems or different instances of a single system.

For example, if machine A needs to send a request to machine B, the request will first land on the message queue and sit on it. Machine B must retrieve this request from the message queue, execute the request and then send back the response to machine A. Once this is done, the request is then popped from the message queue.

Apache Kafka, Rabbit MQ, and Amazon Simple Queue service are some of the major message queue services.

![A comparison of popular message queues | Better Engineering Blog](https://better.engineering/static/2772f41f7aaff4e240def8ce7ed29f44/31493/message_queue.png align="left")

# In-memory or databases?

A message queue can be implemented in memory or databases as well. There are pros and cons to both and it depends on the use case.

In-memory message queues are typically faster than database-backed message queues because they don't require disk I/O operations. This can make them a good choice for applications that need to process messages very quickly or handle high message volumes.

In-memory message queues are also often simpler to set up and manage, as they don't require an external data store. However, they are less durable, as messages are not in a persistent space. If the server crashes, then everything in the message queue is gone.

On the other hand, database-backed message queues are typically slower than in-memory message queues due to disk I/O operations. However, they are more durable, as messages are stored in a persistent data store and can be retrieved even if the application or server crashes. This makes them a good choice for applications that require high message durability, or that handle sensitive data.

Which one is more scalable? The database one. Why? THINK.

# Real-Life Example

Let's say you have an e-commerce website that sells products to customers. When a customer makes a purchase, you need to process their order and update your inventory system to reflect the fact that you've sold one of your products.

To handle this scenario, you might use message queues in the following way:

1. When a customer makes a purchase, your website's order processing application sends a message to a message queue that contains the order details.
    
2. The message queue then stores the order message until it can be processed.
    
3. Your inventory management application pulls messages from the message queue one at a time and updates your inventory system to reflect the fact that a product has been sold.
    
4. Once the message has been processed, it's removed from the message queue.
    

By using a message queue in this scenario, you're decoupling the order processing and inventory management systems, which makes them more scalable and reliable. If one of the systems fails, the messages will still be stored in the message queue until the system is back up and running, ensuring that no orders or inventory updates are lost.

![Microservice Architecture Best Practices: Messaging Queues - DZone](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSedwTnEPM_P3aS6ClTExnTI2w23UoI2TNlpg&usqp=CAU align="left")

# Pros & Cons of a Message Queue

### Pros

1. Scalability: Message queues allow you to build scalable applications by decoupling the components of your application. This means you can add more consumers to process messages as your application grows.
    
2. Reliability: Message queues provide a reliable way to communicate between components of your application. Messages are stored in the queue until they can be processed, which means they won't be lost if a component of your application fails.
    
3. Asynchrony: Message queues enable asynchronous communication between components of your application. This means that components can communicate with each other without having to wait for a response, which can improve the overall performance of your application.
    

Cons

1. Increased complexity: Using a message queue can add complexity to your application, as it introduces an additional layer of abstraction that must be managed and monitored.
    
2. Higher latency: While message queues can improve system scalability and reliability, they can also introduce additional latency to message processing. This is because messages must be written to the queue and then read and processed by a consumer, which can take time.
    

# Conclusion

So that was it. A message queue is a great tool that can be added to your system which will help you in scaling your system and handling a lot of asynchronous tasks efficiently. By using best practices and carefully considering the pros and cons of message queues, you can build a robust and reliable messaging architecture for your distributed application.

I hope you learned something new today! Follow CSWithIyush for more such articles on various topics that I keep on learning.