# Ephemeral-storage pressure / eviction

## Expected signals
Depending on kubelet and filesystem accounting, the pod may be evicted after exceeding its ephemeral-storage limit or contribute to node disk pressure.

## Investigation

```bash
kubectl -n sre-lab describe pod ephemeral-storage-demo
kubectl get events -A --sort-by=.lastTimestamp | tail -50
kubectl describe node <node>
kubectl top pod -A
```

Look specifically for eviction messages mentioning `ephemeral-storage` and node conditions related to disk pressure.

## Remediation

- bound temporary data;
- set measured requests and limits;
- use an appropriate persistent or external store for durable/unbounded data;
- alert on node filesystem saturation before eviction thresholds are crossed.
