# Medallion Architecture

A medallion architecture is a data design pattern used to logically organize data in a lakehouse, with the goal of incrementally and progressively improving the structure and quality of data as it flows through each layer of the architecture (from Bronze ⇒ Silver ⇒ Gold layer tables). Medallion architectures are sometimes also referred to as "multi-hop" architectures.

## Bronze layer

Raw data.

## Silver layer

Cleansed and conformed data.

## Gold layer

Curated business-level tables.

## References

* databricks | [Medallion Architecture](https://www.databricks.com/glossary/medallion-architecture)
* Medium | [Medallion architecture: best practices for managing Bronze, Silver and Gold](https://piethein.medium.com/medallion-architecture-best-practices-for-managing-bronze-silver-and-gold-486de7c90055)
* LinkedIn | [Consider Gold, Silver, and Bronze for your Data, not just the Olympics](https://www.linkedin.com/pulse/consider-gold-silver-bronze-your-data-just-olympics-ruaidhri-hallinan)
