#Twitter Sentiment Analytics using Apache Spark Streaming APIs and Python 

The aim of this project is to have hands-on experience about processing live data streams (Twitter) using Kafka, Spark’s streaming APIs, Python, PySpark that follows ETL Pipeline Architecture and checking the sentiment of real-time tweets at the end for a given twitter hashtag. 

This project have 2 stages:

a) Establsing connection to Twitter and Kafka broker to receive live tweets for a given twitter hastag.
b) Collecting the tweets to Kafka Consumer, applying Spark Transformations using PySpark for tweets and display the Sentiment count at the end of application run.

##Requirements
One of the first requirements is to get access to the streaming data; in this case, real-time tweets. Twitter provides a very 
convenient API to fetch tweets in a streaming manner 
 
In addition, I also used Kafka to buffer the tweets before processing. Kafka provides a distributed queuing service which can be used to store the data when the data creation rate is more than processing rate. It also has several other uses. 

###Project Setup 
 
####Installing Required Python Libraries 
I have provided a text file containing the required python packages: `requirements.txt`

To install all of these at once, simply run (only missing packages will be installed):    
`$ sudo pip install -r requirements.txt`
 
####Installing and Initializing Kafka 
Download and extract the latest binary from https://kafka.apache.org/downloads.html

#####Start zookeeper service:  
`$ bin/zookeeper-server-start.sh config/zookeeper.properties`
 
#####Start kafka service: 
`$ bin/kafka-server-start.sh config/server.properties`
 
#####Create a topic named twitterstream in kafka: 
`$ bin/kafka-topics.sh --create --zookeeper --partitions 1 --topic twitterstream localhost:2181 --replication-factor 1`

 
####Using the Twitter Streaming API 
In order to download the tweets from twitter streaming API and push them to kafka queue, I have created a python script
app.py. The script will need your twitter authentication tokens (keys).

Once you have your authentication tokens, create or update the `twitter-app-credentials.txt` with these  credentials.

After updating the text file with your twitter keys, you can start downloading tweets from the twitter stream API and push them to the twitterstream topic in Kafka. Do this by running the script as follows:   
`$ python app.py`   
Note: This program should be kept running for collecting tweets. 
 

