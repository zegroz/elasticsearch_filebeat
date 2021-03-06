# elasticsearch_filebeat
Elasticsearch, filebeat and kibana docker stack

# set virtual memory for a virtual machine (temporary)
``
sysctl -w vm.max_map_count=262144
``

# or permanent
```
sudo nano /etc/sysctl.conf

vm.max_map_count=262144

sudo sysctl -p
```

# docker-compose.yml
``
docker-compose up -d
``

# find elasticsearch container ip
``
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' elasticsearch
``
# setup 
```
docker pull docker.elastic.co/beats/filebeat:7.16.3 \
docker run --network=elastic docker.elastic.co/beats/filebeat:7.16.2 setup \
  -E setup.kibana.host=172.19.0.3:5601 \
  -E output.elasticsearch.hosts=["172.19.0.2:9200"]
```

source: https://www.elastic.co/guide/en/beats/filebeat/current/running-on-docker.html


