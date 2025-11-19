# Bitcoin RPC Node with Ephemeral GitHub Runners, Metrics, and Snapshot Automation

This repository provides a fully containerized, production-ready environment for running a **Bitcoin testnet RPC node**, complete with:

- Ephemeral GitHub Actions runners deployed via AWS Fargate
- JSON-RPC aggregation and proxying using Flask (`jsonrpcserver.py`) and OpenResty
- Snapshot automation using EBS and DynamoDB-based locking
- Rolling deployments based on real-time sync status from Prometheus metrics
- Full monitoring and alerting stack (Prometheus + Alertmanager → Slack)

---

## Architecture Overview

```text
+----------------------------+
|    GitHub Actions Runners |  <-- Dockerized, ephemeral, GitHub App-based
+----------------------------+

+--------------------------+    +------------------------+
|    OpenResty Proxy       |<-->|   Bitcoin RPC Node     |
+--------------------------+    +------------------------+
        |                                |
        +--> healthcheck.lua             |
        |                                +--> Prometheus metrics
        +--> JSON-RPC router             |
        +--> jsonrpcserver.py ----------->
             |
             +-> Aggregates and proxies inbound JSON-RPC calls
```

# This repository contains only the documentation and overview.

The full implementation is private. If you would like access to the full implementation, please open a new GitHub issue using the “Access Request” template
