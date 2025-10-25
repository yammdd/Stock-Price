FROM bde2020/hadoop-base:2.0.0-hadoop3.2.1-java8

MAINTAINER Ivan Ermilov <ivan.s.ermilov@gmail.com>

HEALTHCHECK CMD curl -f http://localhost:8088/ || exit 1

RUN sed -i '/stretch-updates/d' /etc/apt/sources.list && \
    sed -i 's|deb.debian.org|archive.debian.org|g' /etc/apt/sources.list && \
    sed -i 's|security.debian.org|archive.debian.org|g' /etc/apt/sources.list && \
    echo 'Acquire::Check-Valid-Until "false";' > /etc/apt/apt.conf.d/99ignore-check-valid-until

RUN apt-get update && apt-get install -y dos2unix

ADD run.sh /run.sh
RUN dos2unix /run.sh && chmod +x /run.sh

EXPOSE 8088

CMD ["/run.sh"]
