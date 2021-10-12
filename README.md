# Data-streaming-kafka-python

# Environment setup
Start by opening a new Terminal window and connecting to Kafka shell. You should have Zookeeperand Kafka containers running already, so start them if that’s not the case:

	docker exec -it kafka /bin/sh
	cd /opt/kafka_<version>/bin
	ls
	
Next, create a topic to store Python-generated messages. Here’s how you can make a topic named messages and then verify it was created by listing all Kafka Topics:

	kafka-topics.sh --create --zookeeper zookeeper:2181 --replication-factor 1 --partitions 1 --topic messages

To list kafka topics, execute the following command:

	kafka-topics.sh --list --zookeeper zookeeper:2181

That’s all you have to do in a Kafka shell. You can leave it now by typing exit into the console. 

The next step is to install the Python package for working with Kafka. It’s called kafka-python , and you can install it with the following command:

	python3 -m pip install kafka-python

Next, clone this repo or copy python files in a folder on your machine. Open the folder in terminal and run the code as follows:

	python3 data-gerator.py
	
This generates dummy streaming data.

Next, open two terminals. arrange them side-by-side. First run the kaka-consumer code in one terminal as follows:

	python3 consumer.py

In the second terminal, run kafka-producer as follows:

	python3 producer.py

You’ll immediately a message printed out in the terminals. Remember that the Producer sleeps for a random number of seconds before sending the next message. It’s best to leave both windows running for a minute or so, just to verify everything is working properly.


