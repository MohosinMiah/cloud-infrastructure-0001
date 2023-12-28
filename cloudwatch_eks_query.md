Sure, CloudWatch Logs Insights allows you to run advanced queries on your logs. Here are 100 example queries that you can use to analyze Amazon EKS deployment services and pods:

1. **List all log groups:**
   ```
   fields @log_group
   | sort @log_group
   ```

2. **Show the latest logs for a specific log group:**
   ```
   fields @timestamp, @message
   | filter @log_group = 'your-log-group-name'
   | sort @timestamp desc
   | limit 20
   ```

3. **Filter logs by a specific keyword:**
   ```
   fields @timestamp, @message
   | filter @message like /your-keyword/
   | limit 20
   ```

4. **Count log entries by log level:**
   ```
   fields @log_level
   | stats count() by @log_level
   ```

5. **List all unique log levels:**
   ```
   fields @log_level
   | stats count() by @log_level
   ```

6. **Show logs for a specific time range:**
   ```
   fields @timestamp, @message
   | filter @timestamp >= '2023-01-01T00:00:00Z' and @timestamp <= '2023-01-31T23:59:59Z'
   | limit 20
   ```

7. **List all log streams within a log group:**
   ```
   fields @log_stream
   | filter @log_group = 'your-log-group-name'
   | sort @log_stream
   ```

8. **Count log entries by log stream:**
   ```
   fields @log_stream
   | stats count() by @log_stream
   ```

9. **Show logs for a specific pod:**
   ```
   fields @timestamp, @message
   | filter @log_stream = 'your-pod-name'
   | sort @timestamp desc
   | limit 20
   ```

10. **List all unique Kubernetes namespaces:**
    ```
    fields kubernetes.namespace_name
    | stats count() by kubernetes.namespace_name
    ```

11. **Show logs for a specific namespace:**
    ```
    fields @timestamp, @message
    | filter kubernetes.namespace_name = 'your-namespace'
    | sort @timestamp desc
    | limit 20
    ```

12. **Count logs by container name:**
    ```
    fields kubernetes.container_name
    | stats count() by kubernetes.container_name
    ```

13. **Show logs for a specific container:**
    ```
    fields @timestamp, @message
    | filter kubernetes.container_name = 'your-container'
    | sort @timestamp desc
    | limit 20
    ```

14. **List all unique services:**
    ```
    fields kubernetes.labels.app
    | stats count() by kubernetes.labels.app
    ```

15. **Show logs for a specific service:**
    ```
    fields @timestamp, @message
    | filter kubernetes.labels.app = 'your-service'
    | sort @timestamp desc
    | limit 20
    ```

16. **Count logs by log source:**
    ```
    fields @log_stream
    | stats count() by @log_stream
    ```

17. **List all unique node names:**
    ```
    fields kubernetes.node_name
    | stats count() by kubernetes.node_name
    ```

18. **Show logs for a specific node:**
    ```
    fields @timestamp, @message
    | filter kubernetes.node_name = 'your-node'
    | sort @timestamp desc
    | limit 20
    ```

19. **Count logs by EKS cluster name:**
    ```
    fields eks.cluster_name
    | stats count() by eks.cluster_name
    ```

20. **Show logs for a specific EKS cluster:**
    ```
    fields @timestamp, @message
    | filter eks.cluster_name = 'your-cluster'
    | sort @timestamp desc
    | limit 20
    ```

21. **Count logs by pod phase:**
    ```
    fields kubernetes.pod.phase
    | stats count() by kubernetes.pod.phase
    ```

22. **Show logs for a specific pod phase:**
    ```
    fields @timestamp, @message
    | filter kubernetes.pod.phase = 'your-phase'
    | sort @timestamp desc
    | limit 20
    ```

23. **Count logs by pod status:**
    ```
    fields kubernetes.pod.status.phase
    | stats count() by kubernetes.pod.status.phase
    ```

24. **Show logs for a specific pod status:**
    ```
    fields @timestamp, @message
    | filter kubernetes.pod.status.phase = 'your-status'
    | sort @timestamp desc
    | limit 20
    ```

25. **Count logs by deployment name:**
    ```
    fields kubernetes.deployment.name
    | stats count() by kubernetes.deployment.name
    ```

26. **Show logs for a specific deployment:**
    ```
    fields @timestamp, @message
    | filter kubernetes.deployment.name = 'your-deployment'
    | sort @timestamp desc
    | limit 20
    ```

27. **Count logs by replica set name:**
    ```
    fields kubernetes.replicaset.name
    | stats count() by kubernetes.replicaset.name
    ```

28. **Show logs for a specific replica set:**
    ```
    fields @timestamp, @message
    | filter kubernetes.replicaset.name = 'your-replicaset'
    | sort @timestamp desc
    | limit 20
    ```

29. **Count logs by daemon set name:**
    ```
    fields kubernetes.daemonset.name
    | stats count() by kubernetes.daemonset.name
    ```

30. **Show logs for a specific daemon set:**
    ```
    fields @timestamp, @message
    | filter kubernetes.daemonset.name = 'your-daemonset'
    | sort @timestamp desc
    | limit 20
    ```

31. **Count logs by stateful set name:**
    ```
    fields kubernetes.statefulset.name
    | stats count() by kubernetes.statefulset.name
    ```

32. **Show logs for a specific stateful set:**
    ```
    fields @timestamp, @message
    | filter kubernetes.statefulset.name = 'your-statefulset'
    | sort @timestamp desc
    | limit 20
    ```

33. **Count logs by service name:**
    ```
    fields kubernetes.service.name
    | stats count() by kubernetes.service.name
    ```

34. **Show logs for a specific service:**
    ```
    fields @timestamp, @message
    | filter kubernetes.service.name = 'your-service'
    | sort @timestamp desc
    | limit 20
    ```

35. **Count logs by namespace, deployment, and container:**
    ```
    fields kubernetes.namespace_name, kubernetes.deployment.name, kubernetes.container_name
    | stats count() by kubernetes.namespace_name, kubernetes.deployment.name, kubernetes.container_name


    ```

36. **Show logs for a specific namespace, deployment, and container:**
    ```
    fields @timestamp, @message
    | filter kubernetes.namespace_name = 'your-namespace' and kubernetes.deployment.name = 'your-deployment' and kubernetes.container_name = 'your-container'
    | sort @timestamp desc
    | limit 20
    ```

37. **Count logs by namespace, pod, and container:**
    ```
    fields kubernetes.namespace_name, kubernetes.pod.name, kubernetes.container_name
    | stats count() by kubernetes.namespace_name, kubernetes.pod.name, kubernetes.container_name
    ```

38. **Show logs for a specific namespace, pod, and container:**
    ```
    fields @timestamp, @message
    | filter kubernetes.namespace_name = 'your-namespace' and kubernetes.pod.name = 'your-pod' and kubernetes.container_name = 'your-container'
    | sort @timestamp desc
    | limit 20
    ```

39. **Count logs by namespace, service, and container:**
    ```
    fields kubernetes.namespace_name, kubernetes.service.name, kubernetes.container_name
    | stats count() by kubernetes.namespace_name, kubernetes.service.name, kubernetes.container_name
    ```

40. **Show logs for a specific namespace, service, and container:**
    ```
    fields @timestamp, @message
    | filter kubernetes.namespace_name = 'your-namespace' and kubernetes.service.name = 'your-service' and kubernetes.container_name = 'your-container'
    | sort @timestamp desc
    | limit 20
    ```

41. **Count logs by namespace, node, and container:**
    ```
    fields kubernetes.namespace_name, kubernetes.node_name, kubernetes.container_name
    | stats count() by kubernetes.namespace_name, kubernetes.node_name, kubernetes.container_name
    ```

42. **Show logs for a specific namespace, node, and container:**
    ```
    fields @timestamp, @message
    | filter kubernetes.namespace_name = 'your-namespace' and kubernetes.node_name = 'your-node' and kubernetes.container_name = 'your-container'
    | sort @timestamp desc
    | limit 20
    ```

43. **Count logs by namespace, pod phase, and container:**
    ```
    fields kubernetes.namespace_name, kubernetes.pod.phase, kubernetes.container_name
    | stats count() by kubernetes.namespace_name, kubernetes.pod.phase, kubernetes.container_name
    ```

44. **Show logs for a specific namespace, pod phase, and container:**
    ```
    fields @timestamp, @message
    | filter kubernetes.namespace_name = 'your-namespace' and kubernetes.pod.phase = 'your-phase' and kubernetes.container_name = 'your-container'
    | sort @timestamp desc
    | limit 20
    ```

45. **Count logs by namespace, pod status, and container:**
    ```
    fields kubernetes.namespace_name, kubernetes.pod.status.phase, kubernetes.container_name
    | stats count() by kubernetes.namespace_name, kubernetes.pod.status.phase, kubernetes.container_name
    ```

46. **Show logs for a specific namespace, pod status, and container:**
    ```
    fields @timestamp, @message
    | filter kubernetes.namespace_name = 'your-namespace' and kubernetes.pod.status.phase = 'your-status' and kubernetes.container_name = 'your-container'
    | sort @timestamp desc
    | limit 20
    ```

47. **Count logs by namespace, deployment, pod, and container:**
    ```
    fields kubernetes.namespace_name, kubernetes.deployment.name, kubernetes.pod.name, kubernetes.container_name
    | stats count() by kubernetes.namespace_name, kubernetes.deployment.name, kubernetes.pod.name, kubernetes.container_name
    ```

48. **Show logs for a specific namespace, deployment, pod, and container:**
    ```
    fields @timestamp, @message
    | filter kubernetes.namespace_name = 'your-namespace' and kubernetes.deployment.name = 'your-deployment' and kubernetes.pod.name = 'your-pod' and kubernetes.container_name = 'your-container'
    | sort @timestamp desc
    | limit 20
    ```

49. **Count logs by namespace, deployment, service, and container:**
    ```
    fields kubernetes.namespace_name, kubernetes.deployment.name, kubernetes.service.name, kubernetes.container_name
    | stats count() by kubernetes.namespace_name, kubernetes.deployment.name, kubernetes.service.name, kubernetes.container_name
    ```

50. **Show logs for a specific namespace, deployment, service, and container:**
    ```
    fields @timestamp, @message
    | filter kubernetes.namespace_name = 'your-namespace' and kubernetes.deployment.name = 'your-deployment' and kubernetes.service.name = 'your-service' and kubernetes.container_name = 'your-container'
    | sort @timestamp desc
    | limit 20
    ```

51. **Count logs by namespace, deployment, node, and container:**
    ```
    fields kubernetes.namespace_name, kubernetes.deployment.name, kubernetes.node_name, kubernetes.container_name
    | stats count() by kubernetes.namespace_name, kubernetes.deployment.name, kubernetes.node_name, kubernetes.container_name
    ```

52. **Show logs for a specific namespace, deployment, node, and container:**
    ```
    fields @timestamp, @message
    | filter kubernetes.namespace_name = 'your-namespace' and kubernetes.deployment.name = 'your-deployment' and kubernetes.node_name = 'your-node' and kubernetes.container_name = 'your-container'
    | sort @timestamp desc
    | limit 20
    ```

53. **Count logs by namespace, deployment, pod phase, and container:**
    ```
    fields kubernetes.namespace_name, kubernetes.deployment.name, kubernetes.pod.phase, kubernetes.container_name
    | stats count() by kubernetes.namespace_name, kubernetes.deployment.name, kubernetes.pod.phase, kubernetes.container_name
    ```

54. **Show logs for a specific namespace, deployment, pod phase, and container:**
    ```
    fields @timestamp, @message
    | filter kubernetes.namespace_name = 'your-namespace' and kubernetes.deployment.name = 'your-deployment' and kubernetes.pod.phase = 'your-phase' and kubernetes.container_name = 'your-container'
    | sort @timestamp desc
    | limit 20
    ```

55. **Count logs by namespace, deployment, pod status, and container:**
    ```
    fields kubernetes.namespace_name, kubernetes.deployment.name, kubernetes.pod.status.phase, kubernetes.container_name
    | stats count() by kubernetes.namespace_name, kubernetes.deployment.name, kubernetes.pod.status.phase, kubernetes.container_name
    ```

56. **Show logs for a specific namespace, deployment, pod status, and container:**
    ```
    fields @timestamp, @message
    | filter kubernetes.namespace_name = 'your-namespace' and kubernetes.deployment.name = 'your-deployment
