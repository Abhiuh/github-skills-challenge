## Task 3 — Anomaly Detection

### Detection Results

The provided anomaly detector uses fixed thresholds:

- Response time threshold: 500 ms
- CPU utilization threshold: 80%
- Memory utilization threshold: 80%

The pipeline processed 10 records and detected 2 anomalies.

### Detected Anomalies

The first anomaly occurred at `2026-09-20T10:05:00`.

- Response time: 610 ms
- CPU: 75%
- Memory: 70%
- Log level: ERROR
- Detection reason: High response time

The second anomaly occurred at `2026-09-20T10:06:00`.

- Response time: 640 ms
- CPU: 94%
- Memory: 91%
- Log level: ERROR
- Detection reasons:
  - High response time
  - High CPU utilization
  - High memory utilization

### Missed Expected Anomaly

The detector contains a log-based detection condition for `WARNING` logs:

`if record["log_level"] == "WARNING":`

However, the synthetic data uses `ERROR` for the abnormal log records. Therefore, the detector does not generate the intended log-based reason for the ERROR logs.

The two abnormal records are still detected because their metric values exceed the configured thresholds.

### False Positives

No obvious false positives were observed in the provided 10-record dataset.

### Detector Limitation

The detector relies on fixed thresholds and simple rule-based checks. It does not dynamically learn normal behaviour. Additionally, its log-level rule checks for `WARNING` while the synthetic abnormal records use `ERROR`.