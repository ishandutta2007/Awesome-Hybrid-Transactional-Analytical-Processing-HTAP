# Awesome-Hybrid-Transactional-Analytical-Processing-HTAP

# Top Hybrid Transactional/Analytical Processing (HTAP) Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Real-Time Analytics, Distributed SQL & Self-Hosted HTAP Engines*  
**Last updated: November 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Hybrid Transactional/Analytical Processing (HTAP)**. These systems enable organizations to run transactional workloads and analytical queries on the same data without ETL pipelines or separate data warehouses—eliminating the latency and complexity of moving data between OLTP and OLAP systems.

**Examples** include Snowflake Hybrid Tables (Unistore), SingleStore Helios, PingCAP TiDB Cloud, Google Cloud Spanner, CockroachDB Dedicated, AlloyDB for PostgreSQL, Oracle HeatWave, MariaDB SkySQL, Azure Cosmos DB, and AWS Aurora Limitless (the category leaders).

**Open-source emphasis**: HTAP is a domain where open-source tooling is **genuinely mature at the distributed SQL layer but the definition of "HTAP" varies widely**. **TiDB** is the most complete open-source HTAP system—a MySQL-compatible distributed SQL database with **TiFlash**, a columnar engine that replicates row data in real-time and serves analytical queries without impacting transactional performance . **CockroachDB** provides distributed SQL with serializable isolation and strong consistency, though its analytical capabilities are less developed than TiDB's TiFlash . **Apache Doris** and **StarRocks** are MPP analytical engines that can ingest transactional data but are not true HTAP systems (they lack multi-row ACID transactions) . The critical caveat: **commercial platforms differentiate on managed serverless scaling and multi-region consistency**—Google Spanner's TrueTime and Aurora Limitless's distributed transaction handling remain commercial advantages. **SingleStore Helios** offers a managed HTAP platform with universal storage, but the open-source path (SingleStore Free) has limitations .

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-products)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Snowflake Hybrid Tables (Unistore)](https://www.snowflake.com/)**  
  Snowflake's HTAP offering for transactional workloads within the data cloud; Hybrid Tables support row-level ACID transactions and are optimized for low-latency, high-concurrency access while remaining queryable alongside Snowflake's analytical tables.

- **[SingleStore Helios](https://www.singlestore.com/)**  
  Managed HTAP platform with **Universal Storage** (single table serving both transactional and analytical workloads); supports real-time dashboards, JSON/vector data, and hybrid vector search. **Helios** is the fully managed cloud offering; **SingleStore Free** exists but with limits.

- **[PingCAP TiDB Cloud](https://www.pingcap.com/)**  
  Managed TiDB with **TiFlash** for real-time HTAP; separates row store (TiKV) from columnar analytics (TiFlash) so analytical queries do not impact transactional performance.

- **[Google Cloud Spanner](https://cloud.google.com/spanner)**  
  Globally distributed, strongly consistent database with **TrueTime** for external consistency; supports analytical queries via federated queries and BigQuery integration, though it is primarily OLTP.

- **[CockroachDB Dedicated](https://www.cockroachlabs.com/)**  
  Managed distributed SQL with serializable isolation and multi-region survivability; analytical capabilities via columnar indexes and vector search, but not a dedicated HTAP engine.

- **[AlloyDB for PostgreSQL](https://cloud.google.com/alloydb)**  
  Google's managed PostgreSQL-compatible database with **columnar engine** for accelerated analytical queries; bridges OLTP and OLAP without data movement.

- **[Oracle HeatWave](https://www.oracle.com/)**  
  MySQL-compatible HTAP service with in-memory columnar engine for real-time analytics; queries run directly on transactional data without ETL.

- **[MariaDB SkySQL](https://mariadb.com/)**  
  Managed MariaDB with HTAP capabilities via **ColumnStore** for analytical workloads alongside transactional tables.

- **[Azure Cosmos DB](https://azure.microsoft.com/en-us/products/cosmos-db)**  
  Multi-model distributed database with **Synapse Link** for HTAP—analytical queries run against transactional data without impacting performance.

- **[AWS Aurora Limitless](https://aws.amazon.com/rds/aurora/)**  
  Distributed PostgreSQL-compatible database with horizontally scaled write and read capacity; designed for high-throughput transactional workloads with analytical query support.

## Open-Source GitHub Projects

### Full HTAP Engines (TiDB, CockroachDB)

- **[TiDB](https://github.com/pingcap/tidb)**  
  The **most complete open-source HTAP system** (Apache 2.0). Architecture: **TiKV** (row store for OLTP) + **TiFlash** (columnar store for OLAP)—TiFlash replicates data from TiKV in real-time and serves analytical queries without impacting transactional performance . MySQL-compatible; supports ACID transactions, distributed SQL, and real-time analytics in one system . **Best for organizations wanting true HTAP** with MySQL compatibility and separated row/column workloads—but it requires significant operational expertise to deploy and tune.

- **[CockroachDB](https://github.com/cockroachdb/cockroach)**  
  Distributed SQL database with **serializable isolation** and multi-region survivability (Apache 2.0 / BSL for some features). Supports transactional workloads and analytical queries via columnar indexes and vector search . **Best for globally distributed OLTP** needing strong consistency—but analytical capabilities are less mature than TiDB's TiFlash .

### Analytical Engines (Not True HTAP)

- **[Apache Doris](https://github.com/apache/doris)**  
  MySQL-compatible **real-time MPP analytical database** (Apache 2.0). Supports high-concurrency point queries and real-time analytics, but **lacks multi-row ACID transactions**—it is OLAP-first, not HTAP . **Best for real-time analytics** where full transactional guarantees are not required.

- **[StarRocks](https://github.com/StarRocks/starrocks)**  
  Real-time MPP OLAP database (Apache 2.0) with MySQL compatibility and lakehouse acceleration. **Not an HTAP engine**—optimized for analytical workloads, not transactional processing.

### Additional Strong Open-Source Options

- **PostgreSQL + Citus** — Citus extends PostgreSQL for distributed transactions and parallel queries; provides some HTAP-like capabilities (real-time analytics on transactional data) without a separate columnar store . **Best for PostgreSQL teams** wanting scale-out OLTP with analytical queries—but not a dedicated HTAP engine.
- **MySQL + HeatWave (Open Source alternatives)** — Oracle HeatWave is commercial; open-source alternatives for MySQL analytics include **ClickHouse** (via MySQL protocol) or **Apache Doris**—neither provides true HTAP.

**Frameworks for building custom systems**: For a **true open-source HTAP system with separated row/column stores**, TiDB with TiFlash is the mature standard . For **distributed OLTP with some analytical capability**, CockroachDB . For **real-time analytics without full transactional guarantees**, Apache Doris or StarRocks . **No open-source project matches the managed serverless scaling and multi-region consistency** of Google Spanner or Aurora Limitless—those are commercial advantages in infrastructure and global distribution .

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- HTAP platforms handling transactional and analytical workloads must comply with organizational security policies and data governance requirements; **self-hosted solutions place full responsibility for tuning, scaling, and maintaining separation between OLTP and OLAP workloads on the operator**.
- **Open-source HTAP is mature at the distributed SQL layer but the definition varies**—**TiDB is the most complete true HTAP system** with separated row (TiKV) and columnar (TiFlash) stores . **Apache Doris and StarRocks are OLAP engines**, not HTAP—they lack multi-row ACID transactions . Choose based on whether you need true transactional guarantees (TiDB, CockroachDB) or real-time analytics (Doris, StarRocks).
- Verify license terms for commercial use; TiDB and CockroachDB are open-source (check repositories for specific licenses), and Apache Doris/StarRocks use Apache 2.0 .

---

**Made for data platform engineers, database architects, and organizations evaluating HTAP systems.**  
Let's make hybrid transactional/analytical processing more open, but with clear eyes about the definitional differences between true HTAP engines and OLAP systems that ingest transactional data.
