FROM alpine:3.20.6

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories && \
    apk update && \
    apk add --no-cache build-base tcl tcl-dev libc-dev && \
    cd /tmp && \
    wget https://download.redis.io/redis-stable.tar.gz && \
    tar zxf redis-stable.tar.gz -C /tmp && \
    cd /tmp/redis-stable && \
    make -j$(nproc) malloc=libc && \
    make install && \
    apk del build-base tcl-dev libc-dev && \
    rm -rf /tmp/redis* /var/cache/apk/* && \
    mkdir -p /etc/redis /var/lib/redis && \
    adduser -D -H -s /bin/sh redis && \
    chown -R redis:redis /var/lib/redis

COPY ./redis.conf /etc/redis/redis.conf

USER redis

EXPOSE 6379
CMD ["redis-server", "/etc/redis/redis.conf"]
