<h1 align="center">Kubewatch</h1>


Deploying Bitnami applications as Helm Charts is the easiest way to get started with our applications on Kubernetes. Our application containers are designed to work well together, are extensively documented, and like our other application formats, our containers are continuously updated when new versions are made available.

 Try, test and work with the application in your local environment
 Deploy production-ready applications in your Kubernetes cluster
 
 ### What is Kubewatch?
 
 Kubewatch is a Kubernetes watcher that currently publishes notification to Slack. Run it in your k8s cluster, and you will get event notifications in a slack channel.
 
 
 
 
### Prerequisites
Kubernetes 1.12+

Helm 3.1.0

### Why use Bitnami Images?

Bitnami closely tracks upstream source changes and promptly publishes new versions of this image using our automated systems.

With Bitnami images the latest bug fixes and features are available as soon as possible.

Bitnami containers, virtual machines and cloud images use the same components and configuration approach - making it easy to switch between formats based on your project needs.

All our images are based on minideb a minimalist Debian based container image which gives you a small base container image and the familiarity of a leading Linux distribution.

All Bitnami images available in Docker Hub are signed with Docker Content Trust (DCT). You can use DOCKER_CONTENT_TRUST=1 to verify the integrity of the images.

Bitnami container images are released daily with the latest distribution packages available.

This CVE scan report contains a security report with all open CVEs. To get the list of actionable security issues, find the "latest" tag, click the vulnerability report link under the corresponding "Security scan" field and then select the "Only show fixable" filter on the next page.


#### Configuration


**Environment variables**

The Kubewatch instance can be customized by specifying the below environment variables on the first run:

KW_SLACK_CHANNEL: Slack channel. No defaults.

KW_SLACK_TOKEN: Slack token. No defaults.

KW_HIPCHAT_ROOM: HipChat room. No defaults.

KW_HIPCHAT_TOKEN: HipChat token. No defaults.

KW_HIPCHAT_URL: HipChat URL. No defaults.

KW_MATTERMOST_CHANNEL: Mattermost channel. No defaults.

KW_MATTERMOST_URL: Mattermost URL. No defaults.

KW_MATTERMOST_USERNAME: Mattermost username. No defaults.

KW_FLOCK_URL: Flock URL. No defaults.

KW_WEBHOOK_URL: WEBHOOK URL. No defaults.


# Objective of tutorial

In this tutorial,we are going to cover following topics:

- What is Kubewtach ?

- how to use kubewatch and to integarte with Slack channel?

- How to Install Kubewatch Bitnami Helm Chart and verify its successful installation?

- Verify status of pods and services. 

- Uninstall Kafka Helm Chart and release resources.





