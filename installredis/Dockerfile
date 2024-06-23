FROM alpine:3.15.11

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories

RUN apk update && \
    apk add --no-cache build-base tcl tcl-dev libc-dev && \
    cd /root && \
    wget https://download.redis.io/redis-stable.tar.gz && \
    tar zxf /root/redis-stable.tar.gz -C /root && \
    cd /root/redis-stable && \
    make malloc=libc -j4 -l4 && \
    make install && \
    mkdir -p /etc/redis && \
    mkdir -p /var/lib/redis && \
    apk del build-base tcl-dev libc-dev && \
    rm -rf /root/redis-stable.tar.gz /root/redis-stable /var/cache/apk/*

COPY ./redis.conf /etc/redis

EXPOSE 6379

CMD ["redis-server", "/etc/redis/redis.conf"]
