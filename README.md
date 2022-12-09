# webinar-app-postgres
This repo is archived and only for reference before it is deleted.

This repo is for use during the webinar with ondat storage to deploy a statefulset of postgresql with ondat storage and policy checks

The manifests are in the deploy directory

The statefulset should have the following set to pass the policy checks:

```
volumeClaimTemplates:
    - metadata:
        name: postgres-data
        labels:
          storageos.com/replicas: "1" # Possible mistake here?
          storageos.com/nocompress: "true"
      spec:
        accessModes: ["ReadWriteOnce"]
        storageClassName: "storageos" # Possible mistake here?
        resources:
          requests:
            storage: 5Gi
```

If the storageclass is set incorrectly or the labels do not exist then the policy checks will fail.

