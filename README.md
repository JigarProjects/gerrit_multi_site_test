This is an example of gerrit multisite

We will have 2 different networks which would represent different DC.
Each data center would have one gerrit instance.

We will have Kafka, zookeeper and HAProxy in separate DC.

To cleanup 
``docker-compose down -v``

Steps:

1. Spin up containers 
   ```
    docker-compose build --no-cache
    docker-compose up -d
    ```
2. Go to https://localhost:6443/ with 
   username/password = cn=admin,dc=example,dc=org/secret
   
   create a new child node of type "Courier Mail Account"
   ```
    Given Name: Gerrit
    Last Name: Admin
    Common Name: Gerrit Admin
    User ID: gerritadmin
    Email: gerritadmin@localdomain
    Password: secret
   ```

3. Login to gerrit-1 and setup ssh key for gerrit_2
   ```
   $ docker exec -it gerrit_2 bash
   $ 
   ```
