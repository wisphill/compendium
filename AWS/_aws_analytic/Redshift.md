---
description: Redshift is OLAP (online analytical processing) for analytic and data warehousing
layout: post
---
#aws #analytics #redshift

Redshift is OLAP (online analytical processing) for analytic and data warehousing
### Specification
- RDBMS but not OLTP
- Better x10 performance for other data warehousing
- BI tool like AWS Quicksight can integrate with it.
- vs Athena: It is more faster thanks to index.

### AWS Redshift Cluster
![[Redshift.excalidraw|600]]
Notes: Can use Reserved Instances for cost-saving

### Snapshot and DR
- Incremental snapshot (snapshots only for changes)
- Redshift has mult AZ mode for some cluster
- Automate/ Manual/Restore to new cluster.
- Can copy snapshot to other regions.

### Loading data to Redshift
![[Data flow to Redshift.excalidraw|600]]

### Redshift Spectrum
![[Redshift Spectrum.excalidraw|600]]
Analyze data from S3 without importing to Redshift. Require more power to run.
- Compare with Athena query, it's cost less effort & cost to implement if already using Redshift.