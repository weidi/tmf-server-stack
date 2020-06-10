# PHP 5 is mandatory to run aseco
FROM alpine:3.8

ARG MYSQL_SERVER='mysql'
ARG MYSQL_LOGIN='tmf'
ARG MYSQL_PASSWORD='tmfpass'
ARG ASECO_MASTER_ADMIN='MasterAdmin'
ARG ASECO_ADMIN='Admin'
ARG SERVER_SA_PASSWORD='SuperAdmin'
ARG SERVER_IP='tmserver'

ENV MYSQL_SERVER $MYSQL_SERVER
ENV MYSQL_LOGIN $MYSQL_LOGIN
ENV MYSQL_PASSWORD $MYSQL_PASSWORD
ENV ASECO_MASTER_ADMIN $ASECO_MASTER_ADMIN
ENV ASECO_ADMIN $ASECO_ADMIN
ENV SERVER_SA_PASSWORD $SERVER_SA_PASSWORD
ENV SERVER_IP $SERVER_IP

RUN mkdir -p /home/tmf/xaseco

WORKDIR /home/tmf/xaseco

# Allows this image to be able to wait for a DB to be ready
COPY wait-for-it.sh .
COPY startup.sh .
COPY xaseco_116.zip .
# Follow install instructions from http://www.gamers.org/tmf/quickstart.html#xaseco

RUN apk update &&\
	apk add unzip \
	bash \
	php5 \
	php5-xml \
	php5-mysql &&\
	unzip xaseco_116.zip -d .. &&\
	mv newinstall/*.xml . &&\
	mv newinstall/*.php ./includes/ &&\
	rm xaseco_116.zip

CMD ["./startup.sh"]