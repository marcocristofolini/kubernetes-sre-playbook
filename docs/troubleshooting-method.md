# Troubleshooting Method

## 1. Establish impact
Identify what users or dependent services are experiencing and when it started.

## 2. Inspect desired vs. actual state
Check the workload controller, replicas, rollout status and pod placement.

## 3. Read events chronologically
Events often expose scheduling, image, volume, probe and eviction failures before logs do.

## 4. Inspect container termination state
Use current and previous container state. A restarted container may have already lost the most useful log context.

## 5. Check resource and node pressure
CPU throttling, memory pressure, PID pressure and ephemeral storage can all produce symptoms that look application-specific.

## 6. Correlate with observability
Use metrics, logs and traces around the same time window. Avoid treating one telemetry source as complete truth.

## 7. Form a falsifiable hypothesis
State what evidence would confirm or reject the suspected cause.

## 8. Fix the cause, not only the symptom
Increasing a limit may stop a crash while leaving a leak, traffic amplification or unbounded temporary data problem unresolved.
