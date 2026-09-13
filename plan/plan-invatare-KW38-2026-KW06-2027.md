# Plan de învățare: 14.09.2026 – 14.02.2027

**Durată:** 22 de săptămâni calendaristice (KW 38/2026 – KW 06/2027)
**Ritm:** 2 fire intercalate, 50/50. Fir 1 dimineața, Fir 2 seara.
**Ținta:** rol de DevOps / Application Manager, cu profil hibrid Java + cloud.

---

## Legendă

| Simbol | Înseamnă |
|---|---|
| **F1** | Fir 1: devops și cloud engineering (materie nouă) |
| **F2** | Fir 2: Java application support (consolidarea profilului existent) |
| **PC** | Punct comun: aceeași materie, două perspective. Se învață o singură dată. |
| **⚓** | Ancoră de sincronizare. Firul care ajunge primul așteaptă. |
| **E***n*** | Punct de evaluare |
| **L** | Livrabil în repo |

## Reguli de bază

1. Aplicările la joburi rulează zilnic, în afara planului. Nu se negociază.
2. Ancorele (⚓) se ating în ordine. Datele sunt orientative, ordinea nu.
3. Între ancore, firele pot aluneca liber. Nu se forțează sincronizarea.
4. Dacă un fir termină devreme: write-up în repo sau timp de proiect. Nu se accelerează mai departe.
5. Dacă F1 rămâne în urmă: se taie din coadă, nu se comprimă. Ordinea de sacrificiu: AI/Rekognition → OpenShift ca profunzime → Argo CD ca practică. Nu se taie niciodată Docker, Terraform, Kubernetes de bază.
6. Reevaluare la fiecare 2 săptămâni, notată în `00-STARE.md`, două rânduri.

---

# Luna 1 — KW 38-41 (14.09 – 11.10.2026)

> **Nivel atins la final de lună:** poți administra autonom un server Linux care rulează aplicații Java, poți citi un thread dump și un heap dump, și poți explica de ce un TLS handshake eșuează. Nivel de „application support solid". Încă nu ai nimic cloud.

### KW 38 — 14.09 – 20.09

**F1 · Linux I**
- Filesystem hierarchy, mount, permisiuni, ownership, ACL
- Procese: `ps`, `top`, semnale, nice, procese zombie
- Gestiune pachete (apt/dnf), useri, sudoers
- `journalctl`, rotația logurilor, `logrotate`

**F2 · JVM I: memorie și garbage collection**
- Structura memoriei JVM: heap, metaspace, stack, direct buffers
- Generațiile heap, cum funcționează un GC
- Colectoare: G1, Parallel, ZGC. Ce alegi și de ce
- Flag-uri: `-Xms`, `-Xmx`, `-XX:+UseG1GC`, GC logging
- `jstat`, citirea unui GC log

**L:** README repo `devops-lab`, structura pe module.

### KW 39 — 21.09 – 27.09

**F1 · Linux II**
- systemd: units, targets, dependențe, `systemctl`, servicii proprii
- Tuning: `ulimit`, `sysctl`, file descriptors, swappiness
- Performanță: `vmstat`, `iostat`, `sar`, `lsof`, presiune pe CPU/IO/memorie
- cron și systemd timers

**F2 · JVM II: dumps și troubleshooting** ⚓ **PC: metodologie de troubleshooting**
- Thread dumps: `jstack`, `jcmd`, citirea stărilor de thread, deadlock, contention
- Heap dumps: `jmap`, `HeapDumpOnOutOfMemoryError`, analiză în Eclipse MAT
- Java Flight Recorder și JFR events
- JMX: MBeans, conectare cu JConsole / VisualVM
- Laborator: provoci un OutOfMemoryError și un deadlock, le diagnostichezi

**E1 — Evaluare:** primești un thread dump și un GC log necunoscute. Spui ce se întâmplă în aplicație în maximum 15 minute.
**L:** write-up „Cum citesc un thread dump".

### KW 40 — 28.09 – 04.10

**F1 · Networking I**
- Model TCP/IP, porturi, socket states, `ss`, `netstat`
- DNS: tipuri de înregistrări, rezoluție, `dig`, caching
- Rutare, NAT, subnetting (obligatoriu pentru VPC mai târziu)
- Firewall: `nftables` / `iptables`

**F2 · Connection pools**
- Datasource în Tomcat (`context.xml`) și WildFly (`standalone.xml`)
- Parametri: max pool size, min idle, validation query, timeout-uri
- HikariCP: configurare și leak detection
- Pool exhaustion: cum arată în thread dump, cum se distinge de „baza e lentă"
- Laborator: provoci exhaustion pe PostgreSQL, îl diagnostichezi

### KW 41 — 05.10 – 11.10

**F1 · Networking II: TLS și proxy**
- TLS handshake pas cu pas, cipher suites, SNI, ALPN
- Lanț de certificate, CA, validare, expirare
- nginx și Apache httpd ca reverse proxy: config, headers, timeouts
- HAProxy: backends, health checks, sticky sessions, failover

**F2 · Keystores și certificate** ⚓ **PC: TLS**
- `keytool`, JKS vs PKCS12, import de lanț
- Keystore vs truststore, unde se configurează în Tomcat și WildFly
- mTLS: client certificates, configurare pe ambele capete
- Depanare: `openssl s_client`, handshake failures între proxy și app server
- Reînnoire de certificate fără downtime

**E2 — Evaluare:** configurezi de la zero HAProxy → Tomcat cu TLS și mTLS, apoi spargi lanțul intenționat și îl repari.
**L:** write-up „Depanarea unui TLS handshake failure".

---

# Luna 2 — KW 42-45 (12.10 – 08.11.2026)

> **Nivel atins la final de lună:** scrii scripturi de automatizare în Bash și Python, lucrezi cu Git ca într-o echipă, și înțelegi de ce un deployment Java modern eșuează la migrare. Ești pregătit pentru interviu pe partea de application support. Cloud încă nu.

### KW 42 — 12.10 – 18.10

**F1 · Bash și Git** **PC: Bash, Git**
- Scripturi robuste: `set -euo pipefail`, trap, exit codes, argumente
- `grep`, `sed`, `awk`, procesare de loguri
- Git: branching, merge vs rebase, conflicte, tag-uri
- Workflow: trunk-based vs GitFlow, pull requests, code review
- `.gitignore`, gitleaks, zero secrete în repo (regula de la ziua 1)

**F2 · Logging**
- log4j2 și logback: appenders, layouts, niveluri, schimbare la runtime
- Corelarea request-urilor: MDC, trace ID
- Stivă centralizată: Loki + Promtail (sau ELK dacă vrei varianta enterprise)
- Laborator: loguri Java → stivă centralizată, o căutare utilă la un incident

### KW 43 — 19.10 – 25.10

**F1 · Python I: fundamente**
- Sintaxă de la zero: variabile, `if`, `for`, `while`, funcții
- Structuri de date: list, dict, set, tuple, comprehensions
- Erori și excepții, context managers
- Laborator: rescrii în Python două scripturi Bash din KW 42

**F2 · Java 17 și migrarea jakarta**
- Ce s-a schimbat de la Java 8: module system, API-uri scoase
- `javax.*` → `jakarta.*`: ce sparge și unde
- Compatibilitate WildFly și Payara pe versiuni
- Laborator: migrezi o aplicație mică de pe Java 8 pe 17 și repari ce cade

### KW 44 — 26.10 – 01.11

**F1 · Python II: fișiere și date**
- Fișiere, JSON, YAML, CSV
- Module, pachete, `venv`, `pip`, `requirements.txt`
- `requests`: consum de REST API, tratarea erorilor, retry
- Logging în Python, argparse
- Laborator: script care interoghează un REST API și scrie un raport

**F2 · Artefacte, build și classloading**
- Maven: lifecycle, dependențe, scopes, `settings.xml`. Ant pentru build-uri vechi
- Structura WAR și EAR, `MANIFEST.MF`
- Classloading în Tomcat și WildFly, conflicte de clase, `NoClassDefFoundError`
- Nexus sau Artifactory: repository de artefacte, versionare, snapshots

### KW 45 — 02.11 – 08.11

**F1 · Python III: automatizare**
- Testare cu `pytest`, structura unui proiect Python
- Interacțiune cu sistemul: `subprocess`, `pathlib`, `os`
- Introducere `boto3` (pregătire pentru AWS)
- Laborator: un mic tool de health-check pentru aplicații

**F2 · Autentificare enterprise**
- LDAP și Active Directory: bind, search, grupuri
- SSO, SAML pe scurt, OAuth2 și OIDC în detaliu
- Keycloak: realms, clients, roluri, integrare cu o aplicație Java
- Laborator: protejezi o aplicație cu Keycloak

**E3 — Evaluare:** scrii de la zero, fără ajutor, un script Python care citește un config YAML, apelează un API și raportează. Plus: explici oral fluxul OIDC.
**L:** primul repo de vitrină curat, cu README și 4-5 write-up-uri din F2.

---

# Luna 3 — KW 46-49 (09.11 – 06.12.2026)

> **Nivel atins la final de lună:** containerizezi și rulezi aplicații Java, scrii playbook-uri Ansible care fac deploy real, și lucrezi cu SQL peste nivelul de „am uitat". Aici profilul tău devine vizibil hibrid: application support care știe să automatizeze.

### KW 46 — 09.11 – 15.11 ⚓ **PC: SQL**

**F1 · SQL fundamente**
- SELECT, JOIN-uri, agregări, subqueries, window functions
- Indexuri: tipuri, când ajută, când strică
- Tranzacții, niveluri de izolare, locking, deadlocks
- Normalizare, chei, constrângeri

**F2 · SQL aplicat pe PostgreSQL și DB2**
- `EXPLAIN` / `EXPLAIN ANALYZE`, citirea unui plan de execuție
- Query lent: cum îl găsești (pg_stat_statements), cum îl repari
- Administrare: backup/restore, vacuum, statistici, conexiuni
- Legătura cu connection pools din KW 40

**E4 — Evaluare:** primești o schemă și 3 query-uri lente. Le explici și le optimizezi.

### KW 47 — 16.11 – 22.11 ⚓ **PC: containere**

**F1 · Docker I**
- Imagini vs containere, layers, registry
- Dockerfile: instrucțiuni, cache, multi-stage build
- Volume, bind mounts, rețele, port mapping
- `docker compose` pentru stack-uri multi-serviciu

**F2 · Tomcat și WildFly în container**
- Imagini oficiale, ce configurezi prin variabile de mediu
- Deployment de WAR în container, hot deploy vs imagine imutabilă
- Heap sizing în container: cgroup limits, `MaxRAMPercentage`
- Loguri și JMX dintr-un container

### KW 48 — 23.11 – 29.11

**F1 · Docker II și DevSecOps pe imagini**
- Imagini minimale: distroless, alpine, user non-root
- Scanare: Trivy, SBOM, semnare cu Cosign
- Debugging în container: `exec`, `logs`, ephemeral containers
- Healthchecks, restart policies, resource limits

**F2 · Proiect: stack-ul Java containerizat**
- Aplicație Java + PostgreSQL + nginx în `docker compose`
- Configurare externalizată, secrete în afara imaginii
- Rulezi și diagnostichezi un incident în stack-ul propriu

**L:** repo `java-app-lab` public, cu compose funcțional și README.

### KW 49 — 30.11 – 06.12 ⚓ **PC: Ansible**

**F1 · Ansible**
- Inventar, ad-hoc commands, module de bază
- Playbooks, taskuri, handlers, idempotență
- Roluri, variabile, `group_vars`, templating Jinja2
- `ansible-vault` pentru secrete

**F2 · Ansible aplicat: deploy de WAR pe WildFly**
- Rol care: oprește serviciul, face backup, copiază artefactul, pornește, verifică
- Rollback automat la eșec
- Multi-environment: dev, test, prod cu variabile separate

**E5 — Evaluare:** playbook care face deploy complet plus rollback, rulat de două ori consecutiv cu același rezultat (idempotență dovedită).
**L:** rol Ansible publicat, cu README și exemplu de inventar.

---

# Luna 4 — KW 50-53 (07.12 – 03.01.2027)

> **Nivel atins la final de lună:** știi AWS la nivel de operare (IAM, VPC, EC2, S3, RDS, Lambda) și ai început Terraform. Acum poți candida credibil pe roluri de cloud application manager, nu doar on-premise. Atenție: două săptămâni sunt de sărbători, planul e deliberat mai ușor.

### KW 50 — 07.12 – 13.12

**F1 · AWS I: fundamente**
- IAM: users, roles, policies, assume role, least privilege
- VPC: subnets, route tables, IGW, NAT, security groups vs NACL
- EC2: tipuri de instanțe, AMI, user data, EBS
- S3: buckets, storage classes, policies, lifecycle, presigned URLs
- Costuri și billing alarms (de la început, nu la final)

**F2 · Proiect foto-app: backend**
- API de upload, validare, structura bucket-urilor
- Sesiune fără persistență, ștergere la închidere
- Scris în Python, testat local cu compose

### KW 51 — 14.12 – 20.12

**F1 · AWS II: servicii de aplicație**
- RDS: PostgreSQL managed, backup, multi-AZ, parameter groups
- Lambda: runtime, triggers, layers, limite, cold start
- API Gateway, Route53, CloudWatch (logs, metrics, alarms)
- ECS pe scurt, ca punte spre Kubernetes

**F2 · Proiect foto-app: integrare AWS**
- Upload → S3 → Lambda → S3 output
- IAM roles pentru fiecare componentă
- Loguri în CloudWatch

### KW 52 — 21.12 – 27.12 · *săptămână de sărbători, ritm redus*

**Consolidare, nu materie nouă**
- Curățenie în repo, README-uri, write-up-uri restante
- Actualizare CV cu tot ce ai acumulat în 14 săptămâni
- Pregătire de interviu: 20 de întrebări tehnice pe F2, răspunsuri scrise
- Recapitulare: Linux, JVM, Docker, Ansible

### KW 53 — 28.12 – 03.01.2027 · *săptămână de sărbători, ritm redus*

**F1 · Terraform I (lejer)**
- HCL: resurse, variabile, outputs, data sources
- Providers, `init`, `plan`, `apply`, `destroy`
- State: ce e, de ce contează, backend remote pe S3 + DynamoDB lock

**F2 · Proiect: primele resurse în Terraform**
- Cele două bucket-uri S3 din concept, scrise ca IaC

---

# Luna 5 — KW 01-04 (04.01 – 31.01.2027)

> **Nivel atins la final de lună:** infrastructură ca cod, pipeline de CI/CD funcțional și GitOps. Ăsta e pragul la care titlul de DevOps engineer devine defensibil la interviu, nu doar aspirațional.

### KW 01 — 04.01 – 10.01

**F1 · Terraform II**
- Module: scriere, reutilizare, versionare
- Workspaces, environments, `for_each`, `count`, expresii
- Drift, `import`, refactoring de state
- DevSecOps: `tfsec`, `checkov`, policy as code cu OPA/Conftest

**F2 · Proiect: infrastructura completă în Terraform**
- S3, Lambda, IAM, API Gateway, CloudWatch, totul ca IaC
- Mediu dev și mediu prod din același cod

**E6 — Evaluare:** distrugi complet infrastructura și o reconstruiești din cod, fără intervenție manuală.

### KW 02 — 11.01 – 17.01 ⚓ **PC: Jenkins și CI/CD**

**F1 · CI/CD**
- Jenkins: pipeline as code (`Jenkinsfile`), stages, agents, credentials
- Shared libraries, parametrizare, artifact management
- GitHub Actions: workflows, jobs, secrets, matrix builds
- Strategii de release: blue-green, canary, rollback

**F2 · Pipeline pentru aplicația Java**
- Build Maven → test → scanare (SAST, dependențe, imagine) → push în registry → deploy prin Ansible
- Aici consolidezi Jenkins-ul pe care deja îl cunoști, cu vocabularul modern

### KW 03 — 18.01 – 24.01

**F1 · Argo CD și GitOps**
- Principiul GitOps: Git ca sursă de adevăr, pull vs push
- Applications, Projects, sync policies, self-healing, drift detection
- App of Apps, Kustomize și Helm ca surse
- Secrete în GitOps: Sealed Secrets sau External Secrets
- Flux ca alternativă, la nivel de comparație

**F2 · Proiect: pipeline complet end-to-end**
- De la commit la aplicație rulând, fără pas manual

### KW 04 — 25.01 – 31.01 ⚓ **PC: Kubernetes**

**F1 · Kubernetes I**
- Arhitectura clusterului, pods, replicasets, deployments
- Services, ingress, DNS intern
- ConfigMaps, secrets, volume, persistent volumes
- `kubectl`: logs, describe, exec, port-forward, debugging

**F2 · Aplicația Java pe Kubernetes**
- Probes: liveness, readiness, startup. De ce contează pentru app servers Java
- Resource requests și limits, heap în raport cu limita de memorie
- Graceful shutdown, `terminationGracePeriodSeconds`

---

# Luna 6 (parțial) — KW 05-06 (01.02 – 14.02.2027)

> **Nivel atins la final:** profil hibrid complet. Poți conduce o aplicație Java de la cod la producție pe Kubernetes sau OpenShift, cu IaC, pipeline și observabilitate. Ăsta e exact profilul de Application Manager cu competențe DevOps pe care îl caută enterprise-ul german.

### KW 05 — 01.02 – 07.02 ⚓ **PC: OpenShift**

**F1 · Kubernetes II și OpenShift**
- RBAC, service accounts, namespaces, network policies
- Helm: charts, values, releases
- Autoscaling: HPA, resource management
- OpenShift: Routes vs Ingress, Projects, BuildConfig, ImageStream, Source-to-Image, SecurityContextConstraints, Operators, `oc` vs `kubectl`
- Laborator local: CRC (OpenShift Local) sau OKD

**F2 · Aplicația Java pe OpenShift**
- Deployment prin S2I și prin imagine proprie
- SCC și de ce container-ul tău non-root contează
- Route cu TLS, folosind tot ce ai învățat în KW 41

**E7 — Evaluare:** aceeași aplicație rulând pe Kubernetes și pe OpenShift, cu explicația diferențelor.

### KW 06 — 08.02 – 14.02 ⚓ **PC: observability**

**F1 · Observability**
- Prometheus: arhitectură, scraping, exporteri, PromQL
- Grafana: dashboards, variabile, alerting
- Alertmanager: reguli, rutare, silencing
- OpenTelemetry și tracing distribuit, la nivel de concept plus un exemplu

**F2 · Monitorizarea JVM în Prometheus**
- JMX Exporter sau Micrometer pe aplicația Java
- Dashboard JVM: heap, GC pauses, threads, connection pool
- Alerte utile: memory pressure, GC time, pool exhaustion
- Aici se închide cercul cu JMX-ul din KW 39

**E8 — Evaluare finală:** prezinți proiectul complet ca și cum ai fi la interviu tehnic. 20 de minute: arhitectură, decizii, ce ai învățat, ce ai face altfel.
**L:** repo-ul de vitrină finalizat, README care poate fi citit de un recrutor în 2 minute.

---

## Ce nu a încăput în 22 de săptămâni

Conștient lăsate pe dinafară, în ordinea în care le-ai adăuga dacă ai timp:

1. **AI / Rekognition** în aplicația de poze. Componenta de recunoaștere rămâne stub sau simplă verificare de calitate.
2. **Azure.** Nu se atinge. Un al doilea cloud fără primul solid nu ajută la interviu.
3. **Kafka, Apache Camel, data lake, data warehouse.** Firul de date rămâne pentru după februarie. SQL din KW 46-47 e fundația lui.
4. **Kubernetes la nivel de arhitect.** În 22 de săptămâni ajungi la „operez și depanez", nu la „proiectez clustere".

## Puncte de evaluare, pe scurt

| | Săptămâna | Ce dovedești |
|---|---|---|
| **E1** | KW 39 | Citești un thread dump și un GC log |
| **E2** | KW 41 | Configurezi și depanezi TLS end-to-end |
| **E3** | KW 45 | Scrii Python util fără ajutor |
| **E4** | KW 46 | Optimizezi query-uri pe baza planului de execuție |
| **E5** | KW 49 | Deployment idempotent cu rollback |
| **E6** | KW 01 | Infrastructură reconstruită complet din cod |
| **E7** | KW 05 | Aceeași aplicație pe Kubernetes și OpenShift |
| **E8** | KW 06 | Prezentare de proiect ca la interviu tehnic |

## Realism

Planul are 22 de săptămâni pentru un conținut de aproximativ 24. Compresia e reală și se resimte în lunile 4 și 5, unde AWS, Terraform și CI/CD vin peste munca de proiect, iar două săptămâni sunt de sărbători. Dacă la KW 49 ești în urmă cu mai mult de o săptămână, aplici regula 5 de la început: tai din coadă, nu comprimi.
