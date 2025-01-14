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

## Training Sessions

### 2024-12-02 T-Mobile

- https://github.com/sika-training-examples/2024-12-02_fluxcd-example
- https://github.com/sika-training-examples/2024-12-03_t-mobile-fluxcd-example
