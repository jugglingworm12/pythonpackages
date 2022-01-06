# kafkautil-ecs 

<img src="../img/ecs.png" width="50%" height="50%" >

## About

This is a command line (CLI) tool built in python for simple testing of kafka connections. This tool is used in command line interface, with three different commands.

## Installation

This package is available python's Pypi repository, therefore it can be installed using pip. There is only one version currently available v. 1.0.0.

```pip install kafkautil-ecs```


The package can be found at [https://pypi.org/project/kafkautil-ecs/](https://pypi.org/project/kafkautil-ecs/)

## Requirements

Current requirements are:

* python 3 installed
* python's click package
* pythons's kafka-python package

click and kafka-python should be installed automatically with the kafkautil-ecs package.

## Entrypoint

Once installed the entrypoint for the cli tool is ```kafkautil```. Therefore you can reach the utility by opening your terminal and typing ```kafkautil```

Once installed try typing ```kafkautil --help```

## Commands

The package comes with three commands:

* kafkautil test-connection
* kafkautil read-data
* kafkautil send-data

## Examples

Below are examples for each command

##### kafkautil test-connection

Runing ```kafkautil test-connection --help``` will display the following:

```
    Usage: kafkautil test-connection [OPTIONS] BOOTSTRAP_SERVER

    BOOTSTRAP_SERVER: Server address for kafka topic

    Options:
    --help  Show this message and exit.
  
```  
```kafkautil test-connection``` takes one argument ```BOOTSTRAP_SERVER```.

```BOOTSTRAP_SERVER``` is the location of the kafka instance. 

Example:

```kafkautil test-connection ipaddress:9092```

It can take in a list, as a kafka cluster may have multiple ip addresses:

```kafkautil test-connection ipaddress:9092,ipaddress:9093```

##### kafkautil read-data

Runing ```kafkautil read-data --help``` will display the following:

```
    Usage: kafkautil read-data [OPTIONS] BOOTSTRAP_SERVER TOPIC

    BOOTSTRAP_SERVER: Server address for kafka topic

    TOPIC: Kafka topic Name

    Options:
    --offset TEXT  Offset can be earliest or latest
    --help         Show this message and exit.

```

```kafkautil read-data``` takes two arguments and one option argument. 

```BOOTSTRAP_SERVER``` and ```TOPIC``` are required arguments. ```--offset``` is an optional argument, although it defaults to "earliest".
```--offset``` can be one of two values: "earliest" or "latest". If set to "earliest" it will grab all messages currently in the kafka topic. If set to "latest" the program will stay open waiting for the latest message to come through. Once the message comes through the program will end. If set to latest it will not show any existing messages on the topic.

Example:

```kafkautil read-data xxx.xxx.xx:9092 myTopic```

This defaults to ```--offset earliest```

Example with ```--offset latest```

```kafkautil read-data xxx.xxx.xx:9092 myTopic --offset latest```









