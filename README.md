### 1. What is amqp?

AMQP (Advanced Message Queuing Protocol) is an open standard network protocol for message-oriented middleware. It defines how messages are formatted, sent, and received between applications through a message broker (like RabbitMQ). It ensures messages are reliably delivered between producers and consumers regardless of what programming language or platform they use.

### 2. What does it mean? guest:guest@localhost:5672 , what is the first guest, and what is the second guest, and what is localhost:5672 is for?

First guest: The username used to authenticate with the RabbitMQ broker.
Second guest: The password for that username.
localhost: The host address where RabbitMQ is running. In this case, it's on the same machine as our program.
5672: The port that RabbitMQ listens on for AMQP connections.

### 3. How much data your publisher program will send to the message broker in one run?

The publisher sends 5 events in one run, one for each publish_event call. Each event is a UserCreatedEventMessage containing two fields; a user_id and a user_name. So, in total, it publishes:
- user_id: "1", user_name: "2406495432-A"
- user_id: "2", user_name: "2406495432-B"
- user_id: "3", user_name: "2406495432-C"
- user_id: "4", user_name: "2406495432-D"
- user_id: "5", user_name: "2406495432-E"

Each message is very small so the total data sent per run is roughly only a few hundred bytes in total after serialization via Borsh.

### 4. The url of: “amqp://guest:guest@localhost:5672” is the same as in the subscriber program, what does it mean?

It means both the publisher and subscriber are connecting to the same RabbitMQ broker at the same address. The publisher uses it to send events to the broker and the subscriber uses it to listen for events from that same broker. Neither program talks directly to the other. The broker in the middle is what receives, stores, and forwards the messages. This is the core idea of event-driven architecture. The publisher and subscriber are completely independent and only coupled through the shared broker.

### 5. RabbitMQ

![RabbitMQ](./assets/rabbitmq.png)
![RabbitMQ Logged In](./assets/rabbitmq_loggedin.png)

### 5. Event

![RabbitMQ](./assets/rabbitmq_2.png)
![Publisher](./assets/publisher_1.png)
![Subscriber](./assets/subscriber_1.png)
