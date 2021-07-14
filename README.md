# solo-testbed-apps

### Frontend
- bookinfo-v1 (only has reviews-v2)
- bookinfo-beta (has reviews-v1 and reviews-v3)
- httpbin

### Platform
- argocd
- gloo-edge-oss-helm
- istio/profiles
    - default
    - demo
    - openshift
    - workshop

# Kustomize Structure

Instances - Overlays base manifests and can provide additional kustomize configuration (i.e. patchesStrategicMerge, namespace, resource, etc.)
Manifests - base manifests are organized here
