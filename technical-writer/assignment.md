# Using the `kubectl` Tool to Interact with Kubernetes

<img alt="" Title="" src="">

## Introduction
Kubernetes, often abbreviated as K8s, is an open-source platform designed to automate the deployment, scaling, and management of containerized applications. It is incredibly powerful, but if you are just getting started, it may seem overly complicated. The `kubectl` command-line tool provides a simple way for developers and system administrators to manage and troubleshoot containers.<br>

---
&#9432; **_NOTE:_** _You may have heard of the following tools:_
* kube-control
* kube-cuddle
* kube-ectl

_These are different ways of pronouncing the name of the_ `kubectl` _tool._

---


Let's explore the `kubectl` tool, specifically, the following operations:

* [`get`](#kubectl-get)
* [`logs`](#kubectl-logs)
* [`exec`](#kubectl-exec)
* [`debug`](#kubectl-debug)

---

#### `kubectl get`
The `get` operation is fundamental because it allows users to query and view important information about a specific resource (e.g., Pods, Services, et cetera).

Issue the followign command to list the `pods` resource type:
```shell
kubectl get pods
```

---
&#128421; <span style="color:#72A8F5">***OUTPUT***</span>

| NAME         | READY | STATUS  | RESTARTS | AGE  |
|--------------|-------|---------|----------|------|
| loadbal-pod  | 1/1   | Running | 0        | 4d4h |
| frontend-pod | 1/1   | Running | 0        | 4d   |
| backend-pod  | 1/1   | Running | 0        | 4d   |

---
<br>

>&#9888; **_WARNING:_** _If a namespace is not specified, the system selects the default namespace. The **--all-namespace** option shows all resources (e.g., pods) across every namespace._
> 
> _For more information, consult the [Namespaces](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/) page from Kubernetes docs._

<br>

#### `kubectl logs`
[PLACEHOLDER]

#### `kubectl exec`
[PLACEHOLDER]

#### `kubectl debug`
[PLACEHOLDER]

---

### Conclusion
In this article, we learned...

### References
For details about each `kubectl` command, including examples and all options, see the [kubectl]() reference documentation.

Additionally, if you are new to Kubernetes, check out the [Overview]() page within the **Kubernetes Documentation** site.