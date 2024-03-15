# ElasticSearchDockerCompose

a docker compose file to create elastic search container

# Run

```bash
docker-compose up
```

If you are creating the container for the first time, please follow these actions after the container has been created ([More Information](https://www.elastic.co/guide/en/elasticsearch/reference/8.12/docker.html)):

1. reset password
   On Linux:

   ```bash
   docker exec -it es01 /usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic
   docker exec -it es01 /usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s kibana
   ```

   On Windows:

   ```bash
   docker exec -it es01 //usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic
   docker exec -it es01 //usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s kibana
   ```

   store password after run first command

2. copy crt file
   ```bash
   docker cp es01:/usr/share/elasticsearch/config/certs/http_ca.crt .
   ```
3. Use the crt file and the credentials (elastic:your_password) to send requests to the Elasticsearch service.  
   e.g.
   ```bash
   curl --cacert http_ca.crt -u elastic:your_password https://localhost:9200
   ```

# Remove Container

```bash
docker-compose down
```
