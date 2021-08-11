# Rabbit test project

This microservice designed as a Rabbit microservice skeleton for newbies.
Deploy your RabbitMQ server and run this project.
You can copy this proyect to your local machine twice in two separate directories and run one as a client and the other as a server.

Tons of thanks to Luka Gado for his [tutorial](https://medium.com/q-software/symfony-and-rabbitmq-86b14dd604b1)

## Responsibilities

1. Send AMQP messages to a RabbitMQ server.
2. Consume AMQP messages from a RabbitMQ server.

### My feelings

After weeks of learning the "official" Symfony and RabbitMQ way, I realized that it is the simplest and fastest way to code microservices in Symfony. It took me a couple of hours to get two microservices sharing simple JSON messages.

I'm sure there is a way to get it done with the "official" Symfony bundle, but it did not work for me. I was close... too close to success, but I did not.

Sharing PHP objects between microservices through a AMQP servers was not the goal. We need some simpler, coding language agnostic.

And I think that's the way to go.
