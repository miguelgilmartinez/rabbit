# Rabbit test project

This microservice designed as a Rabbit microservice skeleton for newbies.
Deploy your RabbitMQ server and run this project.
You can copy this proyect to your local machine twice in two separate directories and run one as a client and the other as a server.

Tons of thanks to Luka Gado for his [tutorial](https://medium.com/q-software/symfony-and-rabbitmq-86b14dd604b1)

## Responsibilities

1. Send AMQP messages to a RabbitMQ server.
2. Consume AMQP messages from a RabbitMQ server.

## Installation

```bash
composer require php-amqplib/rabbitmq-bundle
composer require annotations

# This below if for creating random data.
# Do not use this for production.
composer require fzaninotto/faker
```

In your local.env o .env file, add the following:

```txt
###> php-amqplib/rabbitmq-bundle ###
RABBITMQ_URL=amqp://guest:guest@localhost:5672
###< php-amqplib/rabbitmq-bundle ###
```

## Usage

1. config/old_sound_rabbit_mq.yaml: Don't change this name. This is the place to add queues and exchanges. `my_messaging` is the transport name. It's related to `App\Rabbit\MessageProducer: '@old_sound_rabbit_mq.my_messaging_producer'` in services.yaml.
2. MessageController: Just for testing. It triggers messages by browsing to <http://ip:port/send-message/XXX> where XXX is the number of testing messages you want to send.
3. MessageConsumer: This controlls the consumer. If your microservice does not consume any queue, ignore this. Add here your code when incoming mesages arrive.
4. MessageProducer: This encapsulates the message and sends it to the queue by `->publish($message)`. It's a very simple class which extends `OldSound\RabbitMqBundle\RabbitMq\Producer` class
5. MessageService: It's the one which creates and sends the messages. It's called by MessageController.
6. Run consumer with `bin/console rabbitmq:consumer messaging`, where `messaging` is the name of the queue.

   



## My feelings

After weeks of learning the "official" Symfony and RabbitMQ way, I realized that it is the simplest and fastest way to code microservices in Symfony. It took me a couple of hours to get two microservices sharing simple JSON messages.

I'm sure there is a way to get it done with the "official" Symfony bundle, but it did not work for me. I was close... too close to success, but I did not.

Sharing PHP objects between microservices through a AMQP servers was not the goal. We need some simpler, coding language agnostic.

And I think that's the way to go.
