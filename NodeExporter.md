### NodeExporter
#### This container need to be ran client nodes which we need to configure for monitoring:
#### Here in this example,  I run node-exporter container on these nodes 127.0.0.1:9100 , 192.168.100.20:9100 , 192.168.100.199:9100
    podman run -d --name=node-exporter -p 9100:9100 quay.io/prometheus/node-exporter

    Note: container should be persistent after host rebooted
    
#### Add this below entries to "/etc/prometheus/prometheus.yml"

    - job_name: 'node-exporters'
      scrape_interval: 5s
      static_configs:
        - targets: 
          - '127.0.0.1:9100'
          - '192.168.100.20:9100'
          - '192.168.100.199:9100'

#### Restart prometheus service
    systemctl restart prometheus.service

---
#### Go to graphana dashboard to IMPORT prometheus data source for Node-Exporter with ID 1860

![Photo](https://github.com/Adrianhein/NodeExporter-cAdvisor/blob/main/images/import.png)
#
![Photo](https://github.com/Adrianhein/NodeExporter-cAdvisor/blob/main/images/1860_for-node-exporter.png)

---
#### And then we can see now in the dashboard

![Photo](https://github.com/Adrianhein/NodeExporter-cAdvisor/blob/main/images/127.png)
#
![Photo](https://github.com/Adrianhein/NodeExporter-cAdvisor/blob/main/images/199.png)
#
![Photo](https://github.com/Adrianhein/NodeExporter-cAdvisor/blob/main/images/20.png)

---
### OS firewalld service disabled state for this senario
