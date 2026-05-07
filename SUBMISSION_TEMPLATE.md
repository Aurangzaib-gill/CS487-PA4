<div align="center">

# PA4 Submission: TaskFlow Pipeline

<img alt="GitHub only" src="https://img.shields.io/badge/Submit-GitHub%20URL%20Only-10b981?style=for-the-badge">
<img alt="Total points" src="https://img.shields.io/badge/Total-100%20points-7c3aed?style=for-the-badge">

</div>

<div style="background:#f5f3ff;color:#111827;border-left:6px solid #6330bc;padding:14px 18px;border-radius:10px;margin:18px 0;">
Copy this file to <code style="color:#111827;background:#ddd6fe;padding:2px 4px;border-radius:4px;">SUBMISSION.md</code>. Put every screenshot in <code style="color:#111827;background:#ddd6fe;padding:2px 4px;border-radius:4px;">docs/</code>, embed it under the correct task, and write a short description below each image explaining what it proves. The grader should not need any file outside this repository.
</div>

## Student Information

| Field | Value |
|---|---|
| Name | TODO |
| Roll Number | TODO |
| GitHub Repository URL | TODO |
| Resource Group | `rg-sp26-TODO` |
| Assigned Region | TODO: `uaenorth` or `ukwest` |

## Evidence Rules

- Use relative image paths, for example: `![AKS nodes](docs/aks-nodes.png)`.
- Every image must have a 1-3 sentence description below it.
- Azure Portal screenshots must show the resource name and enough page context to identify the service.
- CLI screenshots must show the command and output.
- Mask secrets such as function keys, ACR passwords, and storage connection strings.


## Task 1: App Service Web App (15 points)

### Evidence 1.1: Forked Repository

TODO: Embed screenshot of your forked GitHub repository.

Description: TODO: Explain that this is your working fork and that it contains the PA4 starter structure.

### Evidence 1.2: App Service Overview

TODO: Embed screenshot of the Web App overview page showing `webapp-<rollnum>` and Running status.

Description: TODO: State the resource group, region, runtime, and public URL.

### Evidence 1.3: Deployment Center / GitHub Actions

TODO: Embed screenshot of Deployment Center or the successful GitHub Actions deployment.

Description: TODO: Explain how the Web App is connected to your GitHub fork.

### Evidence 1.4: Live Web UI

TODO: Embed screenshot of the TaskFlow page loaded in a browser.

Description: TODO: Explain that the App Service is serving the frontend successfully.

---

## Task 2: Azure Container Registry (15 points)

### Evidence 2.1: ACR Overview

TODO: Embed screenshot of `crpa4<rollnum>` overview.

Description: TODO: Identify the registry SKU and resource group.

### Evidence 2.2: Docker Builds

TODO: Embed screenshot showing successful local builds for `validate-api`, `report-job`, and `func-app`.

Description: TODO: Explain which folder produced each image.

### Evidence 2.3: ACR Repositories

TODO: Embed screenshot or CLI output showing all three repositories in ACR.

Description: TODO: Confirm `validate-api:v1`, `report-job:v1`, and `func-app:v1` were pushed.

---

## Task 3: Durable Function Implementation (12 points)

### Evidence 3.1: Completed Function Code

TODO: Link to your completed file: `[function_app.py](function-app/function_app.py)`.

Description: TODO: Summarize how your orchestrator chains validation and report generation.

### Evidence 3.2: Local Function Handler Listing

TODO: Embed screenshot of `func start` showing the HTTP starter, orchestrator, and activities.

Description: TODO: Explain that the Durable Functions runtime discovered your handlers.

---

## Task 4: Function App Container Deployment (8 points)

### Evidence 4.1: Function App Container Configuration

TODO: Embed screenshot showing the Function App uses your `func-app:v1` image from ACR.

Description: TODO: State the Function App name and image URI.

### Evidence 4.2: Orchestration Smoke Test

TODO: Embed screenshot of the `curl` output that starts an orchestration and returns status URLs.

Description: TODO: Explain what the returned `id` and `statusQueryGetUri` prove.

### Evidence 4.3: Expected Failed Status Before Downstream Wiring

TODO: Embed screenshot of the status query JSON showing the expected failure before `VALIDATE_URL` is configured.

Description: TODO: Explain why this failure is expected at this stage.

---

## Task 5: AKS Validator (15 points)

### Evidence 5.1: AKS Cluster

TODO: Embed screenshot of AKS overview showing `aks-<rollnum>` succeeded.

Description: TODO: State node count, node size, region, and resource group.

### Evidence 5.2: Kubernetes Nodes and Pods

TODO: Embed screenshot of `kubectl get nodes` and `kubectl get pods`.

Description: TODO: Explain that the validator pod is scheduled and running.

### Evidence 5.3: Kubernetes Service

TODO: Embed screenshot of `kubectl get service validate-service`.

Description: TODO: Identify the external IP and port exposed by the LoadBalancer.

### Evidence 5.4: Validator API Tests

TODO: Embed screenshot of `curl /health`, a valid `curl /validate`, and an invalid `curl /validate`.

Description: TODO: Explain the accepted path and the `qty > 100` rejection rule.

### Evidence 5.5: Function App `VALIDATE_URL`

TODO: Embed screenshot showing the Function App application setting `VALIDATE_URL`.

Description: TODO: Explain how the Durable Function reaches the AKS validator.

### Evidence 5.6: AKS Idle Behavior

TODO: Embed AKS metrics screenshot and/or `kubectl` output after the service is idle.

Description: TODO: Explain that the AKS node remains running even when there are no orders.

---

## Task 6: ACI Report Job (15 points)

### Evidence 6.1: Blob Container

TODO: Embed screenshot of the `reports` blob container.

Description: TODO: Explain where generated PDFs are stored.

### Evidence 6.2: Manual ACI Run

TODO: Embed screenshot of `az container show` for `ci-report-test`.

Description: TODO: State the final container state and why the job exits.

### Evidence 6.3: ACI Logs

TODO: Embed screenshot of `az container logs`.

Description: TODO: Explain what the report job printed after generating and uploading the PDF.

### Evidence 6.4: Generated PDF

TODO: Embed screenshot showing `TEST-001.pdf` in Blob Storage or opened from Blob Storage.

Description: TODO: Explain how this proves the ACI wrote to storage.

### Evidence 6.5: Function App Managed Identity and IAM

TODO: Embed screenshots of system-assigned identity enabled and Contributor role assignment on your resource group.

Description: TODO: Explain why the Function App needs this permission to create ACIs.

### Evidence 6.6: Report App Settings

TODO: Embed screenshot of `REPORT_*`, `ACR_*`, `STORAGE_CONN`, and `SUBSCRIPTION_ID` settings.

Description: TODO: Explain what each group of settings is used for. Mask secrets.

---

## Task 7: End-to-End Pipeline (15 points)

### Evidence 7.1: Web App Wiring

TODO: Embed screenshot showing `FUNCTION_START_URL` and `FUNCTION_STATUS_URL` configured on the Web App.

Description: TODO: Explain how the frontend starts and polls the Durable orchestration.

### Evidence 7.2: Happy Path UI

TODO: Embed screenshots of the form before submit, Running status, and Completed status with report URL.

Description: TODO: Explain the valid order payload and final result.

### Evidence 7.3: Backend Participation

TODO: Embed screenshots showing Function App invocation, AKS validator evidence, ACI evidence, and Blob PDF evidence.

Description: TODO: Trace the same order ID across services.

### Evidence 7.4: Reject Path UI

TODO: Embed screenshot of an order with `qty > 100` being rejected.

Description: TODO: Explain why no report ACI should be created for this order.

---

## Task 8: Write-up and Architecture Diagram (5 points)

### Evidence 8.1: Architecture Diagram

TODO: Embed your architecture diagram from `docs/`.

Description: TODO: Confirm that it shows GitHub, App Service, Durable Function, AKS, ACI, Blob Storage, ACR, and IAM.

 Task 8 Write-Up
3.1 Service Selection
App Service. Azure App Service is a good fit for the TaskFlow front-end because it provides managed
hosting for a browser-facing web application with minimal operational overhead. The assignment needed
GitHub-driven CI/CD, HTTPS hosting, and a stable public URL, all of which App Service supports directly
through Deployment Center. Cost stays predictable because the web app runs on a fixed App Service plan
rather than launching new infrastructure for each request. It also scales more simply than managing a
container platform for a relatively lightweight UI.
Durable Functions. Durable Functions are appropriate for the workflow layer because the application
is not a single fast request-response action. Instead, it validates an order, conditionally starts a report
generation step, and exposes polling endpoints while the process continues. Durable orchestration gives
built-in state persistence, checkpoints, and status-query URLs, which are ideal for a workflow that can
take up to about a minute. Operationally, this is much simpler than manually storing workflow state in a
database and coordinating retries by hand.
AKS. AKS is the right choice for the validator because the service behaves like a long-running HTTP API
with an external endpoint. The validator benefits from a stable deployment object, service abstraction,
and Kubernetes-style scaling model rather than one-shot execution. Even when traffic is low, the cluster
remains provisioned and ready, which makes it operationally heavier and usually more expensive than server
less options. That cost is acceptable here because the assignment explicitly requires learning Kubernetes
deployment, networking, and service exposure.
ACI. Azure Container Instances are a strong fit for the report generator because report generation is a
short-lived batch job rather than a continuously served API. ACI starts a container for one run, lets it
complete its work, and then the job can terminate without leaving a full orchestration platform running.
This aligns well with cost efficiency because billing is tied to the container’s active lifetime instead of an
always-on cluster. Operationally, it is much simpler than putting the same ephemeral report process into
AKS.
3.2 ACI vs. AKS: Hands-On Comparison
When AKS is idle for ten minutes, the validator pod may receive no traffic, but the cluster still exists, the
node VM remains allocated, and the service endpoint stays provisioned. In other words, idle on AKS means
low application activity, not zero infrastructure cost. The cluster remains ready to serve immediately, which
is useful for APIs but not especially cost-efficient for bursty one-shot work.
In contrast, idle for ACI in this pipeline means there is no container instance running at all between report
requests. The report job is created only when a valid order reaches report
activity; outside that window
there is nothing continuously serving traffic. If a malicious user submitted 1000 requests in a minute, ACI
would likely create the largest burst-related cost because each valid request could launch another short-lived
container. AKS would also incur load, but its baseline cost is already present; ACI’s cost grows more directly
with the number of report jobs started.
3.3 Why Durable Functions Instead of Plain HTTP Chaining
Implementing the same flow with two plain HTTP-triggered functions would be harder because the appli
cation would need to manage workflow state manually across multiple steps. A normal HTTP chain would
need explicit storage for the order status, plus code to recover progress if the validation or report step failed
CS487 PA4 Report Documentation
Page 10
midway. Long-running report generation also increases the chance of request timeouts or awkward client-side
waiting, while Durable Functions natively support asynchronous start, checkpointing, and status polling.
Retries are another major concern: Durable orchestration makes retryable, stateful coordination far easier
than wiring two stateless HTTP calls together.
3.4 Cost Review
Based on the assignment design and the screenshot evidence, the single most expensive resource is the
AKS cluster because it keeps compute allocated even when request volume is low. App Service and ACR
typically contribute modest steady cost, while ACI charges are short-lived and tied to actual report runs.
Blob Storage cost for generated PDFs should be minimal for a student workload. Although a dedicated
Cost Analysis screenshot was not present in the uploaded archive, the deployment pattern strongly suggests
AKS dominates the total assignment spend.
3.5 Challenges Faced and Debugging Notes
Two common integration challenges are visible in the evidence trail. First, the Function App smoke test
reaches the orchestrator but fails before downstream integration is complete; this is exactly the sort of staged
failure expected when environment variables such as VALIDATE
URL are not yet configured. The screenshots
show that debugging proceeded by checking the orchestration status JSON and then wiring the missing app
settings.
Second, the report pipeline depends on several coordinated settings: ACR credentials, report image name,
storage account endpoint, and Function App identity. A misconfiguration in any of these values can prevent
the report job from starting or writing its PDF. The evidence indicates the debugging strategy centered
on validating application settings in the portal, confirming the blob container existed, and verifying the
ACI/report execution path after infrastructure setup.
