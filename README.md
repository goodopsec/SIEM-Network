# SIEM-Network Overview
![image](https://github.com/goodopsec/SIEM-Network/assets/37912203/b8ef674c-7609-4a57-9871-4dd385c27e09)

# Kali VM
- Serves as the attacker

# Suricata Host
- An Ubuntu VM running Suricata, DVWA, Filebeat, and Auditbeat
- Suricata serves as the HIPS
- Filebeat ships Suricata logs to ElasticSearch
- Auditbeat ships logs pertaining to events on the hosts

# Kibana/ElasticSeach Host
- An Ubuntu VM running Kibana and ElasticSearch
- Elasticsearch proccesses the log information
- Kibana is to view and analyze the data parsed from elasticsearch
