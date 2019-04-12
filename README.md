# pyspark-docker
docker files to run paspark in docker container

Based on the following tutorial:
https://towardsdatascience.com/a-journey-into-big-data-with-apache-spark-part-1-5dfcc2bccdd2

1. run the cluster: `docker-compose up`. This will create a Spark Master and one Spark Worker

2. (you can scale the amount of workers by running `docker-compose up --scale spark-worker=3` for e.g. 3 workers)

3. go to: `http://localhost:8080` to see the sparkUI

4. to interact with spark, we need to build another docker image to be the Spark Driver. Build the driver image from the home directory like so: `docker build -t spark-driver ./docker`.

5. then run the driver image: `docker run --rm -it -v "$(pwd)":/project -w /project --network spark_spark-network spark-driver /bin/sh`. This will land us in a bash shell of the driver, at the /project directory (this directory is mounted to the current directory from which you run this command).

6. Then when in the shell run: `../spark/bin/spark-submit --master spark://spark-master:7077 pi.py  1000`, to run the pi.py example. You can add your own python scipts in the same directory as pi.py on your local computer and they will be immediately available to run like the example above.
