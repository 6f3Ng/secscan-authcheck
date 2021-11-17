FROM docker.io/jormar/python3.6-alpine 

MAINTAINER sec@zto.cn

ENV LANG C.UTF-8
ENV DEBIAN_FRONTEND noninteractive
ENV mongo_database acc
ENV mongo_host 127.0.0.1
ENV mongo_port 27017
# ENV mongo_user user
# ENV mongo_password 123456
ENV redis_host 127.0.0.1
ENV redis_port 6379
ENV redis_db 0
# ENV redis_password 123456

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories

# RUN apk update && apk upgrade && apk add gcc g++ linux-headers wget zlib-dev build-base && wget https://www.python.org/ftp/python/3.6.5/Python-3.6.5.tgz && tar xvf Python-3.6.5.tgz && cd Python-3.6.5 && ./configure --enable-optimizations --with-ensurepip=install && make -j 8 && make altinstall
RUN apk update && apk add gcc g++ linux-headers wget 

COPY . /opt/authcheck

WORKDIR /opt/authcheck

RUN python3 -m pip install -r requirements.txt -i http://mirrors.aliyun.com/pypi/simple/ --trusted-host mirrors.aliyun.com

EXPOSE 8888

CMD uwsgi uwsgi.ini
