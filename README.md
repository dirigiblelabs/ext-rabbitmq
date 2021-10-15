# RabbitMQ API

## Overview

API endpoints for working with RabbitMQ messaging broker in Eclipse Dirigible

## Getting Started

You will need RabbitMQ installed on your machine. You can find all relevant information in the official documentation below:

- [Debian/Ubuntu](https://www.rabbitmq.com/install-debian.html)
- [MacOS/Homebrew](https://www.rabbitmq.com/install-debian.html)
- [Windows](https://www.rabbitmq.com/install-windows.html)

## API Endpoints

## RabbitMQ Consumer

The RabbitMQ Consumer is listening on a queue destination to a RabbitMQ server.

### Basic Usage

`Start listening on a queue`

    var consumer = require("rabbitmq/consumer");
    consumer.startListening("rabbitmq-queue", "<rabbitmq-project>/<rabbitmq-handler>");

File: `<rabbitmq-project>/<rabbitmq-handler>`

    exports.onMessage = function(message) {
        console.log("Hello from My RabbitMQ Listener! Message: " + message);
    };

    exports.onError = function(error) {
        console.error("Error from My RabbitMQ Listener! Error: " + error);
    };

`Stop listening on a queue`

    var consumer = require("rabbitmq/consumer");
    consumer.stopListening("rabbitmq-queue", "<rabbitmq-project>/<rabbitmq-handler>");

## RabbitMQ Producer

The RabbitMQ Producer is sending message to a queue to a RabbitMQ server

### Basic Usage

`Send message to a give queue (implicitly creates connection, channel and the named queue if missing)`

    var producer = require("rabbitmq/producer");
    consumer.sendMessage("rabbitmq-queue", "My RabbitMQ message");
