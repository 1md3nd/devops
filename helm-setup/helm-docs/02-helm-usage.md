# How can we use Helm Charts

## Installation

## create a namespace inside k8s cluster

```
kubectl create namespace 3tier-demo
```

### To install the created helm-chart `3tier-helm-demo`.

```
helm install 3tier-app 3tier-helm-demo/ -n 3tier-demo
```

service name : `3tier-app`
directory : `3tier-helm-demo`
-n namespace : `3tier-demo`

### Check helm history

```
helm history 3tier-app -n 3tier-demo
```

### Upgrading the helm configurations i.e having service upgrade

Frist we will make all the necessary changes inside the `values.yaml`:

Then, we will make the version upgrade of our service inside the `charts.yaml`:

- here we will change the `version: 0.1.0` to suitable `version: 0.1.1`.
- the also in case change the `appVersion: "1.16.0"` to suitable `appVersion: "1.16.1"`.

The apply the upgrade:

```
helm upgrade 3tier-app 3tier-helm-demo/ -n 3tier-demo
```

### Rollback

In case if we want to rollback in any previous version or REVISION we can easily rollback.

```
helm rollback 1 3tier-app -n 3tier-demo
```
