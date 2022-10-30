# A-pyspark-testing-suite

```
VNC Server
	ralph.liang@gmail.com

Zotero/Home Assistant cloud
	ralph.liang@gmail.com

Raspberrry Pi 4
	Login in: ycliang
	
portainer/portainer-ce
http://192.168.31.249:9000
admin


docker run -d -p 9000:9000 -v //var/run/docker.sock:/var/run/docker.sock --restart=always --name portainer -v portainer_data:/data portainer/portainer-ce

docker pull jupyter/pyspark-notebook:aarch64-spark-3.2.1

docker run -d -p 8888:8888 --name pyspark3.2.1 -v /home/ycliang/pyspark:/home/jovyan -e SPARK_OPTS="--packages io.delta:delta-core_2.12:2.0.0 --driver-java-options=-Xms1024M --driver-java-options=-Xmx6144M --driver-java-options=-Dlog4j.logLevel=info --ResourceUseDisplay.mem_limit" jupyter/pyspark-notebook:aarch64-spark-3.2.1
Ncu2022!

在 container 中安裝所需套件
pip install msteams delta-spark  tableauserverclient dash jupyter-git delta-spark==2.0.0
pip install --upgrade jupyterlab jupyterlab-git
pip install psycopg2-binary

下列指令可以產生可使用的jar file under 目錄下
pyspark --packages io.delta:delta-core_2.12:2.0.0 \
  --conf "spark.sql.extensions=io.delta.sql.DeltaSparkSessionExtension" \
  --conf "spark.sql.catalog.spark_catalog=org.apache.spark.sql.delta.catalog.DeltaCatalog"

對等寫法

  .config("spark.jars.packages", "io.delta:delta-core_2.12:2.0.0") \
  .config("spark.sql.extensions", "io.delta.sql.DeltaSparkSessionExtension") \
  .config("spark.sql.catalog.spark_catalog", "org.apache.spark.sql.delta.catalog.DeltaCatalog") \

pip install delta-spark==2.0.0

wget https://jdbc.postgresql.org/download/postgresql-42.5.0.jar

docker cp ./postgresql-42.5.0.jar  3bdcf761d4f0:/usr/local/spark/jars

docker commit 3bdcf761d4f0 jupyter/pyspark-notebook:aarch64-spark-3.2.1

docker save -o aarch64-spark-3.2.1.tar 5785fd005f7e

gzip aarch64-spark-3.2.1.tar

gzip -d aarch64-spark-3.2.1.tar.gz

docker load -I aarch64-spark-3.2.1.tar

docker tag  5785fd005f7e jupyter/pyspark-notebook:aarch64-spark-3.2.1

GitHub RalphLiang
DockerHub ralphliang
```
