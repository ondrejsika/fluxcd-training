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

```bash
export GITLAB_TOKEN=
GITLAB_HOSTNAME=gitlab.sikademo.com
GITLAB_USERNAME=ondrejsika
GITLAB_PROJECT_PATH=clusters/sikademo
```

```bash
flux bootstrap gitlab \
  --deploy-token-auth \
  --owner=$GITLAB_USERNAME \
  --repository=example \
  --branch=master \
  --hostname=$GITLAB_HOSTNAME \
  --path=$GITLAB_PROJECT_PATH \
  --personal
```
