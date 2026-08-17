# 📖 AETHER Enterprise Kubernetes Platform — Comprehensive Walkthrough & Operator Manual

> **Version 2.0.0 (Go Edition)**  
> **Author**: Aditya Raj  
> **Last Updated**: August 2026  

---

## 🚀 Quick Access URLs

| Service | Port / URL | Description |
| :--- | :--- | :--- |
| **Aether Platform UI** | **[`http://localhost:3080/`](http://localhost:3080/)** | React 18 & Monaco Dashboard |
| **Go Backend REST & WebSockets** | **[`http://localhost:4080/`](http://localhost:4080/)** | Native Go API backend & client-go gateway |
| **Cluster Health Probe** | **[`http://localhost:4080/api/health`](http://localhost:4080/api/health)** | System status check endpoint |
| **Interactive Swagger API Docs** | **[`http://localhost:4080/swagger`](http://localhost:4080/swagger)** | OpenAPI 3.0 interactive documentation |

---

## 🧭 Complete Feature Walkthrough

### 1. Cluster Overview & Interactive Event Inspector
1. Open [`http://localhost:3080/`](http://localhost:3080/).
2. View cluster health cards (**CPU Utilized**, **Memory Allocated**, **Active Pods**, **Running Nodes**).
3. Scroll down to **Recent Events** on the right side of the dashboard.
4. Click on any cluster event card:
   - The **Cluster Event Inspector Modal** opens.
   - Inspect **Event Message**, **Reason Badge** (`Scheduled`, `Killing`, `Unhealthy`, `Created`, `Started`, `RELOAD`), **Involved Resource**, **Namespace**, **Timestamp**, and **Severity Type**.
   - View the formatted, copyable **Raw OpenAPI 3.0 JSON Payload**.

---

### 2. Live Container Streaming Logs (WebSockets)
1. Click **`Workloads`** or **`Pods`** in the sidebar.
2. Select any active pod (e.g. `demo-node-app` or `nginx-ingress-controller`).
3. Click **`View Container Logs`**:
   - The live log modal connects over WebSockets (`ws://localhost:4080/ws/logs`).
   - Runs `kubectl logs <pod> -n <namespace> --tail=100 -f` in real time.
   - Filter logs dynamically with the built-in search bar or toggle **Auto-scroll**.

---

### 3. Pod-Level Prometheus Telemetry Explorer
1. Click **`Observability & Prometheus`** in the sidebar.
2. Select a pod from the **Pod Telemetry Explorer** dropdown (e.g., `demo-node-app` vs `nginx-ingress`).
3. View high-resolution pod metrics:
   - **Pod CPU Allocation & Usage (mCPU)**.
   - **Pod Memory Consumption (MiB)**.
   - **Pod Network I/O Receive & Transmit Rates (MB/s)**.

---

### 4. In-Pod Live Code Studio & GitOps Hot-Patching
1. Click **`In-Pod Code Studio`** in the sidebar.
2. Browse directory paths inside active containers (`/app`, `/src`, `/etc`).
3. Select `/app/server.js`:
   - Code loads into the **Monaco Editor** with JavaScript syntax highlighting.
4. Edit container code in real time:
   - Click **`Hot-Patch to Pod`** to execute `kubectl exec` and apply runtime file changes immediately.
5. Click **`Commit to GitOps`**:
   - Open the **Monaco Split-Screen Diff Viewer** to compare original vs edited code.
   - Enter your commit message and trigger **ArgoCD Reconciliation** to sync changes across GitOps repos.

---

### 5. AI Autonomous Diagnostic Copilot
1. Click **`AI Diagnostic Copilot`** in the sidebar.
2. Select any crashing or failing pod (`CrashLoopBackOff`, `OOMKilled`, `Error`).
3. Click **`Run AI Autonomous Diagnostics`**:
   - The AI Copilot analyzes container exit codes, status specs, and tail logs.
   - Displays root-cause diagnosis and generates a 1-click **Automated Remediation Patch**.
4. Click **`Apply Remediation Patch`**:
   - Applies the patch via `client-go` and records an audit entry into SQLite.

---

### 6. SQLite Database & 48-Hour Retention Store
1. All system user credentials, operational audit logs, and cluster events are saved in **SQLite database file ([`server-go/data/aether.db`](file:///home/addy/work/k8s-platform/server-go/data/aether.db))**.
2. Click **`Audit Trail`** in the sidebar to review all recorded administrative actions.
3. Records older than 48 hours are automatically purged by the background retention engine.

---

### 7. Interactive Swagger API Documentation
1. Navigate to **[`http://localhost:4080/swagger`](http://localhost:4080/swagger)** or click **Swagger API** in the header.
2. Test REST endpoints interactively directly in your browser!
