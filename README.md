# Kubernetes Secret Decode

### Description
Be able to easily see the values of a secret.

YAML and JSON are both supported and detection of the input type is performed automatically.

**Before:**
```yaml
$ kubectl get secret my-secret -o yaml
apiVersion: v1
data:
  password: cGFzc3dvcmQ=
  username: dXNlcm5hbWU=
kind: Secret
metadata:
  creationTimestamp: 2018-05-09T21:01:37Z
  name: my-secret
  namespace: default
  resourceVersion: "20229"
  selfLink: /api/v1/namespaces/default/secrets/my-secret
  uid: 29ef8024-53cc-11e8-967d-080027cd91ae
type: Opaque
```

**After:**
```yaml
$ kubectl ksd get secret my-secret -o yaml
apiVersion: v1
stringData:
  password: password
  username: username
kind: Secret
metadata:
  creationTimestamp: "2018-05-09T21:01:37Z"
  name: my-secret
  namespace: default
  resourceVersion: "20229"
  selfLink: /api/v1/namespaces/default/secrets/my-secret
  uid: 29ef8024-53cc-11e8-967d-080027cd91ae
type: Opaque
```

### Installation
```
go install github.com/fxposter/kubectl-ksd@latest
```

### Usage
```
kubectl ksd get secret my-secret -o yaml
kubectl ksd get secret my-secret -o json
```
