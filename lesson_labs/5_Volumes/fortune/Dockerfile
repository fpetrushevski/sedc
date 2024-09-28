FROM ubuntu:latest
RUN apt-get update ; apt-get -y install fortune
RUN mkdir -p /usr/local
COPY ./fortuneloop.sh /usr/local/fortuneloop.sh

ENTRYPOINT /bin/fortuneloop.sh

