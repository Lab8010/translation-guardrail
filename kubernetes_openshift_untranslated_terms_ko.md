# Korean Subtitling Addendum: Red Hat Kubernetes & OpenShift Training Videos

## 1. Introduction
This document is the **Korean-specific addendum** for producing subtitles for Red Hat technical training videos narrated in English (e.g., DO180, DO280 course solution walkthroughs). It assumes the reader already has the language-neutral term list from `kubernetes_openshift_glossary_common.md` — the "which terms stay in English and why" question is answered there. This file covers only what is specific to Korean: subtitle rules that don't apply to every language (most importantly, particle/case-marker attachment, which has no equivalent in Japanese), and one Korean example sentence per term.

Read `kubernetes_openshift_glossary_common.md` first for:
- The full glossary (Recommended Form, Category, Justification) for every term referenced below.
- The common subtitle rules that apply to all target languages (screen-literal matching, literal identifiers, lab/command lines, course codes, numbers/units, spoken filler, case sensitivity, no pluralizing the retained term, subtitle brevity).

---

## 1a. Korean-Specific Subtitle Rules
Apply these on top of the common rules in the glossary file.

1. **Script constraint.** Retained terms must never be transliterated into Hangul (한글 표기) — e.g., `Deployment` must not become "디플로이먼트" when referring to the API resource. The subtitle term must match the visible English text on screen verbatim. Different translators transliterating the same term inconsistently (e.g., 파드 vs 포드 for `Pod`) is itself a reason to keep the term in English.
2. **Particle attachment (조사 결합) — the key Korean-specific issue.** Korean, unlike Japanese, requires choosing between paired particles (을/를, 이/가, 은/는, 과/와, 으로/로) depending on whether the preceding word ends in a consonant sound (받침, "batchim") or a vowel sound. Because the retained term stays in Latin script, decide the particle by how the term is *pronounced* in Korean, not by its English spelling:
   - Mentally sound out the term as it would be transliterated (e.g., `Pod` → 파드, ends in a vowel sound → use 를/가/는/와): `Pod를 생성합니다`.
   - If the transliterated form ends in a consonant sound (받침) (e.g., `ConfigMap` → 컨피그맵, ends in ㅂ → use 을/이/은/과): `ConfigMap을 생성합니다`.
   - When the correct particle is genuinely ambiguous or awkward (acronyms, multi-word UI labels), sidestep the issue by inserting a short Korean classifier noun instead of guessing: `Actions 드롭다운에서` instead of `Actions에서`, `lab 명령어로` instead of guessing `lab로`/`lab으로`.
   - Section 2 below gives the resolved particle for every glossary term — reuse those forms for consistency across all subtitles in a course.
3. **No space before the particle.** The particle attaches directly to the English term with no intervening space (`Pod를`, not `Pod 를`), exactly as it would attach to a Hangul noun.
4. **Spacing elsewhere (띄어쓰기).** Outside of particle attachment, follow standard Korean spacing rules: leave a space between the English term and any following independent word (e.g., `Pod 리소스를 생성합니다`, not `Pod리소스를`).
5. **Reading-length discipline.** English resource names are long. Keep the Korean wording concise (standard Korean subtitle reading-speed guidelines target roughly 12–15 characters per second) so the subtitle plus the retained English fits on screen. Drop filler from the narration ("what we're going to do right now is…" → 「지금부터는…」) rather than shortening a technical term.
6. **Pluralization.** Do not add "s"/"es" to the retained term, and do not append the Korean plural marker 들 directly onto it. Write "여러 `Pod`" rather than "`Pods`" or "`Pod`들" — plurality is expressed with a quantifier word (여러, 몇 개의, 다수의) placed before the term.

---

## 2. Term-by-Term Particle Reference and Examples
The particle shown is pre-resolved based on the term's pronunciation in Korean (see rule 2 above), so subtitlers do not need to re-derive it per line.

### Core Kubernetes Workload Resources

| Term | Particle Basis | Korean Integration Example |
| :--- | :--- | :--- |
| **Pod** | 파드 (vowel-ending) → 를/가 | `Pod` 안의 컨테이너가 실행 중인지 확인합니다. |
| **Deployment** | 디플로이먼트 (vowel-ending) → 를/가 | `Deployment` 매니페스트를 적용해서 애플리케이션을 업데이트합니다. |
| **ReplicaSet** | 레플리카셋 (ㅅ 받침) → 을/이 | `ReplicaSet`이 레플리카 수를 자동으로 유지합니다. |
| **StatefulSet** | 스테이트풀셋 (ㅅ 받침) → 을/이 | 데이터베이스처럼 상태를 유지해야 하는 애플리케이션에는 `StatefulSet`을 사용합니다. |
| **DaemonSet** | 데몬셋 (ㅅ 받침) → 을/이 | 로그 수집 에이전트는 `DaemonSet`으로 배포됩니다. |
| **Job** | 잡 (ㅂ 받침) → 을/이 | 배치 작업을 실행하기 위해 `Job`을 생성합니다. |
| **CronJob** | 크론잡 (ㅂ 받침) → 을/이 | 정기 실행 작업은 `CronJob`으로 스케줄링합니다. |

### Networking and Storage Resources

| Term | Particle Basis | Korean Integration Example |
| :--- | :--- | :--- |
| **Service** | 서비스 (vowel-ending) → 를/가 | 외부 트래픽을 분산시키기 위해 `Service`를 정의합니다. |
| **Endpoints** | vowel-ending → 를/가 | `oc get endpoints`로 `Endpoints`가 등록되었는지 확인합니다. |
| **Ingress** | 인그레스 (vowel-ending) → 를/가 | 클러스터 외부의 HTTP 트래픽은 `Ingress`로 제어합니다. |
| **PersistentVolume** | 퍼시스턴트볼륨 (ㅁ 받침) → 을/이 | 외부 스토리지의 실체로서 `PersistentVolume`을 생성합니다. |
| **PersistentVolumeClaim** | …클레임 (ㅁ 받침) → 을/이 | 볼륨을 요청하기 위해 `PersistentVolumeClaim`을 정의합니다. |
| **StorageClass** | 스토리지클래스 (vowel-ending) → 를/가 | 동적 프로비저닝을 위해 적절한 `StorageClass`를 지정합니다. |

### Configuration, Metadata, and Scoping

| Term | Particle Basis | Korean Integration Example |
| :--- | :--- | :--- |
| **ConfigMap** | 컨피그맵 (ㅂ 받침) → 을/이 | 환경 변수를 관리하기 위해 `ConfigMap`을 사용합니다. |
| **Secret** | 시크릿 (ㅅ 받침) → 을/이 | 비밀번호 등 민감한 정보는 `Secret`에 저장합니다. |
| **Namespace** | 네임스페이스 (vowel-ending) → 를/가 | 개발 환경과 운영 환경을 `Namespace`로 분리합니다. |
| **CustomResourceDefinition** | CRD, vowel-ending → 를/가 | 사용자 정의 리소스 타입을 추가하기 위해 `CustomResourceDefinition`을 생성합니다. |
| **CustomResource** | 커스텀리소스 (vowel-ending) → 를/가 | 정의한 CRD를 기반으로 `CustomResource`를 배포합니다. |

### OpenShift Specific Resources and Extensions

| Term | Particle Basis | Korean Integration Example |
| :--- | :--- | :--- |
| **Route** | 라우트 (vowel-ending) → 를/가 | `Route`를 생성해서 애플리케이션을 외부에 공개합니다. |
| **DeploymentConfig** | vowel-ending → 를/가 | 레거시 환경에서는 `DeploymentConfig`가 사용되는 경우가 있습니다. |
| **BuildConfig** | vowel-ending → 를/가 | 소스 코드로 이미지를 빌드하는 설정을 `BuildConfig`에 정의합니다. |
| **Build** | 빌드 (vowel-ending) → 를/가 | 새 이미지를 만들기 위해 `Build`를 트리거합니다. |
| **ImageStream** | 이미지스트림 (ㅁ 받침) → 을/이 | 컨테이너 이미지 변경을 감지하기 위해 `ImageStream`을 사용합니다. |
| **ImageStreamTag** | …태그 (vowel-ending) → 를/가 | 특정 버전을 가리키기 위해 `ImageStreamTag`를 지정합니다. |
| **SecurityContextConstraints** | SCC, vowel-ending → 를/가 | Pod에 적절한 권한을 부여하기 위해 `SecurityContextConstraints`를 조정합니다. |
| **ClusterResourceQuota** | …쿼터 (vowel-ending) → 를/가 | 여러 프로젝트에 걸친 제한에는 `ClusterResourceQuota`를 적용합니다. |
| **Project** | 프로젝트 (vowel-ending) → 를/가 | 새 애플리케이션 개발을 위해 `Project`를 생성합니다. |

### Health Checks and Resource Management

| Term | Particle Basis | Korean Integration Example |
| :--- | :--- | :--- |
| **Readiness Probe** | …프로브 (vowel-ending) → 를/가 | `Readiness Probe`가 성공하면 `Endpoints`에 추가됩니다. |
| **Liveness Probe** | vowel-ending → 가 | `Liveness Probe`가 실패하면 컨테이너가 재시작됩니다. |
| **Startup Probe** | vowel-ending → 를 | 시작이 느린 애플리케이션에는 `Startup Probe`를 설정합니다. |
| **Health Check** | (menu action, use classifier) | Actions 메뉴에서 `Add health checks`를 선택합니다. |
| **Requests / Limits** | (use classifier 값) | CPU의 `requests` 값과 `limits` 값을 설정합니다. |
| **millicore(s)** | (attaches to numeral, use 로) | CPU의 request를 `200 millicores`로 설정합니다. |
| **Mi / Gi** | (attaches to numeral, use 로) | 메모리 limit을 `1 Gi`로 설정합니다. |
| **replica(s)** | 레플리카 (vowel-ending) → 로 | 가용성을 위해 `3 replicas`로 스케일합니다. |
| **rollout** | 롤아웃 (ㅅ 받침) → 이 | 변경할 때마다 새로운 `rollout`이 시작됩니다. |

### CLI Commands and Web Console UI Labels

| Term | Particle Basis | Korean Integration Example |
| :--- | :--- | :--- |
| **oc** | 오씨 (vowel-ending) → 로 | `oc set image`로 새 이미지를 지정합니다. |
| **kubectl** | 쿠버컨트롤 (vowel-ending) → 로 | `kubectl`로 리소스를 조작합니다. |
| **lab** | (use classifier 명령어) | `lab grade compreview-scale` 명령어로 채점합니다. |
| **Web Console** | (use 에) | `OpenShift Web Console`에 로그인합니다. |
| **Topology** | (on-screen label, use 에서) | `Topology` 화면에서 frontend `Deployment`를 선택합니다. |
| **Workload** | (use 에) | `Secret`을 `Workload`에 추가합니다. |
| **Actions (drop-down)** | (use classifier 드롭다운) | `Actions` 드롭다운에서 `Edit resource limits`를 선택합니다. |
| **image** | 이미지 (vowel-ending) → 를 | `oc set image`로 배포용 `image`를 업데이트합니다. |

### Identity, Authentication, and Access Control

| Term | Particle Basis | Korean Integration Example |
| :--- | :--- | :--- |
| **Identity Provider (IdP)** | (use 를) | 로그인 시 `Identity Provider`를 선택합니다. |
| **Red Hat Identity Management** | (use 를) | `Red Hat Identity Management`를 IdP로 사용해 인증합니다. |
| **Role-Based Access Control (RBAC)** | pronounced letter-by-letter, vowel-ending → 로 | 역할과 권한은 `RBAC`로 관리합니다. |
| **developer / admin (user)** | (use classifier 사용자) | `developer` 사용자로 로그인합니다. |

### Architecture and Cluster Components

| Term | Particle Basis | Korean Integration Example |
| :--- | :--- | :--- |
| **Cluster** | 클러스터 (vowel-ending) → 의 | `Cluster` 전체의 상태를 확인합니다. |
| **Node** | 노드 (vowel-ending) → 를 | 스케일 아웃을 위해 새 `Node`를 클러스터에 추가합니다. |
| **Control Plane** | 플레인 (ㄴ 받침, use classifier 컴포넌트) | `Control Plane` 컴포넌트의 상태를 모니터링합니다. |
| **Kubelet** | 큐블릿 (ㅅ 받침) → 이 | 각 노드에서 `Kubelet` 서비스가 실행 중이어야 합니다. |
| **kube-apiserver** | …서버 (vowel-ending) → 를 | 모든 작업은 `kube-apiserver`를 통해 처리됩니다. |
| **kube-scheduler** | vowel-ending → 가 | `kube-scheduler`가 최적의 노드를 선택합니다. |
| **kube-controller-manager** | vowel-ending → 가 | 각종 리소스의 상태는 `kube-controller-manager`가 유지합니다. |
| **etcd** | 이티씨디 (vowel-ending) → 의 | `etcd`의 백업을 정기적으로 수행하는 것이 권장됩니다. |

### Advanced Ecosystem and Common Tooling

| Term | Particle Basis | Korean Integration Example |
| :--- | :--- | :--- |
| **Operator** | 오퍼레이터 (vowel-ending) → 를 | `Operator`를 사용해서 복잡한 애플리케이션의 운영을 자동화합니다. |
| **Service Mesh** | vowel-ending → 를 | 마이크로서비스 간 통신 관리를 위해 `Service Mesh`를 도입합니다. |
| **Serverless** | 서버리스 (vowel-ending) → 가 | 이벤트 기반 애플리케이션에는 `Serverless` 아키텍처가 적합합니다. |
| **GitOps** | 깃옵스 (vowel-ending) → 를 | 클러스터 상태를 Git으로 관리하는 `GitOps`를 채택합니다. |
| **Helm** | 헬름 (ㅁ 받침) → 을 | 애플리케이션 패키징에 `Helm` 차트를 사용합니다. |
