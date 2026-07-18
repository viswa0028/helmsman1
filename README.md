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
[![Platform](https://img.shields.io/badge/Kubernetes-kind-blue.svg)](#)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-blue.svg)](#)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](#)

</p>

<p align="center">
AI-powered Kubernetes operations where multiple agents negotiate infrastructure changes while a programmatic safety engine guarantees availability.
</p>

# 📌 Overview

**HelmsMan** is an **MCP (Model Context Protocol) server** that enables autonomous Kubernetes operations through **collaborating AI agents**.

Unlike traditional monitoring dashboards that simply visualize metrics or CPU-based autoscalers that react to thresholds, HelmsMan **reasons over the live cluster state** before taking actions.

Two specialized agents negotiate every infrastructure change:

- 💰 **FinOps Agent** – minimizes infrastructure cost by reducing unnecessary resources.
- 🛡️ **Availability Guardian** – prevents any action that could violate Kubernetes availability policies.

The result is an AI-powered system that **optimizes cloud costs without compromising reliability.**

---

## ❗ Problem

Modern Kubernetes management is largely reactive.

Autoscalers respond only to CPU or memory thresholds and cannot reason about operational safety. Engineers must manually decide whether infrastructure changes are safe, often leading to:

- 💸 Over-provisioned clusters
- ⚠️ Unsafe scale-down operations
- 🧑‍💻 Continuous manual intervention
- 🚨 Accidental downtime

# 💡 Our Solution

%%{init: {
  'theme': 'base',
  'themeVariables': {
    'primaryColor': '#E3F2FD',
    'primaryTextColor': '#0D47A1',
    'primaryBorderColor': '#64B5F6',
    'lineColor': '#1976D2',
    'secondaryColor': '#E8F5E9',
    'tertiaryColor': '#fff'
  },
  'flowchart': {
    'nodeSpacing': 50,
    'rankSpacing': 70
  }
}%%}

graph TD
    %% Define Nodes
    U[("👤 User")]
    
    subgraph Agents ["🧠 MCP Multi-Agent Negotiation Loop"]
        FO[("🤖 FinOps Agent<br/>(Cost Optimizer)")]
        AG[("🛡️ Availability Guardian<br/>(Risk Analyzer)")]
    end
    
    subgraph Enforcement ["🔐 Programmatic Veto"]
        SE{"🚦 NitroStack<br/>Safety Engine<br/>(TS Code)"}
    end
    
    K8S[("☸️ Live Kubernetes Cluster<br/>(Target Infrastructure)")]

    %% Define Connections & Descriptions
    U -- "Requests Optimization<br/>(e.g., 'Reduce Costs')" --> FO
    
    FO == "Proposes Scale-Down<br/>(get_cluster_state tool)" ==> AG
    
    AG -- "Reviews against SLAs" --> FO
    AG == "Approves/Modifies Proposal" ==> SE
    
    SE -.->|Rejects via PDB check| AG
    SE == "Executes Validated Action<br/>(scale_deployment tool)" ==> K8S

    %% Node Styling
    classDef plain fill:#fff,stroke:#333,stroke-width:1px,rx:5,ry:5;
    classDef agent fill:#E3F2FD,stroke:#1976D2,stroke-width:2px,rx:10,ry:10,color:#0D47A1;
    classDef guardian fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px,rx:10,ry:10,color:#1B5E20;
    classDef safety fill:#FFFDE7,stroke:#FBC02D,stroke-width:2px,stroke-dasharray: 5 5,color:#F57F17;
    classDef k8s fill:#f9f9f9,stroke:#326ce5,stroke-width:2px,rx:15,ry:15,color:#326ce5;
    classDef user fill:#fafafa,stroke:#616161,stroke-width:2px,rx:30,ry:30,color:#212121;

    class U user;
    class FO agent;
    class AG guardian;
    class SE safety;
    class K8S k8s;

    %% Subgraph Styling
    style Agents fill:#fbfbfb,stroke:#e0e0e0,stroke-width:1px,stroke-dasharray: 5 5,color:#616161
    style Enforcement fill:#fbfbfb,stroke:#e0e0e0,stroke-width:1px,stroke-dasharray: 5 5,color:#616161

---

# 🎯 Key Features

## 🤖 Multi-Agent Decision Making

### FinOps Agent

Responsible for:

- Reducing cloud cost
- Detecting over-provisioned deployments
- Scaling idle workloads
- Improving cluster utilization

---

### Availability Guardian

Responsible for:

- Protecting application availability
- Checking PodDisruptionBudgets
- Preventing unsafe replica reductions
- Rejecting risky scaling operations

---

## 🔴 Live Kubernetes Integration

HelmsMan communicates directly with a running Kubernetes cluster.

Supports:

- Deployments
- Pods
- Nodes
- Services
- PodDisruptionBudgets

No simulated data.

Everything comes from the real Kubernetes API.

---

## 🛡️ Server-side Safety Enforcement

Even if an AI agent requests:

```

scale\_deployment(checkout-service, replicas=1)

```

HelmsMan checks:

- Current replicas
- PDB requirements
- Minimum available pods

If availability would be violated:

```

{
"rejected": true,
"reason": "Scaling would violate PodDisruptionBudget"

}

```

The operation never reaches Kubernetes.

---

# 🌍 Live Cluster Data

HelmsMan continuously reasons over:

- Pod health
- Replica counts
- Deployment status
- Node conditions
- PodDisruptionBudgets
- kube-state-metrics

The demo uses a local **kind** Kubernetes cluster.

---

# 🧠 MCP Capabilities

## 🔧 Tools

| Tool | Description |
|------|-------------|
| `get_cluster_state()` | Returns live cluster summary |
| `get_pod_health(namespace)` | Retrieves pod health information |
| `scale_deployment(name, replicas)` | Safely scales deployments |
| `rollback_deployment(name)` | Rolls back deployment revisions |
| `cordon_node(node)` | Marks node unschedulable |

---

## 📚 Resources

| Resource | Purpose |
|-----------|----------|
| `k8s://cluster/topology` | Live cluster topology |
| `k8s://policy/disruption-budgets` | PodDisruptionBudget information |
| `k8s://actions/log` | Action history |

---

## 💬 Prompts

### cluster_health_brief

Generates:

- Cluster summary
- Health status
- Recommendations

---

### change_record

Produces:

- Approved actions
- Blocked actions
- Reason for rejection
- Safety audit trail

---

# 🏗 Architecture

![Architecture](images/architecture.png)

---

# ⚙️ Tech Stack

- Node.js
- TypeScript
- NitroStack MCP SDK
- Kubernetes Client SDK
- kind
- kubectl
- kube-state-metrics
- Docker Desktop

---

# 📂 Project Structure

```

helmsman/

├── src/
│ ├── agents/
│ │ ├── orchestrator.ts
│ │ ├── executor.ts
│ │ ├── prompts.ts
│ │ └── tools.ts
│ │
│ ├── modules/
│ │ └── k8s/
│ │ ├── client.ts
│ │ ├── k8s.module.ts
│ │ ├── k8s.tools.ts
│ │ ├── k8s.resources.ts
│ │ ├── k8s.prompts.ts
│ │ ├── safety.ts
│ │ ├── audit.ts
│ │ └── policy.data.ts
│ │
│ ├── app.module.ts
│ └── index.ts
│
├── manifests/
│ ├── namespace.yaml
│ ├── pdbs.yaml
│ └── kube-state-metrics.yaml
│
├── scripts/
│ ├── setup-cluster.ps1
│ ├── setup.sh
│ ├── reset-demo.ps1
│ └── demo-chaos.sh
│
└── README.md

```

---

# 🚀 Getting Started

## Prerequisites

- Node.js 18+
- Docker Desktop
- kind
- kubectl
- NitroStudio
- NitroStack CLI

---

## Install Dependencies

```bash
npm install
```

---

## Create Kubernetes Cluster

```bash
powershell -File scripts/setup-cluster.ps1
```

or

```bash
kind create cluster --name helmsman
```

---

## Deploy Demo Resources

```bash
kubectl apply -f manifests/
```

---

## Build

```bash
npm run build
```

---

## Run Tests

```bash
npm run test:safety
```

Expected output

```
Safety self-check: OK
```

---

## Start MCP Server

```bash
npm run dev
```

Open **NitroStudio**

```
Select Project
↓

Connect
```

---

# 🎬 Demo Flow

### Step 1

Start the local Kubernetes cluster.

---

### Step 2

Deploy an intentionally over-provisioned application.

```
checkout-service

Replicas = 5
```

---

### Step 3

Ask the FinOps Agent to reduce replicas.

```
scale_deployment(
name="checkout-service",
replicas=1
)
```

---

### Step 4

Availability Guardian checks

- PodDisruptionBudget
- Minimum replicas
- Current health

---

### Step 5

Safety engine blocks the operation.

```
Rejected

Reason:
Scaling would violate
PodDisruptionBudget
```

---

### Step 6

Run

```
change_record
```

Blocked action appears in the audit log.

---

### Step 7

Observe

```
kubectl get pods
```

The deployment remains unchanged.

No downtime.

---

# 🧪 Safety Verification

The safety engine is independently tested.

```bash
npm run test:safety
```

The test validates:

- Replica calculations
- PDB enforcement
- Scale-down rejection
- Safe scaling scenarios

---

# 🌟 Why HelmsMan?

Traditional Kubernetes tools:

- React to CPU usage
- Ignore operational policies
- Require manual intervention

HelmsMan:

- Understands cluster state
- Reasons with AI agents
- Enforces Kubernetes safety
- Prevents risky operations
- Maintains a complete audit trail

It is not just monitoring—it is **autonomous, policy-aware Kubernetes remediation**.

---

# 🔮 Future Enhancements

- Horizontal Pod Autoscaler integration
- Predictive scaling using historical metrics
- Multi-cluster federation
- GitOps integration (ArgoCD)
- Slack / Teams notifications
- Prometheus alert ingestion
- LLM-generated remediation plans
- RBAC-aware agent permissions

---

# 🏆 Hackathon Highlights

✅ Live Kubernetes API integration

✅ Multi-Agent AI negotiation

✅ Real-time cluster reasoning

✅ Server-side policy enforcement

✅ MCP Tools, Resources & Prompts

✅ Live demo with observable Kubernetes state

✅ Complete audit trail

---

# 👥 Team

**HelmsMan**

Autonomous Kubernetes Remediation using MCP

Built for the **NitroStack MCP Hackathon**.
