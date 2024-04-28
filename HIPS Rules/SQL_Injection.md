# Detecting SQL Injection
### Using DVWA (Damn Vulnerable Web Application) as a vulnerable webserver
![image](https://github.com/goodopsec/SIEM-Network/assets/37912203/f6569eb0-75ad-4213-b515-65cd2518ddbd)
### Using ``%' or 0=0 union select null, version() #`` to show that it is vulnerable to SQL injection
![image](https://github.com/goodopsec/SIEM-Network/assets/37912203/b31e80f2-32d8-4f24-8720-490c2956b469)

## Suricata Rule
- The single quote ``'``, ``SELECT``, ``UNION`` are commonly used to preform SQL injection attacks
### Using these 3 rules drops the traffic and causes the site to hang
- ``drop http any any -> 10.0.2.15 any (msg: "Possible SQL Injection attack (Contains singlequote)"; flow:established,to_server; content:"'"; nocase; http_uri; sid:4;)``
- ``drop http any any -> 10.0.2.15 any (msg: "Possible SQL Injection attack (Contains UNION)"; flow:established,to_server; content:"union"; nocase; http_uri; sid:5;)``
- ``drop http any any -> 10.0.2.15 any (msg: "Possible SQL Injection attack (Contains SELECT)"; flow:established,to_server; content:"select"; nocase; http_uri; sid:6;)``

![image](https://github.com/goodopsec/SIEM-Network/assets/37912203/0d85a987-bb38-4040-bab5-36a90e64051d)
![image](https://github.com/goodopsec/SIEM-Network/assets/37912203/303bf774-2b02-4846-8a02-d439fe2166ed)

``04/28/2024-11:27:59.308948  [Drop] [1:4:0] Possible SQL Injection attack (Contains singlequote) [Classification: (null)] [Priority: 3] {TCP} 10.0.2.4:38130 -> 10.0.2.15:80`` <br>
``04/28/2024-11:27:59.308948  [Drop] [1:5:0] Possible SQL Injection attack (Contains UNION) [Classification: (null)] [Priority: 3] {TCP} 10.0.2.4:38130 -> 10.0.2.15:80`` <br>
``04/28/2024-11:27:59.308948  [Drop] [1:6:0] Possible SQL Injection attack (Contains SELECT) [Classification: (null)] [Priority: 3] {TCP} 10.0.2.4:38130 -> 10.0.2.15:80``

## Elasticsearch
### Finding the logs in Elasticsearch using the query <br>
- ``suricata.eve.alert.signature_id : 4 or suricata.eve.alert.signature_id:5 or suricata.eve.alert.signature_id:6``
  ![Untitled](https://github.com/goodopsec/SIEM-Network/assets/37912203/53fed23d-db8e-4917-aae9-1209e9acddd4)
