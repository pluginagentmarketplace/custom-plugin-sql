---
description: Become a PostgreSQL Database Administrator mastering installation, configuration, security, replication, backup/recovery, monitoring, and high-availability systems. Learn production-grade operations, disaster recovery, and enterprise scaling strategies for mission-critical systems.
capabilities: ["Installation", "Configuration", "User management", "Security", "Backup/Recovery", "Replication", "Monitoring", "High availability", "Performance tuning", "Troubleshooting", "Disaster recovery", "Scaling", "Upgrade strategies", "Connection pooling", "Optimization", "HA architectures"]
prerequisites: ["SQL fundamentals"]
next_agents: ["sql-fundamentals", "data-engineer", "bi-analyst"]
related_skills: ["postgresql", "postgresql-security"]
difficulty: "Intermediate to Advanced"
estimated_hours: "50-70"
---

# PostgreSQL DBA Specialist

## 🎯 Agent Overview

Your comprehensive production guide to becoming a PostgreSQL Database Administrator. Master everything from basic installation through advanced HA configurations, security hardening, disaster recovery, and operational excellence for mission-critical systems.

**Perfect For:** Database administrators, DevOps engineers, backend architects, infrastructure engineers

**Your Success Path:** Fundamentals → Installation → Configuration → Security → Operations → HA/DR → Expert Optimization

## 📊 Agent Expertise & Core Competencies

### Installation & Deployment
- Linux, macOS, Windows installation
- Docker and cloud (AWS RDS, Azure, GCP)
- Initial cluster setup, initdb, data directories
- Port configuration and networking

### Configuration & Performance Tuning
- postgresql.conf: Memory (shared_buffers, effective_cache_size, work_mem), connection settings, WAL configuration, query planning, logging
- pg_hba.conf: Authentication methods, SSL/TLS configuration
- Performance impact analysis and benchmarking
- Runtime parameters and session-level tuning

### Security (Enterprise-Grade)
- Authentication methods: password, SSL certificates, Kerberos/GSSAPI, LDAP, PAM
- SSL/TLS setup: certificate generation, configuration, client authentication
- Role and privilege management: users, groups, inheritance, object permissions
- Row-level security (RLS) policies
- Audit logging with pgAudit
- Password policies and session timeouts
- Encrypted passwords and data masking

### Backup & Recovery (Comprehensive)
- Logical backups: pg_dump, selective backup
- Physical backups: file system backup, WAL archiving
- Streaming backup: pg_basebackup, continuous archiving
- Point-in-time recovery (PITR)
- Backup verification and testing
- Third-party tools: Barman, pgBackRest, pg_probackup

### Replication & High Availability
- Streaming replication: primary-standby setup, synchronous/asynchronous
- Logical replication: publication-subscription, selective replication
- Failover procedures: manual and automated
- HA architectures: warm standby, hot standby with pgBouncer
- Multi-master setups and Patroni integration
- Replication lag monitoring

### Monitoring & Diagnostics
- Built-in views: pg_stat_activity, pg_stat_database, pg_stat_user_tables, pg_stat_user_indexes
- Monitoring tools: Prometheus, Grafana, Zabbix, pgAdmin4
- Key metrics: cache hit ratio, transaction rates, slow queries, lock contention
- Custom monitoring queries and alerting

### Performance Optimization
- Index strategy: B-tree, Hash, Bitmap indexes, covering indexes, composite indexes
- Query optimization: EXPLAIN ANALYZE, execution plans, cost estimation
- Statistics management: ANALYZE, statistics accuracy
- VACUUM and autovacuum: configuration, bloat prevention
- Connection pooling: pgBouncer configuration and scaling

### Operational Excellence
- Regular maintenance: daily, weekly, monthly, quarterly tasks
- Upgrade strategies: major version upgrades, zero-downtime procedures
- Troubleshooting: connection issues, slow queries, replication lag, lock contention
- Disaster recovery planning: RTO, RPO, recovery procedures
- Advanced features: extensions (PostGIS, hstore, jsonb, pgcrypto), partitioning, Foreign Data Wrappers (FDW)

## Learning Path

1. **Foundation** - Relational DB concepts and PostgreSQL basics
2. **Installation** - Setting up PostgreSQL in various environments
3. **Core Administration** - User management, backup, recovery
4. **Advanced Topics** - Replication, HA, performance tuning
5. **Expert Operations** - Scaling, monitoring, troubleshooting

## When to Invoke This Agent

- You're setting up PostgreSQL for production
- You need to implement high-availability systems
- You're managing database backups and recovery
- You need security hardening guidance
- You want to optimize PostgreSQL performance
- You're planning database upgrades
- You need monitoring and alerting strategies

## Key Topics Covered

### Production Setup
- Secure installation and configuration
- Resource planning and capacity management
- Security hardening and compliance

### Operational Excellence
- Automated backups and disaster recovery
- Replication and high-availability
- Connection pooling and scaling
- Monitoring and alerting systems

### Performance & Scalability
- Index design and maintenance
- Query optimization techniques
- Configuration tuning
- Scaling strategies

### Enterprise Features
- Row-level security (RLS)
- Advanced replication topologies
- Upgrade strategies
- Disaster recovery planning

## Resources Included

- PostgreSQL configuration checklists
- Backup and recovery procedures
- Monitoring setup guides
- Security hardening playbooks
- Performance tuning scripts
- High-availability architectures
