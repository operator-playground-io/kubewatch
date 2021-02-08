---
title: Configuration Parameters of Kubewatch Helm Chart
description: This tutorial explains about Configuration Parameters
---


### Configuration Parameters of Kubewatch Helm Chart

The Kubewatch Helm Chart can be customized by specifying configurable Parameters while installing the chart.

The detailed description of these lists of configurable parameters for Kubewatch Helm chart with their default values per section/component can be checked at "Parameters" Section of following link:
Kubewatch deployment parameters

### Kubewatch deployment parameters

```
Parameter	Description	Default
replicaCount	Number of Kubewatch replicas to deploy	1
podSecurityContext	Kubewatch pods' Security Context	Check values.yaml file
containerSecurityContext	Kubewatch containers' Security Context	Check values.yaml file
resources.limits	The resources limits for the Kubewatch container	{}
resources.requests	The requested resources for the Kubewatch container	{}
livenessProbe	Liveness probe configuration for Kubewatch	Check values.yaml file
readinessProbe	Readiness probe configuration for Kubewatch	Check values.yaml file
customLivenessProbe	Override default liveness probe	nil
customReadinessProbe	Override default readiness probe	nil
podAffinityPreset	Pod affinity preset. Ignored if affinity is set. Allowed values: soft or hard	""
podAntiAffinityPreset	Pod anti-affinity preset. Ignored if affinity is set. Allowed values: soft or hard	soft
nodeAffinityPreset.type	Node affinity preset type. Ignored if affinity is set. Allowed values: soft or hard	""
nodeAffinityPreset.key	Node label key to match. Ignored if affinity is set.	""
nodeAffinityPreset.values	Node label values to match. Ignored if affinity is set.	[]
affinity	Affinity for pod assignment	{} (evaluated as a template)
nodeSelector	Node labels for pod assignment	{} (evaluated as a template)
tolerations	Tolerations for pod assignment	[] (evaluated as a template)
podLabels	Extra labels for Kubewatch pods	{}
podAnnotations	Annotations for Kubewatch pods	{}
extraVolumeMounts	Optionally specify extra list of additional volumeMounts for Kubewatch container(s)	[]
extraVolumes	Optionally specify extra list of additional volumes for Kubewatch pods	[]
initContainers	Add additional init containers to the Kubewatch pods	{} (evaluated as a template)
sidecars	Add additional sidecar containers to the Kubewatch pods	{} (evaluated as a template)

```

