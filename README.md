<p align="center">
  <img src="images/banner.png" alt="HelmsMan Banner"/>
</p>

<h1 align="center">⚓ HelmsMan</h1>

<p align="center">
<b>Autonomous Kubernetes Remediation using the Model Context Protocol (MCP)</b>
</p>

<p align="center">

[![Track](https://img.shields.io/badge/Track-Cloud--Native-blue.svg)](#)
[![Framework](https://img.shields.io/badge/Framework-NitroStack_MCP-orange.svg)](#)
[![Platform](https://img.shields.io/badge/Kubernetes-kind-326CE5.svg)](#)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-3178C6.svg)](#)
[![Node.js](https://img.shields.io/badge/Node.js-18+-339933.svg)](#)
[![License](https://img.shields.io/badge/License-MIT-success.svg)](#)

</p>

<p align="center">
HelmsMan is an <b>MCP (Model Context Protocol) server</b> that enables autonomous Kubernetes remediation using multiple AI agents while enforcing deterministic safety through live Kubernetes policy validation.
</p>

---

# 📖 Overview

Cloud-native infrastructure is becoming increasingly complex, yet Kubernetes operations remain largely manual and reactive. Existing autoscaling mechanisms rely on simple CPU or memory thresholds and lack awareness of operational safety, often resulting in over-provisioned clusters, higher cloud costs, and risky remediation actions.

**HelmsMan** addresses this challenge by introducing a **multi-agent autonomous remediation framework** built on the **Model Context Protocol (MCP)**.

Instead of allowing a single AI model to make infrastructure decisions, HelmsMan orchestrates specialized agents that negotiate proposed actions while a deterministic safety engine validates every operation against the live Kubernetes cluster before execution.

The result is an intelligent remediation system that optimizes infrastructure cost **without compromising application availability**.

---

# 🎯 Key Highlights

- 🤖 Multi-Agent AI Decision Making
- ☸️ Live Kubernetes Cluster Integration
- 🛡️ Programmatic Safety Enforcement
- 💰 Cost-Aware Infrastructure Optimization
- 📜 Complete Audit Trail
- 🔌 Native MCP Tools, Resources & Prompts
- ⚡ Built using NitroStack MCP SDK

---

# ❗ Problem Statement

Modern Kubernetes operations are reactive.

Platform engineers continuously monitor dashboards and manually decide:

- Which deployment should be scaled?
- Can replicas safely be reduced?
- Will the action violate PodDisruptionBudgets?
- Should a deployment be rolled back?
- Is the cluster healthy enough for remediation?

Current autoscalers only react to CPU or memory utilization.

They **do not understand operational safety**.

This often results in:

- 💸 Over-provisioned clusters
- ⚠️ Unsafe scale-down operations
- 🧑‍💻 Continuous manual intervention
- 🚨 Accidental downtime
- 📈 Increased cloud costs

---

# 💡 Our Solution

HelmsMan transforms Kubernetes operations from **reactive monitoring** into **autonomous, policy-aware remediation**.

Instead of relying only on infrastructure metrics, HelmsMan continuously reasons over the **live cluster state** before executing any action.

The workflow consists of:

1. Reading the live Kubernetes cluster
2. Understanding deployments, pods, nodes, and disruption budgets
3. Negotiating remediation decisions using specialized AI agents
4. Validating every action using server-side safety policies
5. Executing only operations that preserve application availability

Unlike traditional AI systems, **HelmsMan never trusts LLM output alone**.

Every infrastructure change is validated directly against the Kubernetes API before execution.

---

# 🔄 Multi-Agent Workflow

<p align="center">
<img src="images/architecture-flow.png" width="950"/>
</p>

### 💰 FinOps Agent

Responsible for:

- Detecting idle workloads
- Identifying over-provisioned deployments
- Optimizing infrastructure costs
- Proposing replica reductions

---

### 🛡️ Availability Guardian

Responsible for:

- Evaluating infrastructure risk
- Inspecting PodDisruptionBudgets
- Preventing unsafe scale-down operations
- Reviewing every remediation proposal

---

### 🔐 Safety Engine

The Safety Engine acts as the final authority.

Before executing any infrastructure action it validates:

- Deployment status
- Replica count
- PodDisruptionBudget
- Minimum available replicas
- Cluster health

If any availability policy would be violated, the operation is rejected before reaching Kubernetes.

---

# 🏗️ System Architecture

<p align="center">
<img src="images/architecture.png" width="1000"/>
</p>

The architecture combines AI reasoning with deterministic policy enforcement.

Rather than allowing agents to directly manipulate Kubernetes resources, all remediation requests pass through the MCP server where safety rules are enforced programmatically before interacting with the Kubernetes API.

---

# 📊 Dashboard

<p align="center">
<img src="images/dashboard.png" width="1000"/>
</p>

The HelmsMan dashboard provides real-time visibility into:

- Cluster topology
- Deployment health
- Pod status
- Agent decisions
- Approved actions
- Rejected actions
- Audit history

Operators can observe the complete remediation lifecycle while maintaining full transparency over every decision made by the system.

---

# ✨ Features

| Feature | Description |
|----------|-------------|
| 🤖 Multi-Agent Negotiation | Specialized AI agents collaboratively decide infrastructure actions |
| ☸️ Live Kubernetes Integration | Reads Deployments, Pods, Nodes, Services and PodDisruptionBudgets |
| 🛡️ Deterministic Safety Engine | Prevents unsafe operations using real Kubernetes policies |
| 💰 Cost Optimization | Detects over-provisioned workloads and recommends efficient scaling |
| 📜 Audit Trail | Records every approved and rejected remediation |
| ⚡ MCP Native | Exposes Tools, Resources and Prompts through the Model Context Protocol |
| 🔍 Real-Time Cluster Reasoning | Continuously evaluates the live cluster state before every action |

---

# 🌐 Live Kubernetes Integration

HelmsMan communicates directly with a running Kubernetes cluster.

Supported resources include:

- Deployments
- Pods
- ReplicaSets
- Nodes
- Services
- Namespaces
- PodDisruptionBudgets
- kube-state-metrics

Unlike simulation-based demonstrations, every decision shown by HelmsMan is derived from the **live Kubernetes API**.

---

# 🛡️ Safety First

Safety is not delegated to AI.

Instead, HelmsMan enforces infrastructure policies directly inside the MCP server.

Every proposed operation undergoes:

- Live Kubernetes API validation
- Replica verification
- PodDisruptionBudget inspection
- Availability checks
- Policy enforcement

Unsafe actions are rejected automatically, ensuring that remediation never compromises application availability.

---

# 🧠 MCP Capabilities

HelmsMan is built as a native **Model Context Protocol (MCP)** server using the **NitroStack MCP SDK**.

It exposes Kubernetes functionality through **Tools**, **Resources**, and **Prompts**, enabling AI agents to reason over and safely operate a live Kubernetes cluster.

---

## 🔧 MCP Tools

| Tool | Description |
|------|-------------|
| `get_cluster_state()` | Returns a live summary of the Kubernetes cluster |
| `get_pod_health(namespace)` | Retrieves pod health and readiness information |
| `list_deployments(namespace)` | Lists deployments within a namespace |
| `scale_deployment(name, replicas)` | Safely scales a deployment after policy validation |
| `rollback_deployment(name)` | Rolls back a deployment to its previous revision |
| `cordon_node(node)` | Marks a node as unschedulable |
| `uncordon_node(node)` | Makes a node schedulable again |
| `drain_node(node)` | Safely evicts workloads from a node |

---

## 📚 MCP Resources

| Resource | Purpose |
|-----------|----------|
| `k8s://cluster/topology` | Live cluster topology |
| `k8s://cluster/nodes` | Node information |
| `k8s://cluster/deployments` | Deployment summaries |
| `k8s://policy/disruption-budgets` | PodDisruptionBudget information |
| `k8s://audit/history` | Complete remediation history |
| `k8s://cluster/metrics` | Cluster metrics collected from kube-state-metrics |

---

## 💬 MCP Prompts

### `cluster_health_brief`

Generates:

- Cluster summary
- Current health status
- Resource utilization
- Recommendations

---

### `change_record`

Produces:

- Approved actions
- Blocked actions
- Reason for rejection
- Safety validation
- Complete audit trail

---

# ⚙️ Technology Stack

| Category | Technologies |
|-----------|--------------|
| **Language** | TypeScript |
| **Runtime** | Node.js |
| **Framework** | NitroStack MCP SDK |
| **Container Platform** | Docker Desktop |
| **Orchestration** | Kubernetes |
| **Local Cluster** | kind |
| **CLI** | kubectl |
| **Metrics** | kube-state-metrics |
| **Infrastructure API** | Kubernetes Client SDK |

---

# 📂 Project Structure

```text
helmsman/
│
├── src/
│   ├── agents/
│   │   ├── orchestrator.ts
│   │   ├── executor.ts
│   │   ├── prompts.ts
│   │   └── tools.ts
│   │
│   ├── modules/
│   │   └── k8s/
│   │       ├── client.ts
│   │       ├── k8s.module.ts
│   │       ├── k8s.tools.ts
│   │       ├── k8s.resources.ts
│   │       ├── k8s.prompts.ts
│   │       ├── safety.ts
│   │       ├── audit.ts
│   │       └── policy.data.ts
│   │
│   ├── app.module.ts
│   └── index.ts
│
├── manifests/
│   ├── namespace.yaml
│   ├── pdbs.yaml
│   └── kube-state-metrics.yaml
│
├── scripts/
│   ├── setup-cluster.ps1
│   ├── setup.sh
│   ├── reset-demo.ps1
│   └── demo-chaos.sh
│
├── images/
│
└── README.md
```

---

# 🚀 Getting Started

## Prerequisites

Install the following before running HelmsMan.

- Node.js **18+**
- Docker Desktop
- Kubernetes CLI (`kubectl`)
- kind
- NitroStudio
- NitroStack CLI

Verify your installation:

```bash
node -v
kubectl version --client
kind version
docker --version
```

---

# 📦 Installation

Clone the repository.

```bash
git clone https://github.com/<your-username>/helmsman.git
```

Move into the project.

```bash
cd helmsman
```

Install dependencies.

```bash
npm install
```

---

# ☸️ Create the Kubernetes Cluster

Using the provided setup script:

### Windows

```powershell
powershell -ExecutionPolicy Bypass -File scripts/setup-cluster.ps1
```

### Linux / macOS

```bash
chmod +x scripts/setup.sh
./scripts/setup.sh
```

Or manually:

```bash
kind create cluster --name helmsman
```

Verify:

```bash
kubectl get nodes
```

---

# 🚀 Deploy Demo Resources

Deploy the sample workloads.

```bash
kubectl apply -f manifests/
```

Verify:

```bash
kubectl get pods -A
```

---

# 🔨 Build the Project

Compile the MCP server.

```bash
npm run build
```

---

# 🧪 Run Safety Tests

Execute the safety validation suite.

```bash
npm run test:safety
```

Expected output:

```text
Running Safety Tests...

✔ Replica validation
✔ PodDisruptionBudget enforcement
✔ Safe scale-down validation
✔ Unsafe operation rejection

Safety self-check: OK
```

---

# ▶️ Start the MCP Server

Run the development server.

```bash
npm run dev
```

or

```bash
npm start
```

---

# 🖥 Connect with NitroStudio

1. Open NitroStudio

2. Import the project

3. Start the MCP Server

4. Connect to the server

5. View available:

- Tools
- Resources
- Prompts

The server is now ready to receive agent requests.

---

# 🎬 Demo Walkthrough

## Step 1 — Start Kubernetes

Create the local **kind** cluster.

```bash
kubectl get nodes
```

Ensure the cluster is healthy.

---

## Step 2 — Deploy the Demo Application

Deploy an intentionally over-provisioned application.

```text
checkout-service

Replicas = 5
```

---

## Step 3 — Request Cost Optimization

The FinOps Agent proposes:

```text
Scale checkout-service

5 replicas

↓

1 replica
```

---

## Step 4 — Guardian Review

The Availability Guardian evaluates:

- Deployment health
- Replica count
- PodDisruptionBudget
- Minimum availability

---

## Step 5 — Safety Validation

The Safety Engine checks the live Kubernetes API.

If scaling would violate a PodDisruptionBudget:

```json
{
  "approved": false,
  "reason": "Scaling would violate PodDisruptionBudget"
}
```

The operation is rejected before reaching Kubernetes.

---

## Step 6 — Audit Trail

Query:

```text
change_record
```

Result:

- Requested action
- Safety validation
- Decision
- Timestamp
- Rejection reason

---

## Step 7 — Verify the Cluster

```bash
kubectl get pods
```

The deployment remains healthy.

No pods are terminated.

Application availability is preserved.

---

# 📈 Observability

HelmsMan continuously reasons over:

- Deployment status
- ReplicaSets
- Pod readiness
- Node conditions
- Cluster topology
- PodDisruptionBudgets
- kube-state-metrics
- Previous remediation history

This allows the AI agents to make informed decisions using the current cluster state rather than relying on static metrics.


# 🌟 Why HelmsMan?

Traditional Kubernetes tooling focuses on monitoring metrics and reacting to predefined thresholds. HelmsMan introduces an AI-driven, policy-aware remediation framework that reasons over the live cluster state before executing any infrastructure change.

## Comparison

| Traditional Kubernetes Operations | ⚓ HelmsMan |
|-----------------------------------|------------|
| CPU/Memory Threshold Autoscaling | Multi-Agent AI Decision Making |
| Reactive Monitoring | Autonomous Remediation |
| Manual Scaling Decisions | Intelligent Cost Optimization |
| No Operational Reasoning | Live Cluster State Reasoning |
| Safety Depends on Engineers | Deterministic Safety Engine |
| No Negotiation | Multi-Agent Negotiation |
| Limited Auditability | Complete Audit Trail |
| Metrics Only | Metrics + Kubernetes Policies |

---

# 🛡️ Safety by Design

HelmsMan follows a **"Trust, but Verify"** approach.

AI agents are free to propose remediation actions, but **they never interact directly with the Kubernetes API**.

Instead, every operation flows through the MCP server where the Safety Engine validates:

- Deployment status
- Replica count
- PodDisruptionBudget constraints
- Minimum available replicas
- Cluster health
- Kubernetes API responses

Only validated operations are executed.

This architecture guarantees that **availability is enforced programmatically rather than relying solely on LLM reasoning**.

---

# 📊 Example Workflow

```text
                    User Request
                          │
                          ▼
                 FinOps Agent Analysis
                          │
                          ▼
             Availability Guardian Review
                          │
                          ▼
             HelmsMan Safety Engine
                          │
        ┌─────────────────┴─────────────────┐
        │                                   │
        ▼                                   ▼
 Policy Passed                      Policy Violated
        │                                   │
        ▼                                   ▼
 Execute via Kubernetes API          Reject Operation
        │                                   │
        └──────────────┬────────────────────┘
                       ▼
                Audit Trail Updated
```

---

# 🔐 Safety Guarantees

HelmsMan guarantees that every remediation action:

- ✅ Preserves PodDisruptionBudget constraints
- ✅ Protects minimum replica availability
- ✅ Validates against the live Kubernetes API
- ✅ Records every action in the audit history
- ✅ Rejects unsafe infrastructure changes automatically

---

# 📸 Project Screenshots

## System Architecture

<p align="center">
<img src="images/architecture.png" width="900"/>
</p>

---

## Multi-Agent Workflow

<p align="center">
<img src="images/architecture-flow.png" width="900"/>
</p>

---

## NitroStudio Dashboard

<p align="center">
<img src="images/dashboard.png" width="900"/>
</p>

---

# 🔮 Future Roadmap

We plan to extend HelmsMan with several advanced cloud-native capabilities.

### Kubernetes

- Horizontal Pod Autoscaler integration
- Vertical Pod Autoscaler integration
- Multi-cluster federation
- StatefulSet remediation
- DaemonSet support

### AI

- Predictive scaling using historical metrics
- LLM-generated remediation plans
- Incident root-cause analysis
- Autonomous rollback recommendations
- Learning-based optimization strategies

### DevOps

- ArgoCD integration
- GitOps workflows
- Prometheus AlertManager integration
- Grafana dashboards
- Slack & Microsoft Teams notifications

### Security

- RBAC-aware AI agents
- Policy-based access control
- OPA / Gatekeeper integration
- Compliance-aware remediation

---

# 🏆 Hackathon Highlights

✅ Built using the **NitroStack MCP SDK**

✅ Native **Model Context Protocol (MCP)** implementation

✅ Live Kubernetes cluster integration

✅ Multi-Agent AI collaboration

✅ Deterministic server-side safety engine

✅ Real-time policy validation using PodDisruptionBudgets

✅ Observable infrastructure state

✅ Complete remediation audit trail

---

# 📚 References

- Kubernetes Documentation
- Model Context Protocol (MCP)
- NitroStack MCP SDK
- PodDisruptionBudget (PDB)
- kube-state-metrics
- kind (Kubernetes in Docker)

---

# 🤝 Contributing

Contributions are welcome!

If you'd like to improve HelmsMan:

1. Fork the repository
2. Create a feature branch

```bash
git checkout -b feature/my-feature
```

3. Commit your changes

```bash
git commit -m "Add awesome feature"
```

4. Push to GitHub

```bash
git push origin feature/my-feature
```

5. Open a Pull Request 🚀

---

# 👥 Team

Built with ❤️ for the **NitroStack MCP Hackathon**

| Member | Role |
|---------|------|
| Mounish Senisetty | MCP Server • Backend • Kubernetes |
| Ashrith | AI Agents • Kubernetes |
| Sandhiya | Research • Testing • Documentation |

---

# 📄 License

This project is licensed under the **MIT License**.

Feel free to use, modify and distribute this project in accordance with the license terms.

---

# 🙏 Acknowledgements

Special thanks to:

- Kubernetes Community
- NitroStack MCP Team
- Docker
- OpenAI
- The Cloud-Native Ecosystem

for providing the tools and technologies that made this project possible.

---

# ⭐ Support the Project

If you found HelmsMan interesting or useful:

- ⭐ Star this repository
- 🍴 Fork the project
- 🛠️ Contribute improvements
- 🐛 Report issues
- 💬 Share your feedback

---

<p align="center">

### ⚓ HelmsMan

**Autonomous Kubernetes Remediation using the Model Context Protocol**

Built for the **NitroStack MCP Hackathon**

</p>
