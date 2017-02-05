FROM gliderlabs/alpine
MAINTAINER kost - https://github.com/kost

RUN apk --update add mysql mysql-client pwgen openssl tini && rm -f /var/cache/apk/* && \
echo "Success"

ADD scripts/run.sh /scripts/run.sh
RUN mkdir /scripts/pre-exec.d && \
mkdir /scripts/pre-init.d && \
chmod -R 755 /scripts

RUN mkdir -p /run/mysqld/ \
&& chown -R mysql:mysql /var/lib/mysql /run/mysqld/ \
&& mkdir -p /etc/mysql/my.cnf.d \
&& chmod a+rwx -R /var/lib/mysql /run/mysqld


USER 100

EXPOSE 3306
# WORKDIR /app

VOLUME ["/var/lib/mysql"]

ENTRYPOINT ["/scripts/run.sh"]

