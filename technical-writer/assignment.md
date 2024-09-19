# Using the `kubectl` Tool to Interact with Kubernetes

![Kubernetes](https://raw.githubusercontent.com/xonixeus/spectrocloud-clone/lenardson-branch/static/kubernetes.png)

## Introduction
Kubernetes, often abbreviated as K8s, is an open-source platform designed to automate the deployment, scaling, and management of containerized applications. It is incredibly powerful, but if you are just getting started, it may seem overly complicated. The `kubectl` command-line tool provides a simple way for administrators to manage Kubernetes objects and clusters.

> &#9432; **_NOTE:_** _You may have heard of the following tools:_
> - kube-control
> - kube-cuddle
> - kube-ectl
>
>_These are different ways of pronouncing the name of the_ `kubectl` _tool._

## Prerequisite(s)
* You need a Kubernetes cluster to use `kubectl`. To learn how to create a cluster from scratch using minikube, consult the [minikube start](https://minikube.sigs.k8s.io/docs/start/) tutorial.

<br>

Now, let's explore the `kubectl` tool, specifically, the following operations:

* [`get`](#kubectl-get)
* [`logs`](#kubectl-logs)
* [`exec`](#kubectl-exec)
* [`debug`](#kubectl-debug)

<br>

---

#### `kubectl get`
The `get` operation is fundamental because it allows users to query and view important information about a specific resource (e.g., Pods, Services, et cetera).

List the `pods` resource type in the default **namespace**, issue the following command:
```shell
kubectl get pods
```
---
&#128421; <span style="color:#72A8F5">***OUTPUT***</span>

>| NAME         | READY | STATUS  | RESTARTS | AGE  |
>|--------------|-------|---------|----------|------|
>| loadbal-pod  | 1/1   | Running | 0        | 4d4h |
>| frontend-pod | 1/1   | Running | 0        | 4d   |
>| backend-pod  | 1/1   | Running | 0        | 4d   |
---
<br>

>&#9888; **_WARNING:_** _If a namespace is not specified, the system selects the default namespace. The **--all-namespace** option shows all resources (e.g., pods) across every namespace._
> 
> _For more information, consult the [Namespaces](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/) page from Kubernetes docs._

<br>

#### `kubectl logs`
The `log` operation allows users to view logs from pods, helping them to understand what is happening inside containers. This tool plays an essential role in debugging, allowing users to check the output of a running application and diagnose issues.

View the `logs` of a pod with the following command:
```shell
kubectl logs loadbal-pod
```
> &#9432; **_NOTE:_** _Replace <span style="color:red">**loadbal-pod**</span> with the name of a pod in your environment._
---
&#128421; <span style="color:#72A8F5">***OUTPUT***</span>
```text
2023-09-18T10:00:00.123Z INFO Starting application version 1.0.0
2023-09-18T10:00:01.456Z INFO Server is listening on port 443
2023-09-18T10:00:05.789Z INFO Connected to database successfully
2023-09-18T10:00:10.012Z INFO Received request: GET /api/v1/users
2023-09-18T10:00:10.015Z INFO Responded with status 200 in 3ms
2023-09-18T10:00:15.345Z ERROR Failed to process request: Invalid user ID
2023-09-18T10:00:20.678Z WARN High memory usage detected
```
---

<br>

#### `kubectl exec`
The `exec` operation allows a user to issue a command inside a container, helping them interact with running containers for troubleshooting, configuration, or diagnostics.

> &#9432; **_NOTE:_** _The `exec` operation requires a command, e.g., `date`._
> 
> _For more information, consult the [kubectl exec](https://kubernetes.io/docs/reference/kubectl/generated/kubectl_exec/) page from Kubernetes docs._

Retrieve the date from a pod, using the first container by default, with the following command:
```shell
kubectl exec loadbal-pod -- date
```
> &#9432; **_NOTE:_** _Replace <span style="color:red">**loadbal-pod**</span> with the name of a pod in your environment._
---
&#128421; <span style="color:#72A8F5">***OUTPUT***</span>
```text
Mon Sep 18 10:00:00 UTC 2023
```
---

<br>

#### `kubectl debug`
Use the `debug` operation for troubleshooting issues in containers by creating an ephemeral debug container. This advanced operation builds on everything we have learned so far—understanding the state of pods, reading logs, and interacting with containers using exec.

Create and attache a temporary debug container using the **busybox** image, with the following command:
```shell
kubectl debug loadbal-pod --image=busybox
```
> &#9432; **_NOTE:_** _Replace <span style="color:red">**loadbal-pod**</span> with the name of a pod in your environment._
> 
---
&#128421; <span style="color:#72A8F5">***OUTPUT***</span>
```text
Creating debugging container with image busybox ...

root@loadbal-pod:/#
```
---

<br>

### Conclusion
This article covers some of the common `kubectl` operations you may use when managing a Kubernetes cluster. However, there are many more operations that are just as important as the ones covered here. You can learn more about `kubectl` and Kubernetes by visint the links in the following section.<br />

### Reference(s)
For details about each `kubectl` command, including examples and all options, consult the [kubectl](https://kubernetes.io/docs/reference/kubectl/generated/) page from Kubernetes docs.

Additionally, if you are new to Kubernetes, consult the [Concepts](https://kubernetes.io/docs/concepts/) section from Kubernetes docs.