# Guiderail for Japanese Subtitling of Red Hat Kubernetes & OpenShift Training Videos

## 1. Introduction
This document is the guiderail for producing **Japanese subtitles** for Red Hat technical training videos that are narrated in English (e.g., DO180, DO280 course solution walkthroughs). When the presenter demonstrates work in a terminal or the OpenShift web console, certain technical terms, resource types, component names, CLI commands, on-screen UI labels, and literal identifiers must remain in their original English form inside the Japanese subtitle. This document provides a comprehensive glossary of Kubernetes and OpenShift terminology that should **not** be translated into Japanese characters (Katakana, Hiragana, or Kanji), plus subtitle-specific rules.

### Why Retain Original English?
1. **On-Screen Correlation:** In a training video the viewer sees the presenter type commands and click UI elements while reading the subtitle. If the subtitle says "デプロイメント" but the console shows `Deployment`, the viewer cannot map the narration to what is on screen. The subtitle term must match the visible English text verbatim.
2. **CLI and API Consistency:** Kubernetes and OpenShift resources are managed via command-line interfaces (`kubectl`, `oc`) and YAML/JSON configuration files. Translating names like `Deployment` or `ConfigMap` would make it impossible for viewers to correlate the narration with actual commands and manifests.
3. **Industry Standards:** The Japanese IT community widely adopts English spelling for specific cloud-native concepts. Translating them can sound unnatural or obscure the technical meaning.
4. **Ambiguity Prevention:** Translating a word like "Service" to "サービス" (Sābisu) may confuse a specific Kubernetes API resource with a generic business or software service.

---

## 1a. Subtitle-Specific Rules
Subtitles have constraints that ordinary document translation does not. Apply these rules in addition to the glossary below.

1. **Match the screen literally.** Any string the presenter types or that appears in the console — resource names (`quotesdb`, `frontend`, `famous-quotes`), namespaces/projects (`compreview-scale`), secret names (`dbparams`), CLI verbs (`oc set image`), UI menu labels (`Topology`, `Secrets`, `Add health checks`, `Edit resource limits`) — is kept exactly as shown, including case. Do not translate, transliterate, or pluralize it.
2. **Never translate literal identifiers.** Environment-variable names, secret keys, values, usernames, passwords, hostnames, ports, paths, and flags are verbatim: `MYSQL_USER`, `MYSQL_PASSWORD`, `MYSQL_DATABASE`, `HOSTNAME`, `operator1`, `redhat123`, `quotes`, `quotesdb`, `/bin/sh`, `-c`, `mysqladmin`, `-u`, `-p`, `ping`, `/status`, `/env`, `port 8000`, prefixes like `MYSQL_` and `QUOTES_`. These are code, not words.
3. **Keep lab/command lines intact.** Commands such as `lab start compreview-scale`, `lab grade compreview-scale`, `lab finish compreview-scale`, `oc get events -n compreview-scale`, and `oc get endpoints` appear verbatim; translate only the surrounding narration ("run the command …" → 「…コマンドを実行します」).
4. **Course and product codes stay English.** `DO280`, `DO180`, `Red Hat OpenShift Administration II`, `Red Hat Identity Management`, `Red Hat` — never localize the code; a Japanese gloss of the course title may follow in parentheses if helpful.
5. **Reading-length discipline.** English resource names are long. Keep the Japanese wording concise (aim for ≤ ~2 characters/frame reading speed) so the subtitle plus the retained English fits on screen. Drop filler from the narration ("what we're going to do right now is…" → 「ここでは…」) rather than shortening a technical term.
6. **Numbers and units stay as written.** `200 millicores`, `500 millicores`, `256 Mi`, `1 Gi`, `512 Mi`, `3 replicas`, `3 pods` — keep the numeral and the English unit; do not convert (`millicores` ≠ ミリコア in the value, though ミリコア may be used in free prose).
7. **Spoken filler and self-corrections.** Presenters ad-lib ("Ross, sorry, I went to the wrong menu", "happy days", "leaning on our experience"). Render meaning naturally and briefly; these do not need literal or word-for-word subtitles and may be condensed.
8. **Half-width spacing.** Leave a half-width space between a retained English term and adjacent Japanese characters for readability (e.g., `Pod を作成` not `Podを作成`).

---

## 2. Core Kubernetes Workload Resources

| Term / Resource | Recommended Form | Category | Justification & Guidelines | Japanese Integration Example |
| :--- | :--- | :--- | :--- | :--- |
| **Pod** | Pod | Workload | Smallest deployable unit in Kubernetes. Never translate to Katakana (ポッド) or Kanji when referring to the resource. | `Pod` 内のコンテナが起動しているか確認します。 |
| **Deployment** | Deployment | Workload | Declarative updates for Pods and ReplicaSets. Keep capitalized. | `Deployment` マニフェストを適用して、アプリケーションを更新します。 |
| **ReplicaSet** | ReplicaSet | Workload | Ensures a specified number of pod replicas are running. Maintain camelCase. | `ReplicaSet` によって自動的にレプリカ数が維持されます。 |
| **StatefulSet** | StatefulSet | Workload | Manages deployment and scaling of a set of Pods with unique identities. | データベースなどのステートフルなアプリには `StatefulSet` を使用します。 |
| **DaemonSet** | DaemonSet | Workload | Ensures that all (or some) Nodes run a copy of a Pod. | ログ収集エージェントは `DaemonSet` として配置されます。 |
| **Job** | Job | Workload | Creates one or more Pods and ensures that a specified number of them successfully terminate. | バッチ処理を実行するために `Job` を作成します。 |
| **CronJob** | CronJob | Workload | Manages time-based Jobs. | 定期実行ジョブは `CronJob` でスケジュールします。 |

---

## 3. Networking and Storage Resources

| Term / Resource | Recommended Form | Category | Justification & Guidelines | Japanese Integration Example |
| :--- | :--- | :--- | :--- | :--- |
| **Service** | Service | Networking | An abstract way to expose an application running on a set of Pods. Retain English to separate from generic "services". | 外部からのトラフィックを分散するために `Service` を定義します。 |
| **Endpoints** | Endpoints | Networking | The Endpoints object tracks the IP addresses of Pods backing a Service. Appears as the `oc get endpoints` output on screen — keep verbatim. | `oc get endpoints` で `Endpoints` が登録されているか確認します。 |
| **Ingress** | Ingress | Networking | API object that manages external access to the services in a cluster (typically HTTP). | クラスター外部からの HTTP トラフィックを `Ingress` で制御します。 |
| **PersistentVolume** | PersistentVolume (PV) | Storage | A piece of storage in the cluster that has been provisioned by an administrator or dynamically provisioned using Storage Classes. | 外部ストレージの実体として `PersistentVolume` を作成します。 |
| **PersistentVolumeClaim** | PersistentVolumeClaim (PVC) | Storage | A request for storage by a user. | ボリュームを要求するために `PersistentVolumeClaim` を定義します。 |
| **StorageClass** | StorageClass | Storage | Provides a way for administrators to describe the "classes" of storage they offer. | 動的プロビジョニングのために適切な `StorageClass` を指定します。 |

---

## 4. Configuration, Metadata, and Scoping

| Term / Resource | Recommended Form | Category | Justification & Guidelines | Japanese Integration Example |
| :--- | :--- | :--- | :--- | :--- |
| **ConfigMap** | ConfigMap | Configuration | Used to store non-confidential data in key-value pairs. Maintain camelCase. | 環境変数を管理するために `ConfigMap` を利用します。 |
| **Secret** | Secret | Configuration | Objects containing a small amount of sensitive data such as passwords, tokens, or keys. | パスワードなどの機密情報は `Secret` に格納します。 |
| **Namespace** | Namespace | Scoping | A mechanism to isolate groups of resources within a single cluster. | 開発環境と本番環境で `Namespace` を分離します。 |
| **CustomResourceDefinition** | CustomResourceDefinition (CRD) | Extension | Allows users to add custom resources to their Kubernetes cluster. | 独自のリソースタイプを追加するために `CustomResourceDefinition` を作成します。 |
| **CustomResource** | CustomResource (CR) | Extension | An instance of a CustomResourceDefinition. | 定義した CRD に基づいて `CustomResource` をデプロイします。 |

---

## 5. OpenShift Specific Resources and Extensions

OpenShift introduces several native resources that extend Kubernetes functionality. These must strictly follow the original casing used in the OpenShift API and `oc` CLI.

| Term / Resource | Recommended Form | Category | Justification & Guidelines | Japanese Integration Example |
| :--- | :--- | :--- | :--- | :--- |
| **Route** | Route | OpenShift Net | OpenShift's way of exposing a service externally (creates a hostname). Do not translate to ルート. | `Route` を作成して、アプリケーションを外部公開します。 |
| **DeploymentConfig** | DeploymentConfig | OpenShift Workload | OpenShift-specific resource for managing deployments (older than Kubernetes Deployment but still used). | レガシーな環境では `DeploymentConfig` が使われている場合があります。 |
| **BuildConfig** | BuildConfig | OpenShift Build | Defines a build process in OpenShift (Source-to-Image, Dockerfile, etc.). | ソースコードからイメージをビルドする設定を `BuildConfig` に記述します。 |
| **Build** | Build | OpenShift Build | The actual execution instance of a BuildConfig. | 新しいイメージを作成するために `Build` をトリガーします。 |
| **ImageStream** | ImageStream | OpenShift Registry | Abstraction for referencing container images from within OpenShift. | コンテナイメージの変更を検知するために `ImageStream` を使用します。 |
| **ImageStreamTag** | ImageStreamTag | OpenShift Registry | References a specific tag of an ImageStream. | 特定のバージョンを指すために `ImageStreamTag` を指定します。 |
| **SecurityContextConstraints** | SecurityContextConstraints (SCC) | OpenShift Security | Controls permissions for Pods (similar to PodSecurityStandards/PSP). Crucial security term. | Pod に適切な権限を付与するため `SecurityContextConstraints` を調整します。 |
| **ClusterResourceQuota** | ClusterResourceQuota | OpenShift Management | Resource quotas that can span multiple projects. | 複数プロジェクトを跨ぐ制限には `ClusterResourceQuota` を適用します。 |
| **Project** | Project | OpenShift Scoping | An extension of Kubernetes Namespace providing multi-tenancy features. Do not translate to プロジェクト when referring to the API object. | 新しいアプリケーションの開発用に `Project` を作成します。 |

---

## 6. Health Checks and Resource Management
These appear constantly in solution walkthroughs when configuring probes and setting requests/limits from the web console. Retain English to match the console labels the viewer sees.

| Term / Concept | Recommended Form | Category | Justification & Guidelines | Japanese Integration Example |
| :--- | :--- | :--- | :--- | :--- |
| **Readiness Probe** | Readiness Probe / readiness probe | Health | Determines when a Pod is ready to receive traffic; its endpoint is added to the Service only when it passes. Matches the "Add health checks" dialog. | `Readiness Probe` が成功すると `Endpoints` に追加されます。 |
| **Liveness Probe** | Liveness Probe / liveness probe | Health | Determines whether a Pod should be restarted. On failure the Pod is killed and the restart count increases. | `Liveness Probe` が失敗するとコンテナが再起動されます。 |
| **Startup Probe** | Startup Probe / startup probe | Health | Delays liveness/readiness checks until the application has started. | 起動が遅いアプリには `Startup Probe` を設定します。 |
| **Health Check** | Health Check / ヘルスチェック | Health | Umbrella term; also the exact console menu label "Add health checks". Keep English when referring to the menu action. | Actions メニューから `Add health checks` を選択します。 |
| **Requests / Limits** | requests / limits | Resource Mgmt | The requested and maximum CPU/memory for a container ("Edit resource limits" dialog). Keep English for the fields and the console label. | CPU の `requests` と `limits` を設定します。 |
| **millicore(s)** | millicore (m) | Unit | CPU unit (1000m = 1 core). Keep the numeral and unit as shown, e.g. `200 millicores`. Note the common mistake of confusing `500 millicores` with `500 cores`. | CPU の request を `200 millicores` に設定します。 |
| **Mi / Gi** | Mi / Gi | Unit | Binary memory units (Mebibyte/Gibibyte). Never convert or translate, e.g. `256 Mi`, `1 Gi`, `512 Mi`. | メモリの limit を `1 Gi` に設定します。 |
| **replica(s)** | replica | Scaling | The number of Pod copies. Keep English for the count concept, e.g. `3 replicas`. (See also `ReplicaSet`.) | 可用性のために `3 replicas` にスケールします。 |
| **rollout** | rollout | Deployment | A new deployment/rollout is triggered by each change (e.g. `oc set image`). Keep English or render as ロールアウト consistently. | 変更ごとに新しい `rollout` が開始されます。 |

---

## 7. CLI Commands and Web Console UI Labels
Anything the presenter types or clicks is shown on screen; the subtitle must reproduce it verbatim.

| Term / Label | Recommended Form | Category | Justification & Guidelines | Japanese Integration Example |
| :--- | :--- | :--- | :--- | :--- |
| **oc** | oc | CLI | The OpenShift CLI. Keep the command and all subcommands/flags verbatim, e.g. `oc set image`, `oc get events`, `oc get endpoints`. | `oc set image` で新しいイメージを指定します。 |
| **kubectl** | kubectl | CLI | The Kubernetes CLI. Never translate. | `kubectl` でリソースを操作します。 |
| **lab** | lab | CLI (Training) | The Red Hat training lab command. Keep the full line verbatim, e.g. `lab start compreview-scale`, `lab grade compreview-scale`, `lab finish compreview-scale`. | `lab grade compreview-scale` で採点します。 |
| **Web Console** | Web Console / Web コンソール | Console | The OpenShift web console. Keep English when naming the product UI; a Japanese gloss is acceptable in prose. | `OpenShift Web Console` にログインします。 |
| **Topology** | Topology | Console UI | The Topology view in the Developer perspective. It is an on-screen label — do not translate. | `Topology` ビューで frontend の Deployment を選択します。 |
| **Workload** | Workload | Console UI | The console's grouping for deployable resources ("Add to workload", "select the workload"). Keep English to match the UI. | Secret を `Workload` に追加します。 |
| **Actions (drop-down)** | Actions | Console UI | The Actions drop-down menu label. Keep verbatim, along with its items (`Add health checks`, `Edit resource limits`). | `Actions` ドロップダウンから `Edit resource limits` を選択します。 |
| **image** | image | Registry | A container image reference. Keep English in commands and when it is the console field, e.g. `oc set image`. | `oc set image` でデプロイ用の `image` を更新します。 |

---

## 8. Identity, Authentication, and Access Control
| Term / Concept | Recommended Form | Category | Justification & Guidelines | Japanese Integration Example |
| :--- | :--- | :--- | :--- | :--- |
| **Identity Provider (IdP)** | Identity Provider (IdP) | Auth | The source that authenticates users. Keep English when it is the login-screen option or an API concept. | ログイン時に `Identity Provider` を選択します。 |
| **Red Hat Identity Management** | Red Hat Identity Management (IdM) | Auth (Product) | Red Hat product name used as an identity provider. Never translate the product name. | `Red Hat Identity Management` を IdP として認証します。 |
| **Role-Based Access Control (RBAC)** | RBAC / role-based access control | Auth | Access model in Kubernetes/OpenShift. Keep the acronym `RBAC`; the expansion may be glossed. | ロールと権限は `RBAC` で管理します。 |
| **developer / admin (user)** | developer / admin | Auth (Identifier) | Literal usernames demonstrated in the lab. Keep verbatim as identifiers, not as generic job titles. | `developer` ユーザーとしてログインします。 |

---

## 9. Architecture and Cluster Components

| Term / Component | Recommended Form | Category | Justification & Guidelines | Japanese Integration Example |
| :--- | :--- | :--- | :--- | :--- |
| **Cluster** | Cluster | Architecture | A set of node machines for running containerized applications. Often written in Katakana (クラスター) in prose, but keep in English when part of an architecture label or component name. | `Cluster` 全体のステータスを確認します。 |
| **Node** | Node | Architecture | A worker machine in Kubernetes (VM or physical machine). Can be written as ノード in descriptive text, but English is preferred for precise technical context. | 新しい `Node` をクラスターに追加してスケールアウトします。 |
| **Control Plane** | Control Plane / コントロールプレーン | Architecture | The collection of components that make global decisions about the cluster. Both forms are acceptable; choose English for technical architectural documents. | `Control Plane` コンポーネントの健全性を監視します。 |
| **Kubelet** | Kubelet | Component | The primary "node agent" that runs on each node. | 各ノード上で `Kubelet` サービスが稼働している必要があります。 |
| **kube-apiserver** | kube-apiserver | Component | Component on the control plane that exposes the Kubernetes API. | 全ての操作は `kube-apiserver` を経由して処理されます。 |
| **kube-scheduler** | kube-scheduler | Component | Control plane component that watches for newly created Pods with no assigned node, and selects a node for them to run on. | `kube-scheduler` が最適なノードを選択します。 |
| **kube-controller-manager** | kube-controller-manager | Component | Control plane component that runs controller processes. | 各種リソースの状態は `kube-controller-manager` によって維持されます。 |
| **etcd** | etcd | Component | Consistent and highly-available key value store used as Kubernetes' backing store for all cluster data. | `etcd` のバックアップを定期的に取得することが推奨されます。 |

---

## 10. Advanced Ecosystem and Common Tooling

| Term / Concept | Recommended Form | Category | Justification & Guidelines | Japanese Integration Example |
| :--- | :--- | :--- | :--- | :--- |
| **Operator** | Operator | Pattern / Concept | A method of packaging, deploying and managing a Kubernetes application. | `Operator` を使用して、コンプレックスなアプリケーションの運用を自動化します。 |
| **Service Mesh** | Service Mesh / サービスメッシュ | Ecosystem | An infrastructure layer for managing service-to-service communication (e.g., Red Hat OpenShift Service Mesh based on Istio). | マイクロサービス間の通信管理に `Service Mesh` を導入します。 |
| **Serverless** | Serverless / サーバーレス | Ecosystem | Cloud-native development model for creating apps without managing servers (e.g., OpenShift Serverless based on Knative). | イベント駆動型アプリケーションには `Serverless` アーキテクチャが適しています。 |
| **GitOps** | GitOps | Paradigm | Operational framework that takes DevOps best practices used for application development and applies them to infrastructure automation. | クラスターの状態を Git で管理する `GitOps` を採用します。 |
| **Helm** | Helm | Tooling | A package manager for Kubernetes. | アプリケーションのパッケージ化に `Helm` チャートを使用します。 |

---

## 11. General Rules for Japanese Sentence Structure
When integrating these untranslated English terms into Japanese subtitles and sentences, follow these structural norms:
1. **Case Sensitivity:** Maintain the exact case sensitivity found in the official technical specifications (e.g., camelCase for `ConfigMap`, lowercase for `kube-apiserver`, capitalized for `Pod`). For literal identifiers this is critical: the grading script rejects `mysql_user`; only `MYSQL_USER` (uppercase) works.
2. **Spacing:** It is common in professional Japanese technical writing to leave a half-width space before and after English words when they are enclosed in text, though markdown inline code blocks (backticks `` ` ``) automatically provide visual separation.
3. **Pluralization:** Do not add "s" or "es" for plurals within Japanese context. For instance, write "複数の `Pod`" rather than "複数の `Pods`". The plurality is inferred from the Japanese context (e.g., 複数の, 幾つかの).
4. **Subtitle brevity:** When a line is too long to read comfortably, condense the Japanese narration, never the retained English term or a literal identifier. The technical string is the one part of the subtitle the viewer verifies against the screen.
