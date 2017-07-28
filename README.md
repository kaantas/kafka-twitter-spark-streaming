# Twitter and Spark Streaming with Apache Kafka

This project counts tweets that include #GoTS7 hashtag per user in real-time. <br>
Also, username and tweet counts are printed. 

## Code Explanation

1. Authentication operations were completed with Tweepy module of Python.
2. StreamListener named KafkaPushListener was create for Twitter Streaming. StreamListener produces data for Kafka Consumer.
3. Producing data was filtered about including Game of Thrones hashtag.
4. SparkContext was created to connect Spark Cluster.
5. Kafka Consumer that consumes data from 'twitter' topic was created.
6. Calculated how many tweets include #GotS7 hashtag per user and printed usernames and counts in real-time.

## Running

1. Create Twitter API account and get keys for [twitter_config.py](https://github.com/kaantas/kafka-twitter-spark-streaming/blob/master/twitter_config.py)
2. Start Apache Kafka <br>
```
./kafka/kafka_2.11-0.11.0.0/bin/kafka-server-start.sh ./kafka/kafka_2.11-0.11.0.0/config/server.properties
```
3. Run [kafka_push_listener.py](https://github.com/kaantas/kafka-twitter-spark-streaming/blob/master/kafka_push_listener.py) with Python version 3.
```
PYSPARK_PYTHON=python3 bin/spark-submit kafka_push_listener.py
```
4. Run [kafka_twitter_spark_streaming.py](https://github.com/kaantas/kafka-twitter-spark-streaming/blob/master/kafka_twitter_spark_streaming.py) with Python version 3.
```
PYSPARK_PYTHON=python3 bin/spark-submit --packages org.apache.spark:spark-streaming-kafka-0-8_2.11:2.2.0 kafka_twitter_spark_streaming.py
```
