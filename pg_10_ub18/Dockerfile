FROM ubuntu:18.04
RUN  apt update
RUN  DEBIAN_FRONTEND=noninteractive apt install -y vim postgresql-10 
#RUN  pg_ctlcluster  10 main start
#   1  /usr/lib/postgresql/10/bin/pg_ctl -D /var/lib/postgresql/10/main 
#   2  /usr/lib/postgresql/10/bin/pg_ctl -D /var/lib/postgresql/10/main  init
#   3  rm /var/lib/postgresql/10/main
#   4  rm /var/lib/postgresql/10/main -fr
#   5  /usr/lib/postgresql/10/bin/pg_ctl -D /var/lib/postgresql/10/main  init
#   6  history >/tmp/history.postgres
COPY  ICAT.sql  pg_dbinit.sh  pg_startup.sh /tmp/
