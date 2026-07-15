# Japanese Subtitling Addendum: Red Hat Kubernetes & OpenShift Training Videos

## 1. Introduction
This document is the **Japanese-specific addendum** for producing subtitles for Red Hat technical training videos narrated in English (e.g., DO180, DO280 course solution walkthroughs). It assumes the reader already has the language-neutral term list from `kubernetes_openshift_glossary_common.md` — the "which terms stay in English and why" question is answered there. This file covers only what is specific to Japanese: subtitle rules that don't apply to every language, and one Japanese example sentence per term.

Read `kubernetes_openshift_glossary_common.md` first for:
- The full glossary (Recommended Form, Category, Justification) for every term referenced below.
- The common subtitle rules that apply to all target languages (screen-literal matching, literal identifiers, lab/command lines, course codes, numbers/units, spoken filler, case sensitivity, no pluralizing the retained term, subtitle brevity).

---

## 1a. Japanese-Specific Subtitle Rules
Apply these on top of the common rules in the glossary file.

1. **Script constraint.** Retained terms must never be rendered in Katakana, Hiragana, or Kanji — e.g., `Deployment` must not become「デプロイメント」when referring to the API resource. The subtitle term must match the visible English text on screen verbatim.
2. **Reading-length discipline.** English resource names are long. Keep the Japanese wording concise (aim for ≤ ~2 characters/frame reading speed) so the subtitle plus the retained English fits on screen. Drop filler from the narration ("what we're going to do right now is…" → 「ここでは…」) rather than shortening a technical term.
3. **Half-width spacing.** Leave a half-width space between a retained English term and adjacent Japanese characters for readability (e.g., `Pod を作成` not `Podを作成`).
4. **Pluralization.** Do not add "s" or "es" for plurals within Japanese context. For instance, write "複数の `Pod`" rather than "複数の `Pods`". The plurality is inferred from the Japanese context (e.g., 複数の, 幾つかの) — no marker is ever attached to the term itself.
5. **Particles are invariant.** Unlike some target languages (e.g., Korean), Japanese case particles (を, が, は, に, で, と) do not change form based on the preceding word's sound, so no special agreement rule is needed when attaching them to a retained English term.

---

## 2. Core Kubernetes Workload Resources — Examples

| Term | Japanese Integration Example |
| :--- | :--- |
| **Pod** | `Pod` 内のコンテナが起動しているか確認します。 |
| **Deployment** | `Deployment` マニフェストを適用して、アプリケーションを更新します。 |
| **ReplicaSet** | `ReplicaSet` によって自動的にレプリカ数が維持されます。 |
| **StatefulSet** | データベースなどのステートフルなアプリには `StatefulSet` を使用します。 |
| **DaemonSet** | ログ収集エージェントは `DaemonSet` として配置されます。 |
| **Job** | バッチ処理を実行するために `Job` を作成します。 |
| **CronJob** | 定期実行ジョブは `CronJob` でスケジュールします。 |

---

## 3. Networking and Storage Resources — Examples

| Term | Japanese Integration Example |
| :--- | :--- |
| **Service** | 外部からのトラフィックを分散するために `Service` を定義します。 |
| **Endpoints** | `oc get endpoints` で `Endpoints` が登録されているか確認します。 |
| **Ingress** | クラスター外部からの HTTP トラフィックを `Ingress` で制御します。 |
| **PersistentVolume** | 外部ストレージの実体として `PersistentVolume` を作成します。 |
| **PersistentVolumeClaim** | ボリュームを要求するために `PersistentVolumeClaim` を定義します。 |
| **StorageClass** | 動的プロビジョニングのために適切な `StorageClass` を指定します。 |

---

## 4. Configuration, Metadata, and Scoping — Examples

| Term | Japanese Integration Example |
| :--- | :--- |
| **ConfigMap** | 環境変数を管理するために `ConfigMap` を利用します。 |
| **Secret** | パスワードなどの機密情報は `Secret` に格納します。 |
| **Namespace** | 開発環境と本番環境で `Namespace` を分離します。 |
| **CustomResourceDefinition** | 独自のリソースタイプを追加するために `CustomResourceDefinition` を作成します。 |
| **CustomResource** | 定義した CRD に基づいて `CustomResource` をデプロイします。 |

---

## 5. OpenShift Specific Resources and Extensions — Examples

| Term | Japanese Integration Example |
| :--- | :--- |
| **Route** | `Route` を作成して、アプリケーションを外部公開します。 |
| **DeploymentConfig** | レガシーな環境では `DeploymentConfig` が使われている場合があります。 |
| **BuildConfig** | ソースコードからイメージをビルドする設定を `BuildConfig` に記述します。 |
| **Build** | 新しいイメージを作成するために `Build` をトリガーします。 |
| **ImageStream** | コンテナイメージの変更を検知するために `ImageStream` を使用します。 |
| **ImageStreamTag** | 特定のバージョンを指すために `ImageStreamTag` を指定します。 |
| **SecurityContextConstraints** | Pod に適切な権限を付与するため `SecurityContextConstraints` を調整します。 |
| **ClusterResourceQuota** | 複数プロジェクトを跨ぐ制限には `ClusterResourceQuota` を適用します。 |
| **Project** | 新しいアプリケーションの開発用に `Project` を作成します。 |

---

## 6. Health Checks and Resource Management — Examples

| Term | Japanese Integration Example |
| :--- | :--- |
| **Readiness Probe** | `Readiness Probe` が成功すると `Endpoints` に追加されます。 |
| **Liveness Probe** | `Liveness Probe` が失敗するとコンテナが再起動されます。 |
| **Startup Probe** | 起動が遅いアプリには `Startup Probe` を設定します。 |
| **Health Check** | Actions メニューから `Add health checks` を選択します。 |
| **Requests / Limits** | CPU の `requests` と `limits` を設定します。 |
| **millicore(s)** | CPU の request を `200 millicores` に設定します。 |
| **Mi / Gi** | メモリの limit を `1 Gi` に設定します。 |
| **replica(s)** | 可用性のために `3 replicas` にスケールします。 |
| **rollout** | 変更ごとに新しい `rollout` が開始されます。 |

---

## 7. CLI Commands and Web Console UI Labels — Examples

| Term | Japanese Integration Example |
| :--- | :--- |
| **oc** | `oc set image` で新しいイメージを指定します。 |
| **kubectl** | `kubectl` でリソースを操作します。 |
| **lab** | `lab grade compreview-scale` で採点します。 |
| **Web Console** | `OpenShift Web Console` にログインします。 |
| **Topology** | `Topology` ビューで frontend の Deployment を選択します。 |
| **Workload** | Secret を `Workload` に追加します。 |
| **Actions (drop-down)** | `Actions` ドロップダウンから `Edit resource limits` を選択します。 |
| **image** | `oc set image` でデプロイ用の `image` を更新します。 |

---

## 8. Identity, Authentication, and Access Control — Examples

| Term | Japanese Integration Example |
| :--- | :--- |
| **Identity Provider (IdP)** | ログイン時に `Identity Provider` を選択します。 |
| **Red Hat Identity Management** | `Red Hat Identity Management` を IdP として認証します。 |
| **Role-Based Access Control (RBAC)** | ロールと権限は `RBAC` で管理します。 |
| **developer / admin (user)** | `developer` ユーザーとしてログインします。 |

---

## 9. Architecture and Cluster Components — Examples

| Term | Japanese Integration Example |
| :--- | :--- |
| **Cluster** | `Cluster` 全体のステータスを確認します。 |
| **Node** | 新しい `Node` をクラスターに追加してスケールアウトします。 |
| **Control Plane** | `Control Plane` コンポーネントの健全性を監視します。 |
| **Kubelet** | 各ノード上で `Kubelet` サービスが稼働している必要があります。 |
| **kube-apiserver** | 全ての操作は `kube-apiserver` を経由して処理されます。 |
| **kube-scheduler** | `kube-scheduler` が最適なノードを選択します。 |
| **kube-controller-manager** | 各種リソースの状態は `kube-controller-manager` によって維持されます。 |
| **etcd** | `etcd` のバックアップを定期的に取得することが推奨されます。 |

---

## 10. Advanced Ecosystem and Common Tooling — Examples

| Term | Japanese Integration Example |
| :--- | :--- |
| **Operator** | `Operator` を使用して、コンプレックスなアプリケーションの運用を自動化します。 |
| **Service Mesh** | マイクロサービス間の通信管理に `Service Mesh` を導入します。 |
| **Serverless** | イベント駆動型アプリケーションには `Serverless` アーキテクチャが適しています。 |
| **GitOps** | クラスターの状態を Git で管理する `GitOps` を採用します。 |
| **Helm** | アプリケーションのパッケージ化に `Helm` チャートを使用します。 |
