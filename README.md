This is an example of gerrit multisite

We will have 2 different networks which would represent different DC.
Each data center would have one gerrit instance.

We will have Kafka, zookeeper and HAProxy in separate DC.

To setup 

```
docker-compose build --no-cache
docker-compose up -d
```

To cleanup 
``docker-compose down -v``
