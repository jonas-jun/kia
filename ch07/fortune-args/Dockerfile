FROM ubuntu:latest

RUN apt-get update ; apt-get -y install fortune
ADD fortuneloop.sh /bin/fortuneloop.sh

# exec 형태의 ENTRYPOINT 명령
ENTRYPOINT [ "/bin/fortuneloop.sh" ]
# 기본 인자
CMD [ "10" ]