## This is fork of [eddiezane/kubectl-gitlab_bootstrap](https://gitlab.com/eddiezane/kubectl-gitlab_bootstrap)

With the release hosted gitlab issue resolved. See [Issue](https://gitlab.com/gitlab-org/gitlab/-/issues/36691)

## kubectl-gitlab_bootstrap

This is a [kubectl plugin](https://kubernetes.io/docs/tasks/extend-kubectl/kubectl-plugins/) that makes adding a Kubernetes cluster to a GitLab project a breeze.

The plugin will use the cluster set as your current context to create a ServiceAccount named `gitlab-admin` with the ClusterRole of `cluster-admin`. It will then use the provided [GitLab personal access token](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html) to bootstrap your cluster into the provided GitLab project. From there it's just two simple clicks to install Helm and the GitLab Runner.

**Note:** Once GitLab implements API support for cluster applications we will be able to install the Runner directly into the cluster as well. Tracked at [this issue](https://gitlab.com/gitlab-org/gitlab-ce/issues/55778).

## Installation

Download the [latest release binary](https://github.com/fastengineer/kubectl-gitlab_bootstrap/files/6007092/kubectl-gitlab_bootstrap.zip) and place in `$PATH` (probably `/usr/local/bin`).

## Usage

```
kubectl gitlab-bootstrap gitlab-project-id
...
Cluster successfully added to project!
To finish up visit: https://gitlab.com/eddiezane/kubectl-gitlab_bootstrap/clusters/68697 and install Helm and Runner.
```

## LICENSE

MIT

## Development

Clone the repository

`go mod download`
`go get github.com/fastengineer/kubectl-gitlab_bootstrap/pkg/cmd`
`go run cmd/kubectl-gitlab_bootstrap.go`
`go build cmd/kubectl-gitlab_bootstrap.go`
`env GOOS=linux go build cmd/kubectl-gitlab_bootstrap.go`

Example usage:

`go run cmd/kubectl-gitlab_bootstrap.go 2 --gitlab-api-token 20chartokenhere16192 --insecure-skip-tls-verify --kubeconfig config`