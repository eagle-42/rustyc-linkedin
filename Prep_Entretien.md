# Préparation entretien — PROJET B
## POSTE - (client final)

> **Entretien final = avec le client, EN ANGLAIS.** Ils se présentent d'abord, puis te posent *« What do you understand about Project B? »*, puis tu te présentes en reliant ton expérience. Objectif : montrer que tu as compris le **problème business** + l'**architecture technique**, et que ton parcours coche les cases.
>
> ⚠️ Process rapide (appel d'offre) — à finaliser avant mercredi. Sois prêt, carré, direct.

---

## 0. Cheat sheet (à relire 10 min avant)

| Élément | Réponse |
|---|---|
| Le projet en 1 phrase | Plateforme de calcul distribuée GPU, greenfield, sur AA, pour accélérer et réduire le coût des calculs de la plateforme de scenario planning du client |
| Mon rôle | **Software-engineering-first DevOps + Cloud Ops** — pas du pur SRE. J'écris du tooling et des frameworks, pas juste de l'exploitation |
| Kernel de calcul | Rust / gRPC, GPU-bound, owned par l'équipe interne du client |
| Couche distribuée | Apache Pulsar (orchestration/messaging) |
| Données / I/O | LU / sur AA |
| Observabilité | Grafana + Prometheus |
| CI/CD & IaC | GitLab CI + Terraform |
| Mes chiffres chocs | MTTR < 5 min (GE) · jobs HPC jusqu'à 2 semaines en run continu · 10 ans plateformes critiques |
| Mon angle de progression | À l'aise DevOps/cloud/obs en contexte HPC ; je consolide le pointu perf GPU/CPU via la Gray Scott School (bootcamp HPC/GPU) |
| Package | 78K fixe accepté · je pousse un variable sur réussite + revalo au renouvellement |

---

## 1. Comprendre PROJET B (leur 1re question)

### Le problème business
Le client édite une plateforme d'**AI-driven scenario planning** (planification stratégique, financière et opérationnelle — finance & supply chain). Aujourd'hui, la plateforme tourne bien sur **CPU**, mais les clients demandent **toujours plus de calcul** : plus lourd, plus long, avec des pics (« spiky ») difficiles à absorber et à contrôler côté coût. La plateforme n'était **pas conçue pour du calcul distribué** au départ.

### La solution (PROJET B)
Construire **from scratch** une plateforme de calcul **distribuée, cloud-native (AA), qui pool du GPU** (et bascule GPU/CPU) pour faire tourner les calculs **plus vite et moins cher**. Le code n'est **pas encore en prod** côté distribué : les choix techno sont faits, mais presque tout reste à bâtir → **ambiguïté + design from scratch**, pas de la maintenance.

### L'architecture (à savoir dessiner)
```
   Client / soumission de calcul
              │
   ┌──────────▼───────────┐
   │  Couche distribuée    │  ← apache (messaging, propagation de contexte)
   │  orchestration/msg    │
   └──────────┬───────────┘
              │
   ┌──────────▼───────────┐
   │  Compute kernel       │  ← Rust / gRPC, GPU-bound (owned par l'équipe interne client)
   │  (CPU ⇄ GPU pooling)  │
   └──────────┬───────────┘
              │
   ┌──────────▼───────────┐
   │  Données / I/O        │  ← TROTRO / FF for TROTRO (AA)
   └──────────────────────┘

   ↑ MA COUCHE : operational layer
     CI/CD · env de dev · benchmarking · frameworks de test · observabilité · IaC
```

### Ta phrase d'ouverture (anglais)
> *"As I understand it, Project B is a greenfield, GPU-accelerated distributed compute platform built on AA. The goal is to take a planning workload that today runs on CPU and doesn't scale well with spiky demand, and re-architect it as a distributed, GPU/CPU-pooled platform that runs calculations faster and more cost-effectively. The Rust/gRPC compute kernel is owned by your internal team; around it sits a distributed layer on Apache Pulsar and a high-performance data layer on TROTRO/FF. My role lives in the operational layer above that — CI/CD, dev environments, benchmarking and observability frameworks — and it's explicitly a software-engineering-first DevOps role, not pure operations."*

C'est la réponse qui pose tout : tu montres que tu as compris le **business**, l'**archi**, et **ton périmètre**.

---

## 2. Ta présentation (self-pitch)

### Version courte EN (60-90 sec, à dire après leur question projet)
> *"I'm a DevOps, Data and Software engineer with around ten years on critical platforms — e-health, R&D, finance and industry. My common thread is taking fragile or non-existent setups and turning them into industrialised, observable, reliable platforms.*
>
> *Most relevant for Project B: at General Electric I worked on an HPC simulation platform with compute jobs running up to two weeks. I built Rust/gRPC microservices to drive the compute workflows — submission, control, post-job recovery — and a real-time observability stack with Grafana and VictoriaMetrics that brought MTTR under five minutes, with a proper SRE approach: SLOs, error budgets, post-mortems.*
>
> *At Renault/Ampère I built a GitLab CI/CD chain from scratch and secured GCP cloud access for automated workloads. At Groupama I led Python and DataOps pipelines for sensitive financial data, with full CI/CD automation and a strong focus on traceability and auditability.*
>
> *So I'm comfortable on the DevOps, cloud and observability side, including in an HPC context. Where I'm deliberately sharpening — and why I joined the Gray Scott School HPC/GPU bootcamp — is the very low-level GPU/CPU performance work. I want to bring my platform and reliability know-how to an environment where performance really is critical, which is exactly Project B."*

### Règle d'or
- **Relie chaque point à leur besoin.** Pas un CV récité : « j'ai fait X → c'est utile pour vous parce que Y ».
- **Assume tes acquis, cadre ta progression.** Tu ne « rattrapes pas un retard », tu « consolides du pointu GPU/CPU ». Le reste, tu sais déjà faire.
- **Ne sors jamais tes lacunes en négatif.** Le bootcamp HPC = preuve de proactivité, pas d'insuffisance.

---

## 3. Mapping expérience → besoins du poste

| Ce qu'ils veulent | Ta preuve concrète | Phrase d'accroche |
|---|---|---|
| Rust / gRPC (lire le kernel) | Microservices Rust/gRPC pour workflows HPC chez GE | "I've written Rust/gRPC services to orchestrate HPC compute workflows" |
| CI/CD from scratch | Chaîne GitLab CI from scratch chez Renault/Ampère | "I built a GitLab CI chain from zero — base image, pipeline templates, external SDK integration" |
| Workflow distribué pour système GPU | Soumission/contrôle/reprise post-job de jobs HPC (GE) | "I designed submission, control and recovery flows for long-running compute jobs" |
| Observabilité / métriques utiles | Stack OTel + Grafana + VictoriaMetrics, MTTR < 5 min | "I instrument end-to-end — metrics, logs, traces — and define what actually matters: SLOs" |
| Kubernetes en prod | K8s dans ta stack (déploiement, configs, troubleshooting) | À consolider — voir §4 |
| Apache Pulsar (ou Kafka/Spark) | Expérience messaging/streaming + Spark (Korian)  | "I haven't used Pulsar itself, but I've worked with streaming systems and the model maps directly, the concepts map directly to Pulsar"  |
| TROTRO / FF | Pas de hands-on — je sais l'instrumenter (débit, IOPS, latence métadata) | "I'd own the observability of that layer, not operate the filesystem internals|
| IaC (Terraform/Ansible) | Ansible massif (GE, Groupama, Korian), Terraform dans la stack | "Heavy Ansible across roles, Terraform for provisioning" |
| Contexte finance | Groupama — pipelines finance audités, traçabilité direction financière | "I've operated under financial-grade traceability and audit requirements" |
| Culture SRE/reliability | SLO, error budgets, post-mortems, guidelines (GE) | "Reliability-first: SLOs, error budgets, blameless post-mortems" |

---

## 4. Deep-dive technique — questions probables & réponses

> Réponds en **anglais**, en STAR quand c'est une expérience (Situation → Task → Action → Result).

### Rust / gRPC
**Q : Talk about your Rust experience.**
- GE : microservices Rust/gRPC pour piloter des workflows HPC (soumission, contrôle, reprise post-job). Pourquoi Rust : sûreté mémoire + perf + binaires statiques sans runtime → idéal pour de l'outillage sur chemins critiques.
- Sois honnête sur le niveau : *"I'm productive in Rust for systems tooling and gRPC services; I'm not claiming kernel-level GPU Rust yet — that's part of what I'm deepening."* Ils ont dit Rust « ou capacité à monter en compétence ».
- Anticipe : *reading from the kernel* via gRPC, mise à jour du protocole gRPC (`.proto`, versioning, rétro-compat). Sur CUDA, sois net : "I haven't written CUDA — the GPU kernel is your internal team's domain. My value is the operational layer around it: benchmarking, observability, CI/CD. The Gray Scott bootcamp is where I'm building the low-level GPU intuition.

### CI/CD from scratch
**Q : How would you build CI/CD for a distributed GPU system from scratch?**
- Story Renault : image de base → templates de pipeline → intégration SDK externe → accès cloud sécurisés (IAM, service accounts headless).
- Pour PROJET B : pipelines GitLab, build reproductible des composants Rust, tests + benchmarks intégrés au pipeline, artefacts versionnés, promotion dev→prod, secrets gérés proprement.

### Design de workflow distribué GPU (ils veulent une story)
**Q : How would you design distributed components for a GPU system?**
- Découplage soumission ↔ exécution via Pulsar (les workers consomment les messages).
- Scheduling GPU : pools d'instances GPU, requests/limits, node selectors/taints en K8s.
- Gestion du spiky : autoscaling (HPA + cluster autoscaler), file d'attente Pulsar comme buffer.
- Reprise sur erreur : idempotence, retries, reprise post-job (tu l'as fait chez GE).
- SLURM : à citer en connaissance du paysage, pas en vécu. "Historically SLURM owns scheduling in HPC, including GPU; you've gone for a Pulsar-based cloud-native design, which makes sense here." Ne prétends pas l'avoir opéré.

### Observabilité — quelles métriques ?
**Q : What kind of metrics are useful here?**
- **Système** : utilisation GPU (occupancy, mémoire), CPU, I/O TROTRO (débit, IOPS, latence métadata), saturation file Pulsar.
- **Métier/perf** : temps par calcul, throughput jobs, **coût par calcul** (clé pour un client qui veut réduire les coûts), comparaison output/perf GPU vs CPU.
- **Fiabilité** : taux d'erreur, MTTR, SLO/error budgets.
- Propagation de contexte : trace-id propagé à travers Pulsar (OpenTelemetry) pour suivre un calcul de bout en bout.

### Story GE (STAR) — ton meilleur atout :

S : plateforme de simulation HPC, jobs jusqu'à 2 semaines, aucune visualisation temps réel de l'avancement/santé des calculs.
T : donner à la R&D du temps réel et fiabiliser la plateforme.
A : stack OpenTelemetry + Grafana + VictoriaMetrics, métriques système & métier en continu, SLO et budgets d'erreur définis avec la R&D, post-mortems.
R : MTTR < 5 min, culture reliability-first installée.

Le pont vers PROJET B : "At GE the compute was CPU-bound, but the observability and reliability methodology is identical. What changes for Project B is what you measure: GPU occupancy and memory, TROTRO I/O, Pulsar queue depth, and above all cost per computation and GPU-vs-CPU output comparison. The framework transposes directly."

### Kubernetes en prod (à consolider)
**Q : Kubernetes in production?**
- Objets : Deployment, Service, ConfigMap/Secret, Jobs/CronJobs (batch de calcul).
- GPU : NVIDIA device plugin, `nvidia.com/gpu` requests, pools GPU dédiés.
- Autoscaling : HPA, cluster autoscaler — lien direct avec le « spiky compute ».
- Si on creuse au-delà de ton vécu : *"I've deployed and operated workloads on K8s; cluster-level GPU scheduling at scale is an area I'm actively deepening."* Honnête + proactif.

### Apache Pulsar
**Q : Experience with Pulsar / Kafka / Spark?**
- Concepts : topics, producers/consumers, subscriptions ; **découple** soumission et exécution.
- Pulsar vs Kafka : multi-tenancy natif, séparation compute/stockage, geo-replication — pertinent pour une plateforme distribuée. Spark (Korian) pour le traitement distribué.
- Honnête : concepts maîtrisés via systèmes similaires, montée rapide sur Pulsar spécifiquement.

### Optimisation coût & GPU
**Q : How would you optimise cost and GPU usage for distributed workflows?**
 - Sois honnête : tu n'as pas fait d'optimisation coût GPU en hands-on. 
 - Vends le raisonnement, pas un faux vécu :
  - "I haven't done GPU cost optimisation hands-on, but the approach is clear: you can't optimise what you don't measure. First, benchmark GPU vs CPU on cost per computation, not just speed. Then route work to GPU only where the gain justifies it, use spot instances for tolerant batch, right-size GPU instance families, and pack workloads. The benchmark decides."
  - Pour un poste from-scratch, savoir comment aborder le problème vaut plus qu'un vécu sur une autre stack.

### Terraform / alternatives
**Q : Terraform — et une alternative ?**
- Terraform = provisioning d'infra (state distant S3+lock, modules réutilisables).
- Alternatives à citer : Pulumi (IaC en vrai langage de prog, cohérent avec une équipe software-first), AA CDK, OpenTofu (fork open-source de Terraform). Montre que tu connais le paysage.

### TROTRO
**Q : TROTRO?**
- FS parallèle haute perf ; sur AA = **FF for TROTRO** (lié à S3, scratch vs persistent, débit par TiB).
- Ce que tu **instrumentes** : débit, IOPS, latence métadata, saturation OST. C'est là que ton observabilité rejoint la couche données.

---

## 5. Comment tu vois le rôle (cadrage important)

Le client a été **explicite** : c'est un **software-engineering-first DevOps avec dimension Cloud Ops — PAS du pur SRE**. Tu dois **écrire du tooling et des frameworks**, pas seulement exploiter.

**Ta réponse type :**
> *"I see it as a software-engineering role with a strong cloud-ops dimension, not pure infra operations. The value I bring is building the operational foundations as real software — CI/CD, reproducible dev environments, testing and benchmarking frameworks, and observability — so the team can iterate fast on a system that's still being designed. I'm comfortable contributing to code, not just running infrastructure."*

C'est exactement ce qu'ils veulent entendre. Tu confirmes que tu n'es pas un « gendarme infra » mais un builder.

---

## 6. Comportemental / Cultural fit (STAR prêt)

> Ils valorisent **transparence + communication**. Réponses honnêtes, jamais défensives.

**« Have you ever had a disagreement with a colleague? »**
- S : désaccord technique sur une approche (ex. archi monitoring chez GE/Korian).
- T : trancher sans casser la relation.
- A : j'ai exposé les trade-offs factuellement, écouté son angle, proposé de tester les deux sur un critère mesurable / ou escaladé proprement au manager si besoin.
- R : décision prise sur des faits, relation intacte. *"The point isn't to win — it's to make the right call transparently."*

**« Have you ever missed a deadline? »**
- La **bonne** réponse (ils l'ont quasi soufflée) : *"What matters is to communicate early. I flagged the risk to my manager as soon as I saw it, explained the why, and we re-prioritised together."* Transparence > excuse.

**« Have you worked in an agile environment? »**
- Oui — Renault/Ampère en **SAFe**. Cérémonies, itérations, collaboration inter-équipes. Donne un exemple concret.

**Autres à préparer :**
- Pourquoi quitter le freelance pour un CDI ? → *"I want to commit long-term to a hard, meaningful platform problem and a strong team, rather than rotating between missions."*
- Contexte international / anglais → tu es à l'aise (préviens si tu veux qu'ils ralentissent un peu, c'est normal et bien vu).

---

## 7. Questions à leur poser (prépare-en 4-5)

- *What are the first tasks you'd want me to tackle in my first weeks on Project B?*
- *The team has 10 years of experience together — what does the current state of the distributed layer look like, and what have the three people already onboarded built so far?*
- *Who owns the infrastructure today, and where's the boundary between the internal kernel team and the operational layer I'd own?*
- *Is Apache Pulsar locked in, or still being validated?*
- *What does success look like for Project B in the first 6–12 months?*
- *How do you balance speed of iteration with reliability at this early stage?*

Ces questions montrent que tu penses **delivery, périmètre et fiabilité** — pas juste « est-ce que j'aurai le poste ».

---

## 8. Kit anglais (entretien en anglais)

**Pour gagner du temps / cadrer :**
- *"Let me make sure I understand the question correctly…"*
- *"To give you a concrete example from my experience…"*
- *"I'd approach it in two steps: first… then…"*
- *"I want to be transparent here:"* (avant une réponse honnête sur une limite)

**Vocabulaire à avoir fluide :**
compute kernel · distributed layer · message broker · context propagation · throughput · latency · GPU occupancy · cost per computation · autoscaling · reproducible environments · error budget · blameless post-mortem · idempotency · spot instances · right-sizing.

**Si tu bloques sur un mot :** ne te fige pas, reformule. *"How can I put this…"* / *"In other words…"* C'est mieux vu que de t'arrêter.

**Conseil :** si tu utilises Whisper Flow ou un outil de transcription pour t'entraîner, fais 2-3 répétitions à voix haute de ta présentation et de ta réponse « What do you understand about Project B ». C'est ce qui fera la différence le jour J.

---

## 9. Package (rappel — surtout pas le sujet de l'entretien technique)

---

## 10. Checklist finale (J-1)

- [ ] Je sais réciter ma réponse *"What do you understand about Project B"* (la phrase d'ouverture §1) sans notes
- [ ] Self-pitch EN de 60-90 sec rodé à voix haute (§2)
- [ ] 3 stories STAR prêtes : GE (Rust+obs+MTTR), Renault (CI/CD from scratch), Groupama (finance/traçabilité)
- [ ] Je sais dessiner l'archi kernel → Pulsar → TROTRO → operational layer
- [ ] Réponse « software-eng-first, pas pure SRE » prête (§5)
- [ ] 3 réponses comportementales (désaccord, deadline, agile) en mode transparence
- [ ] 4-5 questions à leur poser
- [ ] Vocabulaire anglais HPC/GPU fluide
- [ ] Chiffres en tête : MTTR < 5 min · jobs 2 semaines · 10 ans
- [ ] Setup technique OK (connexion, caméra, environnement calme) si visio
- [ ] Process finalisé avant mercredi

---

### Le mindset du jour J
Tu n'es pas en train de demander une faveur. Ils ont **gagné un appel d'offre**, ont besoin de livrer, ont **déjà placé 3 personnes**, et t'ont dit que ton profil **coche toutes les cases**. Tu arrives en **partenaire qui résout leur problème**, pas en candidat qui espère. Tu connais le business, tu connais l'archi. Sois posé, concret, honnête sur ce que tu sais et clair sur ce que tu consolides. C'est gagnable — vas-y en boss.
