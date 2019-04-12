# pyspark-docker
docker files to run paspark in docker container

Based on the following tutorial:
https://towardsdatascience.com/a-journey-into-big-data-with-apache-spark-part-1-5dfcc2bccdd2

1. run the cluster: `docker-compose run --rm -w /project spark-driver`. This will create and run a Spark Master and one Spark Worker container. It also runs a spark-driver container and lands you into its bash shell.

    1. (Go to: `http://localhost:8080` to see the sparkUI)
   
    1. (you can scale the amount of workers by first running `docker-compose scale spark-worker=3` for e.g. 3 workers)

2. When in the shell run: `../spark/bin/spark-submit --master spark://spark-master:7077 pi.py  1000`, to run the pi.py example. You can add your own python scipts in the same directory as pi.py on your local computer and they will be immediately available to run, like the example above.

3. (When done `ctrl+D` to quit bash and run `docker-compose stop` to stop the containers)