# Kubernetes Deployment Manifest for HomeAssistant

This Kubernetes Deployment manifest is designed for deploying HomeAssistant, a popular home automation platform. Below is an explanation of the manifest and instructions on fields to be modified.

## Manifest Overview

### Purpose
The manifest deploys a single replica of HomeAssistant within the Kubernetes cluster.

### Key Components
- **Container:** Runs the HomeAssistant application.
- **Volumes:** Mounts necessary paths for configuration and timezone settings.
- **Resources:** Specifies resource limits for CPU and memory usage.

## Instructions for Modification

### 1. Application Configuration

- **Image:** Update the `image` field under `containers` with the desired HomeAssistant Docker image.

### 2. Environment Configuration

- **Timezone (TZ):** Set your desired timezone in the `env` section under `containers`.

### 3. Volume Configuration

- **Config Volume:** Update the `persistentVolumeClaim` section under `volumes` with the correct Longhorn persistent volume name.
- It is assumed that a persistent volume and claim is existing. This should be created first so you can set a custom name and retention policy on volumes. 

### 4. Resource Limits

- Adjust the `resources` section under `containers` based on your application's resource requirements.
- Bear in mind that your cluster should also be able to provide this on any given node unless you apply taints to lower resource nodes.

### 5. General Settings

- **Deployment Name and Namespace:** Modify the `name` and `namespace` fields under `metadata` as needed.
