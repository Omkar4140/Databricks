''' mermaid
flowchart TD
    subgraph "Data Sources"
        Kafka[Kafka Stream]
        Kinesis[Kinesis Stream]
        Storage[Cloud Storage]
    end

    subgraph "Ingestion with Auto Loader"
        AutoLoader[Databricks Auto Loader]
        Kafka --> AutoLoader
        Kinesis --> AutoLoader
        Storage --> AutoLoader
    end

    subgraph "Delta Lake"
        Bronze[Bronze Layer]
        Silver[Silver Layer]
        Gold[Gold Layer]
        AutoLoader --> Bronze
        Bronze --> Silver
        Silver --> Gold
    end

    subgraph "Analytics and ML"
        Dashboard[Dashboard]
        MLModel[ML Model]
        BI[BI Tool]
        Gold --> Dashboard
        Gold --> MLModel
        Gold --> BI
    end
'''
