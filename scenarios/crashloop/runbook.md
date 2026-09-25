# CrashLoopBackOff

## Expected signals
- restart count increases;
- pod alternates between Running/Waiting;
- waiting reason becomes `CrashLoopBackOff`.

## Investigation

```bash
kubectl -n sre-lab get pod crashloop-demo -w
kubectl -n sre-lab describe pod crashloop-demo
kubectl -n sre-lab logs crashloop-demo --previous
```

## Reasoning

CrashLoopBackOff is Kubernetes backoff behavior after repeated process failure. It is a symptom.

Use the previous container logs and termination state to identify the actual startup failure.
