# fluxcd-training

## Course

## Install the Flux CLI

- https://fluxcd.io/flux/installation/#install-the-flux-cli

Mac

```bash
brew install fluxcd/tap/flux
```

or upgrade

```bash
brew upgrade fluxcd/tap/flux
```

Linux

```bash
curl -s https://fluxcd.io/install.sh | sudo bash
```

Autocomplete

```bash
. <(flux completion bash)
```

ZSH

```zsh
. <(flux completion zsh)
```

## Bootstrap using Gitlab

- https://fluxcd.io/flux/installation/bootstrap/gitlab/
- https://gitlab.sikademo.com/-/user_settings/personal_access_tokens

Create in group

```bash
export GITLAB_TOKEN=
GITLAB_HOSTNAME=gitlab.sikademo.com
GITLAB_OWNER=ondrejsika
GITLAB_REPOSIOTRY=example
GITLAB_PROJECT_PATH=clusters/sikademo
```

```bash
flux bootstrap gitlab \
  --deploy-token-auth \
  --owner=$GITLAB_OWNER \
  --repository=$GITLAB_REPOSIOTRY \
  --branch=master \
  --hostname=$GITLAB_HOSTNAME \
  --path=$GITLAB_PROJECT_PATH
```

or personal

```bash
export GITLAB_TOKEN=
GITLAB_HOSTNAME=gitlab.sikademo.com
GITLAB_OWNER=ondrejsika
GITLAB_REPOSIOTRY=example
GITLAB_PROJECT_PATH=clusters/sikademo
```

```bash
flux bootstrap gitlab \
  --deploy-token-auth \
  --owner=$GITLAB_OWNER \
  --repository=$GITLAB_REPOSIOTRY \
  --branch=master \
  --hostname=$GITLAB_HOSTNAME \
  --path=$GITLAB_PROJECT_PATH \
  --personal # required for personal project
```

## Helm Repoisotry

```bash
apiVersion: source.toolkit.fluxcd.io/v1beta2
kind: HelmRepository
metadata:
  name: sikalabs
  namespace: flux-system
spec:
  url: https://helm.sikalabs.io
  interval: 1m
```

## Helm Repoisotry from Artifactory

```bash
apiVersion: source.toolkit.fluxcd.io/v1beta2
kind: HelmRepository
metadata:
  name: artifactory
  namespace: flux-system
spec:
  url: https://artifactory.sikademo.com/artifactory/api/helm/hello-world-helm
  interval: 1m
  secretRef:
    name: artifactory-credentials
---
apiVersion: v1
kind: Secret
metadata:
  name: artifactory-credentials
  namespace: flux-system
type: Opaque
stringData:
  username: admin
  password: cmVmdGtuOjAxOjE3NjQ3MDc4Mjk6dFZKWXpZeEN4VTM0Rm9CWVNqQ2tBMjI4Y2RO
```

## Helm Release

```bash
apiVersion: helm.toolkit.fluxcd.io/v2beta1
kind: HelmRelease
metadata:
  name: hello-world
  namespace: default
spec:
  releaseName: hello-world
  chart:
    spec:
      chart: hello-world
      sourceRef:
        kind: HelmRepository
        name: sikalabs
        namespace: flux-system
      version: 0.10.0
  interval: 1m
  values:
    host: hello-world.k8s.sikademo.com
    replicas: 2
```

## Training Sessions

### 2024-12-02 T-Mobile

- https://github.com/sika-training-examples/2024-12-02_fluxcd-example
- https://github.com/sika-training-examples/2024-12-03_t-mobile-fluxcd-example
