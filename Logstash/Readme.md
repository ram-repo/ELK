## Logstash

### File Format suppourts
*   logstash.conf
*   logstash.conf.j2
*   logstash.conf.template



## Logstach Configuration 
```
cd /etc/logstash/conf.d/filename.config
```
### Input Filebeats and Out Put Elasticsearch
```
input
{
    beats 
    {
        port => 5044
    }
}
filter
{
    grok 
    {
        "match" => { "message" => "%{COMBINEDAPACHELOG}"}
    }
}
output 
{
    elasticsearch
    {
        index => "apache-%{+yyyy.MM.dd}"
        hosts => "10.128.0.9"
    }
    
}

```

## Service cmd
sudo systemctl start logstash.service
sudo systemctl enable logstash.service
sudo systemctl status logstash.service