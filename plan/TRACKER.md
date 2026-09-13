# TRACKER — nivel pe topic

> Se actualizează **vineri**, la evaluarea săptămânală, și la fiecare ancoră.
> Nu zilnic. Ziua se notează în `00-STARE.md`.

## Cele trei stări

| Stare | Înseamnă |
| --- | --- |
| **R** | Recunosc. Știu că există și ce problemă rezolvă. Nu îl pot folosi. |
| **M** | Pot cu `man`. Îl pot face cu documentația deschisă. |
| **F** | Pot fără ajutor. Îl pot face și îl pot explica altcuiva. |

**Regula de onestitate:** dacă la o evaluare rezultatul contrazice tracker-ul, tracker-ul se corectează, nu evaluarea. Coloana *Data* = ziua în care ai trecut ultima dată în starea curentă.

---

## Luna 1 — KW 38-41 · aplicații Java pe Linux

| KW | Fir | Topic | Stare | Data | Ținta |
| --- | --- | --- | --- | --- | --- |
| 38 | F1 | Filesystem, mount, permisiuni, ACL | | | F |
| 38 | F1 | Procese, semnale, nice, zombie | | | F |
| 38 | F1 | Pachete, useri, sudoers | | | M |
| 38 | F1 | journalctl, logrotate | | | F |
| 38 | F2 | Structura memoriei JVM | | | F |
| 38 | F2 | Generații heap, funcționarea unui GC | | | F |
| 38 | F2 | Colectoare: G1, Parallel, ZGC | | | M |
| 38 | F2 | Flag-uri JVM, GC logging, jstat | | | F |
| 39 | F1 | systemd: units, targets, dependențe | | | F |
| 39 | F1 | Tuning: ulimit, sysctl, file descriptors | | | M |
| 39 | F1 | vmstat, iostat, sar, lsof | | | M |
| 39 | F1 | cron și systemd timers | | | M |
| 39 | F2 | Thread dumps: jstack, jcmd, deadlock | | | F |
| 39 | F2 | Heap dumps: jmap, MAT | | | M |
| 39 | F2 | JFR | | | R |
| 39 | F2 | JMX, MBeans, JConsole | | | M |
| 39 | PC | **Metodologie de troubleshooting** ⚓ | | | F |
| 40 | F1 | TCP/IP, porturi, socket states, ss | | | F |
| 40 | F1 | DNS, dig, caching | | | M |
| 40 | F1 | Rutare, NAT, subnetting | | | M |
| 40 | F1 | nftables / iptables | | | R |
| 40 | F2 | Datasource Tomcat / WildFly | | | F |
| 40 | F2 | HikariCP, leak detection | | | M |
| 40 | F2 | Pool exhaustion: diagnostic | | | F |
| 41 | F1 | TLS handshake, cipher suites, SNI, ALPN | | | F |
| 41 | F1 | Lanț de certificate, CA, validare | | | F |
| 41 | F1 | nginx / httpd ca reverse proxy | | | M |
| 41 | F1 | HAProxy: backends, health checks | | | M |
| 41 | F2 | keytool, JKS vs PKCS12 | | | F |
| 41 | F2 | Keystore vs truststore | | | F |
| 41 | F2 | mTLS | | | M |
| 41 | F2 | openssl s_client, handshake failures | | | F |
| 41 | PC | **TLS** ⚓ | | | F |

## Luna 2 — KW 42-45 · automatizare și profil de interviu

| KW | Fir | Topic | Stare | Data | Ținta |
| --- | --- | --- | --- | --- | --- |
| 42 | PC | Bash robust: set -euo pipefail, trap, exit codes | | | F |
| 42 | PC | grep, sed, awk | | | F |
| 42 | PC | Git: branching, merge vs rebase, conflicte | | | F |
| 42 | PC | Workflow: trunk-based, PR, code review | | | M |
| 42 | PC | .gitignore, gitleaks | | | F |
| 42 | F2 | log4j2 / logback | | | F |
| 42 | F2 | MDC, trace ID | | | M |
| 42 | F2 | Loki + Promtail | | | M |
| 43 | F1 | Python: sintaxă, if/for/while, funcții | | | F |
| 43 | F1 | list, dict, set, tuple, comprehensions | | | F |
| 43 | F1 | Excepții, context managers | | | M |
| 43 | F2 | Java 17: module system, API-uri scoase | | | M |
| 43 | F2 | javax → jakarta | | | F |
| 43 | F2 | Compatibilitate WildFly / Payara | | | M |
| 44 | F1 | Fișiere, JSON, YAML, CSV | | | F |
| 44 | F1 | venv, pip, requirements.txt | | | F |
| 44 | F1 | requests: REST, erori, retry | | | F |
| 44 | F1 | logging, argparse | | | M |
| 44 | F2 | Maven lifecycle, scopes, settings.xml | | | F |
| 44 | F2 | WAR / EAR, MANIFEST.MF | | | M |
| 44 | F2 | Classloading, NoClassDefFoundError | | | F |
| 44 | F2 | Nexus / Artifactory | | | M |
| 45 | F1 | pytest, structura unui proiect Python | | | M |
| 45 | F1 | subprocess, pathlib, os | | | F |
| 45 | F1 | boto3 (introducere) | | | R |
| 45 | F2 | LDAP / AD: bind, search, grupuri | | | M |
| 45 | F2 | OAuth2 și OIDC | | | F |
| 45 | F2 | SAML | | | R |
| 45 | F2 | Keycloak: realms, clients, roluri | | | M |

## Luna 3 — KW 46-49 · SQL, containere, Ansible

| KW | Fir | Topic | Stare | Data | Ținta |
| --- | --- | --- | --- | --- | --- |
| 46 | PC | SELECT, JOIN, agregări, subqueries ⚓ | | | F |
| 46 | PC | Window functions | | | M |
| 46 | PC | Indexuri: tipuri, când ajută | | | F |
| 46 | PC | Tranzacții, izolare, locking, deadlocks | | | F |
| 46 | F2 | EXPLAIN / EXPLAIN ANALYZE | | | F |
| 46 | F2 | pg_stat_statements, query lent | | | F |
| 46 | F2 | Backup/restore, vacuum, statistici | | | M |
| 47 | PC | Imagini vs containere, layers, registry ⚓ | | | F |
| 47 | PC | Dockerfile, cache, multi-stage | | | F |
| 47 | PC | Volume, rețele, port mapping | | | F |
| 47 | PC | docker compose | | | F |
| 47 | F2 | Tomcat / WildFly în container | | | F |
| 47 | F2 | Heap în container: cgroups, MaxRAMPercentage | | | F |
| 48 | F1 | Imagini minimale, non-root, distroless | | | M |
| 48 | F1 | Trivy, SBOM, Cosign | | | M |
| 48 | F1 | Debugging în container | | | F |
| 48 | F1 | Healthchecks, restart policies, limits | | | F |
| 49 | PC | Inventar, ad-hoc, module de bază ⚓ | | | F |
| 49 | PC | Playbooks, handlers, idempotență | | | F |
| 49 | PC | Roluri, group_vars, Jinja2 | | | M |
| 49 | PC | ansible-vault | | | M |
| 49 | F2 | Deploy WAR + rollback pe WildFly | | | F |
| 49 | F2 | Multi-environment | | | M |

## Luna 4 — KW 50-53 · AWS și primul Terraform

| KW | Fir | Topic | Stare | Data | Ținta |
| --- | --- | --- | --- | --- | --- |
| 50 | F1 | IAM: users, roles, policies, assume role | | | F |
| 50 | F1 | VPC: subnets, route tables, SG vs NACL | | | F |
| 50 | F1 | EC2: tipuri, AMI, user data, EBS | | | M |
| 50 | F1 | S3: policies, lifecycle, presigned URLs | | | F |
| 50 | F1 | Costuri și billing alarms | | | M |
| 51 | F1 | RDS: backup, multi-AZ, parameter groups | | | M |
| 51 | F1 | Lambda: runtime, triggers, limite, cold start | | | F |
| 51 | F1 | API Gateway, Route53, CloudWatch | | | M |
| 51 | F1 | ECS | | | R |
| 53 | F1 | HCL: resurse, variabile, outputs, data sources | | | F |
| 53 | F1 | init / plan / apply / destroy | | | F |
| 53 | F1 | State și backend remote | | | F |

## Luna 5 — KW 01-04 · IaC, CI/CD, GitOps, Kubernetes

| KW | Fir | Topic | Stare | Data | Ținta |
| --- | --- | --- | --- | --- | --- |
| 01 | F1 | Module Terraform: scriere, versionare | | | F |
| 01 | F1 | Workspaces, for_each, count | | | M |
| 01 | F1 | Drift, import, refactoring de state | | | M |
| 01 | F1 | tfsec, checkov, OPA/Conftest | | | M |
| 02 | PC | Jenkinsfile: stages, agents, credentials ⚓ | | | F |
| 02 | PC | Shared libraries, artifact management | | | M |
| 02 | PC | GitHub Actions: workflows, secrets, matrix | | | M |
| 02 | PC | Blue-green, canary, rollback | | | M |
| 03 | F1 | GitOps: pull vs push, Git ca sursă de adevăr | | | F |
| 03 | F1 | Argo CD: Applications, sync policies, self-heal | | | M |
| 03 | F1 | Kustomize / Helm ca surse | | | M |
| 03 | F1 | Sealed Secrets / External Secrets | | | R |
| 04 | PC | Pods, replicasets, deployments ⚓ | | | F |
| 04 | PC | Services, ingress, DNS intern | | | F |
| 04 | PC | ConfigMaps, secrets, PV | | | F |
| 04 | PC | kubectl: logs, describe, exec, debugging | | | F |
| 04 | F2 | Probes: liveness, readiness, startup | | | F |
| 04 | F2 | Requests/limits vs heap | | | F |
| 04 | F2 | Graceful shutdown | | | M |

## Luna 6 — KW 05-06 · OpenShift și observability

| KW | Fir | Topic | Stare | Data | Ținta |
| --- | --- | --- | --- | --- | --- |
| 05 | F1 | RBAC, service accounts, network policies | | | M |
| 05 | F1 | Helm: charts, values, releases | | | M |
| 05 | F1 | HPA, autoscaling | | | M |
| 05 | F1 | OpenShift: Routes, BuildConfig, S2I, SCC ⚓ | | | M |
| 05 | F2 | Aplicația Java pe OpenShift | | | M |
| 06 | F1 | Prometheus: scraping, exporteri, PromQL ⚓ | | | F |
| 06 | F1 | Grafana: dashboards, alerting | | | M |
| 06 | F1 | Alertmanager: reguli, rutare, silencing | | | M |
| 06 | F1 | OpenTelemetry, tracing distribuit | | | R |
| 06 | F2 | JMX Exporter / Micrometer | | | F |
| 06 | F2 | Dashboard JVM + alerte utile | | | F |

---

## Evaluări

| | KW | Ce dovedesc | Stare | Data |
| --- | --- | --- | --- | --- |
| **E1** | 39 | Citesc un thread dump și un GC log | | |
| **E2** | 41 | Configurez și depanez TLS end-to-end | | |
| **E3** | 45 | Scriu Python util fără ajutor | | |
| **E4** | 46 | Optimizez query-uri pe baza planului | | |
| **E5** | 49 | Deployment idempotent cu rollback | | |
| **E6** | 01 | Infrastructură reconstruită din cod | | |
| **E7** | 05 | Aceeași aplicație pe K8s și OpenShift | | |
| **E8** | 06 | Prezentare de proiect ca la interviu | | |

Stare posibilă: `trecut` / `repetat` / `—`. O evaluare netrecută se repetă înainte de a merge mai departe.

---

## Reevaluări la 2 săptămâni

| Data | Ce am ajustat |
| --- | --- |
| | |
