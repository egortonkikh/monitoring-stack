Monitoring Stack

Production-grade monitoring stack using Prometheus + Grafana.
Что входит

    Prometheus (port 9090) — time series DB + scraper
    Node Exporter (port 9100) — Linux system metrics
    cAdvisor (port 8080) — Docker container metrics
    Grafana (port 3000) — dashboards

Запуск

docker compose up -d

После старта:

     Grafana: http://localhost:3000 (admin / admin)
     Prometheus: http://localhost:9090
     cAdvisor: http://localhost:8080
     Node Exporter metrics: http://localhost:9100/metrics

Дашборды

Datasource Prometheus автоматически провижинится при старте (см. grafana/provisioning/datasources/prometheus.yml).

Импортированный дашборд:

     Node Exporter Full (ID: 1860) — CPU, RAM, disk, network Linux-сервера

Структура
text
 
  
 
 
monitoring-stack/
├── docker-compose.yml
├── prometheus/
│   └── prometheus.yml          # scrape configs
└── grafana/
    └── provisioning/
        └── datasources/
            └── prometheus.yml  # auto-datasource provisioning
 
 
Что мониторится

     CPU utilization (per core, load average)
     Memory usage (RAM, swap, available)
     Disk usage (per filesystem, I/O)
     Network traffic (per interface)
     Docker containers (CPU, memory, network — via cAdvisor)