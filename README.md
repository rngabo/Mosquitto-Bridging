# Mosquitto-Bridging

This repository provides instructions for setting up and running two Mosquitto MQTT brokers.

## Installation

1. Install Mosquitto on your system. Refer to the official Mosquitto documentation for installation instructions specific to your operating system.

## Configuration

1. After installing Mosquitto, navigate to the directory `/etc/mosquitto/conf.d/`.

2. Create two configuration files: `broker1.conf` and `broker2.conf`, in the `/etc/mosquitto/conf.d/` directory.

3. In each configuration file, specify the configuration options for the respective brokers. Customize the configurations as per your requirements.

## Starting Brokers

1. Open two terminal tabs or windows.

2. In the first terminal tab, start the first broker by running the following command:

mosquitto -c /etc/mosquitto/conf.d/broker1.conf -d


This command starts the broker in the background (`-d`) using the configuration file `/etc/mosquitto/conf.d/broker1.conf`.

3. In the second terminal tab, start the second broker by running the following command:

mosquitto -c /etc/mosquitto/conf.d/broker2.conf -d

This command starts the second broker in the background (`-d`) using the configuration file `/etc/mosquitto/conf.d/broker2.conf`.

## Subscribing to Brokers

1. Open two additional terminal tabs or windows.

2. In the first terminal tab, subscribe to the first broker by running the following command:


mosquitto_sub -h 127.0.0.1 -p 1221 -t "test"


This command subscribes to the first broker on the local machine (`127.0.0.1`) using port `1221` and topic "test".


3. In the second terminal tab, subscribe to the second broker by running the following command:

mosquitto_sub -h 127.0.0.1 -p 1222 -t "test"


## Publish message to both brokers using one broker


mosquitto_pub -h 127.0.0.1 -p 1221 -t "bridge/to-broker2/test" -m "Hello, Kigali!" -u mosq-user1 -P Aa000000 -q 0 

message to appear on both brokers"


