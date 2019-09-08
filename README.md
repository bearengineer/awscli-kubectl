# awscli-kubectl

# What is awscli?

> Awscli is the Amazon web services command line interface.

[Overview of awscli](https://docs.aws.amazon.com/cli/index.html)

# What is Kubectl?

> Kubectl is the Kubernetes command line interface.

[Overview of kubectl](https://kubernetes.io/docs/reference/kubectl/overview/)

# TL;DR;

```bash
$ docker run -ti --rm bearengineer/awscli-kubectl
```

```bash
$ docker run -ti -e 'AWS_ACCESS_KEY_ID=********************' -e 'AWS_SECRET_ACCESS_KEY=****************************************' -v '/Users/bearengineer/.kube:/root/.kube' --rm bearengineer/awscli-kubectl kubectl get pods --all-namespaces
```

```bash
$ docker run -ti -v '/Users/bearengineer/.aws:/root/.aws' -v '/Users/bearengineer/.kube:/root/.kube' --rm bearengineer/awscli-kubectl kubectl get pods --all-namespaces
```


# Supported tags and respective `Dockerfile` links

* [`awscli-1.16-kubectl-1.15`, `latest` (Dockerfile)](https://github.com/bearengineer/awscli-kubectl/blob/Dockerfile)

Subscribe to project updates by watching the [bearengineer/awscli-kubectl GitHub repo](https://github.com/bearengineer/awscli-kubectl).

# Get this image

The recommended way to get the Bear Engineer awscli-kubectl Docker Image is to pull the prebuilt image from the [Docker Hub Registry](https://hub.docker.com/r/bearengineer/awscli-kubectl).

```bash
$ docker pull bearengineer/awscli-kubectl:latest
```

To use a specific version, you can pull a versioned tag. You can view the [list of available versions](https://hub.docker.com/r/bearengineer/awscli-kubectl/tags/) in the Docker Hub Registry.

```bash
$ docker pull bearengineer/awscli-kubectl:[TAG]
```

If you wish, you can also build the image yourself.

```bash
$ docker build -t bearengineer/awscli-kubectl:latest 'https://github.com/bearengineer/awscli-kubectl.git#master'
```

# Configuration

## Running commands

To run commands inside this container you can use `docker run`, for example to execute `kubectl --version` you can follow the example below:

```bash
$ docker run --rm --name kubectl bearengineer/awscli-kubectl:latest -- kubectl version
```

Consult the [Kubectl Reference Documentation](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) or the [AWS CLI Reference Documentation](https://docs.aws.amazon.com/cli/index.html) to find the completed list of commands available.

## AWS Credentials

AWS credentials can either be passed by environment variables, or by mounting a volume with aws credentials file under `/root/.aws`.

### Environment variables

```bash
$ docker run -ti -e 'AWS_ACCESS_KEY_ID=********************' -e 'AWS_SECRET_ACCESS_KEY=****************************************' --rm bearengineer/awscli-kubectl aws s3 ls
```

### AWS directory

```bash
docker run -ti -v '/Users/bearengineer/.aws:/root/.aws' --rm bearengineer/awscli-kubectl aws s3
```

## Kubectl credentials

Kubectl credentials can be passed by mounting a volume with the kubeconfig under `/root/.kube`.

### Kubectl directory

```bash
docker run -ti -v '/Users/bearengineer/.kube:/root/.kube' --rm bearengineer/awscli-kubectl kubectl get pods
```

# Contributing

We'd love for you to contribute to this container. You can request new features by creating an [issue](https://github.com/bearengineer/awscli-kubectl/issues), or submit a [pull request](https://github.com/bearengineer/awscli-kubectl/pulls) with your contribution.

# Issues

If you encountered a problem running this container, you can file an [issue](https://github.com/bearengineer/awscli-kubectl/issues). For us to provide better support, be sure to include the following information in your issue:

- Host OS and version
- Docker version (`docker version`)
- Output of `docker info`
- Version of this container
- The command you used to run the container, and any relevant output you saw (masking any sensitive information)

# License

Copyright (c) 2019 Bear Engineer. All rights reserved.

This work is licensed under the terms of the MIT license.  
For a copy, see <https://opensource.org/licenses/MIT>.

