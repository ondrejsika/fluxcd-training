# fluxcd-training

## Course

## Bootstrap using Gitlab

- https://fluxcd.io/flux/installation/bootstrap/gitlab/
- https://gitlab.sikalabs.com/-/user_settings/personal_access_tokens

```bash
export GITLAB_TOKEN=
GITLAB_HOSTNAME=gitlab.sikademo.com
GITLAB_USERNAME=ondrejsika
GITLAB_PROJECT_PATH=ondrejsika/fluxcd-example
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
