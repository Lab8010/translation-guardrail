# Common Glossary: Untranslated Kubernetes & OpenShift Terms (Language-Neutral)

## 1. Purpose
This document is the **language-neutral glossary** for producing subtitles for Red Hat technical training videos that are narrated in English (e.g., DO180, DO280 course solution walkthroughs). It lists the Kubernetes and OpenShift terms — resource types, component names, CLI commands, on-screen UI labels, and literal identifiers — that must be **retained in their original English form** in any target-language subtitle, regardless of which language the video is being localized into.

This file intentionally has **no target-language example sentences and no target-language grammar rules**. Each target language has its own addendum file that:
- Adds language-specific subtitle rules (spacing, particle/case-marker behavior, reading-speed conventions, pluralization handling).
- Provides one example sentence per term showing correct integration into that language.

Currently available addenda:
- Japanese: `kubernetes_openshift_untranslated_terms_ja.md`
- Korean: `kubernetes_openshift_untranslated_terms_ko.md`

When adding a new target language, create a new addendum file following the same pattern rather than duplicating this glossary.

### Why Retain Original English?
1. **On-Screen Correlation:** In a training video the viewer sees the presenter type commands and click UI elements while reading the subtitle. If the subtitle translates or transliterates a term but the console shows the original English string (e.g., `Deployment`), the viewer cannot map the narration to what is on screen. The subtitle term must match the visible English text verbatim.
2. **CLI and API Consistency:** Kubernetes and OpenShift resources are managed via command-line interfaces (`kubectl`, `oc`) and YAML/JSON configuration files. Translating or transliterating names like `Deployment` or `ConfigMap` would make it impossible for viewers to correlate the narration with actual commands and manifests.
3. **Industry Standards:** IT communities worldwide widely adopt English spelling for cloud-native concepts. Translating or transliterating them can sound unnatural, obscure the technical meaning, or produce inconsistent renderings across translators.
4. **Ambiguity Prevention:** Translating a word like "Service" into a generic target-language equivalent may confuse a specific Kubernetes API resource with a generic business or software service.

---

## 2. Common Subtitle Rules
These rules apply regardless of target language. Each language addendum adds further rules on top of these (spacing/particles, reading-speed targets, pluralization mechanics).

1. **Match the screen literally.** Any string the presenter types or that appears in the console — resource names (`quotesdb`, `frontend`, `famous-quotes`), namespaces/projects (`compreview-scale`), secret names (`dbparams`), CLI verbs (`oc set image`), UI menu labels (`Topology`, `Secrets`, `Add health checks`, `Edit resource limits`) — is kept exactly as shown, including case. Do not translate, transliterate, or pluralize it.
2. **Never translate literal identifiers.** Environment-variable names, secret keys, values, usernames, passwords, hostnames, ports, paths, and flags are verbatim: `MYSQL_USER`, `MYSQL_PASSWORD`, `MYSQL_DATABASE`, `HOSTNAME`, `operator1`, `redhat123`, `quotes`, `quotesdb`, `/bin/sh`, `-c`, `mysqladmin`, `-u`, `-p`, `ping`, `/status`, `/env`, `port 8000`, prefixes like `MYSQL_` and `QUOTES_`. These are code, not words.
3. **Keep lab/command lines intact.** Commands such as `lab start compreview-scale`, `lab grade compreview-scale`, `lab finish compreview-scale`, `oc get events -n compreview-scale`, and `oc get endpoints` appear verbatim; translate only the surrounding narration.
4. **Course and product codes stay English.** `DO280`, `DO180`, `Red Hat OpenShift Administration II`, `Red Hat Identity Management`, `Red Hat` — never localize the code; a target-language gloss of the course title may follow in parentheses if helpful.
5. **Numbers and units stay as written.** `200 millicores`, `500 millicores`, `256 Mi`, `1 Gi`, `512 Mi`, `3 replicas`, `3 pods` — keep the numeral and the English unit; do not convert them, though a target-language unit gloss may appear in free prose.
6. **Spoken filler and self-corrections.** Presenters ad-lib ("Ross, sorry, I went to the wrong menu", "happy days", "leaning on our experience"). Render meaning naturally and briefly; these do not need literal or word-for-word subtitles and may be condensed.
7. **Case Sensitivity.** Maintain the exact case sensitivity found in the official technical specifications (e.g., camelCase for `ConfigMap`, lowercase for `kube-apiserver`, capitalized for `Pod`). For literal identifiers this is critical: a grading script may reject `mysql_user`; only `MYSQL_USER` (uppercase) works.
8. **Never pluralize the retained term itself.** Do not add an English `s`/`es`, nor a target-language plural marker, directly onto the retained term. Express plurality using the target language's own quantifier words placed around the term (each addendum specifies the exact mechanism).
9. **Subtitle brevity.** When a line is too long to read comfortably, condense the target-language narration, never the retained English term or a literal identifier. The technical string is the one part of the subtitle the viewer verifies against the screen.

---

## 3. Core Kubernetes Workload Resources

| Term / Resource | Recommended Form | Category | Justification & Guidelines |
| :--- | :--- | :--- | :--- |
| **Pod** | Pod | Workload | Smallest deployable unit in Kubernetes. Never transliterate into the target language's script when referring to the resource; keep the original capitalization. |
| **Deployment** | Deployment | Workload | Declarative updates for Pods and ReplicaSets. Keep capitalized exactly as in the Kubernetes API. |
| **ReplicaSet** | ReplicaSet | Workload | Ensures a specified number of pod replicas are running. Maintain camelCase exactly as in the API. |
| **StatefulSet** | StatefulSet | Workload | Manages deployment and scaling of a set of Pods with unique, stable identities. |
| **DaemonSet** | DaemonSet | Workload | Ensures that all (or some) Nodes run a copy of a Pod. |
| **Job** | Job | Workload | Creates one or more Pods and ensures that a specified number of them successfully terminate. |
| **CronJob** | CronJob | Workload | Manages time-based Jobs using cron syntax. |

---

## 4. Networking and Storage Resources

| Term / Resource | Recommended Form | Category | Justification & Guidelines |
| :--- | :--- | :--- | :--- |
| **Service** | Service | Networking | An abstract way to expose an application running on a set of Pods. Retain the English API name to distinguish it from the generic business concept of a "service". |
| **Endpoints** | Endpoints | Networking | The Endpoints object tracks the IP addresses of Pods backing a Service. Appears verbatim as `oc get endpoints` output on screen; treat as a singular object name. |
| **Ingress** | Ingress | Networking | API object that manages external access to the services in a cluster (typically HTTP). |
| **PersistentVolume** | PersistentVolume (PV) | Storage | A piece of storage in the cluster that has been provisioned by an administrator or dynamically provisioned using Storage Classes. |
| **PersistentVolumeClaim** | PersistentVolumeClaim (PVC) | Storage | A request for storage by a user. |
| **StorageClass** | StorageClass | Storage | Provides a way for administrators to describe the "classes" of storage they offer. |

---

## 5. Configuration, Metadata, and Scoping

| Term / Resource | Recommended Form | Category | Justification & Guidelines |
| :--- | :--- | :--- | :--- |
| **ConfigMap** | ConfigMap | Configuration | Used to store non-confidential data in key-value pairs. Maintain camelCase. |
| **Secret** | Secret | Configuration | Objects containing a small amount of sensitive data such as passwords, tokens, or keys. |
| **Namespace** | Namespace | Scoping | A mechanism to isolate groups of resources within a single cluster. |
| **CustomResourceDefinition** | CustomResourceDefinition (CRD) | Extension | Allows users to add custom resources to their Kubernetes cluster. |
| **CustomResource** | CustomResource (CR) | Extension | An instance of a CustomResourceDefinition. |

---

## 6. OpenShift Specific Resources and Extensions

OpenShift introduces several native resources that extend Kubernetes functionality. These must strictly follow the original casing used in the OpenShift API and `oc` CLI.

| Term / Resource | Recommended Form | Category | Justification & Guidelines |
| :--- | :--- | :--- | :--- |
| **Route** | Route | OpenShift Net | OpenShift's way of exposing a service externally (creates a hostname). Do not translate or transliterate the resource name. |
| **DeploymentConfig** | DeploymentConfig | OpenShift Workload | OpenShift-specific resource for managing deployments (older than Kubernetes Deployment but still used). |
| **BuildConfig** | BuildConfig | OpenShift Build | Defines a build process in OpenShift (Source-to-Image, Dockerfile, etc.). |
| **Build** | Build | OpenShift Build | The actual execution instance of a BuildConfig. |
| **ImageStream** | ImageStream | OpenShift Registry | Abstraction for referencing container images from within OpenShift. |
| **ImageStreamTag** | ImageStreamTag | OpenShift Registry | References a specific tag of an ImageStream. |
| **SecurityContextConstraints** | SecurityContextConstraints (SCC) | OpenShift Security | Controls permissions for Pods (similar to PodSecurityStandards/PSP). Crucial security term. |
| **ClusterResourceQuota** | ClusterResourceQuota | OpenShift Management | Resource quotas that can span multiple projects. |
| **Project** | Project | OpenShift Scoping | An extension of Kubernetes Namespace providing multi-tenancy features. Do not translate or transliterate the API object name. |

---

## 7. Health Checks and Resource Management
These appear constantly in solution walkthroughs when configuring probes and setting requests/limits from the web console. Retain English to match the console labels the viewer sees.

| Term / Concept | Recommended Form | Category | Justification & Guidelines |
| :--- | :--- | :--- | :--- |
| **Readiness Probe** | Readiness Probe / readiness probe | Health | Determines when a Pod is ready to receive traffic; its endpoint is added to the Service only when it passes. Matches the "Add health checks" console dialog. |
| **Liveness Probe** | Liveness Probe / liveness probe | Health | Determines whether a Pod should be restarted. On failure the Pod is killed and the restart count increases. |
| **Startup Probe** | Startup Probe / startup probe | Health | Delays liveness/readiness checks until the application has started. |
| **Health Check** | Health Check | Health | Umbrella term; also the exact console menu label "Add health checks". Keep English when referring to the menu action. |
| **Requests / Limits** | requests / limits | Resource Mgmt | The requested and maximum CPU/memory for a container ("Edit resource limits" dialog). Keep English for the fields and the console label. |
| **millicore(s)** | millicore (m) | Unit | CPU unit (1000m = 1 core). Keep the numeral and unit as shown, e.g. `200 millicores`. Note the common mistake of confusing `500 millicores` with `500 cores`. |
| **Mi / Gi** | Mi / Gi | Unit | Binary memory units (Mebibyte/Gibibyte). Never convert or translate, e.g. `256 Mi`, `1 Gi`, `512 Mi`. |
| **replica(s)** | replica | Scaling | The number of Pod copies. Keep English for the count concept, e.g. `3 replicas`. (See also `ReplicaSet`.) |
| **rollout** | rollout | Deployment | A new deployment/rollout is triggered by each change (e.g. `oc set image`). |

---

## 8. CLI Commands and Web Console UI Labels
Anything the presenter types or clicks is shown on screen; the subtitle must reproduce it verbatim.

| Term / Label | Recommended Form | Category | Justification & Guidelines |
| :--- | :--- | :--- | :--- |
| **oc** | oc | CLI | The OpenShift CLI. Keep the command and all subcommands/flags verbatim, e.g. `oc set image`, `oc get events`, `oc get endpoints`. |
| **kubectl** | kubectl | CLI | The Kubernetes CLI. Never translate. |
| **lab** | lab | CLI (Training) | The Red Hat training lab command. Keep the full line verbatim, e.g. `lab start compreview-scale`, `lab grade compreview-scale`, `lab finish compreview-scale`. |
| **Web Console** | Web Console | Console | The OpenShift web console. Keep English when naming the product UI; a target-language gloss is acceptable in prose. |
| **Topology** | Topology | Console UI | The Topology view in the Developer perspective. It is an on-screen label — do not translate. |
| **Workload** | Workload | Console UI | The console's grouping for deployable resources ("Add to workload", "select the workload"). Keep English to match the UI. |
| **Actions (drop-down)** | Actions | Console UI | The Actions drop-down menu label. Keep verbatim, along with its items (`Add health checks`, `Edit resource limits`). |
| **image** | image | Registry | A container image reference. Keep English in commands and when it is the console field, e.g. `oc set image`. |

---

## 9. Identity, Authentication, and Access Control
| Term / Concept | Recommended Form | Category | Justification & Guidelines |
| :--- | :--- | :--- | :--- |
| **Identity Provider (IdP)** | Identity Provider (IdP) | Auth | The source that authenticates users. Keep English when it is the login-screen option or an API concept. |
| **Red Hat Identity Management** | Red Hat Identity Management (IdM) | Auth (Product) | Red Hat product name used as an identity provider. Never translate the product name. |
| **Role-Based Access Control (RBAC)** | RBAC / role-based access control | Auth | Access model in Kubernetes/OpenShift. Keep the acronym `RBAC`; the expansion may be glossed. |
| **developer / admin (user)** | developer / admin | Auth (Identifier) | Literal usernames demonstrated in the lab. Keep verbatim as identifiers, not as generic job titles. |

---

## 10. Architecture and Cluster Components

| Term / Component | Recommended Form | Category | Justification & Guidelines |
| :--- | :--- | :--- | :--- |
| **Cluster** | Cluster | Architecture | A set of node machines for running containerized applications. Keep in English when part of an architecture label or component name (a target-language gloss is acceptable in prose). |
| **Node** | Node | Architecture | A worker machine in Kubernetes (VM or physical machine). English is preferred for precise technical context. |
| **Control Plane** | Control Plane | Architecture | The collection of components that make global decisions about the cluster. English is preferred for technical architectural documents. |
| **Kubelet** | Kubelet | Component | The primary "node agent" that runs on each node. |
| **kube-apiserver** | kube-apiserver | Component | Component on the control plane that exposes the Kubernetes API. |
| **kube-scheduler** | kube-scheduler | Component | Control plane component that watches for newly created Pods with no assigned node, and selects a node for them to run on. |
| **kube-controller-manager** | kube-controller-manager | Component | Control plane component that runs controller processes. |
| **etcd** | etcd | Component | Consistent and highly-available key value store used as Kubernetes' backing store for all cluster data. |

---

## 11. Advanced Ecosystem and Common Tooling

| Term / Concept | Recommended Form | Category | Justification & Guidelines |
| :--- | :--- | :--- | :--- |
| **Operator** | Operator | Pattern / Concept | A method of packaging, deploying and managing a Kubernetes application. |
| **Service Mesh** | Service Mesh | Ecosystem | An infrastructure layer for managing service-to-service communication (e.g., Red Hat OpenShift Service Mesh based on Istio). |
| **Serverless** | Serverless | Ecosystem | Cloud-native development model for creating apps without managing servers (e.g., OpenShift Serverless based on Knative). |
| **GitOps** | GitOps | Paradigm | Operational framework that takes DevOps best practices used for application development and applies them to infrastructure automation. |
| **Helm** | Helm | Tooling | A package manager for Kubernetes. |
