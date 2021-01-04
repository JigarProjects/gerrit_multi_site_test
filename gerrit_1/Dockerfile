FROM gerritcodereview/gerrit:3.2.6
CMD mkdir /usr/local/gerrit
COPY ./gerrit.config /usr/local/gerrit/
COPY ./multi-site.config /usr/local/gerrit/
COPY ./replication.config /usr/local/gerrit/

COPY ./gerrit.config /var/gerrit/etc/
COPY ./multi-site.config /var/gerrit/etc/
COPY ./replication.config /var/gerrit/etc/
