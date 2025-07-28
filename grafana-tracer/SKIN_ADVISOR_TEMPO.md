# Tracing skin-advisor-api with Tempo

This workflow explains how to use Tempo to get detailed trace information for the `skin-advisor-api-<env>` service.

## 1. Find the Tempo Datasource

First, identify the UID of your Tempo datasource.

**Tool Call:**
```
list_datasources(type='tempo')
```

Let's assume the output gives you a datasource UID like `tempo-uid`.

## 2. Find a Trace ID from Loki

The most effective way to use Tempo is to start with a `traceid` from a specific log entry in Loki that corresponds to an event you want to investigate (like an error).

For example, from a Loki log entry, you might find a `traceid` like `0e592d9cae740757aec0d99453dea4a1`.

## 3. Search for the Trace in Tempo

Once you have a `traceid`, you can retrieve the full trace from Tempo.

*Note: There isn't a direct tool to search by trace ID in the provided toolset. However, you can achieve this by using the Tempo search functionality in the Grafana UI or by using an API call if available.*

## 4. Search for Traces by Service

If you don't have a specific `traceid`, you can search for recent traces from the service.

**Tool Call:**
```
find_slow_requests(name='skin-advisor-api-<env>-traces', labels={'service.name': 'skin-advisor-api-<env>'})
```

This will search for slow requests and return a list of traces associated with the `skin-advisor-api-<env>` service. You can then analyze these traces to identify performance bottlenecks or errors.
