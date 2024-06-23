## redis

### How To Use
- basic
```bash
docker run docker run -d --name redis benfus/redis7:alpine-3.15
```
- with port
```bash
docker run docker run -d -p 6379:6379 --name redis benfus/redis7:alpine-3.15
```
- mount config file and data and network
```bash
docker run -p 6379:6379 --name redis --network <network> -v </path/to/conf/redis.conf:/etc/redis/redis.conf> -v </path/to/data/:/var/lib/redis> -d benfus/redis7:alpine-3.15 redis-server /etc/redis/redis.conf
```
