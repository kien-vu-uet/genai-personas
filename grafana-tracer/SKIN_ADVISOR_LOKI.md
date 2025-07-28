# Tracing skin-advisor-api with Loki

This workflow outlines how to trace the `skin-advisor-api-<env>` service using Loki for log analysis.

## 1. Identify the Service Name

First, you need to identify the exact `service_name` for the environment you want to inspect. You can list all available `service_name` values from Loki.

**Tool Call:**
```
list_loki_label_values(datasourceUid='aegh21e3u78cga', labelName='service_name')
```

**Example Output:**
```
["edupia-video-api-prod","edupia-video-worker-prod","excelsql","genai-api","nginx","skin-advisor-api-dev","skin-advisor-api-prod","skin-advisor-api-stag"]
```
From this list, you can choose the appropriate service, for example, `skin-advisor-api-<env>`.

## 2. Query Logs for the Service

Once you have the service name, you can query its logs.

**Tool Call:**
```
query_loki_logs(datasourceUid='aegh21e3u78cga', logql='{service_name="skin-advisor-api-<env>"}', limit=100)
```
This will retrieve the 100 most recent log entries for the `skin-advisor-api-<env>` service.

## 3. Filter by Log Level

To narrow down your search, you can filter by log level. Common levels include `INFO`, `DEBUG`, `WARN`, and `ERROR`.

**Tool Call to find errors:**
```
query_loki_logs(datasourceUid='aegh21e3u78cga', logql='{service_name="skin-advisor-api-<env>", level="error"}', limit=50)
```

This will show you the 50 most recent error logs, which is a good starting point for debugging. From these logs, you can extract a `traceid` to use with Tempo for more in-depth analysis.
