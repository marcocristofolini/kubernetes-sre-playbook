# OOMKilled

## Expected signals
- container restarts increase;
- last termination reason is `OOMKilled`;
- memory usage approaches the configured limit.

## Investigation

```bash
kubectl -n sre-lab get pod oom-demo
kubectl -n sre-lab describe pod oom-demo
kubectl -n sre-lab get pod oom-demo -o jsonpath='{.status.containerStatuses[*].lastState.terminated.reason}'
kubectl -n sre-lab logs oom-demo --previous
```

## Reasoning

An OOM kill confirms that the container exceeded an enforced memory boundary. It does not by itself explain why memory grew.

Check traffic, heap behavior, caches, leaks, batch size and concurrency before simply raising the limit.
