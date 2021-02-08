---
title: How to Uninstall kubewatch Helm chart 
description: This tutorial explains how to Uninstall Kafka helm chart
---

### Uninstall Kafka Helm Chart

Check your deployed Kafka helm chart:

```execute
 helm list -n kubewatch
```

 Output will be similar:

```output
NAME            NAMESPACE       REVISION        UPDATED                                 STATUS          CHART           APP VERSION
my-release      kubewatch           1               2021-01-06 22:12:07.138654803 -0600 CST deployed        kafka-12.5.0    2.7.0
```

To uninstall the Kafka helm chart, use the helm delete command:

```execute
helm delete my-release -n kubewatch
```

Output:

```output
release "my-release" uninstalled
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

```execute
helm status my-release -n kubewatch
```

Output:

```
Error: release: not found
```

```
