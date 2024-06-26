# Rule Blocking incoming SSH traffic from Kali VM (10.0.2.4)
### Suricata rule list located at ``/var/lib/suricata/rules/suricata.rules``
![image](https://github.com/goodopsec/SIEM-Network/assets/37912203/cc326573-a5a8-4188-a0c1-3938b7e746e8)
### In Elasticseach I can view the alerts using the "suricata.eve.alert.signature.id". The SSH rule has an SID of 3. As of the past 15 minutes there are no alerts for this rule.
![image](https://github.com/goodopsec/SIEM-Network/assets/37912203/b4646612-6019-4bb8-973f-88ae5bdb8f24)
### Attempting to SSH into Suricata VM (10.0.2.15) via Kali VM
![image](https://github.com/goodopsec/SIEM-Network/assets/37912203/89d0d77b-b146-4cd3-845f-dacec1b4e72c)
### The SSH connection hangs but an alert is generated.
![image](https://github.com/goodopsec/SIEM-Network/assets/37912203/960d9334-fde5-4779-8245-43d523def1de)
## Key JSON data
`` 

     "source": {
      "address": "10.0.2.4",
      "port": 37428,
      "bytes": 199,
      "ip": "10.0.2.4",
      "packets": 3
    },

    "destination": {
      "address": "10.0.2.15",
      "port": 22,
      "bytes": 60,
      "ip": "10.0.2.15",
      "packets": 1
    },
    
     "rule": {
      "name": "SSH connection attempt",
      "id": "3"
    },

     "suricata": {
      "eve": {
        "community_id": "1:05iW6TkFhzyXcIarUPWyJpn7mQ0=",
        "event_type": "alert",
        "alert": {
          "signature_id": 3,
          "rev": 1,
          "gid": 1,
          "signature": "SSH connection attempt",
          "category": ""
        },
        
        "flow_id": "977096556253744",
        "ssh": {
          "client": {
            "proto_version": "2.0",
            "software_version": "OpenSSH_9.0p1"
          }
        },
    ``
