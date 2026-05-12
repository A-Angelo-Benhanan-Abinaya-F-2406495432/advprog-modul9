### 1. What is amqp?

AMQP (Advanced Message Queuing Protocol) is an open standard network protocol for message-oriented middleware. It defines how messages are formatted, sent, and received between applications through a message broker (like RabbitMQ). It ensures messages are reliably delivered between producers and consumers regardless of what programming language or platform they use.

### 2. What does it mean? guest:guest@localhost:5672 , what is the first guest, and what is the second guest, and what is localhost:5672 is for?

First guest: The username used to authenticate with the RabbitMQ broker.
Second guest: The password for that username.
localhost: The host address where RabbitMQ is running. In this case, it's on the same machine as our program.
5672: The port that RabbitMQ listens on for AMQP connections.