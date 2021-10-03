# Install and Configure Filebeat
* Filebeat is used to send logs to the Logstash or Elasticsearch for parsing. In this section, we will install the Filebeat and configure it to send logs to the Logstash.

```
sudo apt-get install filebeat -y
```
* Once installed, edit the Filebeat main configuration file and configure it to send logs to the Logstash.


### sudo nano /etc/filebeat/filebeat.yml
```
#output.elasticsearch:
  # Array of hosts to connect to.
#  hosts: ["localhost:9200"]
Comment out the following lines:

#output.elasticsearch:
  # Array of hosts to connect to.
#  hosts: ["localhost:9200"]

# Uncomment the following lines:

output.logstash:
hosts: ["localhost:5044"]
```
### Restart service 
```
systemctl start filebeat
systemctl enable filebeat
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
