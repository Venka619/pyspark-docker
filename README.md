# pyspark-docker
docker files to run paspark in docker container

Based on the following tutorial:
https://towardsdatascience.com/a-journey-into-big-data-with-apache-spark-part-1-5dfcc2bccdd2

to start run: `docker-compose up`

to interact with spark, run another docker instance like so: `docker run --rm -it --network docker_spark-network \
    spark:latest /bin/sh`
then when in the shell, for example run: `/spark/bin/spark-submit --master spark://spark-master:7077 /spark/examples/src/main/python/pi.py  1000`
