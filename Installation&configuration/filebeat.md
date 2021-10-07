# Install and Configure Filebeat
* Filebeat is used to send logs to the Logstash or Elasticsearch for parsing. In this section, we will install the Filebeat and configure it to send logs to the Logstash.

```
sudo apt-get install filebeat -y
```
* Once installed, edit the Filebeat main configuration file and configure it to send logs to the Logstash.


### sudo nano /etc/filebeat/filebeat.yml

### Filebets Inputs
![preview](./images/filebeats1.png)

### General Fields and Tags
![preview](./images/filebeats2.png)

### Logstash Configuration
![preview](./images/filebeats3.png)

### Restart service 
```
sudo systemctl start filebeat
sudo systemctl enable filebeat
```

### Next, enable the Filebeat system module, which will examine local system logs:
``` 
filebeat modules enable system 
```
### Next, load the index template with the following command:
```
filebeat setup --index-management -E output.logstash.enabled=false -E 'output.elasticsearch.hosts=["localhost:9200"]'

```
### Verify 
```curl -XGET http://localhost:9200/_cat/indices?v```
