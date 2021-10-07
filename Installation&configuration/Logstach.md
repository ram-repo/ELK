# Logstach Installation 
```
sudo apt-get update -y
sudo apt-get install logstash -y
```
### configuration 
### nano /etc/logstash/conf.d/logstash.conf
```
#Specify listening port for incoming logs from the beats

input {
  beats {
    port => 5044
  }
}

# Used to parse syslog messages and send it to Elasticsearch for storing

filter {
  if [type] == "syslog" {
     grok {
        match => { "message" => "%{SYSLOGLINE}" }
  }
     date {
        match => [ "timestamp", "MMM  d HH:mm:ss", "MMM dd HH:mm:ss" ]
     }
  }
}

# Specify an Elastisearch instance

output {
  elasticsearch {
    hosts => ["localhost:9200"]
    index => "%{[@metadata][beat]}-%{+YYYY.MM.dd}"
  }
}
```
```
systemctl start logstash
systemctl enable logstash
```
