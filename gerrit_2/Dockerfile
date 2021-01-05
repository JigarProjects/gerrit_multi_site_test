FROM gerritcodereview/gerrit:3.2.6

USER root
RUN yum install -y openssh-server && \
    yum install -y initscripts

USER gerrit
COPY ./secure.config /var/gerrit/etc/
COPY ./gerrit.config /var/gerrit/etc/
COPY ./multi-site.config /var/gerrit/etc/
COPY ./replication.config /var/gerrit/etc/
CMD ssh-keygen -t rsa -n test -N '' -f /var/gerrit/.ssh/id_rsa
