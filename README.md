# Kubernetes SRE Playbook

Reproducible failure scenarios for practicing **Kubernetes troubleshooting and incident reasoning**.

Each scenario contains:
- a deliberately broken workload;
- a corrected workload;
- expected signals;
- investigation commands;
- remediation guidance.

## Scenarios

| Scenario | Primary signal |
|---|---|
| [OOMKilled](scenarios/oomkilled/runbook.md) | container termination reason and memory pressure |
| [CrashLoopBackOff](scenarios/crashloop/runbook.md) | repeated restart and previous logs |
| [Ephemeral storage eviction](scenarios/ephemeral-storage-eviction/runbook.md) | eviction event and ephemeral-storage usage |

## Method

Do not start with random commands. Build a timeline:

```text
User symptom
  -> workload state
  -> pod/container state
  -> recent events
  -> resource pressure
  -> logs
  -> node / network / storage evidence
  -> hypothesis
  -> verification
```

See [docs/troubleshooting-method.md](docs/troubleshooting-method.md).

> Run destructive lab scenarios only in a disposable development cluster.
