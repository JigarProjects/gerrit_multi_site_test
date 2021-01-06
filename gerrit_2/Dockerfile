FROM gerritcodereview/gerrit:3.2.6

USER root
RUN yum update -y
RUN yum install -y openssh-server && \
    yum install -y initscripts
RUN sed -i 's/#PasswordAuthentication yes/PasswordAuthentication no/g' /etc/ssh/sshd_config &&\
    sed -i 's/PasswordAuthentication yes/PasswordAuthentication no/g' /etc/ssh/sshd_config
RUN ssh-keygen -A
RUN /usr/sbin/sshd &

USER gerrit
COPY ./secure.config /var/gerrit/etc/
COPY ./gerrit.config /var/gerrit/etc/
COPY ./multi-site.config /var/gerrit/etc/
COPY ./replication.config /var/gerrit/etc/

CMD ssh-keygen -t rsa -n test -N '' -f /var/gerrit/.ssh/id_rsa

EXPOSE 22
