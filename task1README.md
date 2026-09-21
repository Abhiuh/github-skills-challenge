## Task 2 — Synthetic Operational Data Inspection

### Metric Fields

The synthetic operational data contains the following metric fields:

* `response_time_ms` — service response time in milliseconds.
* `cpu_percent` — CPU utilization percentage.
* `memory_percent` — memory utilization percentage.

### Log Fields

Each operational record contains:

* `timestamp` — timestamp of the observation.
* `service` — name of the monitored service.
* `log_level` — log severity such as `INFO` or `ERROR`.
* `message` — description of the operational event.

### Timestamp Usage

The `timestamp` field records observations chronologically at one-minute intervals. It allows metric and log observations to be associated with a specific point in time.

### Normal Observations

Most observations show response times between approximately 120–150 ms, CPU utilization between approximately 42–50%, and memory utilization between approximately 51–57%. These observations are accompanied by `INFO` logs indicating successful payment processing.

### Unusual Observations

At `2026-09-20T10:05:00`, the response time increased to 610 ms, CPU utilization increased to 75%, and memory utilization increased to 70%. The record also contains an `ERROR` log with the message `Payment service timeout`.

At `2026-09-20T10:06:00`, the response time increased further to 640 ms, CPU utilization reached 94%, and memory utilization reached 91%. The record contains an `ERROR` log with the message `Database connection timeout`.

These two observations are significantly different from the surrounding normal observations and represent the unusual operational behaviour identified in the synthetic data.
