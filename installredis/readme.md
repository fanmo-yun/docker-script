## redis

### How To Use
- basic
```bash
docker run -d --name redis benfus/redis:tagname
```
- with port
```bash
docker run -d -p 6379:6379 --name redis benfus/redis:tagname
```
- mount config file and data and network
```bash
docker run -p 6379:6379 --name redis --network <network> -v </path/to/conf/redis.conf:/etc/redis/redis.conf> -v </path/to/data/:/var/lib/redis> -d benfus/redis:tagname redis-server /etc/redis/redis.conf
```
