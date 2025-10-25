FROM bde2020/hadoop-base:latest

MAINTAINER Ivan Ermilov <ivan.s.ermilov@gmail.com>

HEALTHCHECK CMD curl -f http://localhost:9870/ || exit 1

ENV HDFS_CONF_dfs_namenode_name_dir=file:///hadoop/dfs/name
RUN mkdir -p /hadoop/dfs/name
VOLUME /hadoop/dfs/name

RUN sed -i '/stretch-updates/d' /etc/apt/sources.list && \
    sed -i 's|deb.debian.org|archive.debian.org|g' /etc/apt/sources.list && \
    sed -i 's|security.debian.org|archive.debian.org|g' /etc/apt/sources.list && \
    echo 'Acquire::Check-Valid-Until "false";' > /etc/apt/apt.conf.d/99ignore-check-valid-until

RUN apt-get update && apt-get install -y dos2unix

ADD run.sh /run.sh
RUN dos2unix /run.sh && chmod +x /run.sh

EXPOSE 9870

CMD ["/run.sh"]
