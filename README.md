# lemmy-ks


A Kustomize deployment for [Lemmy](https://github.com/LemmyNet/lemmy).


##### Things to note:

- This is heavily WIP. Do not use if you expect stability without constantly checking this repo while kinks are ironed.
- This is unsupported from LemmyNet currently, and adapted from their docker-compose examples and documentation.
- UID/GID 991 is used and expected for all deployments
- Ingresses included. ingress-nginx usage expected.


**This is WIP:** My time is very limited, but I would like to get this to a good state for long-term usage. You can see an example of how I'm using it currently until it's all buttoned up and completed. For inspirational purposes you can see how I make use of this repo [here](https://github.com/anthr76/infra/tree/federation/k8s/base/federation/lemmy)


### What's required?

- A secret titled lemmy containing the following:
  - `config.hjson` 
  - `pictrs-api-key`
- Postgres server
- a (optional) PVC for pictrs


```
---
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pictrs-media
spec:
  accessModes:
  - ReadWriteOnce
  resources:
    requests:
      storage: 10Gi
  storageClassName: slow-ceph-block
```

