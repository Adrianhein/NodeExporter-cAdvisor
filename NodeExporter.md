### NodeExporter

### 
    podman run -d --name=node-exporter -p 9100:9100 quay.io/prometheus/node-exporter

    Note: container should be persistent after host rebooted
    
### Add /etc/prometheus/prometheus.yml

    - job_name: 'node-exporters'
      scrape_interval: 5s
      static_configs:
        - targets: 
          - '127.0.0.1:9100'
          - '192.168.100.20:9100'
          - '192.168.100.199:9100'

####



