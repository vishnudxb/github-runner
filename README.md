# Github self-hosted runner Dockerfile and Kubernetes configuration

This repository contains a Dockerfile that builds a Docker image suitable for running a [self-hosted GitHub runner](https://github.com/vishnudxb/github-runner). A Kubernetes Deployment file is also included that you can use as an example on how to deploy this container to a Kubernetes cluster.

## Building the container

`docker build -t github-runner .`

## Features

* Repository runners
* Organizational runners
* Labels
* Graceful shutdown
* Auto-update after the release of a new version

## Examples

Register a runner to a repository.

```sh
docker run --name github-runner \
     -e GITHUB_OWNER=username-or-organization \
     -e GITHUB_REPOSITORY=my-repository \
     -e GITHUB_PAT=[PAT] \
     gcr.io/$GCP_PROJECT/github-runner
```

Create an organization-wide runner.

```sh
docker run --name github-runner \
    -e GITHUB_OWNER=username-or-organization \
    -e GITHUB_PAT=[PAT] \
    gcr.io/$GCP_PROJECT/github-runner
```

Set labels on the runner.

```sh
docker run --name github-runner \
    -e GITHUB_OWNER=username-or-organization \
    -e GITHUB_REPOSITORY=my-repository \
    -e GITHUB_PAT=[PAT] \
    -e RUNNER_LABELS=comma,separated,labels \
    gcr.io/$GCP_PROJECT/github-runner
```


