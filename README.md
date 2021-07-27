# solo-testbed-apps

### Frontend
- bookinfo-v1 (only has reviews-v2)
- bookinfo-beta (has reviews-v1 and reviews-v3)
- httpbin
- sleep
- web-api

### Platform
- argocd
- gloo-edge-oss helm chart
- istio/profiles
    - default
    - demo
    - openshift
    - workshop
    - empty
    - istioinaction
- observability
    - kube-prometheus (Prometheus, AlertManager, Grafana) helm chart
    - kiali (helm)
    - istio dashboards and service monitors
- grafana helm chart
- gloo-mesh

# Kustomize structure

### Environments
Overlays Instances and creates a logical grouping using the app-of-apps pattern. Provides additional environment-specific kustomize configuration for particular environments (i.e. OpenShift) or a setup (i.e. demo, workshop, version-specific)

### Instances
Overlays base manifests and can provide additional kustomize configuration (i.e. patchesStrategicMerge, namespace, resource, etc). Useful for creating individual instances of a particular app before grouping them into environments.

### Manifests
base manifests are organized here. All overlay layers should inherit their configuration from the base manifests. Leave out instance-specific or environment-specific config out of the base manifests as these will be added/patched in other overlays.

# argo-apps structure
Following Kustomize structure above

### Environments
Environments - Argocd apps set up as a logical grouping (function or environment-specific) using the argocd app-of-apps pattern
    - meta - holds the app-of-app for the active directory
    - active - all applications pushed in this directory will be deployed
    - non-active - holding directory for non-active and test instances

### Instances
Instances - Individual apps that have been created as an argo Application CRD. When creating an Environment, copy these individual instances into the the active/non-active directories as required
    - Frontend - generally customer facing apps that can be interacted with or used for demonstrations
    - Platform - generally backend apps that support platform functions (i.e. operators, observability, pub/sub, serverless)