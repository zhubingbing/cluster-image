# kyverno

Kyverno is a policy engine designed for Kubernetes. It can validate, mutate, and generate configurations using admission controls and background scans. Kyverno policies are Kubernetes resources and do not require learning a new language. Kyverno is designed to work nicely with tools you already use like kubectl, kustomize, and Git.

## Prerequisites

- Kubernetes(depends on the app requirements)
- sealos 4.x.x

## Install

Prerequisites example

```shell
sealos run docker.io/labring/kyverno:v1.10.3
```

Custome config

```shell
sealos run docker.io/labring/kyverno:v1.10.3 -e HELM_OPTS="--set admissionController.replicas=3 \
--set backgroundController.replicas=2 \
--set cleanupController.replicas=2 \
--set reportsController.replicas=2"
```

Get pods status

```shell
root@node1:~# kubectl -n kyverno get pods
NAME                                             READY   STATUS    RESTARTS   AGE
kyverno-admission-controller-79dcbc777c-kvgv7    1/1     Running   0          2m47s
kyverno-background-controller-67f4b647d7-htqkh   1/1     Running   0          2m47s
kyverno-cleanup-controller-566f7bc8c-d4jlj       1/1     Running   0          2m47s
kyverno-reports-controller-6f96648477-r7cww      1/1     Running   0          2m47s
```

## uninstall

```shell
helm -n kyverno uninstall kyverno
```
