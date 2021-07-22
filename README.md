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

# Kustomize Structure

### Environments
Overlays Instances and can provide additional environment-specific kustomize configuration (i.e. OpenShift)

### Instances
Overlays base manifests and can provide additional kustomize configuration (i.e. patchesStrategicMerge, namespace, resource, etc.)

### Manifests
base manifests are organized here
