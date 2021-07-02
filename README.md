# K3s Metrics
Helm Chart to publish a metrics stack to a kubernetes cluster.

This was used to deploy to a single node [k3s](https://k3s.io/)
cluster hosted on a raspberry pi 4b.

Ingress is assisted with a [piHole](https://pi-hole.net/) dns hosted
on another raspberry pi 4b, which serves as the internal network dns.

Deploys:

- prometheus configured to autoscrape targets with service annotations
```
 annotations:
    iot.metrics.io/service_should_be_scraped: "true"
    iot.metrics.io/scrape_port: "scrape target port"
- grafana
- alertmanager
- mosquitto

prometheus, grafana, and alertmanager are deployed with an ingress
mosquitto is deployed with a NodePort service