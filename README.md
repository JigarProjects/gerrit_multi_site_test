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

3. generate ssh key on both gerrit docker images
   ```
   docker exec -it gerrit_2 bash
      ssh-keygen ssh-keygen -t rsa -n test -N '' -f /var/gerrit/.ssh/id_rsa
   docker exec -it gerrit_2 bash
      ssh-keygen ssh-keygen -t rsa -n test -N '' -f /var/gerrit/.ssh/id_rsa
   ```

4. Adding authorized key
   
   add gerrit_2's id_rsa.pub to gerrit_1
   ```
   docker exec -it gerrit_1 bash
      echo "GERRIT_1's public key" > /var/gerrit/.ssh/authorized_keys
   ```

5. Override sshd config on both containers

   '''
   docker exec -u root -it gerrit_1 bash
      cat /etc/sssh/sshd_config
      AuthorizedKeysFile	/var/gerrit/.ssh/authorized_keys
   ''''
   
6. start ssh service
   '''
   docker exec -it gerrit_1 bash
      /usr/sbin/sshd & 
   '''