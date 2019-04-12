# pyspark-docker
docker files to run paspark in docker container

Based on the following tutorial:
https://towardsdatascience.com/a-journey-into-big-data-with-apache-spark-part-1-5dfcc2bccdd2

1. run the cluster: `docker-compose up`. This will create a Spark Master and one Spark Worker

3. go to: `http://localhost:8080` to see the sparkUI

4. to interact with spark, run another docker instance like so: `docker run --rm -it --network docker_spark-network spark:latest /bin/sh`. This will be your Spark Driver

5. Then when in the shell, for example run: `/spark/bin/spark-submit --master spark://spark-master:7077 /spark/examples/src/main/python/pi.py  1000`
