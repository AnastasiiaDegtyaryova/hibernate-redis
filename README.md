Hibernate + Redis (Docker)
1. Preconditions
    - Docker installed
    - Redis Insight installed
    - Java 17 installed

2. To Start the Project
- Start Docker Containers:

```bash
# MySQL
docker run -d --name mysql \
-e MYSQL_ROOT_PASSWORD=Password1. \
-p 3307:3306 \
-v mysql_data:/var/lib/mysql \
mysql:8

# Redis + Redis Insight
docker run -d --name redis-stack \
-p 6379:6379 -p 8001:8001 \
redis/redis-stack:latest

# If the containers already exist:
docker start mysql redis-stack
```
- Run the Java Application: The program will connect to MySQL and Redis, load city data, transform it into CityCountry objects, and write them to Redis.

- Check Redis via Redis Insight:
    - Open browser → http://localhost:8001

    - Redis Insight will show keys (city IDs)

    - Click on a key to view stored JSON