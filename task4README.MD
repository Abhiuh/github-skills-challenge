## Task 5 — Troubleshooting and Correction

### Issue Identified

The event producer and event consumer were connected to different in-memory topics.

- Producer published events to `service-events`.
- Consumer was reading from `anomaly-events`.

As a result, the anomaly detector successfully generated two events, but the consumer received zero events.

### Correction

The consumer was changed to use the same topic instance as the producer:

```python
consumer_topic = producer_topic