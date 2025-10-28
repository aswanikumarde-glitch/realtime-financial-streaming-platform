# realtime-financial-streaming-platform

**Real-time Financial Streaming on AWS:** Kafka → Databricks (Spark Structured Streaming) → Delta Lake (S3) → Analytics.

## Architecture (AWS)
- **Kafka** (Amazon MSK or local Docker) publishes `financial-transactions` events  
- **Databricks on AWS** consumes via Spark Structured Streaming  
- **Delta Lake on S3** stores bronze/silver/gold tables with ACID & time-travel  
- **Alerts** via Amazon SNS on high-risk transactions  
- **Dashboards** using Databricks SQL / Power BI

See: `architecture/mermaid-architecture.md`

## Quick Start
1) **Config**  
   - Edit `config/streaming-config.json` (set your S3 bucket + region)  
   - If using MSK, edit `config/kafka-config.json` with MSK bootstrap brokers

2) **Local event generator** (demo)
```bash
pip install kafka-python
python src/ingestion/kafka_producer.py
