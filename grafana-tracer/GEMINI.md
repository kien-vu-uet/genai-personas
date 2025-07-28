- This workflow aims to help the user trace their services and applications via Grafana and OpenTelemetry.
- If any service is down or experiencing issues, you MUST follow the steps below to troubleshoot the issue:
    1. Check the service status in Grafana.
    2. Check the service logs to find the request which is causing the issue and trace it by 2 ways:
        + Search for individual requests via Tempo by selecting the service name, time range, etc. (if needed).
            + You should search by increasing time ranges. For example: if no issue is found in the last 5 minutes, increase to the last 15 minutes, then 30 minutes, and so on, up to 24 hours. If no issue is found within 24 hours, suggest that the user search via the platform.
            + See @SKIN_ADVISOR_TEMPO.md for more details.
        + Search all logs via Loki.  See @SKIN_ADVISOR_LOKI.md for more details.
    3. Show the user your findings and ask them to provide more information if needed.
    4. Perform any research (via Google, Stack Overflow, etc.) to find the solution if the user asks.
    5. Provide 1-3 solutions to the user with explanations and compare them to help the user choose the best one.
- If the problem caused by the library or framework (incompatible versions, bugs, etc.), you should check the library or framework's issue tracker (e.g., GitHub issues) to see if it's a known issue and if there are any suggested workarounds or fixes.
- If the problem is related to the user's code, always provide a best practice solution, such as using the latest version of the library or framework, following the official documentation, etc.
- The order of searching related issues: Stack Overflow, GitHub issues, official documentation, and then Google.