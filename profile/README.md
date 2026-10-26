# Tabsdata — Agentic Data Engineering

**From data request to resolution: hours, not months.**

Tabsdata is an **agentic data engineering platform** built on a **Pub/Sub for Tables** core. An AI agent does the discovery, duplication checks, assembly, and testing; an engineer reviews and approves every change. Every table the agent builds is an immutable, versioned table with lineage recorded by the execution itself — so the agent always knows what depends on what, and nothing it does can be destructive.

- **Website:** https://tabsdata.com
- **Docs:** https://docs.tabsdata.com/guide
- **Tutorials:** https://docs.tabsdata.com/tutorials
- **Release notes:** https://docs.tabsdata.com/release-notes
- **Contact:** hello@tabsdata.com · [LinkedIn](https://www.linkedin.com/company/tabsdata/) · [Substack](https://tabsdata.substack.com)

---

## Why this exists

Every data platform is bolting on agents. An agent stitched across disconnected tools operates blind: it can't see the lineage, semantics, or dependencies that live in the systems around it, so it breaks what it can't see.

Tabsdata was built the other way around. The agent runs inside one system that natively tracks every table, every version, every dependency, and every definition — kept current by a living semantic catalog that classifies data the moment a source or destination is connected.

|  | Tabsdata | Bolted-on agents |
|---|---|---|
| What the agent sees | Every table, version, dependency, and definition | One tool at a time; blind at each platform boundary |
| Lineage | Produced by execution, available at every step | Reconstructed after the fact, if at all |
| Validation | Incremental, before anything propagates | Changes land, then you find out |
| Blast radius | Bounded — every change is a new version, never a mutation | Unbounded — breakage discovered next morning |
| Who approves | A human, every time | Often nobody |

## How it works

Tabsdata treats tables as the unit of data engineering. Dataflows are decoupled Python functions of three kinds:

- **Publishers** bring data in from external systems and land it as versioned tables.
- **Transformers** read tables and produce new tables.
- **Subscribers** deliver tables to external destinations — your warehouse, lake, or application.

Every run of a function produces a new table version. Each version carries its own schema, and the full version history and lineage of a table are stored and readable — by people, by functions, and by the agent.

The agent works the request lifecycle end to end:

1. **Discovery** — the living semantic catalog already knows what data exists, what it means, where it lives, and what has already been built.
2. **Duplication check** — before building anything, the agent checks whether the answer (or part of it) already exists among prior deliveries.
3. **Incremental validation** — the dataflow is assembled step by step; every intermediate step is a versioned table the requester can inspect.
4. **Regression and acceptance** — every change is tested against prior versions before it lands, because every table version and execution is recorded.

Tabsdata exposes all of its functionality over **MCP**, so an external agent (Claude, Cursor, or your own) can be guided through data engineering work on Tabsdata with full context.

## Lands beside your stack, not on top of it

Your warehouse stays the center of gravity — Snowflake, Databricks, GCP, AWS, Azure, wherever your data lives. Tabsdata resolves the request lifecycle around it and delivers governed, versioned tables straight into it. Existing workloads and the tools that run them are untouched; new workloads run end to end on Tabsdata. The adoption decision is per workload, never all at once.

## Get started

```bash
pip install tabsdata
```

Then follow the [getting started guide](https://docs.tabsdata.com/guide) or work through the [tutorials](https://docs.tabsdata.com/tutorials) — installation to your first dataflow.

Tabsdata runs on Kubernetes (self-managed or any public cloud Kubernetes service), on bare metal, and on a development laptop. Your cloud, hybrid, or fully on-premises: data never leaves your network.

**Pricing:** free for self-supported deployments — the full platform, including the agent, the semantic catalog, and lineage. Paid contracts add 24/7 support and indemnification.

## Prove it on one workload

Pick one workload — net-new or fragile. We'll measure time-to-resolution on Tabsdata against your current baseline over 30 days: https://tabsdata.com/prove-it

---

Questions, issues, or ideas → open an issue on the relevant repo or write to hello@tabsdata.com.

## Public repositories

| Repository | Description |
|---|---|
| [tabsdata](https://github.com/tabsdata/tabsdata) | Agentic data engineering built on Pub/Sub for Tables |
| [tabsdata-community-connectors](https://github.com/tabsdata/tabsdata-community-connectors) | Community connectors for Tabsdata publishers and subscribers |
| [tabsdata-benchmarking](https://github.com/tabsdata/tabsdata-benchmarking) | Collection of Tabsdata benchmarks |
| [tabsdata-console](https://github.com/tabsdata/tabsdata-console) | Tabsdata console for VMs |
