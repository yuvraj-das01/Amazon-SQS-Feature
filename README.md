# Amazon-SQS-Feature

Amazon Simple Queue Service (Amazon SQS) offers a secure, durable, and available hosted queue that lets you integrate and decouple distributed software systems and components.It’s a web service that gives you access to a message queue that can be used to store messages while waiting for a computer to process them.
Key Points to remember
SQS was the first service available in AWS.
Any component of an application can later retrieve the messages programmatically using the Amazon SQS API.
Amazon SQS is a distributed queue system that enables web service applications to quickly and reliably queue messages that one component in the application generates to be consumed by another component where a queue is a temporary repository for messages that are awaiting processing.
Amazon SQS offers two queue types for different application requirements:
Standard Queues
Unlimited Throughput: Standard queues support a nearly unlimited number of transactions per second (TPS) per API action.
At-Least-Once Delivery: A message is delivered at least once, but occasionally more than one copy of a message is delivered.
Best-Effort Ordering: Occasionally, messages might be delivered in an order different from which they were sent.

fig 1: Standard Queue
2. FIFO Queues

fig 2: FIFO Queue
Exactly-Once Processing: A message is delivered once and remains available until a consumer processes and deletes it. Duplicates aren’t introduced into the queue.
First-In-First-Out Delivery: The order in which messages are sent and received is strictly preserved (i.e. First-In-First-Out).
High Throughput: If you use batching, FIFO queues support up to 3,000 transactions per second, per API method (SendMessageBatch, ReceiveMessage, or DeleteMessageBatch). The 3000 transactions represent 300 API calls, each with a batch of 10 messages. To request a quota increase, submit a support request. Without batching, FIFO queues support up to 300 API calls per second, per API method (SendMessage ,RecieveMessage, or DeleteMessage).
Amazon SQS visibility timeout
When a consumer receives and processes a message from a queue, the message remains in the queue. Amazon SQS doesn’t automatically delete the message. Because Amazon SQS is a distributed system, there’s no guarantee that the consumer actually receives the message(eg:due to a connectivity issue,consumer application or anything else)Thus, the consumer must delete the message from the queue after receiving and processing it.
Immediately after a message is received, it remains in the queue. To prevent other consumers from processing the message again, Amazon SQS sets a visibility timeout (default:30sec,min.:0 sec,max.:12hrs), a period of time during which Amazon SQS prevents other consumers from receiving and processing the message.
What about RabbitMQ??

fig 3 : Image of RabbitMQ
RabbitMQ is a popular open source message broker. It offers all of the same functionality as SQS and more: for example, it supports various authentication mechanisms for RabbitMQ queues, provides the option of using “lazy queues” that can handle a backlog of millions of messages, and supports queue protocols like JMS and AMQP.
Difference between Amazon SQS and RabbitMQ
Compared to SQS, RabbitMQ’s performance can be better, especially at high loads, and RabbitMQ is also more configurable and flexible. At the same time, RabbitMQ is a self-hosted solution that you need to deploy and maintain yourself. SQS has fewer features and is less flexible but is a fully managed solution.
If your queue system is something you plan to heavily rely on in your infrastructure, and if you are going to require very fast performance from it at very high queue loads, it may be worth hosting your own RabbitMQ installation. Go with SQS if you’re looking to have the queue system managed for you and are OK with fewer features and slightly higher latency in queue operations.
BMW Case Study

fig 4 : Logo of BWM
The BMW Group is using AWS for its new connected-car application that collects sensor data from BMW 7 Series cars to give drivers dynamically updated map information. BMW Group is one of the leading manufacturers of premium cars and mobility services in the world, with brands such as Rolls Royce, BMW, and Mini. BMW built its new car-as-a-sensor (CARASSO) service in only six months leveraging Amazon Simple Storage Service (Amazon S3), Amazon Simple Queue Service (Amazon SQS), Amazon DynamoDB, Amazon Relational Database Service (Amazon RDS), and AWS Elastic Beanstalk. By running on AWS, CARASSO can adapt to rapidly changing load requirements that can scale up and down by two orders of magnitude within 24 hours. By 2018 CARASSO is expected to process data collected by a fleet of 100,000 vehicles traveling more than eight billion kilometers.
RedBus Case Study

fig 5: Redbus logo
RedBus is an Indian travel agency that specializes in bus travel throughout India by selling bus tickets throughout the country. Tickets are purchased through the company’s Website or through the Web services of its agents and partners. The company also offers software, on a Software as a Service (SaaS) basis, which gives bus operators the option of handling their own ticketing and managing their own inventories. To date, the company says they have sold over 30 million bus tickets and has more than 1750 bus operators using the software to manage their operations.
Challenge : The company previously ran its operations from a traditional data center by purchasing and renting its systems and infrastructure. In addition to the expense, several logistical problems evolved from this arrangement. The biggest problem was that the infrastructure could not effectively handle processing fluctuations, which had a negative impact on productivity. Additionally, the procurement of servers or upgrading the server configuration was an extremely time-consuming endeavor. Over time, redBus realized that a better solution was imperative — a solution that offered scalability to handle the company’s processing fluctuations. redBus looked to Amazon Web Services (AWS) for a solution.
Why Amazon Web Services: After testing the AWS solution on a small application for several months, the travel agency determined that it was very workable and convenient. Although redBus was quite enthusiastic about the on-demand instances and variety of instance types, several other features cemented the company’s decision to migrate completely to AWS. These features included the ability to easily manage access to servers through security groups, the easy-to-use, self-service management console, the concept of Elastic IPs, and superior support.
Its Benefits: Since migrating to AWS, redBus has seen measurable improvements in the bottom line. Padmaraju says, “By scaling up and down dynamically based on the load, we maintain performance as well as minimize cost. With the time savings that the IT and development staffs obtain from the AWS solution, AWS gives us an overall cost benefit of about 30–40%.” He adds, “By hosting at [the AWS Asia Pacific (Singapore) region], redBus.in gained significantly in terms of website performance by way of reduced latency (about 4x). This is a great advantage when the customers are from India.”
Of the many excellent characteristics of AWS, perhaps the most significant to redBus is the ability to “instantly replicate the whole setup on demand for testing by creating and destroying instances on demand for experimentation, thereby reducing the time to market.” Less time to market translates to increased profitability and success.


