# Centralized Log Management — ELK Stack

Full ELK stack deployment using Docker Compose for centralized 
Linux log management and visualization.

## Stack
- **Elasticsearch** — stores and indexes logs
- **Logstash** — parses and transforms logs
- **Kibana** — visualizes logs in dashboards
- **Filebeat** — ships logs from host to Logstash

## Architecture
```
[Debian Host /var/log/]
        ↓
   [Filebeat]
        ↓
   [Logstash] ← parses & tags logs
        ↓
[Elasticsearch] ← stores with daily indices
        ↓
    [Kibana] ← dashboard at http://localhost:5601
```

## Results
- 807+ log entries collected across 2 days
- Daily rolling indices (linux-logs-YYYY.MM.DD)
- Real-time log visualization in Kibana dashboard
- Auth logs and system logs monitored

## How to Run
```bash
docker compose up -d
```

Then open http://localhost:5601 and create a data view:
- Index pattern: linux-logs-*
- Timestamp: @timestamp

## How to Stop
```bash
docker compose down
```
